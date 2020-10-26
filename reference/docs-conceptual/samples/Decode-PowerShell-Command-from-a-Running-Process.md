---
ms.date: 11/13/2018
keywords: powershell,cmdlet
title: 从正在运行的进程解码 PowerShell 命令
author: randomnote1
description: 本文演示了如何解码 PowerShell 进程当前运行的脚本块。
ms.openlocfilehash: 95b4b806665bf8137712ebb183329039bc1e1deb
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500481"
---
# <a name="decode-a-powershell-command-from-a-running-process"></a><span data-ttu-id="88938-104">从正在运行的进程解码 PowerShell 命令</span><span class="sxs-lookup"><span data-stu-id="88938-104">Decode a PowerShell command from a running process</span></span>

<span data-ttu-id="88938-105">有时，你可能有一个正在运行的 PowerShell 进程占用了大量资源。</span><span class="sxs-lookup"><span data-stu-id="88938-105">At times, you may have a PowerShell process running that is taking up a large amount of resources.</span></span>
<span data-ttu-id="88938-106">此进程可以在[任务计划程序][]作业或 [SQL Server 代理][]作业的上下文中运行。</span><span class="sxs-lookup"><span data-stu-id="88938-106">This process could be running in the context of a [Task Scheduler][] job or a [SQL Server Agent][] job.</span></span> <span data-ttu-id="88938-107">在运行多个 PowerShell 进程的位置，很难知道哪个进程表示问题。</span><span class="sxs-lookup"><span data-stu-id="88938-107">Where there are multiple PowerShell processes running, it can be difficult to know which process represents the problem.</span></span> <span data-ttu-id="88938-108">本文演示了如何解码 PowerShell 进程当前运行的脚本块。</span><span class="sxs-lookup"><span data-stu-id="88938-108">This article shows how to decode a script block that a PowerShell process is currently running.</span></span>

## <a name="create-a-long-running-process"></a><span data-ttu-id="88938-109">创建一个长时间运行的进程</span><span class="sxs-lookup"><span data-stu-id="88938-109">Create a long running process</span></span>

<span data-ttu-id="88938-110">要演示此场景，请打开一个新的 PowerShell 窗口并运行以下代码。</span><span class="sxs-lookup"><span data-stu-id="88938-110">To demonstrate this scenario, open a new PowerShell window and run the following code.</span></span> <span data-ttu-id="88938-111">它执行一个 PowerShell 命令，每分钟输出一个数字，持续 10 分钟。</span><span class="sxs-lookup"><span data-stu-id="88938-111">It executes a PowerShell command that outputs a number every minute for 10 minutes.</span></span>

```powershell
powershell.exe -Command {
    $i = 1
    while ( $i -le 10 )
    {
        Write-Output -InputObject $i
        Start-Sleep -Seconds 60
        $i++
    }
}
```

## <a name="view-the-process"></a><span data-ttu-id="88938-112">查看进程</span><span class="sxs-lookup"><span data-stu-id="88938-112">View the process</span></span>

<span data-ttu-id="88938-113">PowerShell 正在执行的命令正文存储在  属性中。</span><span class="sxs-lookup"><span data-stu-id="88938-113">The body of the command which PowerShell is executing is stored in the **CommandLine** property of the [Win32_Process][] class.</span></span> <span data-ttu-id="88938-114">如果命令为编码命令， **CommandLine** 属性将包含字符串“EncodedCommand”。</span><span class="sxs-lookup"><span data-stu-id="88938-114">If the command is an encoded command, the **CommandLine** property contains the string "EncodedCommand".</span></span> <span data-ttu-id="88938-115">使用此信息，可以通过以下进程取消对编码命令的模糊处理。</span><span class="sxs-lookup"><span data-stu-id="88938-115">Using this information, the encoded command can be de-obfuscated via the following process.</span></span>

<span data-ttu-id="88938-116">以管理员身份启动 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="88938-116">Start PowerShell as Administrator.</span></span> <span data-ttu-id="88938-117">以管理员身份运行 PowerShell 至关重要，否则在查询正在运行的进程时不会返回任何结果。</span><span class="sxs-lookup"><span data-stu-id="88938-117">It is vital that PowerShell is running as administrator, otherwise no results are returned when querying the running processes.</span></span>

<span data-ttu-id="88938-118">执行以下命令以获取所有具有编码命令的 PowerShell 进程：</span><span class="sxs-lookup"><span data-stu-id="88938-118">Execute the following command to get all of the PowerShell processes that have an encoded command:</span></span>

```powershell
$powerShellProcesses = Get-CimInstance -ClassName Win32_Process -Filter 'CommandLine LIKE "%EncodedCommand%"'
```

<span data-ttu-id="88938-119">下面的命令创建一个自定义 PowerShell 对象，其中包含进程 ID 和编码命令。</span><span class="sxs-lookup"><span data-stu-id="88938-119">The following command creates a custom PowerShell object that contains the process ID and the encoded command.</span></span>

```powershell
$commandDetails = $powerShellProcesses | Select-Object -Property ProcessId,
@{
    name       = 'EncodedCommand'
    expression = {
        if ( $_.CommandLine -match 'encodedCommand (.*) -inputFormat' )
        {
            return $matches[1]
        }
    }
}
```

<span data-ttu-id="88938-120">现在可以解码编码命令。</span><span class="sxs-lookup"><span data-stu-id="88938-120">Now the encoded command can be decoded.</span></span> <span data-ttu-id="88938-121">下面的代码片段循环访问命令详细信息对象、解码编码命令，并将解码后的命令添加回该对象，以便进一步研究。</span><span class="sxs-lookup"><span data-stu-id="88938-121">The following snippet iterates over the command details object, decodes the encoded command, and adds the decoded command back to the object for further investigation.</span></span>

```powershell
$commandDetails | ForEach-Object -Process {
    # Get the current process
    $currentProcess = $_

    # Convert the Base 64 string to a Byte Array
    $commandBytes = [System.Convert]::FromBase64String($currentProcess.EncodedCommand)

    # Convert the Byte Array to a string
    $decodedCommand = [System.Text.Encoding]::Unicode.GetString($commandBytes)

    # Add the decoded command back to the object
    $commandDetails |
        Where-Object -FilterScript { $_.ProcessId -eq $_.ProcessId } |
        Add-Member -MemberType NoteProperty -Name DecodedCommand -Value $decodedCommand
}
$commandDetails[0]
```

<span data-ttu-id="88938-122">现在可以通过选择解码后的命令属性来查看已解码的命令。</span><span class="sxs-lookup"><span data-stu-id="88938-122">The decoded command can now be reviewed by selecting the decoded command property.</span></span>

```Output
ProcessId      : 8752
EncodedCommand : IAAKAAoACgAgAAoAIAAgACAAIAAkAGkAIAA9ACAAMQAgAAoACgAKACAACgAgACAAIAAgAHcAaABpAGwAZQAgACgAIAAkAGkAIAAtAG
                 wAZQAgADEAMAAgACkAIAAKAAoACgAgAAoAIAAgACAAIAB7ACAACgAKAAoAIAAKACAAIAAgACAAIAAgACAAIABXAHIAaQB0AGUALQBP
                 AHUAdABwAHUAdAAgAC0ASQBuAHAAdQB0AE8AYgBqAGUAYwB0ACAAJABpACAACgAKAAoAIAAKACAAIAAgACAAIAAgACAAIABTAHQAYQ
                 ByAHQALQBTAGwAZQBlAHAAIAAtAFMAZQBjAG8AbgBkAHMAIAA2ADAAIAAKAAoACgAgAAoAIAAgACAAIAAgACAAIAAgACQAaQArACsA
                 IAAKAAoACgAgAAoAIAAgACAAIAB9ACAACgAKAAoAIAAKAA==
DecodedCommand :
                     $i = 1

                     while ( $i -le 10 )

                     {

                         Write-Output -InputObject $i

                         Start-Sleep -Seconds 60

                         $i++

                     }
```

[任务计划程序]: /windows/desktop/TaskSchd/task-scheduler-start-page
[Task Scheduler]: /windows/desktop/TaskSchd/task-scheduler-start-page
[SQL Server 代理]: /sql/ssms/agent/sql-server-agent
[SQL Server Agent]: /sql/ssms/agent/sql-server-agent
[Win32_Process]: /windows/desktop/CIMWin32Prov/win32-process
