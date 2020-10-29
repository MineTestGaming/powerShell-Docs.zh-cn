---
ms.date: 10/21/2020
keywords: powershell,cmdlet
title: 编写可移植模块
description: 本文介绍如何创建新模块或更新现有模块，使其能够跨 PowerShell 支持的平台工作。
ms.openlocfilehash: 6d5c36263c3c6d1219f963cea2e94ae92b07e863
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500787"
---
# <a name="portable-modules"></a><span data-ttu-id="e5c1c-104">可移植模块</span><span class="sxs-lookup"><span data-stu-id="e5c1c-104">Portable Modules</span></span>

<span data-ttu-id="e5c1c-105">Windows PowerShell 是为 [.NET Framework][] 编写的，而 PowerShell Core 是为 [.NET Core][] 编写的。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-105">Windows PowerShell is written for [.NET Framework][] while PowerShell Core is written for [.NET Core][].</span></span> <span data-ttu-id="e5c1c-106">可移植模块是同时适用于 Windows PowerShell 和 PowerShell Core 的模块。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-106">Portable modules are modules that work in both Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="e5c1c-107">虽然 .Net Framework 和 .Net Core 高度兼容，但它们之间的可用 API 有所不同。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-107">While .NET Framework and .NET Core are highly compatible, there are differences in the available APIs between the two.</span></span> <span data-ttu-id="e5c1c-108">Windows PowerShell 和 PowerShell Core 中的可用 API 也有所不同。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-108">There are also differences in the APIs available in Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="e5c1c-109">打算在这两种环境中使用的模块需要了解这些差异。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-109">Modules intended to be used in both environments need to be aware of these differences.</span></span>

## <a name="porting-an-existing-module"></a><span data-ttu-id="e5c1c-110">移植现有模块</span><span class="sxs-lookup"><span data-stu-id="e5c1c-110">Porting an existing module</span></span>

### <a name="porting-a-pssnapin"></a><span data-ttu-id="e5c1c-111">移植 PSSnapIn</span><span class="sxs-lookup"><span data-stu-id="e5c1c-111">Porting a PSSnapIn</span></span>

<span data-ttu-id="e5c1c-112">PowerShell [SnapIns](/powershell/scripting/developer/cmdlet/modules-and-snap-ins) 在 PowerShell Core 中不受支持。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-112">PowerShell [SnapIns](/powershell/scripting/developer/cmdlet/modules-and-snap-ins) aren't supported in PowerShell Core.</span></span> <span data-ttu-id="e5c1c-113">然而，将 PSSnapIn 转换为 PowerShell 模块非常简单。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-113">However, it's trivial to convert a PSSnapIn to a PowerShell module.</span></span> <span data-ttu-id="e5c1c-114">通常，PSSnapIn 注册代码位于派生自 [PSSnapIn][] 的类的单个源文件中。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-114">Typically, the PSSnapIn registration code is in a single source file of a class that derives from [PSSnapIn][].</span></span> <span data-ttu-id="e5c1c-115">从生成中删除此源文件；不再需要该文件。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-115">Remove this source file from the build; it's no longer needed.</span></span>

<span data-ttu-id="e5c1c-116">使用 [New-ModuleManifest][] 创建一个新的模块清单，进而无需 PSSnapIn 注册代码。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-116">Use [New-ModuleManifest][] to create a new module manifest that replaces the need for the PSSnapIn registration code.</span></span> <span data-ttu-id="e5c1c-117">**PSSnapIn** 中的某些值（例如 **Description** ）可以在模块清单中重复使用。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-117">Some of the values from the **PSSnapIn** (such as **Description** ) can be reused within the module manifest.</span></span>

<span data-ttu-id="e5c1c-118">模块清单中的 **RootModule** 属性应设置为实施 cmdlet 的程序集 (dll) 的名称。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-118">The **RootModule** property in the module manifest should be set to the name of the assembly (dll) implementing the cmdlets.</span></span>

### <a name="the-net-portability-analyzer-aka-apiport"></a><span data-ttu-id="e5c1c-119">.NET 可移植性分析器 （又称 APIPort）</span><span class="sxs-lookup"><span data-stu-id="e5c1c-119">The .NET Portability Analyzer (aka APIPort)</span></span>

<span data-ttu-id="e5c1c-120">若要移植为 Windows PowerShell 编写的模块以使用 PowerShell Core，可以从 [.NET 可移植性分析器][]开始。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-120">To port modules written for Windows PowerShell to work with PowerShell Core, start with the [.NET Portability Analyzer][].</span></span> <span data-ttu-id="e5c1c-121">对编译后的程序集运行此工具，以确定模块中使用的 .NET API 是否与 .NET Framework、.NET Core 以及其他 .NET 运行时兼容。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-121">Run this tool against your compiled assembly to determine if the .NET APIs used in the module are compatible with .NET Framework, .NET Core, and other .NET runtimes.</span></span> <span data-ttu-id="e5c1c-122">工具将建议使用替代 API（若存在）。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-122">The tool suggests alternate APIs if they exist.</span></span> <span data-ttu-id="e5c1c-123">否则，可能需要添加[运行时检查][]并限制特定运行时中不可用的功能。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-123">Otherwise, you may need to add [runtime checks][] and restrict capabilities not available in specific runtimes.</span></span>

## <a name="creating-a-new-module"></a><span data-ttu-id="e5c1c-124">创建新模块</span><span class="sxs-lookup"><span data-stu-id="e5c1c-124">Creating a new module</span></span>

<span data-ttu-id="e5c1c-125">如果创建一个新模块，建议使用 [.NET CLI][]。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-125">If creating a new module, the recommendation is to use the [.NET CLI][].</span></span>

### <a name="installing-the-powershell-standard-module-template"></a><span data-ttu-id="e5c1c-126">安装 PowerShell Standard 模块模板</span><span class="sxs-lookup"><span data-stu-id="e5c1c-126">Installing the PowerShell Standard module template</span></span>

<span data-ttu-id="e5c1c-127">安装 .NET CLI 后，请安装模板库以生成一个简单的 PowerShell 模块。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-127">Once the .NET CLI is installed, install a template library to generate a simple PowerShell module.</span></span>
<span data-ttu-id="e5c1c-128">该模块将与 Windows PowerShell、PowerShell Core、Windows、Linux 和 macOS 兼容。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-128">The module will be compatible with Windows PowerShell, PowerShell Core, Windows, Linux, and macOS.</span></span>

<span data-ttu-id="e5c1c-129">下面的示例演示如何安装模板：</span><span class="sxs-lookup"><span data-stu-id="e5c1c-129">The following example shows how to install the template:</span></span>

```powershell
dotnet new -i Microsoft.PowerShell.Standard.Module.Template
```

```output
  Restoring packages for C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\restore.csproj...
  Installing Microsoft.PowerShell.Standard.Module.Template 0.1.3.
  Generating MSBuild file C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\obj\restore.csproj.nuget.g.props.
  Generating MSBuild file C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\obj\restore.csproj.nuget.g.targets.
  Restore completed in 1.66 sec for C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\restore.csproj.

Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.
  -n, --name          The name for the output being created. If no name is specified, the name of the current directory is used.
  -o, --output        Location to place the generated output.
  -i, --install       Installs a source or a template pack.
  -u, --uninstall     Uninstalls a source or a template pack.
  --nuget-source      Specifies a NuGet source to use during install.
  --type              Filters templates based on available types. Predefined values are "project", "item" or "other".
  --force             Forces content to be generated even if it would change existing files.
  -lang, --language   Filters templates based on language and specifies the language of the template to create.


Templates                        Short Name         Language          Tags
-----------------------------------------------------------------------------------------------
Console Application              console            [C#], F#, VB      Common/Console
Class library                    classlib           [C#], F#, VB      Common/Library
PowerShell Standard Module       psmodule           [C#]              Library/PowerShell/Module
...
```

### <a name="creating-a-new-module-project"></a><span data-ttu-id="e5c1c-130">创建新模块项目</span><span class="sxs-lookup"><span data-stu-id="e5c1c-130">Creating a new module project</span></span>

<span data-ttu-id="e5c1c-131">安装模板后，可以使用该模板创建一个新的 PowerShell 模块项目。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-131">After the template is installed, you can create a new PowerShell module project using that template.</span></span> <span data-ttu-id="e5c1c-132">在此示例中，示例模块名为“myModule”。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-132">In this example, the sample module is called 'myModule'.</span></span>

```
PS> mkdir myModule

    Directory: C:\Users\Steve

Mode LastWriteTime Length Name
---- ------------- ------ ----
d----- 8/3/2018 2:41 PM myModule

PS> cd myModule
PS C:\Users\Steve\myModule> dotnet new psmodule

The template "PowerShell Standard Module" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\Users\Steve\myModule\myModule.csproj...
  Restoring packages for C:\Users\Steve\myModule\myModule.csproj...
  Installing PowerShellStandard.Library 5.1.0.
  Generating MSBuild file C:\Users\Steve\myModule\obj\myModule.csproj.nuget.g.props.
  Generating MSBuild file C:\Users\Steve\myModule\obj\myModule.csproj.nuget.g.targets.
  Restore completed in 1.76 sec for C:\Users\Steve\myModule\myModule.csproj.

Restore succeeded.
```

### <a name="building-the-module"></a><span data-ttu-id="e5c1c-133">生成模块</span><span class="sxs-lookup"><span data-stu-id="e5c1c-133">Building the module</span></span>

<span data-ttu-id="e5c1c-134">使用标准 .NET CLI 命令来生成项目。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-134">Use standard .NET CLI commands to build the project.</span></span>

```powershell
dotnet build
```

```output
PS C:\Users\Steve\myModule> dotnet build
Microsoft (R) Build Engine version 15.7.179.6572 for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 76.85 ms for C:\Users\Steve\myModule\myModule.csproj.
  myModule -> C:\Users\Steve\myModule\bin\Debug\netstandard2.0\myModule.dll

Build succeeded.
    0 Warning(s)
    0 Error(s)

Time Elapsed 00:00:05.40
```

### <a name="testing-the-module"></a><span data-ttu-id="e5c1c-135">测试模块</span><span class="sxs-lookup"><span data-stu-id="e5c1c-135">Testing the module</span></span>

<span data-ttu-id="e5c1c-136">在生成模块之后，可以导入它并执行示例 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-136">After building the module, you can import it and execute the sample cmdlet.</span></span>

```powershell
Import-Module .\bin\Debug\netstandard2.0\myModule.dll
Test-SampleCmdlet -?
Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat
```

```output
NAME
    Test-SampleCmdlet

SYNTAX
    Test-SampleCmdlet [-FavoriteNumber] <int> [[-FavoritePet] {Cat | Dog | Horse}] [<CommonParameters>]


ALIASES
    None


REMARKS
    None


FavoriteNumber FavoritePet
-------------- -----------
             7 Cat
```

### <a name="debugging-the-module"></a><span data-ttu-id="e5c1c-137">调试模块</span><span class="sxs-lookup"><span data-stu-id="e5c1c-137">Debugging the module</span></span>

<span data-ttu-id="e5c1c-138">有关设置用于调试模块的 Visual Studio Code 的指南，请参阅[使用 Visual Studio Code 调试已编译的 cmdlet][]。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-138">For a guide on setting up Visual Studio Code to debug the module, see [Using Visual Studio Code for debugging compiled cmdlets][].</span></span>

## <a name="supporting-technologies"></a><span data-ttu-id="e5c1c-139">支持技术</span><span class="sxs-lookup"><span data-stu-id="e5c1c-139">Supporting technologies</span></span>

<span data-ttu-id="e5c1c-140">以下各节详细说明了此模板使用的一些技术。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-140">The following sections describe in detail some of the technologies used by this template.</span></span>

### <a name="net-standard-library"></a><span data-ttu-id="e5c1c-141">.NET Standard 库</span><span class="sxs-lookup"><span data-stu-id="e5c1c-141">.NET Standard Library</span></span>

<span data-ttu-id="e5c1c-142">[.NET Standard][] 是可在所有 .NET 实现中使用的 .NET API 的正式规范。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-142">[.NET Standard][] is a formal specification of .NET APIs that are available in all .NET implementations.</span></span> <span data-ttu-id="e5c1c-143">以 .NET Standard 为目标的托管代码适用于与该版本的 .NET Standard 兼容的 .NET Framework 和 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-143">Managed code targeting .NET Standard works with the .NET Framework and .NET Core versions that are compatible with that version of the .NET Standard.</span></span>

> [!NOTE]
> <span data-ttu-id="e5c1c-144">尽管 .Net Standard 中可能存在 API，但 .Net Core 中的 API 实现可能会在运行时引发 `PlatformNotSupportedException`，因此，要验证与 Windows PowerShell 和 PowerShell Core 的兼容性，最佳做法是在这两个环境中运行模块测试。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-144">Although an API may exist in .NET Standard, the API implementation in .NET Core may throw a `PlatformNotSupportedException` at runtime, so to verify compatibility with Windows PowerShell and PowerShell Core, the best practice is to run tests for your module within both environments.</span></span>
> <span data-ttu-id="e5c1c-145">如果模块是跨平台的，还可以在 Linux 和 macOS 上运行测试。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-145">Also run tests on Linux and macOS if your module is intended to be cross-platform.</span></span>

<span data-ttu-id="e5c1c-146">以 .Net Standard 为目标有助于确保随着模块的发展，不会意外地将不兼容的 API 引入到模块中。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-146">Targeting .NET Standard helps ensure that, as the module evolves, incompatible APIs don't accidentally get introduced into the module.</span></span> <span data-ttu-id="e5c1c-147">不兼容性是在编译时而不是运行时发现的。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-147">Incompatibilities are discovered at compile time instead of runtime.</span></span>

<span data-ttu-id="e5c1c-148">但是，只要使用兼容 API，则不需要以 .NET Standard 为目标来让模块来同时适用于 Windows PowerShell 和 PowerShell Core。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-148">However, it isn't required to target .NET Standard for a module to work with both Windows PowerShell and PowerShell Core, as long as you use compatible APIs.</span></span> <span data-ttu-id="e5c1c-149">中间语言 (IL) 在两个运行时之间是兼容的。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-149">The Intermediate Language (IL) is compatible between the two runtimes.</span></span> <span data-ttu-id="e5c1c-150">可面向 .Net Framework 4.6.1，它与 .Net Standard 2.0 兼容。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-150">You can target .NET Framework 4.6.1, which is compatible with .NET Standard 2.0.</span></span> <span data-ttu-id="e5c1c-151">如果不使用 .Net Standard 2.0 之外的 API，模块将适用于 PowerShell Core 6，而无需重新编译。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-151">If you don't use APIs outside of .NET Standard 2.0, then your module works with PowerShell Core 6 without recompilation.</span></span>

### <a name="powershell-standard-library"></a><span data-ttu-id="e5c1c-152">PowerShell Standard 库</span><span class="sxs-lookup"><span data-stu-id="e5c1c-152">PowerShell Standard Library</span></span>

<span data-ttu-id="e5c1c-153">[PowerShell Standard][] 库是 PowerShell API 的正式规范，适用于所有大于或等于该标准版本的 PowerShell 版本。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-153">The [PowerShell Standard][] library is a formal specification of PowerShell APIs available in all PowerShell versions greater than or equal to the version of that standard.</span></span>

<span data-ttu-id="e5c1c-154">例如，[PowerShell Standard 5.1][] 与 Windows PowerShell 5.1 和 PowerShell Core 6.0 或更新版本兼容。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-154">For example, [PowerShell Standard 5.1][] is compatible with both Windows PowerShell 5.1 and PowerShell Core 6.0 or newer.</span></span>

<span data-ttu-id="e5c1c-155">建议使用 PowerShell Standard 库编译模块。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-155">We recommend you compile your module using PowerShell Standard Library.</span></span> <span data-ttu-id="e5c1c-156">该库确保 API 同时适用于 Windows PowerShell 和 PowerShell Core 6 并可在两者中实现。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-156">The library ensures the APIs are available and implemented in both Windows PowerShell and PowerShell Core 6.</span></span>
<span data-ttu-id="e5c1c-157">PowerShell Standard 旨在始终向前兼容。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-157">PowerShell Standard is intended to always be forwards-compatible.</span></span> <span data-ttu-id="e5c1c-158">使用 PowerShell Standard 库 5.1 生成的模块将始终与 PowerShell 的未来版本兼容。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-158">A module built using PowerShell Standard Library 5.1 will always be compatible with future versions of PowerShell.</span></span>

### <a name="module-manifest"></a><span data-ttu-id="e5c1c-159">模块清单</span><span class="sxs-lookup"><span data-stu-id="e5c1c-159">Module Manifest</span></span>

#### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a><span data-ttu-id="e5c1c-160">指示与 Windows PowerShell 和 PowerShell Core 的兼容性</span><span class="sxs-lookup"><span data-stu-id="e5c1c-160">Indicating Compatibility With Windows PowerShell and PowerShell Core</span></span>

<span data-ttu-id="e5c1c-161">在验证模块同时适用于 Windows PowerShell 和 PowerShell Core 之后，模块清单应使用 [CompatiblePSEditions][] 属性显式指示兼容性。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-161">After validating that your module works with both Windows PowerShell and PowerShell Core, the module manifest should explicitly indicate compatibility by using the [CompatiblePSEditions][] property.</span></span> <span data-ttu-id="e5c1c-162">值 `Desktop` 表示模块与 Windows PowerShell 兼容，而值 `Core` 表示模块与 PowerShell Core 兼容。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-162">A value of `Desktop` means that the module is compatible with Windows PowerShell, while a value of `Core` means that the module is compatible with PowerShell Core.</span></span> <span data-ttu-id="e5c1c-163">同时包含 `Desktop` 和 `Core` 意味着该模块同时与 Windows PowerShell 和 PowerShell Core 兼容。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-163">Including both `Desktop` and `Core` means that the module is compatible with both Windows PowerShell and PowerShell Core.</span></span>

> [!NOTE]
> <span data-ttu-id="e5c1c-164">`Core` 并不自动意味着模块与 Windows、Linux 和 macOS 兼容。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-164">`Core` does not automatically mean that the module is compatible with Windows, Linux, and macOS.</span></span>
> <span data-ttu-id="e5c1c-165">PowerShell v5 中引入了 CompatiblePSEditions  属性。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-165">The **CompatiblePSEditions** property was introduced in PowerShell v5.</span></span> <span data-ttu-id="e5c1c-166">在 PowerShell v5 之前的版本中，将无法加载使用 CompatiblePSEditions  属性的模块清单。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-166">Module manifests that use the **CompatiblePSEditions** property fail to load in versions prior to PowerShell v5.</span></span>

### <a name="indicating-os-compatibility"></a><span data-ttu-id="e5c1c-167">指示操作系统兼容性</span><span class="sxs-lookup"><span data-stu-id="e5c1c-167">Indicating OS Compatibility</span></span>

<span data-ttu-id="e5c1c-168">首先，验证模块是否适用于 Linux和 macOS。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-168">First, validate that your module works on Linux and macOS.</span></span> <span data-ttu-id="e5c1c-169">接下来，在模块清单中指示与这些操作系统的兼容性。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-169">Next, indicate compatibility with those operating systems in the module manifest.</span></span> <span data-ttu-id="e5c1c-170">这使得用户在发布到 [PowerShell 库][]时可以更轻松地找到适用于其操作系统的模块。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-170">This makes it easier for users to find your module for their operating system when published to the [PowerShell Gallery][].</span></span>

<span data-ttu-id="e5c1c-171">在模块清单中，`PrivateData` 属性有一个 `PSData` 子属性。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-171">Within the module manifest, the `PrivateData` property has a `PSData` sub-property.</span></span> <span data-ttu-id="e5c1c-172">`PSData` 的可选 `Tags` 属性采用一组在 PowerShell 库中显示的值。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-172">The optional `Tags` property of `PSData` takes an array of values that show up in PowerShell Gallery.</span></span> <span data-ttu-id="e5c1c-173">PowerShell 库支持以下兼容性值：</span><span class="sxs-lookup"><span data-stu-id="e5c1c-173">The PowerShell Gallery supports the following compatibility values:</span></span>

| <span data-ttu-id="e5c1c-174">标记</span><span class="sxs-lookup"><span data-stu-id="e5c1c-174">Tag</span></span>               | <span data-ttu-id="e5c1c-175">说明</span><span class="sxs-lookup"><span data-stu-id="e5c1c-175">Description</span></span>                                |
|-------------------|--------------------------------------------|
| <span data-ttu-id="e5c1c-176">PSEdition_Core</span><span class="sxs-lookup"><span data-stu-id="e5c1c-176">PSEdition_Core</span></span>    | <span data-ttu-id="e5c1c-177">与 PowerShell Core 6 兼容</span><span class="sxs-lookup"><span data-stu-id="e5c1c-177">Compatible with PowerShell Core 6</span></span>          |
| <span data-ttu-id="e5c1c-178">PSEdition_Desktop</span><span class="sxs-lookup"><span data-stu-id="e5c1c-178">PSEdition_Desktop</span></span> | <span data-ttu-id="e5c1c-179">与 Windows PowerShell 兼容</span><span class="sxs-lookup"><span data-stu-id="e5c1c-179">Compatible with Windows PowerShell</span></span>         |
| <span data-ttu-id="e5c1c-180">Windows</span><span class="sxs-lookup"><span data-stu-id="e5c1c-180">Windows</span></span>           | <span data-ttu-id="e5c1c-181">与 Windows 兼容</span><span class="sxs-lookup"><span data-stu-id="e5c1c-181">Compatible with Windows</span></span>                    |
| <span data-ttu-id="e5c1c-182">Linux</span><span class="sxs-lookup"><span data-stu-id="e5c1c-182">Linux</span></span>             | <span data-ttu-id="e5c1c-183">与 Linux（无特定发行版）兼容</span><span class="sxs-lookup"><span data-stu-id="e5c1c-183">Compatible with Linux (no specific distro)</span></span> |
| <span data-ttu-id="e5c1c-184">macOS</span><span class="sxs-lookup"><span data-stu-id="e5c1c-184">macOS</span></span>             | <span data-ttu-id="e5c1c-185">与 macOS 兼容</span><span class="sxs-lookup"><span data-stu-id="e5c1c-185">Compatible with macOS</span></span>                      |

<span data-ttu-id="e5c1c-186">示例：</span><span class="sxs-lookup"><span data-stu-id="e5c1c-186">Example:</span></span>

```powershell
@{
    GUID = "4ae9fd46-338a-459c-8186-07f910774cb8"
    Author = "Microsoft Corporation"
    CompanyName = "Microsoft Corporation"
    Copyright = "(C) Microsoft Corporation. All rights reserved."
    HelpInfoUri = "https://go.microsoft.com/fwlink/?linkid=855962"
    ModuleVersion = "1.2.4"
    PowerShellVersion = "3.0"
    ClrVersion = "4.0"
    RootModule = "PackageManagement.psm1"
    Description = 'PackageManagement (a.k.a. OneGet) is a new way to discover and install software packages from around the web.
 It is a manager or multiplexer of existing package managers (also called package providers) that unifies Windows package management with a single Windows PowerShell interface. With PackageManagement, you can do the following.
  - Manage a list of software repositories in which packages can be searched, acquired and installed
  - Discover software packages
  - Seamlessly install, uninstall, and inventory packages from one or more software repositories'

    CmdletsToExport = @(
        'Find-Package',
        'Get-Package',
        'Get-PackageProvider',
        'Get-PackageSource',
        'Install-Package',
        'Import-PackageProvider'
        'Find-PackageProvider'
        'Install-PackageProvider'
        'Register-PackageSource',
        'Set-PackageSource',
        'Unregister-PackageSource',
        'Uninstall-Package'
        'Save-Package'
    )

    FormatsToProcess  = @('PackageManagement.format.ps1xml')

    PrivateData = @{
        PSData = @{
            Tags = @('PackageManagement', 'PSEdition_Core', 'PSEdition_Desktop', 'Windows', 'Linux', 'macOS')
            ProjectUri = 'https://oneget.org'
        }
    }
}
```

### <a name="dependency-on-native-libraries"></a><span data-ttu-id="e5c1c-187">本机库的依赖项</span><span class="sxs-lookup"><span data-stu-id="e5c1c-187">Dependency on Native Libraries</span></span>

<span data-ttu-id="e5c1c-188">旨在跨不同操作系统或处理器体系结构使用的模块可能依赖于托管库，而托管库本身又依赖于一些本机库。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-188">Modules intended for use across different operating systems or processor architectures may depend on a managed library that itself depends on some native libraries.</span></span>

<span data-ttu-id="e5c1c-189">在使用 PowerShell 7 之前，必须使用自定义代码来加载适当的本机 dll，以便托管库能够正确找到它。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-189">Prior to PowerShell 7, one would have to have custom code to load the appropriate native dll so that the managed library can find it correctly.</span></span>

<span data-ttu-id="e5c1c-190">借助 PowerShell 7，可以在托管库位置（在 [.NET RID 目录][]表示法的子集后面）的子文件夹中搜索要加载的本机二进制文件。</span><span class="sxs-lookup"><span data-stu-id="e5c1c-190">With PowerShell 7, native binaries to load are searched in sub-folders within the managed library's location following a subset of the [.NET RID Catalog][] notation.</span></span>

```
managed.dll folder
    |
    |--- 'win-x64' folder
    |       |--- native.dll
    |
    |--- 'win-x86' folder
    |       |--- native.dll
    |
    |--- 'win-arm' folder
    |       |--- native.dll
    |
    |--- 'win-arm64' folder
    |       |--- native.dll
    |
    |--- 'linux-x64' folder
    |       |--- native.so
    |
    |--- 'linux-x86' folder
    |       |--- native.so
    |
    |--- 'linux-arm' folder
    |       |--- native.so
    |
    |--- 'linux-arm64' folder
    |       |--- native.so
    |
    |--- 'osx-x64' folder
    |       |--- native.dylib
```

<!-- reference links -->
[.NET Framework]: /dotnet/framework/
[.NET Core]: /dotnet/core/
[PSSnapIn]: /dotnet/api/system.management.automation.pssnapin
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[运行时检查]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[runtime checks]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[.NET CLI]: /dotnet/core/tools/?tabs=netcore2x
[使用 Visual Studio Code 调试已编译的 cmdlet]: vscode/using-vscode-for-debugging-compiled-cmdlets.md
[Using Visual Studio Code for debugging compiled cmdlets]: vscode/using-vscode-for-debugging-compiled-cmdlets.md
[.NET Standard]: /dotnet/standard/net-standard
[PowerShell Standard]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[PowerShell 库]: https://www.powershellgallery.com
[PowerShell Gallery]: https://www.powershellgallery.com
[.NET 可移植性分析器]: https://github.com/Microsoft/dotnet-apiport
[.NET Portability Analyzer]: https://github.com/Microsoft/dotnet-apiport
[CompatiblePSEditions]: /powershell/scripting/gallery/concepts/module-psedition-support
[.NET RID 目录]: /dotnet/core/rid-catalog
[.NET RID Catalog]: /dotnet/core/rid-catalog
