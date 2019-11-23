---
ms.date: 07/10/2019
keywords: jea,powershell,安全性
title: JEA 角色功能
ms.openlocfilehash: 7191b90e198ffb539da6870a8ddc3e449ad9e8ae
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017838"
---
# <a name="jea-role-capabilities"></a><span data-ttu-id="353ce-103">JEA 角色功能</span><span class="sxs-lookup"><span data-stu-id="353ce-103">JEA Role Capabilities</span></span>

<span data-ttu-id="353ce-104">创建 JEA 终结点时，需要定义一个或多个角色功能，它们描述了用户可在 JEA 会话中执行哪些操作。</span><span class="sxs-lookup"><span data-stu-id="353ce-104">When creating a JEA endpoint, you need to define one or more role capabilities that describe what someone can do in a JEA session.</span></span> <span data-ttu-id="353ce-105">角色功能是一个带 `.psrc` 扩展名的 PowerShell 数据文件其中列出了向连接用户提供的所有 cmdlet、函数、提供程序和外部程序。</span><span class="sxs-lookup"><span data-stu-id="353ce-105">A role capability is a PowerShell data file with the `.psrc` extension that lists all the cmdlets, functions, providers, and external programs that are made available to connecting users.</span></span>

## <a name="determine-which-commands-to-allow"></a><span data-ttu-id="353ce-106">确定要允许的命令</span><span class="sxs-lookup"><span data-stu-id="353ce-106">Determine which commands to allow</span></span>

<span data-ttu-id="353ce-107">创建角色功能文件时，首先要考虑用户需要访问哪些内容。</span><span class="sxs-lookup"><span data-stu-id="353ce-107">The first step in creating a role capability file is to consider what the users need access to.</span></span> <span data-ttu-id="353ce-108">此需求收集过程可能需要一段时间，但很必要。</span><span class="sxs-lookup"><span data-stu-id="353ce-108">The requirements gathering process can take a while, but it's an important process.</span></span> <span data-ttu-id="353ce-109">如果用户具有访问权限的 cmdlet 和函数太少，则会阻碍他们完成工作。</span><span class="sxs-lookup"><span data-stu-id="353ce-109">Giving users access to too few cmdlets and functions can prevent them from getting their job done.</span></span> <span data-ttu-id="353ce-110">如果允许访问的 cmdlet 和函数太多，则用户能够执行比预期多的操作，从而削弱你的安全状况。</span><span class="sxs-lookup"><span data-stu-id="353ce-110">Allowing access to too many cmdlets and functions can allow users to do more than you intended and weaken your security stance.</span></span>

<span data-ttu-id="353ce-111">你如何执行此过程由你的组织和目标而定。</span><span class="sxs-lookup"><span data-stu-id="353ce-111">How you go about this process depends on your organization and goals.</span></span> <span data-ttu-id="353ce-112">以下提示可帮助确保你正确选择。</span><span class="sxs-lookup"><span data-stu-id="353ce-112">The following tips can help ensure you're on the right path.</span></span>

1. <span data-ttu-id="353ce-113">**标识**用户用于完成工作的命令。</span><span class="sxs-lookup"><span data-stu-id="353ce-113">**Identify** the commands users are using to get their jobs done.</span></span> <span data-ttu-id="353ce-114">这可能需要调查 IT 员工、检查自动化脚本，或者分析 PowerShell 会话脚本和日志。</span><span class="sxs-lookup"><span data-stu-id="353ce-114">This may involve surveying IT staff, checking automation scripts, or analyzing PowerShell session transcripts and logs.</span></span>
2. <span data-ttu-id="353ce-115">将命令行工具改为使用 PowerShell 等效工具（若可能），实现最佳的审核和 JEA 自定义体验  。</span><span class="sxs-lookup"><span data-stu-id="353ce-115">**Update** use of command-line tools to PowerShell equivalents, where possible, for the best auditing and JEA customization experience.</span></span> <span data-ttu-id="353ce-116">不可将外部程序限制为与本机 PowerShell cmdlet 和 JEA 中的函数一样精细。</span><span class="sxs-lookup"><span data-stu-id="353ce-116">External programs can't be constrained as granularly as native PowerShell cmdlets and functions in JEA.</span></span>
3. <span data-ttu-id="353ce-117">将 cmdlet 的范围限制为仅允许特定参数或参数值  。</span><span class="sxs-lookup"><span data-stu-id="353ce-117">**Restrict** the scope of the cmdlets to only allow specific parameters or parameter values.</span></span> <span data-ttu-id="353ce-118">如果用户只该管理系统的一部分，则这尤其重要。</span><span class="sxs-lookup"><span data-stu-id="353ce-118">This is especially important if users should manage only part of a system.</span></span>
4. <span data-ttu-id="353ce-119">创建自定义函数，替换复杂的命令或很难在 JEA 中进行约束的命令  。</span><span class="sxs-lookup"><span data-stu-id="353ce-119">**Create** custom functions to replace complex commands or commands that are difficult to constrain in JEA.</span></span> <span data-ttu-id="353ce-120">封装了复杂命令或应用其他验证逻辑的简单函数可提供额外的掌控力，简化管理员和最终用户的操作。</span><span class="sxs-lookup"><span data-stu-id="353ce-120">A simple function that wraps a complex command or applies additional validation logic can offer additional control for admins and end-user simplicity.</span></span>
5. <span data-ttu-id="353ce-121">通过用户或自动化服务测试允许命令的范围列表，并根据需要进行调整  。</span><span class="sxs-lookup"><span data-stu-id="353ce-121">**Test** the scoped list of allowable commands with your users or automation services, and adjust as necessary.</span></span>

### <a name="examples-of-potentially-dangerous-commands"></a><span data-ttu-id="353ce-122">可能存在危险的命令示例</span><span class="sxs-lookup"><span data-stu-id="353ce-122">Examples of potentially dangerous commands</span></span>

<span data-ttu-id="353ce-123">有必要仔细选择命令，确保 JEA 终结点不允许用户提升其权限。</span><span class="sxs-lookup"><span data-stu-id="353ce-123">Careful selection of commands is important to ensure the JEA endpoint doesn't allow the user to elevate their permissions.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="353ce-124">JEA 会话中用户 successCommands 所需的基本信息通常以提升的权限运行。</span><span class="sxs-lookup"><span data-stu-id="353ce-124">Essential information required for user successCommands in a JEA session are often run with elevated privileges.</span></span>

<span data-ttu-id="353ce-125">下表包含在不受约束的状态下允许使用时可能被恶意使用的命令示例。</span><span class="sxs-lookup"><span data-stu-id="353ce-125">The following table contains examples of commands that can be used maliciously if allowed in an unconstrained state.</span></span> <span data-ttu-id="353ce-126">此列表并非全面详尽，应在开始时谨慎使用。</span><span class="sxs-lookup"><span data-stu-id="353ce-126">This isn't an exhaustive list and should only be used as a cautionary starting point.</span></span>

|                                            <span data-ttu-id="353ce-127">风险</span><span class="sxs-lookup"><span data-stu-id="353ce-127">Risk</span></span>                                            |                                <span data-ttu-id="353ce-128">示例</span><span class="sxs-lookup"><span data-stu-id="353ce-128">Example</span></span>                                |                                                                              <span data-ttu-id="353ce-129">相关命令</span><span class="sxs-lookup"><span data-stu-id="353ce-129">Related commands</span></span>                                                                              |
| ------------------------------------------------------------------------------------------ | --------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="353ce-130">向连接用户授予管理员特权以绕过 JEA</span><span class="sxs-lookup"><span data-stu-id="353ce-130">Granting the connecting user admin privileges to bypass JEA</span></span>                                | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | <span data-ttu-id="353ce-131">`Add-ADGroupMember`、`Add-LocalGroupMember`、`net.exe`、`dsadd.exe`</span><span class="sxs-lookup"><span data-stu-id="353ce-131">`Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`</span></span>                                                                                                        |
| <span data-ttu-id="353ce-132">运行任意代码（如恶意软件、攻击或自定义脚本）以绕过保护</span><span class="sxs-lookup"><span data-stu-id="353ce-132">Running arbitrary code, such as malware, exploits, or custom scripts to bypass protections</span></span> | `Start-Process -FilePath '\\san\share\malware.exe'`                   | <span data-ttu-id="353ce-133">`Start-Process`、`New-Service`、`Invoke-Item`、`Invoke-WmiMethod`、`Invoke-CimMethod`、`Invoke-Expression`、`Invoke-Command`、`New-ScheduledTask`、`Register-ScheduledJob`</span><span class="sxs-lookup"><span data-stu-id="353ce-133">`Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`</span></span> |

## <a name="create-a-role-capability-file"></a><span data-ttu-id="353ce-134">创建角色功能文件</span><span class="sxs-lookup"><span data-stu-id="353ce-134">Create a role capability file</span></span>

<span data-ttu-id="353ce-135">可使用 [New-PSRoleCapabilityFile](/powershell/module/microsoft.powershell.core/new-psrolecapabilityfile?view=powershell-6) cmdlet 创建新的 PowerShell 角色功能文件。</span><span class="sxs-lookup"><span data-stu-id="353ce-135">You can create a new PowerShell role capability file with the [New-PSRoleCapabilityFile](/powershell/module/microsoft.powershell.core/new-psrolecapabilityfile?view=powershell-6) cmdlet.</span></span>

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

<span data-ttu-id="353ce-136">应编辑生成的角色功能文件，以允许角色所需的命令。</span><span class="sxs-lookup"><span data-stu-id="353ce-136">The resulting role capability file should be edited to allow the commands required for the role.</span></span> <span data-ttu-id="353ce-137">PowerShell 帮助文档包括文件配置方式的多个示例。</span><span class="sxs-lookup"><span data-stu-id="353ce-137">The PowerShell help documentation contains several examples of how you can configure the file.</span></span>

### <a name="allowing-powershell-cmdlets-and-functions"></a><span data-ttu-id="353ce-138">允许 PowerShell cmdlet 和函数</span><span class="sxs-lookup"><span data-stu-id="353ce-138">Allowing PowerShell cmdlets and functions</span></span>

<span data-ttu-id="353ce-139">若要授权用户运行 PowerShell cmdlet 或函数，请将 cmdlet 或函数名称添加到 VisibleCmdlets 或 VisibleFunctions 字段。</span><span class="sxs-lookup"><span data-stu-id="353ce-139">To authorize users to run PowerShell cmdlets or functions, add the cmdlet or function name to the VisibleCmdlets or VisibleFunctions fields.</span></span> <span data-ttu-id="353ce-140">如果不确定命令是 cmdlet 还是函数，可运行 `Get-Command <name>` 并查看输出中的 CommandType 属性  。</span><span class="sxs-lookup"><span data-stu-id="353ce-140">If you aren't sure whether a command is a cmdlet or function, you can run `Get-Command <name>` and check the **CommandType** property in the output.</span></span>

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

<span data-ttu-id="353ce-141">有时，特定 cmdlet 或函数的作用域对用户需求而言过于宽泛。</span><span class="sxs-lookup"><span data-stu-id="353ce-141">Sometimes the scope of a specific cmdlet or function is too broad for your users' needs.</span></span> <span data-ttu-id="353ce-142">例如，DNS 管理员可能只需进行访问来重启 DNS 服务。</span><span class="sxs-lookup"><span data-stu-id="353ce-142">A DNS admin, for example, probably only needs access to restart the DNS service.</span></span> <span data-ttu-id="353ce-143">在多租户环境中，租户可访问自助服务管理工具。</span><span class="sxs-lookup"><span data-stu-id="353ce-143">In multi-tenant environments, tenants have access to self-service management tools.</span></span> <span data-ttu-id="353ce-144">应将租户限制为管理其自己的资源。</span><span class="sxs-lookup"><span data-stu-id="353ce-144">Tenants should be limited to managing their own resources.</span></span> <span data-ttu-id="353ce-145">对于这些情况，可限制 cmdlet 或函数中公开的参数。</span><span class="sxs-lookup"><span data-stu-id="353ce-145">For these cases, you can restrict which parameters are exposed from the cmdlet or function.</span></span>

```powershell
VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}
```

<span data-ttu-id="353ce-146">在更高级的场景中，可能还需要限制用户面向这些参数使用的值。</span><span class="sxs-lookup"><span data-stu-id="353ce-146">In more advanced scenarios, you may also need to restrict the values a user may use with these parameters.</span></span> <span data-ttu-id="353ce-147">通过角色功能，可定义一组值，也可定义一种正则表达式模式来确定允许哪些输入。</span><span class="sxs-lookup"><span data-stu-id="353ce-147">Role capabilities let you define a set of values or a regular expression pattern that determine what input is allowed.</span></span>

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> <span data-ttu-id="353ce-148">即使限制可用参数，仍始终允许使用[常用 PowerShell 参数](/powershell/module/microsoft.powershell.core/about/about_commonparameters)。</span><span class="sxs-lookup"><span data-stu-id="353ce-148">The [common PowerShell parameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters) are always allowed, even if you restrict the available parameters.</span></span>
> <span data-ttu-id="353ce-149">不可在参数字段中明确列出这些参数。</span><span class="sxs-lookup"><span data-stu-id="353ce-149">You should not explicitly list them in the Parameters field.</span></span>

<span data-ttu-id="353ce-150">下表介绍自定义可见 cmdlet 或函数的各种方式。</span><span class="sxs-lookup"><span data-stu-id="353ce-150">The table below describes the various ways you can customize a visible cmdlet or function.</span></span>
<span data-ttu-id="353ce-151">可在 VisibleCmdlets 字段中将以下任何内容进行组合和配对  。</span><span class="sxs-lookup"><span data-stu-id="353ce-151">You can mix and match any of the below in the **VisibleCmdlets** field.</span></span>

|                                           <span data-ttu-id="353ce-152">示例</span><span class="sxs-lookup"><span data-stu-id="353ce-152">Example</span></span>                                           |                                                             <span data-ttu-id="353ce-153">用例</span><span class="sxs-lookup"><span data-stu-id="353ce-153">Use case</span></span>                                                              |
| ------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="353ce-154">`'My-Func'` 或 `@{ Name = 'My-Func' }`</span><span class="sxs-lookup"><span data-stu-id="353ce-154">`'My-Func'` or `@{ Name = 'My-Func' }`</span></span>                                                      | <span data-ttu-id="353ce-155">允许用户运行 `My-Func` 且不限制参数。</span><span class="sxs-lookup"><span data-stu-id="353ce-155">Allows the user to run `My-Func` without any restrictions on the parameters.</span></span>                                                      |
| `'MyModule\My-Func'`                                                                        | <span data-ttu-id="353ce-156">允许用户通过模块 `MyModule` 运行 `My-Func` 且不限制参数。</span><span class="sxs-lookup"><span data-stu-id="353ce-156">Allows the user to run `My-Func` from the module `MyModule` without any restrictions on the parameters.</span></span>                           |
| `'My-*'`                                                                                    | <span data-ttu-id="353ce-157">允许用户使用谓词 `My` 运行任意 cmdlet 或函数。</span><span class="sxs-lookup"><span data-stu-id="353ce-157">Allows the user to run any cmdlet or function with the verb `My`.</span></span>                                                                 |
| `'*-Func'`                                                                                  | <span data-ttu-id="353ce-158">允许用户使用名词 `Func` 运行任意 cmdlet 或函数。</span><span class="sxs-lookup"><span data-stu-id="353ce-158">Allows the user to run any cmdlet or function with the noun `Func`.</span></span>                                                               |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`              | <span data-ttu-id="353ce-159">允许用户使用 `Param1` 和 `Param2` 参数运行 `My-Func`。</span><span class="sxs-lookup"><span data-stu-id="353ce-159">Allows the user to run `My-Func` with the `Param1` and `Param2` parameters.</span></span> <span data-ttu-id="353ce-160">可向参数提供任何值。</span><span class="sxs-lookup"><span data-stu-id="353ce-160">Any value can be supplied to the parameters.</span></span>          |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}` | <span data-ttu-id="353ce-161">允许用户使用 `Param1` 参数运行 `My-Func`。</span><span class="sxs-lookup"><span data-stu-id="353ce-161">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="353ce-162">仅可向该参数提供“Value1”和“Value2”。</span><span class="sxs-lookup"><span data-stu-id="353ce-162">Only "Value1" and "Value2" can be supplied to the parameter.</span></span>        |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`    | <span data-ttu-id="353ce-163">允许用户使用 `Param1` 参数运行 `My-Func`。</span><span class="sxs-lookup"><span data-stu-id="353ce-163">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="353ce-164">可向参数提供以“contoso”开头的任意值。</span><span class="sxs-lookup"><span data-stu-id="353ce-164">Any value starting with "contoso" can be supplied to the parameter.</span></span> |

> [!WARNING]
> <span data-ttu-id="353ce-165">最佳的安全做法是，建议在定义可见 cmdlet 或函数时不要使用通配符。</span><span class="sxs-lookup"><span data-stu-id="353ce-165">For best security practices, it is not recommended to use wildcards when defining visible cmdlets or functions.</span></span> <span data-ttu-id="353ce-166">相反，应明确列出每个受信任的命令，确保共享同一命名方案的其他命令均未在无意中获得授权。</span><span class="sxs-lookup"><span data-stu-id="353ce-166">Instead, you should explicitly list each trusted command to ensure no other commands that share the same naming scheme are unintentionally authorized.</span></span>

<span data-ttu-id="353ce-167">无法向同一 cmdlet 或函数同时应用 ValidatePattern 和 ValidateSet   。</span><span class="sxs-lookup"><span data-stu-id="353ce-167">You can't apply both a **ValidatePattern** and **ValidateSet** to the same cmdlet or function.</span></span>

<span data-ttu-id="353ce-168">若如此操作，ValidatePattern 会覆盖 ValidateSet   。</span><span class="sxs-lookup"><span data-stu-id="353ce-168">If you do, the **ValidatePattern** overrides the **ValidateSet**.</span></span>

<span data-ttu-id="353ce-169">有关 ValidatePattern 的详细信息，请参阅[“你好，脚本专家”博文](https://devblogs.microsoft.com/scripting/validate-powershell-parameters-before-running-the-script/)和 [PowerShell 正则表达式](/powershell/module/microsoft.powershell.core/about/about_regular_expressions)参考内容   。</span><span class="sxs-lookup"><span data-stu-id="353ce-169">For more information about **ValidatePattern**, check out [this *Hey, Scripting Guy!* post](https://devblogs.microsoft.com/scripting/validate-powershell-parameters-before-running-the-script/) and the [PowerShell Regular Expressions](/powershell/module/microsoft.powershell.core/about/about_regular_expressions) reference content.</span></span>

### <a name="allowing-external-commands-and-powershell-scripts"></a><span data-ttu-id="353ce-170">允许使用外部命令和 PowerShell 脚本</span><span class="sxs-lookup"><span data-stu-id="353ce-170">Allowing external commands and PowerShell scripts</span></span>

<span data-ttu-id="353ce-171">要使用户能在 JEA 会话中运行可执行文件和 PowerShell 脚本 (.ps1)，必须在 VisibleExternalCommands 字段中添加每个程序的完整路径  。</span><span class="sxs-lookup"><span data-stu-id="353ce-171">To allow users to run executables and PowerShell scripts (.ps1) in a JEA session, you have to add the full path to each program in the **VisibleExternalCommands** field.</span></span>

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

<span data-ttu-id="353ce-172">如果可能，建议使用你授权的任意外部可执行文件的 PowerShell cmdlet 或函数等效项，因为你可控制允许 PowerShell cmdlet 和函数使用哪些参数。</span><span class="sxs-lookup"><span data-stu-id="353ce-172">Where possible, to use PowerShell cmdlet or function equivalents for any external executables you authorize since you have control over the parameters allowed with PowerShell cmdlets and functions.</span></span>

<span data-ttu-id="353ce-173">通过很多可执行文件，可读取当前状态，随后再通过提供其他参数来更改它。</span><span class="sxs-lookup"><span data-stu-id="353ce-173">Many executables allow you to read the current state and then change it by providing different parameters.</span></span>

<span data-ttu-id="353ce-174">例如，考虑使用文件服务器管理员的角色，它可管理系统托管的网络共享。</span><span class="sxs-lookup"><span data-stu-id="353ce-174">For example, consider the role of a file server admin that manages network shares hosted on a system.</span></span> <span data-ttu-id="353ce-175">管理共享的一种方法是使用 `net share`。</span><span class="sxs-lookup"><span data-stu-id="353ce-175">One way of managing shares is to use `net share`.</span></span> <span data-ttu-id="353ce-176">但是，允许 net.exe 会带来风险，因为用户可使用该命令获取 `net group Administrators unprivilegedjeauser /add` 的管理员权限  。</span><span class="sxs-lookup"><span data-stu-id="353ce-176">However, allowing **net.exe** is dangerous because the user could use the command to gain admin privileges with `net group Administrators unprivilegedjeauser /add`.</span></span> <span data-ttu-id="353ce-177">更安全的选项是允许使用 [Get-SmbShare](/powershell/module/smbshare/get-smbshare)，该命令可实现相同的结果，但范围更受限制。</span><span class="sxs-lookup"><span data-stu-id="353ce-177">A more secure option is to allow [Get-SmbShare](/powershell/module/smbshare/get-smbshare), which achieves the same result but has a much more limited scope.</span></span>

<span data-ttu-id="353ce-178">使外部命令可供用户在 JEA 会话中使用时，始终指定可执行文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="353ce-178">When making external commands available to users in a JEA session, always specify the complete path to the executable.</span></span> <span data-ttu-id="353ce-179">这可防止执行位于系统上其他位置的同名潜在恶意程序。</span><span class="sxs-lookup"><span data-stu-id="353ce-179">This prevents the execution of similarly named and potentially malicious programs located elsewhere on the system.</span></span>

### <a name="allowing-access-to-powershell-providers"></a><span data-ttu-id="353ce-180">允许访问 PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="353ce-180">Allowing access to PowerShell providers</span></span>

<span data-ttu-id="353ce-181">默认情况下，PowerShell 提供程序均不适用于 JEA 会话。</span><span class="sxs-lookup"><span data-stu-id="353ce-181">By default, no PowerShell providers are available in JEA sessions.</span></span> <span data-ttu-id="353ce-182">这可降低向连接用户泄漏敏感信息和配置设置的风险。</span><span class="sxs-lookup"><span data-stu-id="353ce-182">This reduces the risk of sensitive information and configuration settings being disclosed to the connecting user.</span></span>

<span data-ttu-id="353ce-183">必要时，可使用 `VisibleProviders` 命令允许访问 PowerShell 提供程序。</span><span class="sxs-lookup"><span data-stu-id="353ce-183">When necessary, you can allow access to the PowerShell providers using the `VisibleProviders` command.</span></span> <span data-ttu-id="353ce-184">有关提供程序的完整列表，请运行 `Get-PSProvider`。</span><span class="sxs-lookup"><span data-stu-id="353ce-184">For a full list of providers, run `Get-PSProvider`.</span></span>

```powershell
VisibleProviders = 'Registry'
```

<span data-ttu-id="353ce-185">对于需要访问文件系统、注册表、证书存储或其他敏感提供程序的简单任务，可考虑编写将代表用户使用提供程序的自定义函数。</span><span class="sxs-lookup"><span data-stu-id="353ce-185">For simple tasks that require access to the file system, registry, certificate store, or other sensitive providers, consider writing a custom function that works with the provider on the user's behalf.</span></span> <span data-ttu-id="353ce-186">JEA 会话中可用的函数、cmdlet 和外部程序所遵循的约束与 JEA 不同。</span><span class="sxs-lookup"><span data-stu-id="353ce-186">The functions, cmdlets, and external programs available in a JEA session aren't subject to the same constraints as JEA.</span></span> <span data-ttu-id="353ce-187">默认情况下，它们可访问任意提供程序。</span><span class="sxs-lookup"><span data-stu-id="353ce-187">They can access any provider by default.</span></span> <span data-ttu-id="353ce-188">如果需要将文件复制到 JEA 终结点或从中复制文件，还可考虑使用[用户驱动器](session-configurations.md#user-drive)。</span><span class="sxs-lookup"><span data-stu-id="353ce-188">Also consider using the [user drive](session-configurations.md#user-drive) when copying files to or from a JEA endpoint is required.</span></span>

### <a name="creating-custom-functions"></a><span data-ttu-id="353ce-189">创建自定义函数</span><span class="sxs-lookup"><span data-stu-id="353ce-189">Creating custom functions</span></span>

<span data-ttu-id="353ce-190">可在角色功能文件中创作自定义函数，简化最终用户的复杂任务。</span><span class="sxs-lookup"><span data-stu-id="353ce-190">You can author custom functions in a role capability file to simplify complex tasks for your end users.</span></span> <span data-ttu-id="353ce-191">如果需要 cmdlet 参数值的高级验证逻辑时，自定义函数也很有用。</span><span class="sxs-lookup"><span data-stu-id="353ce-191">Custom functions are also useful when you require advanced validation logic for cmdlet parameter values.</span></span> <span data-ttu-id="353ce-192">可在 **FunctionDefinitions** 字段中编写简单函数：</span><span class="sxs-lookup"><span data-stu-id="353ce-192">You can write simple functions in the **FunctionDefinitions** field:</span></span>

```powershell
VisibleFunctions = 'Get-TopProcess'

FunctionDefinitions = @{
    Name = 'Get-TopProcess'

    ScriptBlock = {
        param($Count = 10)

        Get-Process | Sort-Object -Property CPU -Descending |
            Microsoft.PowerShell.Utility\Select-Object -First $Count
    }
}
```

> [!IMPORTANT]
> <span data-ttu-id="353ce-193">不要忘记向 **VisibleFunctions** 字段添加自定义函数的名称，使其可由 JEA 用户运行。</span><span class="sxs-lookup"><span data-stu-id="353ce-193">Don't forget to add the name of your custom functions to the **VisibleFunctions** field so they can be run by the JEA users.</span></span>

<span data-ttu-id="353ce-194">自定义函数的主体（脚本块）在系统的默认语言模式下运行，不受 JEA 的语言约束。</span><span class="sxs-lookup"><span data-stu-id="353ce-194">The body (script block) of custom functions runs in the default language mode for the system and isn't subject to JEA's language constraints.</span></span> <span data-ttu-id="353ce-195">这意味着函数可访问文件系统和注册表，并可运行角色功能文件中隐藏的命令。</span><span class="sxs-lookup"><span data-stu-id="353ce-195">This means that functions can access the file system and registry, and run commands that weren't made visible in the role capability file.</span></span> <span data-ttu-id="353ce-196">请注意避免在使用参数时运行任意代码。</span><span class="sxs-lookup"><span data-stu-id="353ce-196">Take care to avoid running arbitrary code when using parameters.</span></span> <span data-ttu-id="353ce-197">避免将用户输入直接传输到 `Invoke-Expression` 等 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="353ce-197">Avoid piping user input directly into cmdlets like `Invoke-Expression`.</span></span>

<span data-ttu-id="353ce-198">在上例中，可注意到使用的是完全限定的模块名称 (FQMN) `Microsoft.PowerShell.Utility\Select-Object`，而非速记 `Select-Object`。</span><span class="sxs-lookup"><span data-stu-id="353ce-198">In the above example, notice that the fully qualified module name (FQMN) `Microsoft.PowerShell.Utility\Select-Object` was used instead of the shorthand `Select-Object`.</span></span>
<span data-ttu-id="353ce-199">角色功能文件中定义的函数仍受限于 JEA 会话的作用域，这包括 JEA 创建用于约束现有命令的代理函数。</span><span class="sxs-lookup"><span data-stu-id="353ce-199">Functions defined in role capability files are still subject to the scope of JEA sessions, which includes the proxy functions JEA creates to constrain existing commands.</span></span>

<span data-ttu-id="353ce-200">默认情况下，`Select-Object` 是所有 JEA 会话中受约束的 cmdlet，不允许选择对象的任意属性。</span><span class="sxs-lookup"><span data-stu-id="353ce-200">By default, `Select-Object` is a constrained cmdlet in all JEA sessions that doesn't allow the selection of arbitrary properties on objects.</span></span> <span data-ttu-id="353ce-201">若要在函数中使用不受约束的 `Select-Object`，必须使用 FQMN 显式请求完整的实现。</span><span class="sxs-lookup"><span data-stu-id="353ce-201">To use the unconstrained `Select-Object` in functions, you must explicitly request the full implementation using the FQMN.</span></span> <span data-ttu-id="353ce-202">通过函数调用 JEA 会话中任何受约束的 cmdlet 时，它都具有相同的约束。</span><span class="sxs-lookup"><span data-stu-id="353ce-202">Any constrained cmdlet in a JEA session has the same constraints when invoked from a function.</span></span> <span data-ttu-id="353ce-203">有关详细信息，请参阅 [about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence)。</span><span class="sxs-lookup"><span data-stu-id="353ce-203">For more information, see [about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence).</span></span>

<span data-ttu-id="353ce-204">如果正在编写多个自定义函数，将其放到 PowerShell 脚本模块中可能更方便。</span><span class="sxs-lookup"><span data-stu-id="353ce-204">If you're writing several custom functions, it's more convenient to put them in a PowerShell script module.</span></span> <span data-ttu-id="353ce-205">与使用内置模块和第三方模块时一样，可使用 VisibleFunctions 字段使这些函数在 JEA 会话中可见  。</span><span class="sxs-lookup"><span data-stu-id="353ce-205">You make those functions visible in the JEA session using the **VisibleFunctions** field like you would with built-in and third-party modules.</span></span>

<span data-ttu-id="353ce-206">为了使 tab 自动补全在 JEA 会话中正常工作，必须在 VisibleFunctions 列表中包含内置函数 `tabexpansion2`  。</span><span class="sxs-lookup"><span data-stu-id="353ce-206">For tab completion to work properly in JEA sessions you must include the built-in function `tabexpansion2` in the **VisibleFunctions** list.</span></span>

## <a name="place-role-capabilities-in-a-module"></a><span data-ttu-id="353ce-207">在模块中放置角色功能</span><span class="sxs-lookup"><span data-stu-id="353ce-207">Place role capabilities in a module</span></span>

<span data-ttu-id="353ce-208">为使 PowerShell 能找到角色功能文件，必须将其存储在 PowerShell 模块的“RoleCapabilities”文件夹中  。</span><span class="sxs-lookup"><span data-stu-id="353ce-208">In order for PowerShell to find a role capability file, it must be stored in a **RoleCapabilities** folder in a PowerShell module.</span></span> <span data-ttu-id="353ce-209">该模块可存储在 `$env:PSModulePath` 环境变量内附的任何文件夹中，但不得放在 System32 中，也不得放到不受信的连接用户可在其中修改文件的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="353ce-209">The module can be stored in any folder included in the `$env:PSModulePath` environment variable, however you shouldn't place it in System32 or a folder where the untrusted, connecting users could modify the files.</span></span> <span data-ttu-id="353ce-210">下例说明了如何在 `$env:ProgramFiles` 路径中创建名为 ContosoJEA 的基本 PowerShell 脚本模块  。</span><span class="sxs-lookup"><span data-stu-id="353ce-210">Below is an example of creating a basic PowerShell script module called **ContosoJEA** in the `$env:ProgramFiles` path.</span></span>

```powershell
# Create a folder for the module
$modulePath = Join-Path $env:ProgramFiles "WindowsPowerShell\Modules\ContosoJEA"
New-Item -ItemType Directory -Path $modulePath

# Create an empty script module and module manifest.
# At least one file in the module folder must have the same name as the folder itself.
New-Item -ItemType File -Path (Join-Path $modulePath "ContosoJEAFunctions.psm1")
New-ModuleManifest -Path (Join-Path $modulePath "ContosoJEA.psd1") -RootModule "ContosoJEAFunctions.psm1"

# Create the RoleCapabilities folder and copy in the PSRC file
$rcFolder = Join-Path $modulePath "RoleCapabilities"
New-Item -ItemType Directory $rcFolder
Copy-Item -Path .\MyFirstJEARole.psrc -Destination $rcFolder
```

<span data-ttu-id="353ce-211">有关 PowerShell 模块的详细信息，请参阅[了解 PowerShell 模块](/powershell/developer/windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="353ce-211">For more information about PowerShell modules, see [Understanding a PowerShell Module](/powershell/developer/windows-powershell).</span></span>

## <a name="updating-role-capabilities"></a><span data-ttu-id="353ce-212">更新角色功能</span><span class="sxs-lookup"><span data-stu-id="353ce-212">Updating role capabilities</span></span>

<span data-ttu-id="353ce-213">可编辑角色功能文件，以便随时更新设置。</span><span class="sxs-lookup"><span data-stu-id="353ce-213">You can edit a role capability file to update the settings at any time.</span></span> <span data-ttu-id="353ce-214">角色功能更新后启动的任意新 JEA 会话均可反映出修订后的功能。</span><span class="sxs-lookup"><span data-stu-id="353ce-214">Any new JEA sessions started after the role capability has been updated will reflect the revised capabilities.</span></span>

<span data-ttu-id="353ce-215">这就是有必要控制角色功能文件夹的访问权限的原因。</span><span class="sxs-lookup"><span data-stu-id="353ce-215">This is why controlling access to the role capabilities folder is so important.</span></span> <span data-ttu-id="353ce-216">只能允许高度受信任的管理员更改角色功能文件。</span><span class="sxs-lookup"><span data-stu-id="353ce-216">Only highly trusted administrators should be allowed to change role capability files.</span></span> <span data-ttu-id="353ce-217">如果不受信任的用户可更改角色功能文件，则其可轻松向自己授予 cmdlet 访问权限，便于提升自身权限。</span><span class="sxs-lookup"><span data-stu-id="353ce-217">If an untrusted user can change role capability files, they can easily give themselves access to cmdlets that allow them to elevate their privileges.</span></span>

<span data-ttu-id="353ce-218">对于想要锁定角色功能访问权限的管理员，请确保本地系统具有角色功能文件的访问权限且包含相关模块。</span><span class="sxs-lookup"><span data-stu-id="353ce-218">For administrators looking to lock down access to the role capabilities, ensure Local System has read access to the role capability files and containing modules.</span></span>

## <a name="how-role-capabilities-are-merged"></a><span data-ttu-id="353ce-219">如何合并角色功能</span><span class="sxs-lookup"><span data-stu-id="353ce-219">How role capabilities are merged</span></span>

<span data-ttu-id="353ce-220">用户进入 JEA 会话时，获得访问[会话配置文件](session-configurations.md)中所有匹配的角色功能的权限。</span><span class="sxs-lookup"><span data-stu-id="353ce-220">Users are granted access to all matching role capabilities in the [session configuration file](session-configurations.md) when they enter a JEA session.</span></span> <span data-ttu-id="353ce-221">JEA 尝试为用户提供所有角色允许的最宽松的命令集。</span><span class="sxs-lookup"><span data-stu-id="353ce-221">JEA tries to give the user the most permissive set of commands allowed by any of the roles.</span></span>

### <a name="visiblecmdlets-and-visiblefunctions"></a><span data-ttu-id="353ce-222">VisibleCmdlets 和 VisibleFunctions</span><span class="sxs-lookup"><span data-stu-id="353ce-222">VisibleCmdlets and VisibleFunctions</span></span>

<span data-ttu-id="353ce-223">最复杂的合并逻辑会影响 cmdlet 和函数，会在 JEA 中限制其参数和参数值。</span><span class="sxs-lookup"><span data-stu-id="353ce-223">The most complex merge logic affects cmdlets and functions, which can have their parameters and parameter values limited in JEA.</span></span>

<span data-ttu-id="353ce-224">规则如下：</span><span class="sxs-lookup"><span data-stu-id="353ce-224">The rules are as follows:</span></span>

1. <span data-ttu-id="353ce-225">如果 cmdlet 仅在一个角色中可见，其对具有任意适用参数约束的用户可见。</span><span class="sxs-lookup"><span data-stu-id="353ce-225">If a cmdlet is only made visible in one role, it is visible to the user with any applicable parameter constraints.</span></span>
2. <span data-ttu-id="353ce-226">如果 cmdlet 在多个角色中可见，并且每个角色在该 cmdlet 上具有相同的约束，则该 cmdlet 对具有这些约束的用户可见。</span><span class="sxs-lookup"><span data-stu-id="353ce-226">If a cmdlet is made visible in more than one role, and each role has the same constraints on the cmdlet, the cmdlet is visible to the user with those constraints.</span></span>
3. <span data-ttu-id="353ce-227">如果 cmdlet 在多个角色中可见，并且每个角色允许使用一组不同的参数，则该 cmdlet 及其在每个角色中定义的所有参数都对用户可见。</span><span class="sxs-lookup"><span data-stu-id="353ce-227">If a cmdlet is made visible in more than one role, and each role allows a different set of parameters, the cmdlet and all the parameters defined across every role are visible to the user.</span></span>
   <span data-ttu-id="353ce-228">如果一个角色没有参数约束，则允许使用所有参数。</span><span class="sxs-lookup"><span data-stu-id="353ce-228">If one role doesn't have constraints on the parameters, all parameters are allowed.</span></span>
4. <span data-ttu-id="353ce-229">如果一个角色定义 cmdlet 参数的验证集或验证模式，另一角色允许使用该参数但不约束参数值，则忽略此验证集或验证模式。</span><span class="sxs-lookup"><span data-stu-id="353ce-229">If one role defines a validate set or validate pattern for a cmdlet parameter, and the other role allows the parameter but does not constrain the parameter values, the validate set or pattern is ignored.</span></span>
5. <span data-ttu-id="353ce-230">如果在多个角色中定义了同一个 cmdlet 参数的验证集，则所有验证集中的所有值均可用。</span><span class="sxs-lookup"><span data-stu-id="353ce-230">If a validate set is defined for the same cmdlet parameter in more than one role, all values from all validate sets are allowed.</span></span>
6. <span data-ttu-id="353ce-231">如果在多个角色中定义了同一个 cmdlet 参数的验证模式，则与任何模式匹配的任何值均可用。</span><span class="sxs-lookup"><span data-stu-id="353ce-231">If a validate pattern is defined for the same cmdlet parameter in more than one role, any values that match any of the patterns are allowed.</span></span>
7. <span data-ttu-id="353ce-232">如果在一个或多个角色中定义验证集，在另一角色中定义相同 cmdlet 参数的验证模式，则将忽略应用于剩余验证模式的验证集和规则 (6)。</span><span class="sxs-lookup"><span data-stu-id="353ce-232">If a validate set is defined in one or more roles, and a validate pattern is defined in another role for the same cmdlet parameter, the validate set is ignored and rule (6) applies to the remaining validate patterns.</span></span>

<span data-ttu-id="353ce-233">以下是如何根据这些规则合并角色的示例：</span><span class="sxs-lookup"><span data-stu-id="353ce-233">Below is an example of how roles are merged according to these rules:</span></span>

```powershell
# Role A Visible Cmdlets
$roleA = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client' } }
}

# Role B Visible Cmdlets
$roleB = @{
    VisibleCmdlets = @{ Name = 'Get-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidatePattern = 'DNS.*' } },
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Server' } }
}

# Resulting permissions for a user who belongs to both role A and B
# - The constraint in role B for the DisplayName parameter on Get-Service
#   is ignored because of rule #4
# - The ValidateSets for Restart-Service are merged because both roles use
#   ValidateSet on the same parameter per rule #5
$mergedAandB = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DNS Server' } }
}
```

### <a name="visibleexternalcommands-visiblealiases-visibleproviders-scriptstoprocess"></a><span data-ttu-id="353ce-234">VisibleExternalCommands、VisibleAliases、VisibleProviders 和 ScriptsToProcess</span><span class="sxs-lookup"><span data-stu-id="353ce-234">VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess</span></span>

<span data-ttu-id="353ce-235">角色功能文件中的所有其他字段均添加到一组集中，其中包含可允许使用的外部命令、别名、提供程序和启动脚本。</span><span class="sxs-lookup"><span data-stu-id="353ce-235">All other fields in the role capability file are added to a cumulative set of allowable external commands, aliases, providers, and startup scripts.</span></span> <span data-ttu-id="353ce-236">一个角色功能中提供的任何命令、别名、提供程序或脚本均可供 JEA 用户使用。</span><span class="sxs-lookup"><span data-stu-id="353ce-236">Any command, alias, provider, or script available in one role capability is available to the JEA user.</span></span>

<span data-ttu-id="353ce-237">请务必确保在某角色功能的提供程序和另一角色功能的 cmdlet/函数/命令共同构成的组合集中，禁止用户意外访问系统资源。</span><span class="sxs-lookup"><span data-stu-id="353ce-237">Be careful to ensure that the combined set of providers from one role capability and cmdlets/functions/commands from another don't allow users unintentional access to system resources.</span></span>
<span data-ttu-id="353ce-238">例如，如果一个角色允许使用 `Remove-Item` cmdlet，而另一角色允许 `FileSystem` 提供程序，则 JEA 用户可能会删除计算机上的任意文件。</span><span class="sxs-lookup"><span data-stu-id="353ce-238">For example, if one role allows the `Remove-Item` cmdlet and another allows the `FileSystem` provider, you are at risk of a JEA user deleting arbitrary files on your computer.</span></span> <span data-ttu-id="353ce-239">要详细了解如何确定用户的有效权限，可参阅[审核 JEA](audit-and-report.md) 一文。</span><span class="sxs-lookup"><span data-stu-id="353ce-239">Additional information about identifying users' effective permissions can be found in the [auditing JEA](audit-and-report.md) article.</span></span>

## <a name="next-steps"></a><span data-ttu-id="353ce-240">后续步骤</span><span class="sxs-lookup"><span data-stu-id="353ce-240">Next steps</span></span>

[<span data-ttu-id="353ce-241">创建会话配置文件</span><span class="sxs-lookup"><span data-stu-id="353ce-241">Create a session configuration file</span></span>](session-configurations.md)