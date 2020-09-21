---
title: 开始使用 PowerShell
description: 在哪里可以找到 PowerShell 以及如何为新用户启动它。
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: e8938a5d36cd1c9c5a74eed1c22cd5d0e1a91966
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786741"
---
# <a name="chapter-1---getting-started-with-powershell"></a><span data-ttu-id="667fd-103">第 1 章 - 开始使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="667fd-103">Chapter 1 - Getting Started with PowerShell</span></span>

<span data-ttu-id="667fd-104">我经常发现，在会议和用户组会议上，许多没有多少经验的新用户已经开始在演示时使用 PowerShell 了。</span><span class="sxs-lookup"><span data-stu-id="667fd-104">I often find that presenters at conferences and user group meetings already have PowerShell running when they start entry-level presentations.</span></span> <span data-ttu-id="667fd-105">本书首先回答了那些之前在上述会议中未使用过 PowerShell 的与会者所提出的相关问题。</span><span class="sxs-lookup"><span data-stu-id="667fd-105">This book begins by answering the questions I've heard attendees who haven't previously used PowerShell ask in those sessions.</span></span>

<span data-ttu-id="667fd-106">具体而言，本章重点介绍如何查找和启动 PowerShell，以及如何解决新用户在刚开始使用 PowerShell 时遇到的一些难点。</span><span class="sxs-lookup"><span data-stu-id="667fd-106">Specifically, this chapter focuses on finding and launching PowerShell, and solving some of the initial pain points that new users experience with PowerShell.</span></span> <span data-ttu-id="667fd-107">请务必在 Windows 10 实验环境计算机上逐步完成本章中展示的示例。</span><span class="sxs-lookup"><span data-stu-id="667fd-107">Be sure to follow along and walk through the examples shown in this chapter on your Windows 10 lab environment computer.</span></span>

## <a name="what-do-i-need-to-get-started-with-powershell"></a><span data-ttu-id="667fd-108">若要开始使用 PowerShell，需要作哪些准备？</span><span class="sxs-lookup"><span data-stu-id="667fd-108">What do I need to get started with PowerShell?</span></span>

<span data-ttu-id="667fd-109">所有新式版本的 Windows 操作系统均安装了 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="667fd-109">All modern versions of Windows operating systems ship with PowerShell installed.</span></span> <span data-ttu-id="667fd-110">如果运行的版本低于 5.1，应安装最新版本。</span><span class="sxs-lookup"><span data-stu-id="667fd-110">If you're running a version older than 5.1, you should install the latest version.</span></span>

- <span data-ttu-id="667fd-111">要升级到 Windows PowerShell 5.1，请参阅[升级现有的 Windows PowerShell][]</span><span class="sxs-lookup"><span data-stu-id="667fd-111">To upgrade to Windows PowerShell 5.1, see [Upgrading existing Windows PowerShell][]</span></span>
- <span data-ttu-id="667fd-112">要安装最新版本的 PowerShell，请参阅[安装 PowerShell][]</span><span class="sxs-lookup"><span data-stu-id="667fd-112">To install the latest version of PowerShell, see [Installing PowerShell][]</span></span>

## <a name="where-do-i-find-powershell"></a><span data-ttu-id="667fd-113">在哪里可以找到 PowerShell？</span><span class="sxs-lookup"><span data-stu-id="667fd-113">Where do I find PowerShell?</span></span>

<span data-ttu-id="667fd-114">在 Windows 10 上查找 PowerShell 的最简单方法是在搜索栏中键入“PowerShell”，如图 1-1 所示。</span><span class="sxs-lookup"><span data-stu-id="667fd-114">The easiest way to find PowerShell on Windows 10 is to type **PowerShell** into the search bar as shown in Figure 1-1.</span></span>

![图 1-1 - 在“开始”菜单中搜索 PowerShell](media/figure1-1.png)

<span data-ttu-id="667fd-116">请注意，图 1-1 显示了四种不同的 PowerShell 快捷方式。</span><span class="sxs-lookup"><span data-stu-id="667fd-116">Notice that four different shortcuts for PowerShell are shown in Figure 1-1.</span></span> <span data-ttu-id="667fd-117">本书中用于演示的计算机运行的是 64 位版本的 Windows 10，如快捷方式上的 (x86) 后缀所示，分别有 64 位以及 32 位版本的 PowerShell 控制台和 PowerShell ISE（集成脚本环境）。</span><span class="sxs-lookup"><span data-stu-id="667fd-117">The computer used for demonstration purposes in this book is running the 64-bit version of Windows 10 so there's a 64-bit version of the PowerShell console and the PowerShell ISE (Integrated Scripting Environment), and a 32-bit version of each one as denoted by the (x86) suffix on the shortcuts.</span></span> <span data-ttu-id="667fd-118">如果运行的是 32 位版本的 Windows 10，则只有两种快捷方式。</span><span class="sxs-lookup"><span data-stu-id="667fd-118">If you happen to be running a 32-bit version of Windows 10, you'll only have two shortcuts.</span></span> <span data-ttu-id="667fd-119">这些项没有 (x86) 后缀，但为 32 位版本。</span><span class="sxs-lookup"><span data-stu-id="667fd-119">Those items don't have the (x86) suffix, but are 32-bit versions.</span></span> <span data-ttu-id="667fd-120">如果使用的是 64 位操作系统，建议运行 64 位版本的 PowerShell，除非出于特殊原因才运行 32 位版本。</span><span class="sxs-lookup"><span data-stu-id="667fd-120">If you have a 64-bit operating system, my recommendation is to run the 64-bit version of PowerShell unless you have a specific reason for running the 32-bit version.</span></span>

<span data-ttu-id="667fd-121">有关在其他 Windows 版本上启动 PowerShell 的信息，请参阅[启动 Windows PowerShell][]。</span><span class="sxs-lookup"><span data-stu-id="667fd-121">For information about starting PowerShell on other versions of Windows, see [Starting Windows PowerShell][].</span></span>

## <a name="how-do-i-launch-powershell"></a><span data-ttu-id="667fd-122">如何启动 PowerShell？</span><span class="sxs-lookup"><span data-stu-id="667fd-122">How do I launch PowerShell?</span></span>

<span data-ttu-id="667fd-123">在支持的生产企业环境中，我使用三个不同的 Active Directory 用户帐户。</span><span class="sxs-lookup"><span data-stu-id="667fd-123">In the production enterprise environments that I support, I use three different Active Directory user accounts.</span></span> <span data-ttu-id="667fd-124">我已在本书使用的实验环境中对这些帐户执行了镜像操作。</span><span class="sxs-lookup"><span data-stu-id="667fd-124">I've mirrored those accounts in the lab environment used in this book.</span></span> <span data-ttu-id="667fd-125">我以非域或非本地管理员的域用户身份登录 Windows 10 计算机。</span><span class="sxs-lookup"><span data-stu-id="667fd-125">I log into the Windows 10 computer as a domain user who is not a domain or local administrator.</span></span>

<span data-ttu-id="667fd-126">我通过单击“Windows PowerShell”快捷方式启动了 PowerShell 控制台，如图 1-1 所示。</span><span class="sxs-lookup"><span data-stu-id="667fd-126">I've launched the PowerShell console by clicking on the "Windows PowerShell" shortcut as shown in Figure 1-1.</span></span>

![图 1-4 - PowerShell 窗口的标题栏](media/figure1-4.png)

<span data-ttu-id="667fd-128">请注意，PowerShell 控制台的标题栏显示为“Windows PowerShell”，如图 1-4 所示。</span><span class="sxs-lookup"><span data-stu-id="667fd-128">Notice that the title bar of the PowerShell console says "Windows PowerShell" as shown in Figure 1-4.</span></span> <span data-ttu-id="667fd-129">一些命令运行正常，但 PowerShell 无法参与用户访问控制 (UAC)。</span><span class="sxs-lookup"><span data-stu-id="667fd-129">Some commands run fine, but PowerShell can't participate in User Access Control (UAC).</span></span> <span data-ttu-id="667fd-130">这意味着它无法提示用户对需要管理员批准的任务进行提升。</span><span class="sxs-lookup"><span data-stu-id="667fd-130">That means it's unable to prompt for elevation for tasks that require the approval of an administrator.</span></span>
<span data-ttu-id="667fd-131">生成以下错误消息：</span><span class="sxs-lookup"><span data-stu-id="667fd-131">The following error message is generated:</span></span>

```powershell
Get-Service -Name W32Time | Stop-Service
```

```Output
Stop-Service : Service 'Windows Time (W32Time)' cannot be stopped due to the following
error: Cannot open W32Time service on computer '.'.
At line:1 char:29
+ Get-Service -Name W32Time | Stop-Service
+
    + CategoryInfo          : CloseError: (System.ServiceProcess.ServiceController:ServiceController)
     [Stop-Service], ServiceCommandException
    + FullyQualifiedErrorId : CouldNotStopService,Microsoft.PowerShell.Commands.StopServiceCommand
```

<span data-ttu-id="667fd-132">解决此问题的方法是以作为域用户的本地管理员身份运行 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="667fd-132">The solution to this problem is to run PowerShell as a domain user who is a local administrator.</span></span>
<span data-ttu-id="667fd-133">这是配置第二个域用户帐户的方式。</span><span class="sxs-lookup"><span data-stu-id="667fd-133">This is how my second domain user account is configured.</span></span> <span data-ttu-id="667fd-134">由于使用权限最低的主体，此帐户不能为域管理员，或不能在域中具有任何提升的权限。</span><span class="sxs-lookup"><span data-stu-id="667fd-134">Using the principal of least privilege, this account should NOT be a domain administrator, or have any elevated privileges in the domain.</span></span>

<span data-ttu-id="667fd-135">关闭 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="667fd-135">Close PowerShell.</span></span> <span data-ttu-id="667fd-136">重启 PowerShell 控制台，但这次需要右键单击 Windows PowerShell 快捷方式，然后选择“以管理员身份运行”，如图 1-5 所示 。</span><span class="sxs-lookup"><span data-stu-id="667fd-136">Relaunch the PowerShell console, except this time right-click on the **Windows PowerShell** shortcut and select **Run as administrator** as shown in Figure 1-5.</span></span>

![图 1-5 - 上下文菜单 - 以管理员身份运行](media/figure1-5.png)

<span data-ttu-id="667fd-138">如果以普通用户身份登录 Windows，系统将提示你输入凭据。</span><span class="sxs-lookup"><span data-stu-id="667fd-138">If you're logged into Windows as a normal user, you'll be prompted for credentials.</span></span> <span data-ttu-id="667fd-139">我将输入我的用户帐户的凭据，其身份是域用户和本地管理员，如图 1-6 所示。</span><span class="sxs-lookup"><span data-stu-id="667fd-139">I'll enter the credentials for my user account who is a domain user and local admin as shown in Figure 1-6.</span></span>

![图 1-6](media/figure1-6.png)

<span data-ttu-id="667fd-141">以管理员身份重启 PowerShell 后，标题栏应显示“管理员：Windows PowerShell”，如图 1-7 所示。</span><span class="sxs-lookup"><span data-stu-id="667fd-141">Once PowerShell is relaunched as an administrator, the title bar should say "Administrator: Windows PowerShell" as shown in Figure 1-7.</span></span>

![图 1-7](media/figure1-7.png)

<span data-ttu-id="667fd-143">现在，由于以本地管理员身份运行了提升的 PowerShell，因此，当在本地计算机上运行某个命令且需要给予提升提示时，不会再产生 UAC 问题。</span><span class="sxs-lookup"><span data-stu-id="667fd-143">Now that PowerShell is being run elevated as a local administrator, UAC will no longer be a problem when a command is run on the local computer that would normally require a prompt for elevation.</span></span> <span data-ttu-id="667fd-144">请记住，通过这个经过提升的 PowerShell 控制台实例运行的所有命令在运行时也会得到提升。</span><span class="sxs-lookup"><span data-stu-id="667fd-144">Keep in mind though that any command run from this elevated instance of the PowerShell console, also runs elevated.</span></span>

<span data-ttu-id="667fd-145">为了简化查找 PowerShell 并以管理员身份启动它的过程，建议将其固定在任务栏上，并将其设置为在每次运行时自动以管理员身份启动。</span><span class="sxs-lookup"><span data-stu-id="667fd-145">To simplify finding PowerShell and launching it as an administrator, I recommend pinning it to the taskbar and setting it to automatically launch as an admin each time it's run.</span></span>

<span data-ttu-id="667fd-146">再次搜索 PowerShell，但这次要右键单击它，然后选择“固定到任务栏”，如图 1-8 所示。</span><span class="sxs-lookup"><span data-stu-id="667fd-146">Search for PowerShell again, except this time right-click on it and select "Pin to taskbar" as shown in Figure 1-8.</span></span>

![图 1-8](media/figure1-8.png)

<span data-ttu-id="667fd-148">右键单击当前固定在任务栏上的 PowerShell 快捷方式，然后选择属性，如图 1-9 所示。</span><span class="sxs-lookup"><span data-stu-id="667fd-148">Right-click on the PowerShell shortcut that's now pinned to the taskbar and select properties as shown in Figure 1-9.</span></span>

![图 1-9 - 用户帐户控制 - 输入凭据](media/figure1-9.png)

<span data-ttu-id="667fd-150">单击图 1-10 中的 #1 所表示的“高级”，然后选中图 1-10 中的 #2 所表示的“以管理员身份运行”复选框，然后双击“确定”，以接受更改并退出这两个对话框。</span><span class="sxs-lookup"><span data-stu-id="667fd-150">Click on "Advanced" as denoted by #1 in Figure 1-10, then check the "Run as administrator" checkbox as denoted by #2 in Figure 1-10, and then click OK twice to accept the changes and exit out of both dialog boxes.</span></span>

![图 1-10 - 显示“管理员”的标题栏](media/figure1-10.png)

<span data-ttu-id="667fd-152">无需再次查找 PowerShell 或再次担心它是否以管理员身份运行。</span><span class="sxs-lookup"><span data-stu-id="667fd-152">You'll never have to worry about finding PowerShell or whether or not it's running as an administrator again.</span></span>

<span data-ttu-id="667fd-153">为防止 UAC 出现问题而以管理员身份运行提升的 PowerShell 仅影响针对本地计算机运行的命令。</span><span class="sxs-lookup"><span data-stu-id="667fd-153">Running PowerShell elevated as an administrator to prevent having problems with UAC only impacts commands that are run against the local computer.</span></span> <span data-ttu-id="667fd-154">它不影响以远程计算机为目标的命令。</span><span class="sxs-lookup"><span data-stu-id="667fd-154">It has no effect on commands that target remote computers.</span></span>

## <a name="what-version-of-powershell-am-i-running"></a><span data-ttu-id="667fd-155">正在运行的是哪个版本的 PowerShell？</span><span class="sxs-lookup"><span data-stu-id="667fd-155">What version of PowerShell am I running?</span></span>

<span data-ttu-id="667fd-156">PowerShell 中有许多用于存储状态信息的自动变量。</span><span class="sxs-lookup"><span data-stu-id="667fd-156">There are a number of automatic variables in PowerShell that store state information.</span></span> <span data-ttu-id="667fd-157">其中某个变量是 `$PSVersionTable`，它包含可用于显示相关 PowerShell 版本信息的哈希表：</span><span class="sxs-lookup"><span data-stu-id="667fd-157">One of these variables is `$PSVersionTable`, which contains a hashtable that can be used to display the relevant PowerShell version information:</span></span>

```powershell
$PSVersionTable
```

```Output
Name                           Value
----                           -----
PSVersion                      5.1.19041.1
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
BuildVersion                   10.0.19041.1
CLRVersion                     4.0.30319.42000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

<span data-ttu-id="667fd-158">较新版本的 Windows PowerShell 作为 Windows Management Framework (WMF) 的一部分分发。</span><span class="sxs-lookup"><span data-stu-id="667fd-158">Newer versions of Windows PowerShell are distributed as part of the Windows Management Framework (WMF).</span></span> <span data-ttu-id="667fd-159">WMF 的版决定了要使用哪个特定版本的 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="667fd-159">A specific version of the .NET Framework is required depending on the WMF version.</span></span> <span data-ttu-id="667fd-160">要升级到 Windows PowerShell 5.1，请参阅[升级现有的 Windows PowerShell][]。</span><span class="sxs-lookup"><span data-stu-id="667fd-160">To upgrade to Windows PowerShell 5.1, see [Upgrading existing Windows PowerShell][].</span></span>

## <a name="execution-policy"></a><span data-ttu-id="667fd-161">执行策略</span><span class="sxs-lookup"><span data-stu-id="667fd-161">Execution Policy</span></span>

<span data-ttu-id="667fd-162">与通常的看法相反，PowerShell 中的执行策略不是安全边界。</span><span class="sxs-lookup"><span data-stu-id="667fd-162">Contrary to popular belief, the execution policy in PowerShell is not a security boundary.</span></span> <span data-ttu-id="667fd-163">它的作用是防止用户无意间运行脚本。</span><span class="sxs-lookup"><span data-stu-id="667fd-163">It's designed to prevent a user from unknowingly running a script.</span></span> <span data-ttu-id="667fd-164">已确定的用户可以轻松绕过 PowerShell 中的执行策略。</span><span class="sxs-lookup"><span data-stu-id="667fd-164">A determined user can easily bypass the execution policy in PowerShell.</span></span> <span data-ttu-id="667fd-165">表 1-2 显示当前 Windows 操作系统的默认执行策略。</span><span class="sxs-lookup"><span data-stu-id="667fd-165">Table 1-2 shows the default execution policy for current Windows operating systems.</span></span>

| <span data-ttu-id="667fd-166">Windows 操作系统版本</span><span class="sxs-lookup"><span data-stu-id="667fd-166">Windows Operating System Version</span></span> | <span data-ttu-id="667fd-167">默认执行策略</span><span class="sxs-lookup"><span data-stu-id="667fd-167">Default Execution Policy</span></span> |
| -------------------------------- | ------------------------ |
| <span data-ttu-id="667fd-168">Server 2019</span><span class="sxs-lookup"><span data-stu-id="667fd-168">Server 2019</span></span>                      | <span data-ttu-id="667fd-169">远程签名</span><span class="sxs-lookup"><span data-stu-id="667fd-169">Remote Signed</span></span>            |
| <span data-ttu-id="667fd-170">Server 2016</span><span class="sxs-lookup"><span data-stu-id="667fd-170">Server 2016</span></span>                      | <span data-ttu-id="667fd-171">远程签名</span><span class="sxs-lookup"><span data-stu-id="667fd-171">Remote Signed</span></span>            |
| <span data-ttu-id="667fd-172">Windows 10</span><span class="sxs-lookup"><span data-stu-id="667fd-172">Windows 10</span></span>                       | <span data-ttu-id="667fd-173">受限</span><span class="sxs-lookup"><span data-stu-id="667fd-173">Restricted</span></span>               |

<span data-ttu-id="667fd-174">无论采用怎样的执行策略设置，任何 PowerShell 命令都可以通过交互方式运行。</span><span class="sxs-lookup"><span data-stu-id="667fd-174">Regardless of the execution policy setting, any PowerShell command can be run interactively.</span></span> <span data-ttu-id="667fd-175">执行策略仅影响脚本中运行的命令。</span><span class="sxs-lookup"><span data-stu-id="667fd-175">The execution policy only affects commands running in a script.</span></span> <span data-ttu-id="667fd-176">`Get-ExecutionPolicy` cmdlet 用于确定当前的执行策略设置，而 `Set-ExecutionPolicy` cmdlet 用于更改执行策略。</span><span class="sxs-lookup"><span data-stu-id="667fd-176">The `Get-ExecutionPolicy` cmdlet is used to determine what the current execution policy setting is and the `Set-ExecutionPolicy` cmdlet is used to change the execution policy.</span></span> <span data-ttu-id="667fd-177">建议使用 RemoteSigned 策略，该策略要求下载的脚本必须由受信任的发布者签名才能运行。</span><span class="sxs-lookup"><span data-stu-id="667fd-177">My recommendation is to use the **RemoteSigned** policy, which requires downloaded scripts to be signed by a trusted publisher in order to be run.</span></span>

<span data-ttu-id="667fd-178">检查当前的执行策略：</span><span class="sxs-lookup"><span data-stu-id="667fd-178">Check the current execution policy:</span></span>

```powershell
Get-ExecutionPolicy
```

```Output
Restricted
```

<span data-ttu-id="667fd-179">当执行策略设置为“受限”时，PowerShell 脚本根本无法运行。</span><span class="sxs-lookup"><span data-stu-id="667fd-179">PowerShell scripts can't be run at all when the execution policy is set to **Restricted**.</span></span> <span data-ttu-id="667fd-180">这是所有 Windows 客户端操作系统上的默认设置。</span><span class="sxs-lookup"><span data-stu-id="667fd-180">This is the default setting on all Windows client operating systems.</span></span> <span data-ttu-id="667fd-181">为了演示该问题，将以下代码另存为名为 `Stop-TimeService.ps1` 的 `.ps1` 文件。</span><span class="sxs-lookup"><span data-stu-id="667fd-181">To demonstrate the problem, save the following code as a `.ps1` file named `Stop-TimeService.ps1`.</span></span>

```powershell
Get-Service -Name W32Time | Stop-Service -PassThru
```

<span data-ttu-id="667fd-182">只要以管理员身份运行提升的 PowerShell，该命令就可通过交互方式运行而不会出错。</span><span class="sxs-lookup"><span data-stu-id="667fd-182">That command runs interactively without error as long as PowerShell is run elevated as an administrator.</span></span> <span data-ttu-id="667fd-183">不过，一旦将其保存为脚本文件并尝试执行该脚本，就会生成错误：</span><span class="sxs-lookup"><span data-stu-id="667fd-183">But as soon as it's saved as a script file and you try to execute the script, it generates an error:</span></span>

```powershell
.\Stop-TimeService.ps1
```

```Output
.\Stop-TimeService.ps1 : File C:\demo\Stop-TimeService.ps1 cannot be loaded because
running scripts is disabled on this system. For more information, see
about_Execution_Policies at http://go.microsoft.com/fwlink/?LinkID=135170.
At line:1 char:1
+ .\Stop-TimeService.ps1
+
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess
```

<span data-ttu-id="667fd-184">请注意，上一组结果中显示的错误明确指示了发生了什么问题（在此系统上禁用了运行脚本）。</span><span class="sxs-lookup"><span data-stu-id="667fd-184">Notice that the error shown in the previous set of results tells you exactly what the problem is (running scripts is disabled on this system).</span></span> <span data-ttu-id="667fd-185">在 PowerShell 中运行命令后如果生成错误消息，请确保阅读该错误消息，而不是只重新运行该命令并希望它成功运行。</span><span class="sxs-lookup"><span data-stu-id="667fd-185">When you run a command in PowerShell that generates an error message, be sure to read the error message instead of just rerunning the command and hoping that it runs successfully.</span></span>

<span data-ttu-id="667fd-186">将 PowerShell 执行策略更改为远程签名。</span><span class="sxs-lookup"><span data-stu-id="667fd-186">Change the PowerShell execution policy to remote signed.</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
```

```Output
Execution Policy Change
The execution policy helps protect you from scripts that you do not trust. Changing the execution
policy might expose you to the security risks described in the about_Execution_Policies help topic
at http://go.microsoft.com/fwlink/?LinkID=135170. Do you want to change the execution policy?
[Y] Yes [A] Yes to All [N] No [L] No to All [S] Suspend [?] Help (default is "N"):y
```

<span data-ttu-id="667fd-187">务必阅读更改执行策略时显示的警告。</span><span class="sxs-lookup"><span data-stu-id="667fd-187">Be sure to read the warning that's displayed when changing the execution policy.</span></span> <span data-ttu-id="667fd-188">另外建议查看 [about_Execution_Policies][] 帮助主题，确保已了解更改执行策略带来的安全影响。</span><span class="sxs-lookup"><span data-stu-id="667fd-188">I also recommend taking a look at the [about_Execution_Policies][] help topic to make sure you understand the security implications of changing the execution policy.</span></span>

<span data-ttu-id="667fd-189">由于已将执行策略设置为 RemoteSigned，`Stop-TimeService.ps1` 脚本将正常运行。</span><span class="sxs-lookup"><span data-stu-id="667fd-189">Now that the execution policy has been set to **RemoteSigned**, the `Stop-TimeService.ps1` script runs error free.</span></span>

```powershell
.\Stop-TimeService.ps1
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  W32Time            Windows Time
```

<span data-ttu-id="667fd-190">在继续之前，请务必启动 Windows 时间服务，否则可能会遇到无法预料的问题。</span><span class="sxs-lookup"><span data-stu-id="667fd-190">Be sure to start your Windows Time service before continuing otherwise you may run into unforeseen problems.</span></span>

```powershell
Start-Service -Name w32time
```

## <a name="summary"></a><span data-ttu-id="667fd-191">总结</span><span class="sxs-lookup"><span data-stu-id="667fd-191">Summary</span></span>

<span data-ttu-id="667fd-192">在本章中，你了解了如何查找和启动 PowerShell，以及如何创建以管理员身份启动 PowerShell 的快捷方式。</span><span class="sxs-lookup"><span data-stu-id="667fd-192">In this chapter, you've learned how to find and launch PowerShell, and how to create a shortcut that launches PowerShell as an administrator.</span></span> <span data-ttu-id="667fd-193">你还了解了默认执行策略及其更改方式。</span><span class="sxs-lookup"><span data-stu-id="667fd-193">You've also learned about the default execution policy and how to change it.</span></span>

## <a name="review"></a><span data-ttu-id="667fd-194">审阅</span><span class="sxs-lookup"><span data-stu-id="667fd-194">Review</span></span>

1. <span data-ttu-id="667fd-195">如何确定计算机正在运行的 PowerShell 版本？</span><span class="sxs-lookup"><span data-stu-id="667fd-195">How do you determine what PowerShell version a computer is running?</span></span>
1. <span data-ttu-id="667fd-196">为什么以管理员身份启动提升的 PowerShell 至关重要？</span><span class="sxs-lookup"><span data-stu-id="667fd-196">Why is it important to launch PowerShell elevated as an administrator?</span></span>
1. <span data-ttu-id="667fd-197">如何确定当前的 PowerShell 执行策略？</span><span class="sxs-lookup"><span data-stu-id="667fd-197">How do you determine the current PowerShell execution policy?</span></span>
1. <span data-ttu-id="667fd-198">Windows 客户端计算机上的默认 PowerShell 执行策略可以防止发生什么情况？</span><span class="sxs-lookup"><span data-stu-id="667fd-198">What does the default PowerShell execution policy on Windows client computers prevent from occurring?</span></span>
1. <span data-ttu-id="667fd-199">如何更改 PowerShell 执行策略？</span><span class="sxs-lookup"><span data-stu-id="667fd-199">How do you change the PowerShell execution policy?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="667fd-200">推荐阅读的主题</span><span class="sxs-lookup"><span data-stu-id="667fd-200">Recommended Reading</span></span>

<span data-ttu-id="667fd-201">如果想详细了解本章所介绍的主题，建议阅读以下 PowerShell 帮助主题。</span><span class="sxs-lookup"><span data-stu-id="667fd-201">For those who want to know more information about the topics covered in this chapter, I recommend reading the following PowerShell help topics.</span></span>

- <span data-ttu-id="667fd-202">[about_Automatic_Variables][]</span><span class="sxs-lookup"><span data-stu-id="667fd-202">[about_Automatic_Variables][]</span></span>
- <span data-ttu-id="667fd-203">[about_Hash_Tables][]</span><span class="sxs-lookup"><span data-stu-id="667fd-203">[about_Hash_Tables][]</span></span>
- <span data-ttu-id="667fd-204">[about_Execution_Policies][]</span><span class="sxs-lookup"><span data-stu-id="667fd-204">[about_Execution_Policies][]</span></span>

<span data-ttu-id="667fd-205">在下一章中，你将了解 PowerShell 中命令的可发现性。</span><span class="sxs-lookup"><span data-stu-id="667fd-205">In the next chapter, you'll learn about the discoverability of commands in PowerShell.</span></span> <span data-ttu-id="667fd-206">下一章将介绍的内容之一是如何更新 PowerShell，以便可以直接在 PowerShell 内部查看这些帮助主题，而不必在 Internet 上查看它们。</span><span class="sxs-lookup"><span data-stu-id="667fd-206">One of the things that will be covered is how to update PowerShell so those help topics can be viewed right from within PowerShell instead of having to view them on the internet.</span></span>

<!-- link references -->
[about_Automatic_Variables]: /powershell/module/microsoft.powershell.core/about/about_automatic_variables
[about_Hash_Tables]: /powershell/module/microsoft.powershell.core/about/about_hash_tables
[about_Execution_Policies]: /powershell/module/microsoft.powershell.core/about/about_execution_policies
[升级现有的 Windows PowerShell]: /powershell/scripting/windows-powershell/install/installing-windows-powershell#upgrading-existing-windows-powershell
[Upgrading existing Windows PowerShell]: /powershell/scripting/windows-powershell/install/installing-windows-powershell#upgrading-existing-windows-powershell
[安装 PowerShell]: /powershell/scripting/install/installing-powershell
[Installing PowerShell]: /powershell/scripting/install/installing-powershell
[启动 Windows PowerShell]: /powershell/scripting/windows-powershell/starting-windows-powershell
[Starting Windows PowerShell]: /powershell/scripting/windows-powershell/starting-windows-powershell
