---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 使用 Process Cmdlet 管理进程
description: PowerShell 提供了多个 cmdlet，可帮助管理本地和远程计算机上的进程。
ms.openlocfilehash: 977a3459eeac22536341753ccd59357d718745f2
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500430"
---
# <a name="managing-processes-with-process-cmdlets"></a><span data-ttu-id="2227f-104">使用 Process Cmdlet 管理进程</span><span class="sxs-lookup"><span data-stu-id="2227f-104">Managing Processes with Process Cmdlets</span></span>

<span data-ttu-id="2227f-105">可以在 Windows PowerShell 中使用 Process cmdlet 来管理 Windows PowerShell 中的本地和远程进程。</span><span class="sxs-lookup"><span data-stu-id="2227f-105">You can use the Process cmdlets in Windows PowerShell to manage local and remote processes in Windows PowerShell.</span></span>

## <a name="getting-processes-get-process"></a><span data-ttu-id="2227f-106">获取进程 (Get-Process)</span><span class="sxs-lookup"><span data-stu-id="2227f-106">Getting Processes (Get-Process)</span></span>

<span data-ttu-id="2227f-107">若要获取在本地计算机上运行的进程，请运行不具有参数的 **Get-Process** 。</span><span class="sxs-lookup"><span data-stu-id="2227f-107">To get the processes running on the local computer, run a **Get-Process** with no parameters.</span></span>

<span data-ttu-id="2227f-108">你可以通过指定其进程名称或进程 ID 来获取特定进程。</span><span class="sxs-lookup"><span data-stu-id="2227f-108">You can get particular processes by specifying their process names or process IDs.</span></span> <span data-ttu-id="2227f-109">以下命令将获取空闲进程：</span><span class="sxs-lookup"><span data-stu-id="2227f-109">The following command gets the Idle process:</span></span>

```
PS> Get-Process -id 0

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
      0       0        0         16     0               0 Idle
```

<span data-ttu-id="2227f-110">尽管某些情况下 cmdlet 不会返回任何数据很正常，但当你按其 ProcessId 指定一个进程时，如果未找到任何匹配项， **Get-Process** 将生成一个错误，因为通常的目的是检索一个已知的正在运行的进程。</span><span class="sxs-lookup"><span data-stu-id="2227f-110">Although it is normal for cmdlets to return no data in some situations, when you specify a process by its ProcessId, **Get-Process** generates an error if it finds no matches, because the usual intent is to retrieve a known running process.</span></span> <span data-ttu-id="2227f-111">如果按该 ID 找不到进程，则很可能该 ID 不正确或相关进程已退出：</span><span class="sxs-lookup"><span data-stu-id="2227f-111">If there is no process with that Id, it is likely that the Id is incorrect or that the process of interest has already exited:</span></span>

```
PS> Get-Process -Id 99

Get-Process : No process with process ID 99 was found.
At line:1 char:12
+ Get-Process  <<<< -Id 99
```

<span data-ttu-id="2227f-112">你可以使用 Get-Process cmdlet 的 Name 参数来基于进程名称指定进程的子集。</span><span class="sxs-lookup"><span data-stu-id="2227f-112">You can use the Name parameter of the Get-Process cmdlet to specify a subset of processes based on the process name.</span></span> <span data-ttu-id="2227f-113">Name 参数可以采用多个名称（在列表中以逗号分隔），并且支持使用通配符，因此，你可以键入名称模式。</span><span class="sxs-lookup"><span data-stu-id="2227f-113">The Name parameter can take multiple names in a comma-separated list and it supports the use of wildcards, so you can type name patterns.</span></span>

<span data-ttu-id="2227f-114">例如，以下命令将获取名称以“ex”开头的进程。</span><span class="sxs-lookup"><span data-stu-id="2227f-114">For example, the following command gets process whose names begin with "ex."</span></span>

```
PS> Get-Process -Name ex*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    234       7     5572      12484   134     2.98   1684 EXCEL
    555      15    34500      12384   134   105.25    728 explorer
```

<span data-ttu-id="2227f-115">由于 .NET System.Diagnostics.Process 类是 Windows PowerShell 进程的基础，因此它遵循 System.Diagnostics.Process 使用的某些约定。</span><span class="sxs-lookup"><span data-stu-id="2227f-115">Because the .NET System.Diagnostics.Process class is the foundation for Windows PowerShell processes, it follows some of the conventions used by System.Diagnostics.Process.</span></span> <span data-ttu-id="2227f-116">其中一个约定是可执行文件的进程名从不在可执行文件名的末尾包含“.exe”。</span><span class="sxs-lookup"><span data-stu-id="2227f-116">One of those conventions is that the process name for an executable never includes the ".exe" at the end of the executable name.</span></span>

<span data-ttu-id="2227f-117">**Get-Process** 还接受 Name 参数的多个值。</span><span class="sxs-lookup"><span data-stu-id="2227f-117">**Get-Process** also accepts multiple values for the Name parameter.</span></span>

```
PS> Get-Process -Name exp*,power*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    540      15    35172      48148   141    88.44    408 explorer
    605       9    30668      29800   155     7.11   3052 powershell
```

<span data-ttu-id="2227f-118">可以使用 Get-Process 的 ComputerName 参数获取远程计算机上的进程。</span><span class="sxs-lookup"><span data-stu-id="2227f-118">You can use the ComputerName parameter of Get-Process to get processes on remote computers.</span></span> <span data-ttu-id="2227f-119">例如，以下命令将获取本地计算机（表示为“localhost”）和两台远程计算机上的 PowerShell 进程。</span><span class="sxs-lookup"><span data-stu-id="2227f-119">For example, the following command gets the PowerShell processes on the local computer (represented by "localhost") and on two remote computers.</span></span>

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server02

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    258       8    29772      38636   130            3700 powershell
    398      24    75988      76800   572            5816 powershell
    605       9    30668      29800   155     7.11   3052 powershell
```

<span data-ttu-id="2227f-120">计算机名在此显示中不可见，但是它们存储在 Get-Process 返回的进程对象的 MachineName 属性中。</span><span class="sxs-lookup"><span data-stu-id="2227f-120">The computer names are not evident in this display, but they are stored in the MachineName property of the process objects that Get-Process returns.</span></span> <span data-ttu-id="2227f-121">下面的命令使用 Format-Table cmdlet 显示进程对象的进程 ID、ProcessName 和 MachineName (ComputerName) 属性。</span><span class="sxs-lookup"><span data-stu-id="2227f-121">The following command uses the Format-Table cmdlet to display the process ID, ProcessName and MachineName (ComputerName) properties of the process objects.</span></span>

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server01 |
  Format-Table -Property ID, ProcessName, MachineName

  Id ProcessName MachineName
  -- ----------- -----------
3700 powershell  Server01
3052 powershell  Server02
5816 powershell  localhost
```

<span data-ttu-id="2227f-122">这一更为复杂的命令将 MachineName 属性添加到标准 Get-Process 显示中。</span><span class="sxs-lookup"><span data-stu-id="2227f-122">This more complex command adds the MachineName property to the standard Get-Process display.</span></span>

```
PS> Get-Process powershell -ComputerName localhost, Server01, Server02 |
    Format-Table -Property Handles,
        @{Label="NPM(K)";Expression={[int]($_.NPM/1024)}},
        @{Label="PM(K)";Expression={[int]($_.PM/1024)}},
        @{Label="WS(K)";Expression={[int]($_.WS/1024)}},
        @{Label="VM(M)";Expression={[int]($_.VM/1MB)}},
        @{Label="CPU(s)";Expression={if ($_.CPU -ne $()){$_.CPU.ToString("N")}}},
        Id, ProcessName, MachineName -auto

Handles  NPM(K)  PM(K) WS(K) VM(M) CPU(s)  Id ProcessName  MachineName
-------  ------  ----- ----- ----- ------  -- -----------  -----------
    258       8  29772 38636   130         3700 powershell Server01
    398      24  75988 76800   572         5816 powershell localhost
    605       9  30668 29800   155 7.11    3052 powershell Server02
```

## <a name="stopping-processes-stop-process"></a><span data-ttu-id="2227f-123">停止进程 (Stop-Process)</span><span class="sxs-lookup"><span data-stu-id="2227f-123">Stopping Processes (Stop-Process)</span></span>

<span data-ttu-id="2227f-124">Windows PowerShell 可以灵活地列出进程，但停止进程呢？</span><span class="sxs-lookup"><span data-stu-id="2227f-124">Windows PowerShell gives you flexibility for listing processes, but what about stopping a process?</span></span>

<span data-ttu-id="2227f-125">**Stop-Process** cmdlet 将采用 Name 或 ID 来指定想要停止的进程。</span><span class="sxs-lookup"><span data-stu-id="2227f-125">The **Stop-Process** cmdlet takes a Name or Id to specify a process you want to stop.</span></span> <span data-ttu-id="2227f-126">能否停止进程取决于你的权限。</span><span class="sxs-lookup"><span data-stu-id="2227f-126">Your ability to stop processes depends on your permissions.</span></span> <span data-ttu-id="2227f-127">某些进程无法停止。</span><span class="sxs-lookup"><span data-stu-id="2227f-127">Some processes cannot be stopped.</span></span> <span data-ttu-id="2227f-128">例如，如果你尝试停止空闲进程，则会出现错误：</span><span class="sxs-lookup"><span data-stu-id="2227f-128">For example, if you try to stop the idle process, you get an error:</span></span>

```
PS> Stop-Process -Name Idle
Stop-Process : Process 'Idle (0)' cannot be stopped due to the following error:
 Access is denied
At line:1 char:13
+ Stop-Process  <<<< -Name Idle
```

<span data-ttu-id="2227f-129">你也可以通过使用 **Confirm** 参数进行强制提示。</span><span class="sxs-lookup"><span data-stu-id="2227f-129">You can also force prompting with the **Confirm** parameter.</span></span> <span data-ttu-id="2227f-130">如果你在指定进程名称时使用通配符，此参数会特别有用，因为可能会意外地匹配到你不想要停止的一些进程：</span><span class="sxs-lookup"><span data-stu-id="2227f-130">This parameter is particularly useful if you use a wildcard when specifying the process name, because you may accidentally match some processes you do not want to stop:</span></span>

```
PS> Stop-Process -Name t*,e* -Confirm
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "explorer (408)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):n
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "taskmgr (4072)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):n
```

<span data-ttu-id="2227f-131">可以通过使用某些对象筛选 cmdlet 来实现复杂的过程操作。</span><span class="sxs-lookup"><span data-stu-id="2227f-131">Complex process manipulation is possible by using some of the object filtering cmdlets.</span></span> <span data-ttu-id="2227f-132">因为 Process 对象具有 Responding 属性，当程序不再响应时该属性为 true，你可以使用以下命令停止所有无响应的应用程序：</span><span class="sxs-lookup"><span data-stu-id="2227f-132">Because a Process object has a Responding property that is true when it is no longer responding, you can stop all nonresponsive applications with the following command:</span></span>

```powershell
Get-Process | Where-Object -FilterScript {$_.Responding -eq $false} | Stop-Process
```

<span data-ttu-id="2227f-133">在其他情况下，可以使用相同的方法。</span><span class="sxs-lookup"><span data-stu-id="2227f-133">You can use the same approach in other situations.</span></span> <span data-ttu-id="2227f-134">例如，假设用户启动另一个应用程序时，辅助通知区域的应用程序将自动运行。</span><span class="sxs-lookup"><span data-stu-id="2227f-134">For example, suppose a secondary notification area application automatically runs when users start another application.</span></span> <span data-ttu-id="2227f-135">你可能会发现在“终端服务”会话中它无法正常工作，但你仍想要将其保留在物理计算机控制台上运行的会话中。</span><span class="sxs-lookup"><span data-stu-id="2227f-135">You may find that this does not work correctly in Terminal Services sessions, but you still want to keep it in sessions that run on the physical computer console.</span></span> <span data-ttu-id="2227f-136">连接到物理计算机桌面的会话始终具有一个为 0 的会话 ID，这样你可以通过使用 **Where-Object** 和进程 **SessionId** 停止在其他会话中的所有进程的实例：</span><span class="sxs-lookup"><span data-stu-id="2227f-136">Sessions connected to the physical computer desktop always have a session ID of 0, so you can stop all instances of the process that are in other sessions by using **Where-Object** and the process, **SessionId** :</span></span>

```powershell
Get-Process -Name BadApp | Where-Object -FilterScript {$_.SessionId -neq 0} | Stop-Process
```

<span data-ttu-id="2227f-137">Stop-Process cmdlet 不具有 ComputerName 参数。</span><span class="sxs-lookup"><span data-stu-id="2227f-137">The Stop-Process cmdlet does not have a ComputerName parameter.</span></span> <span data-ttu-id="2227f-138">因此，若要在远程计算机上运行停止进程，需要使用 Invoke-Command cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2227f-138">Therefore, to run a stop process command on a remote computer, you need to use the Invoke-Command cmdlet.</span></span> <span data-ttu-id="2227f-139">例如，若要停止 Server01 远程计算器上的 PowerShell 进程，请键入：</span><span class="sxs-lookup"><span data-stu-id="2227f-139">For example, to stop the PowerShell process on the Server01 remote computer, type:</span></span>

```powershell
Invoke-Command -ComputerName Server01 {Stop-Process Powershell}
```

## <a name="stopping-all-other-windows-powershell-sessions"></a><span data-ttu-id="2227f-140">停止所有其他 Windows PowerShell 会话</span><span class="sxs-lookup"><span data-stu-id="2227f-140">Stopping All Other Windows PowerShell Sessions</span></span>

<span data-ttu-id="2227f-141">这可能对停止当前会话之外的所有正在运行的 Windows PowerShell 会话偶尔有用。</span><span class="sxs-lookup"><span data-stu-id="2227f-141">It may occasionally be useful to be able to stop all running Windows PowerShell sessions other than the current session.</span></span> <span data-ttu-id="2227f-142">如果会话正在使用过多资源或无法访问（它可能正在远程运行或在另一个桌面会话中运行），可能不能直接将其停止。</span><span class="sxs-lookup"><span data-stu-id="2227f-142">If a session is using too many resources or is inaccessible (it may be running remotely or in another desktop session), you may not be able to directly stop it.</span></span> <span data-ttu-id="2227f-143">如果你尝试停止所有正在运行的会话，但是，这可能会终止当前会话。</span><span class="sxs-lookup"><span data-stu-id="2227f-143">If you try to stop all running sessions, however, the current session may be terminated instead.</span></span>

<span data-ttu-id="2227f-144">每个 Windows PowerShell 会话都具有一个包含 Windows PowerShell 进程的 ID 的环境变量 PID。</span><span class="sxs-lookup"><span data-stu-id="2227f-144">Each Windows PowerShell session has an environment variable PID that contains the Id of the Windows PowerShell process.</span></span> <span data-ttu-id="2227f-145">你可以对比每个会话的 ID 检查 $PID，并仅终止具有不同 ID 的 Windows PowerShell 会话。下面的管道命令执行此操作并返回终止的会话的列表（因为使用了 **PassThru** 参数）：</span><span class="sxs-lookup"><span data-stu-id="2227f-145">You can check the $PID against the Id of each session and terminate only Windows PowerShell sessions that have a different Id. The following pipeline command does this and returns the list of terminated sessions (because of the use of the **PassThru** parameter):</span></span>

```
PS> Get-Process -Name powershell | Where-Object -FilterScript {$_.Id -ne $PID} | Stop-Process -PassThru

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    334       9    23348      29136   143     1.03    388 powershell
    304       9    23152      29040   143     1.03    632 powershell
    302       9    20916      26804   143     1.03   1116 powershell
    335       9    25656      31412   143     1.09   3452 powershell
    303       9    23156      29044   143     1.05   3608 powershell
    287       9    21044      26928   143     1.02   3672 powershell
```

## <a name="starting-debugging-and-waiting-for-processes"></a><span data-ttu-id="2227f-146">启动、调试和等待进程</span><span class="sxs-lookup"><span data-stu-id="2227f-146">Starting, Debugging, and Waiting for Processes</span></span>

<span data-ttu-id="2227f-147">Windows PowerShell 还附带 cmdlet，以启动（或重启）、调试进程，并在运行命令之前等待进程完成。</span><span class="sxs-lookup"><span data-stu-id="2227f-147">Windows PowerShell also comes with cmdlets to start (or restart), debug a process, and wait for a process to complete before running a command.</span></span> <span data-ttu-id="2227f-148">有关这些 cmdlet 的信息，请参阅有关每个 cmdlet 的 cmdlet 帮助主题。</span><span class="sxs-lookup"><span data-stu-id="2227f-148">For information about these cmdlets, see the cmdlet help topic for each cmdlet.</span></span>

## <a name="see-also"></a><span data-ttu-id="2227f-149">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2227f-149">See Also</span></span>

- [<span data-ttu-id="2227f-150">Get-Process</span><span class="sxs-lookup"><span data-stu-id="2227f-150">Get-Process</span></span>](/powershell/module/Microsoft.PowerShell.Management/Get-Process)
- [<span data-ttu-id="2227f-151">Stop-Process</span><span class="sxs-lookup"><span data-stu-id="2227f-151">Stop-Process</span></span>](/powershell/module/Microsoft.PowerShell.Management/Stop-Process)
- [<span data-ttu-id="2227f-152">Start-Process</span><span class="sxs-lookup"><span data-stu-id="2227f-152">Start-Process</span></span>](/powershell/module/Microsoft.PowerShell.Management/Start-Process)
- [<span data-ttu-id="2227f-153">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="2227f-153">Wait-Process</span></span>](/powershell/module/Microsoft.PowerShell.Management/Wait-Process)
- [<span data-ttu-id="2227f-154">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="2227f-154">Debug-Process</span></span>](/powershell/module/Microsoft.PowerShell.Management/Debug-Process)
- [<span data-ttu-id="2227f-155">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="2227f-155">Invoke-Command</span></span>](/powershell/module/Microsoft.PowerShell.Core/Invoke-Command)
