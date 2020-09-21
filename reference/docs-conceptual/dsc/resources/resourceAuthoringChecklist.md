---
ms.date: 07/08/2020
keywords: dsc,powershell,配置,安装程序
title: 资源创作清单
ms.openlocfilehash: f21e2e8563880e0c10cf50b044e9c56ca09fe0fa
ms.sourcegitcommit: d26e2237397483c6333abcf4331bd82f2e72b4e3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2020
ms.locfileid: "86217638"
---
# <a name="resource-authoring-checklist"></a><span data-ttu-id="3061d-103">资源创作清单</span><span class="sxs-lookup"><span data-stu-id="3061d-103">Resource authoring checklist</span></span>

<span data-ttu-id="3061d-104">此清单是创作新 DSC 资源时的最佳做法的列表。</span><span class="sxs-lookup"><span data-stu-id="3061d-104">This checklist is a list of best practices when authoring a new DSC Resource.</span></span>

## <a name="resource-module-contains-psd1-file-and-schemamof-for-every-resource"></a><span data-ttu-id="3061d-105">资源模块包含用于所有资源的 .psd1 文件和 schema.mof</span><span class="sxs-lookup"><span data-stu-id="3061d-105">Resource module contains .psd1 file and schema.mof for every resource</span></span>

<span data-ttu-id="3061d-106">检查资源是否具有正确的结构以及是否包含所有所需文件。</span><span class="sxs-lookup"><span data-stu-id="3061d-106">Check that your resource has correct structure and contains all required files.</span></span> <span data-ttu-id="3061d-107">每个资源模块都应包含 .psd1 文件且每个非复合资源都应具有 schema.mof 文件。</span><span class="sxs-lookup"><span data-stu-id="3061d-107">Every resource module should contain a .psd1 file and every non-composite resource should have schema.mof file.</span></span>
<span data-ttu-id="3061d-108">未包含架构的资源不会被 `Get-DscResource` 列出且用户在针对 ISE 中的这些模块写入代码时不能使用 IntelliSense。</span><span class="sxs-lookup"><span data-stu-id="3061d-108">Resources that do not contain schema will not be listed by `Get-DscResource` and users will not be able to use the intellisense when writing code against those modules in ISE.</span></span> <span data-ttu-id="3061d-109">xRemoteFile 资源是 [xPSDesiredStateConfiguration 资源模块](https://github.com/PowerShell/xPSDesiredStateConfiguration)的一部分，其目录结构如下所示：</span><span class="sxs-lookup"><span data-stu-id="3061d-109">The directory structure for xRemoteFile resource, which is part of the [xPSDesiredStateConfiguration resource module](https://github.com/PowerShell/xPSDesiredStateConfiguration), looks as follows:</span></span>

```
xPSDesiredStateConfiguration
    DSCResources
        MSFT_xRemoteFile
            MSFT_xRemoteFile.psm1
            MSFT_xRemoteFile.schema.mof
    Examples
        xRemoteFile_DownloadFile.ps1
    ResourceDesignerScripts
        GenerateXRemoteFileSchema.ps1
    Tests
        ResourceDesignerTests.ps1
    xPSDesiredStateConfiguration.psd1
```

## <a name="resource-and-schema-are-correct"></a><span data-ttu-id="3061d-110">资源和架构正确</span><span class="sxs-lookup"><span data-stu-id="3061d-110">Resource and schema are correct</span></span>

<span data-ttu-id="3061d-111">验证资源架构 (`*.schema.mof`) 文件。</span><span class="sxs-lookup"><span data-stu-id="3061d-111">Verify the resource schema (`*.schema.mof`) file.</span></span> <span data-ttu-id="3061d-112">你可以使用 [DSC 资源设计器](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0)来帮助开发和测试架构。</span><span class="sxs-lookup"><span data-stu-id="3061d-112">You can use the [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) to help develop and test your schema.</span></span> <span data-ttu-id="3061d-113">请确保：</span><span class="sxs-lookup"><span data-stu-id="3061d-113">Make sure that:</span></span>

- <span data-ttu-id="3061d-114">属性类型正确（例如，不将字符串用于接受数值的属性，应改为使用 UInt32 或其他数值类型）</span><span class="sxs-lookup"><span data-stu-id="3061d-114">Property types are correct (e.g. don't use String for properties which accept numeric values, you should use UInt32 or other numeric types instead)</span></span>
- <span data-ttu-id="3061d-115">按以下格式正确指定属性特性：([key], [required], [write], [read])</span><span class="sxs-lookup"><span data-stu-id="3061d-115">Property attributes are specified correctly as: ([key], [required], [write], [read])</span></span>
- <span data-ttu-id="3061d-116">架构中至少有一个参数被标记为 [key]</span><span class="sxs-lookup"><span data-stu-id="3061d-116">At least one parameter in the schema has to be marked as [key]</span></span>
- <span data-ttu-id="3061d-117">[read] 属性不与下列任意一个属性共同存在：[required]、[key]、[write]</span><span class="sxs-lookup"><span data-stu-id="3061d-117">[read] property does not coexist together with any of: [required], [key], [write]</span></span>
- <span data-ttu-id="3061d-118">如果指定了除 [read] 之外的多个限定符，则 [key] 优先级最高</span><span class="sxs-lookup"><span data-stu-id="3061d-118">If multiple qualifiers are specified except [read], then [key] takes precedence</span></span>
- <span data-ttu-id="3061d-119">如果指定了 [write] 和 [required]，则 [required] 优先级更高</span><span class="sxs-lookup"><span data-stu-id="3061d-119">If [write] and [required] are specified, then [required] takes precedence</span></span>
- <span data-ttu-id="3061d-120">在适当的位置指定了 ValueMap。示例：</span><span class="sxs-lookup"><span data-stu-id="3061d-120">ValueMap is specified where appropriate Example:</span></span>

  ```
  [Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
  ```

- <span data-ttu-id="3061d-121">指定了友好名称且符合 DSC 命名约定</span><span class="sxs-lookup"><span data-stu-id="3061d-121">Friendly name is specified and confirms to DSC naming conventions</span></span>

  <span data-ttu-id="3061d-122">示例： `[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]`</span><span class="sxs-lookup"><span data-stu-id="3061d-122">Example: `[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]`</span></span>

- <span data-ttu-id="3061d-123">每个字段的说明均有意义。</span><span class="sxs-lookup"><span data-stu-id="3061d-123">Every field has meaningful description.</span></span> <span data-ttu-id="3061d-124">PowerShell GitHub 存储库中有典型示例，如 [xRemoteFile 的 .schema.mof](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/DSCResources/DSC_xRemoteFile/DSC_xRemoteFile.schema.mof)</span><span class="sxs-lookup"><span data-stu-id="3061d-124">The PowerShell GitHub repository has good examples, such as the [.schema.mof for xRemoteFile](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/DSCResources/DSC_xRemoteFile/DSC_xRemoteFile.schema.mof)</span></span>

<span data-ttu-id="3061d-125">此外，应使用 [DSC 资源设计器](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0)中的 `Test-xDscResource` 和 `Test-xDscSchema` cmdlet 来自动验证资源和架构：</span><span class="sxs-lookup"><span data-stu-id="3061d-125">Additionally, you should use `Test-xDscResource` and `Test-xDscSchema` cmdlets from [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) to automatically verify the resource and schema:</span></span>

```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```

<span data-ttu-id="3061d-126">例如：</span><span class="sxs-lookup"><span data-stu-id="3061d-126">For example:</span></span>

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="resource-loads-without-errors"></a><span data-ttu-id="3061d-127">资源已加载，未出现错误</span><span class="sxs-lookup"><span data-stu-id="3061d-127">Resource loads without errors</span></span>

<span data-ttu-id="3061d-128">检查是否可以成功地加载资源模块。</span><span class="sxs-lookup"><span data-stu-id="3061d-128">Check whether the resource module can be successfully loaded.</span></span> <span data-ttu-id="3061d-129">你可以手动完成检查，方法是运行 `Import-Module <resource_module> -force` 并确认未发生错误，或者可以编写自动化测试用例来进行检查。</span><span class="sxs-lookup"><span data-stu-id="3061d-129">This can be achieved manually, by running `Import-Module <resource_module> -force` and confirming that no errors occurred, or by writing test automation.</span></span> <span data-ttu-id="3061d-130">如果选用后者，则可以在测试用例中遵循此结构：</span><span class="sxs-lookup"><span data-stu-id="3061d-130">In case of the latter, you can follow this structure in your test case:</span></span>

```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw "Module was not imported correctly. Errors returned: $error"
}
```

## <a name="resource-is-idempotent-in-the-positive-case"></a><span data-ttu-id="3061d-131">在正向用例中资源是幂等的</span><span class="sxs-lookup"><span data-stu-id="3061d-131">Resource is idempotent in the positive case</span></span>

<span data-ttu-id="3061d-132">DSC 资源的基本特征之一是幂等性。</span><span class="sxs-lookup"><span data-stu-id="3061d-132">One of the fundamental characteristics of DSC resources is idempotence.</span></span> <span data-ttu-id="3061d-133">这意味着多次应用包含该资源的 DSC 配置将始终获得相同的结果。</span><span class="sxs-lookup"><span data-stu-id="3061d-133">It means that applying a DSC configuration containing that resource multiple times will always achieve the same result.</span></span> <span data-ttu-id="3061d-134">例如，如果创建包含以下文件资源的配置：</span><span class="sxs-lookup"><span data-stu-id="3061d-134">For example, if we create a configuration which contains the following File resource:</span></span>

```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
}
```

<span data-ttu-id="3061d-135">在第一次应用它之后，test.txt 文件应出现在 `C:\test` 文件夹。</span><span class="sxs-lookup"><span data-stu-id="3061d-135">After applying it for the first time, file test.txt should appear in `C:\test` folder.</span></span> <span data-ttu-id="3061d-136">但是，后续运行相同配置时不会更改计算机的状态（例如，不会创建 `test.txt` 文件的任何副本）。</span><span class="sxs-lookup"><span data-stu-id="3061d-136">However, subsequent runs of the same configuration should not change the state of the machine (e.g. no copies of the `test.txt` file should be created).</span></span> <span data-ttu-id="3061d-137">要确保资源是幂等的，可以在直接测试资源时重复调用 `Set-TargetResource`，或在进行端到端测试时多次调用 `Start-DscConfiguration`。</span><span class="sxs-lookup"><span data-stu-id="3061d-137">To ensure a resource is idempotent you can repeatedly call `Set-TargetResource` when testing the resource directly, or call `Start-DscConfiguration` multiple times when doing end to end testing.</span></span> <span data-ttu-id="3061d-138">每次运行后结果都应是相同的。</span><span class="sxs-lookup"><span data-stu-id="3061d-138">The result should be the same after every run.</span></span>

## <a name="test-user-modification-scenario"></a><span data-ttu-id="3061d-139">测试用户修改场景</span><span class="sxs-lookup"><span data-stu-id="3061d-139">Test user modification scenario</span></span>

<span data-ttu-id="3061d-140">通过更改计算机的状态，然后重新运行 DSC，可以验证 `Set-TargetResource` 和 `Test-TargetResource` 是否正常工作。</span><span class="sxs-lookup"><span data-stu-id="3061d-140">By changing the state of the machine and then rerunning DSC, you can verify that `Set-TargetResource` and `Test-TargetResource` function properly.</span></span> <span data-ttu-id="3061d-141">以下是你要采取的步骤：</span><span class="sxs-lookup"><span data-stu-id="3061d-141">Here are steps you should take:</span></span>

1. <span data-ttu-id="3061d-142">从未在所需状态的资源开始。</span><span class="sxs-lookup"><span data-stu-id="3061d-142">Start with the resource not in the desired state.</span></span>
1. <span data-ttu-id="3061d-143">使用资源运行配置</span><span class="sxs-lookup"><span data-stu-id="3061d-143">Run configuration with your resource</span></span>
1. <span data-ttu-id="3061d-144">验证 `Test-DscConfiguration` 是否返回 True</span><span class="sxs-lookup"><span data-stu-id="3061d-144">Verify `Test-DscConfiguration` returns True</span></span>
1. <span data-ttu-id="3061d-145">修改已配置项使其不在期望状态</span><span class="sxs-lookup"><span data-stu-id="3061d-145">Modify the configured item to be out of the desired state</span></span>
1. <span data-ttu-id="3061d-146">验证 `Test-DscConfiguration` 是否返回 false</span><span class="sxs-lookup"><span data-stu-id="3061d-146">Verify `Test-DscConfiguration` returns false</span></span>

<span data-ttu-id="3061d-147">下文介绍使用 Registry 资源的更为具体的示例：</span><span class="sxs-lookup"><span data-stu-id="3061d-147">Here's a more concrete example using Registry resource:</span></span>

1. <span data-ttu-id="3061d-148">从未在所需状态的注册表项开始</span><span class="sxs-lookup"><span data-stu-id="3061d-148">Start with registry key not in the desired state</span></span>
1. <span data-ttu-id="3061d-149">运行 `Start-DscConfiguration` 及其配置，以将它放入所需状态并验证其是否通过。</span><span class="sxs-lookup"><span data-stu-id="3061d-149">Run `Start-DscConfiguration` with a configuration to put it in the desired state and verify it passes.</span></span>
1. <span data-ttu-id="3061d-150">运行 `Test-DscConfiguration` 并验证它是否返回 true</span><span class="sxs-lookup"><span data-stu-id="3061d-150">Run `Test-DscConfiguration` and verify it returns true</span></span>
1. <span data-ttu-id="3061d-151">修改项的值，使它不在所需状态</span><span class="sxs-lookup"><span data-stu-id="3061d-151">Modify the value of the key so that it is not in the desired state</span></span>
1. <span data-ttu-id="3061d-152">运行 `Test-DscConfiguration` 并验证它是否返回 false</span><span class="sxs-lookup"><span data-stu-id="3061d-152">Run `Test-DscConfiguration` and verify it returns false</span></span>
1. <span data-ttu-id="3061d-153">已使用 `Get-DscConfiguration` 对 `Get-TargetResource` 功能进行了验证</span><span class="sxs-lookup"><span data-stu-id="3061d-153">`Get-TargetResource` functionality was verified using `Get-DscConfiguration`</span></span>

<span data-ttu-id="3061d-154">`Get-TargetResource` 应返回资源的当前状态的详细信息。</span><span class="sxs-lookup"><span data-stu-id="3061d-154">`Get-TargetResource` should return details of the current state of the resource.</span></span> <span data-ttu-id="3061d-155">确保对其进行测试，方法是：在应用该配置之后调用 `Get-DscConfiguration`，并验证输出是否正确反映了计算机的当前状态。</span><span class="sxs-lookup"><span data-stu-id="3061d-155">Make sure to test it by calling `Get-DscConfiguration` after you apply the configuration and verifying that output correctly reflects the current state of the machine.</span></span> <span data-ttu-id="3061d-156">请务必对它进行单独测试，因为在调用 `Start-DscConfiguration` 时此区域的任何问题都不会出现。</span><span class="sxs-lookup"><span data-stu-id="3061d-156">It's important to test it separately, since any issues in this area won't appear when calling `Start-DscConfiguration`.</span></span>

## <a name="call-getsettest-targetresource-functions-directly"></a><span data-ttu-id="3061d-157">直接调用函数 **Get/Set/Test-TargetResource**</span><span class="sxs-lookup"><span data-stu-id="3061d-157">Call **Get/Set/Test-TargetResource** functions directly</span></span>

<span data-ttu-id="3061d-158">请确保对在资源中实现的 `Get/Set/Test-TargetResource` 函数进行测试，可通过直接调用它们并按预期方式进行验证完成此操作。</span><span class="sxs-lookup"><span data-stu-id="3061d-158">Make sure you test the `Get/Set/Test-TargetResource` functions implemented in your resource by calling them directly and verifying that they work as expected.</span></span>

## <a name="verify-end-to-end-using-start-dscconfiguration"></a><span data-ttu-id="3061d-159">使用 Start-DscConfiguration 进行端到端验证</span><span class="sxs-lookup"><span data-stu-id="3061d-159">Verify End to End using Start-DscConfiguration</span></span>

<span data-ttu-id="3061d-160">虽然通过直接调用 `Get/Set/Test-TargetResource` 函数对它们进行测试至关重要，但不是所有问题都能以这种方法发现。</span><span class="sxs-lookup"><span data-stu-id="3061d-160">Testing `Get/Set/Test-TargetResource` functions by calling them directly is important, but not all issues will be discovered this way.</span></span> <span data-ttu-id="3061d-161">你应将测试的关注重心放在使用 `Start-DscConfiguration` 上或请求服务器上。</span><span class="sxs-lookup"><span data-stu-id="3061d-161">You should focus significant part of your testing on using `Start-DscConfiguration` or the pull server.</span></span> <span data-ttu-id="3061d-162">事实上，这就是用户使用资源的方式，所以不要低估此类测试的重要性。</span><span class="sxs-lookup"><span data-stu-id="3061d-162">In fact, this is how users will use the resource, so don't underestimate the significance of this type of tests.</span></span> <span data-ttu-id="3061d-163">可能的问题类型：</span><span class="sxs-lookup"><span data-stu-id="3061d-163">Possible types of issues:</span></span>

- <span data-ttu-id="3061d-164">由于 DSC 代理以服务方式运行，因此凭据/会话的行为可能不同。</span><span class="sxs-lookup"><span data-stu-id="3061d-164">Credential/Session may behave differently because the DSC agent runs as a service.</span></span> <span data-ttu-id="3061d-165">请务必端到端地测试此处的任何功能。</span><span class="sxs-lookup"><span data-stu-id="3061d-165">Be sure to test any features here end to end.</span></span>
- <span data-ttu-id="3061d-166">由 `Start-DscConfiguration` 输出的错误可能与在直接调用 `Set-TargetResource` 函数时显示的错误不同。</span><span class="sxs-lookup"><span data-stu-id="3061d-166">Errors output by `Start-DscConfiguration` may be different than those displayed when calling the `Set-TargetResource` function directly.</span></span>

## <a name="test-compatibility-on-all-dsc-supported-platforms"></a><span data-ttu-id="3061d-167">在所有 DSC 支持的平台上测试兼容性</span><span class="sxs-lookup"><span data-stu-id="3061d-167">Test compatibility on all DSC supported platforms</span></span>

<span data-ttu-id="3061d-168">资源应适用于所有支持 DSC 的平台（Windows Server 2008 R2 或更高版本）。</span><span class="sxs-lookup"><span data-stu-id="3061d-168">Resource should work on all DSC supported platforms (Windows Server 2008 R2 and newer).</span></span> <span data-ttu-id="3061d-169">在操作系统上安装最新的 WMF (Windows Management Framework) 以获取最新版本的 DSC。</span><span class="sxs-lookup"><span data-stu-id="3061d-169">Install the latest WMF (Windows Management Framework) on your OS to get the latest version of DSC.</span></span> <span data-ttu-id="3061d-170">如果资源按设计无法在部分平台上运作，则将返回特定的错误消息。</span><span class="sxs-lookup"><span data-stu-id="3061d-170">If your resource does not work on some of these platforms by design, a specific error message should be returned.</span></span> <span data-ttu-id="3061d-171">此外，确保资源检查你调用的 cmdlet 是否存在于特定的计算机上。</span><span class="sxs-lookup"><span data-stu-id="3061d-171">Also, make sure your resource checks whether cmdlets you are calling are present on particular machine.</span></span> <span data-ttu-id="3061d-172">Windows Server 2012 添加了大量新 cmdlet，即使安装了 WMF，它们在 Windows Server 2008R2 上也不可用。</span><span class="sxs-lookup"><span data-stu-id="3061d-172">Windows Server 2012 added a large number of new cmdlets that are not available on Windows Server 2008R2, even with WMF installed.</span></span>

## <a name="verify-on-windows-client-if-applicable"></a><span data-ttu-id="3061d-173">在 Windows 客户端上验证（如果适用）</span><span class="sxs-lookup"><span data-stu-id="3061d-173">Verify on Windows Client (if applicable)</span></span>

<span data-ttu-id="3061d-174">一个非常常见的测试间隙在于，仅在 Windows 的服务器版本上验证资源。</span><span class="sxs-lookup"><span data-stu-id="3061d-174">One very common test gap is verifying the resource only on server versions of Windows.</span></span> <span data-ttu-id="3061d-175">许多资源也被设计用于客户端 SKU，因此如果你也属于这种情况，请不要忘记在这些平台上测试它。</span><span class="sxs-lookup"><span data-stu-id="3061d-175">Many resources are also designed to work on Client SKUs, so if that's true in your case, don't forget to test it on those platforms as well.</span></span>

## <a name="get-dscresource-lists-the-resource"></a><span data-ttu-id="3061d-176">Get-DSCResource 用于列出资源</span><span class="sxs-lookup"><span data-stu-id="3061d-176">Get-DSCResource lists the resource</span></span>

<span data-ttu-id="3061d-177">部署模块后，调用 `Get-DscResource` 将列出资源等作为结果。</span><span class="sxs-lookup"><span data-stu-id="3061d-177">After deploying the module, calling `Get-DscResource` should list your resource among others as a result.</span></span> <span data-ttu-id="3061d-178">如果无法在列表中找到你的资源，请确保该资源的 schema.mof 文件存在。</span><span class="sxs-lookup"><span data-stu-id="3061d-178">If you can't find your resource in the list, make sure that schema.mof file for that resource exists.</span></span>

## <a name="resource-module-contains-examples"></a><span data-ttu-id="3061d-179">资源模块包含示例</span><span class="sxs-lookup"><span data-stu-id="3061d-179">Resource module contains examples</span></span>

<span data-ttu-id="3061d-180">创建高质量示例可以帮助其他人了解如何使用它。</span><span class="sxs-lookup"><span data-stu-id="3061d-180">Creating quality examples which will help others understand how to use it.</span></span> <span data-ttu-id="3061d-181">这一点至关重要，因为许多用户会将示例代码视为文档。</span><span class="sxs-lookup"><span data-stu-id="3061d-181">This is crucial, especially since many users treat sample code as documentation.</span></span>

- <span data-ttu-id="3061d-182">首先，你应确定要在模块中包含的示例（至少你应涵盖资源的最重要用例）：</span><span class="sxs-lookup"><span data-stu-id="3061d-182">First, you should determine the examples that will be included with the module – at minimum, you should cover most important use cases for your resource:</span></span>
- <span data-ttu-id="3061d-183">如果模块包含几个需要一起用于端到端方案的资源，则最好将基本的端到端示例作为第一个示例。</span><span class="sxs-lookup"><span data-stu-id="3061d-183">If your module contains several resources that need to work together for an end-to-end scenario, the basic end-to-end example would ideally be first.</span></span>
- <span data-ttu-id="3061d-184">最初的示例应非常简单 -- 如何在小的可管理区块中开始使用你的资源（例如，创建新 VHD）</span><span class="sxs-lookup"><span data-stu-id="3061d-184">The initial examples should be very simple -- how to get started with your resources in small manageable chunks (e.g. creating a new VHD)</span></span>
- <span data-ttu-id="3061d-185">随后的示例应该建立在这些示例之上（例如，从 VHD 中创建 VM、删除 VM、修改 VM），且应介绍高级功能（例如，创建具有动态内存的 VM）</span><span class="sxs-lookup"><span data-stu-id="3061d-185">Subsequent examples should build on those examples (e.g. creating a VM from a VHD, removing VM, modifying VM), and show advanced functionality (e.g. creating a VM with dynamic memory)</span></span>
- <span data-ttu-id="3061d-186">示例配置应该参数化（所有的值都应作为参数传递到配置且不能包含硬编码值）：</span><span class="sxs-lookup"><span data-stu-id="3061d-186">Example configurations should be parameterized (all values should be passed to the configuration as parameters and there should be no hardcoded values):</span></span>

```powershell
configuration Sample_xRemoteFile_DownloadFile
{
    param
    (
        [string[]] $nodeName = 'localhost',

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $destinationPath,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $uri,

        [String] $userAgent,

        [Hashtable] $headers
    )

    Import-DscResource -Name MSFT_xRemoteFile -ModuleName xPSDesiredStateConfiguration

    Node $nodeName
    {
        xRemoteFile DownloadFile
        {
            DestinationPath = $destinationPath
            Uri = $uri
            UserAgent = $userAgent
            Headers = $headers
        }
    }
}
```

- <span data-ttu-id="3061d-187">包括（注释掉）关于如何在示例脚本的末尾使用实际值调用配置的示例，就是一个很好的做法。</span><span class="sxs-lookup"><span data-stu-id="3061d-187">It's a good practice to include (commented out) example of how to call the configuration with the actual values at the end of the example script.</span></span> <span data-ttu-id="3061d-188">例如，在上面的配置中，指定 UserAgent 的最佳做法如下所示，但这种最佳做法并非显而易见：</span><span class="sxs-lookup"><span data-stu-id="3061d-188">For example, in the configuration above it isn't necessarily obvious that the best way to specify UserAgent is:</span></span>

  <span data-ttu-id="3061d-189">`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer`：这样，注释可以阐明配置的执行目的：</span><span class="sxs-lookup"><span data-stu-id="3061d-189">`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` In which case a comment can clarify the intended execution of the configuration:</span></span>

```powershell
<#
Sample use (parameter values need to be changed according to your scenario):

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
-userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
#>
```

- <span data-ttu-id="3061d-190">对于每个示例，编写简短说明，解释它能做什么以及参数的意义。</span><span class="sxs-lookup"><span data-stu-id="3061d-190">For each example, write a short description which explains what it does, and the meaning of the parameters.</span></span>
- <span data-ttu-id="3061d-191">确保示例涵盖资源的大部分重要方案，如果没有任何遗漏，验证它们是否都能执行以及是否能让计算机达到所需状态。</span><span class="sxs-lookup"><span data-stu-id="3061d-191">Make sure examples cover most the important scenarios for your resource and if there's nothing missing, verify that they all execute and put machine in the desired state.</span></span>

## <a name="error-messages-are-easy-to-understand-and-help-users-solve-problems"></a><span data-ttu-id="3061d-192">错误消息要易于理解，以便帮助用户解决问题</span><span class="sxs-lookup"><span data-stu-id="3061d-192">Error messages are easy to understand and help users solve problems</span></span>

<span data-ttu-id="3061d-193">好的错误消息应具有以下特性：</span><span class="sxs-lookup"><span data-stu-id="3061d-193">Good error messages should be:</span></span>

- <span data-ttu-id="3061d-194">存在性：错误消息最大的问题在于它们经常不存在，因此应确保它们的确存在。</span><span class="sxs-lookup"><span data-stu-id="3061d-194">There: The biggest problem with error messages is that they often don't exist, so make sure they are there.</span></span>
- <span data-ttu-id="3061d-195">易于理解：人工可读，没有晦涩的错误代码</span><span class="sxs-lookup"><span data-stu-id="3061d-195">Easy to understand: Human readable, no obscure error codes</span></span>
- <span data-ttu-id="3061d-196">精确性：描述问题的具体内容</span><span class="sxs-lookup"><span data-stu-id="3061d-196">Precise: Describe what's exactly the problem</span></span>
- <span data-ttu-id="3061d-197">建设性：建议如何修复问题</span><span class="sxs-lookup"><span data-stu-id="3061d-197">Constructive: Advice how to fix the issue</span></span>
- <span data-ttu-id="3061d-198">礼貌用语：不要责怪用户或让他们感到不舒服</span><span class="sxs-lookup"><span data-stu-id="3061d-198">Polite: Don't blame user or make them feel bad</span></span>

<span data-ttu-id="3061d-199">确保验证端到端方案中的错误（使用 `Start-DscConfiguration`），因为它们可能与直接运行资源函数时返回的错误不同。</span><span class="sxs-lookup"><span data-stu-id="3061d-199">Make sure you verify errors in End to End scenarios (using `Start-DscConfiguration`), because they may differ from those returned when running resource functions directly.</span></span>

## <a name="log-messages-are-easy-to-understand-and-informative-including-verbose-debug-and-etw-logs"></a><span data-ttu-id="3061d-200">日志消息要易于理解且信息量大（包括 –verbose、–debug 和 ETW 日志）</span><span class="sxs-lookup"><span data-stu-id="3061d-200">Log messages are easy to understand and informative (including –verbose, –debug and ETW logs)</span></span>

<span data-ttu-id="3061d-201">确保由资源输出的日志易于理解且向用户提供有价值的信息。</span><span class="sxs-lookup"><span data-stu-id="3061d-201">Ensure that logs outputted by the resource are easy to understand and provide value to the user.</span></span>
<span data-ttu-id="3061d-202">资源应输出所有可能对用户有用的信息，但并不总是日志越多越好。</span><span class="sxs-lookup"><span data-stu-id="3061d-202">Resources should output all information which might be helpful to the user, but more logs is not always better.</span></span> <span data-ttu-id="3061d-203">你应该避免冗余和输出不提供更多价值的数据 - 不要让人为了找到他们要找的内容而浏览成百上千条日志。</span><span class="sxs-lookup"><span data-stu-id="3061d-203">You should avoid redundancy and outputting data which does not provide additional value – don't make someone go through hundreds of log entries in order to find what they're looking for.</span></span> <span data-ttu-id="3061d-204">当然，针对此问题没有任何日志也是不可接受的解决方案。</span><span class="sxs-lookup"><span data-stu-id="3061d-204">Of course, no logs is not an acceptable solution for this problem either.</span></span>

<span data-ttu-id="3061d-205">测试时还应分析 verbose 和 debug 日志（通过合理使用 `–Verbose` 和 `–Debug` 开关运行 `Start-DscConfiguration`）以及 ETW 日志。</span><span class="sxs-lookup"><span data-stu-id="3061d-205">When testing, you should also analyze verbose and debug logs (by running `Start-DscConfiguration` with `–Verbose` and `–Debug` switches appropriately), as well as ETW logs.</span></span> <span data-ttu-id="3061d-206">若要查看 DSC ETW 日志，请转到事件查看器并打开以下文件夹：Applications and Services- Microsoft - Windows - Desired State Configuration。</span><span class="sxs-lookup"><span data-stu-id="3061d-206">To see DSC ETW logs, go to Event Viewer and open the following folder: Applications and Services- Microsoft - Windows - Desired State Configuration.</span></span> <span data-ttu-id="3061d-207">默认情况下设置有“操作”通道，但要确保在运行配置之前启用了“分析”通道和“调试”通道。</span><span class="sxs-lookup"><span data-stu-id="3061d-207">By default there will be Operational channel, but make sure you enable Analytic and Debug channels before running the configuration.</span></span> <span data-ttu-id="3061d-208">若要启用“分析”/“调试”通道，可以执行下面的脚本：</span><span class="sxs-lookup"><span data-stu-id="3061d-208">To enable Analytic/Debug channels, you can execute script below:</span></span>

```powershell
$statusEnabled = $true
# Use "Analytic" to enable Analytic channel
$eventLogFullName = "Microsoft-Windows-Dsc/Debug"
$commandToExecute = "wevtutil set-log $eventLogFullName /e:$statusEnabled /q:$statusEnabled   "
$log = New-Object System.Diagnostics.Eventing.Reader.EventLogConfiguration $eventLogFullName
if($statusEnabled -eq $log.IsEnabled)
{
    Write-Host -Verbose "The channel event log is already enabled"
    return
}
Invoke-Expression $commandToExecute
```

## <a name="resource-implementation-does-not-contain-hardcoded-paths"></a><span data-ttu-id="3061d-209">资源实现不包含硬编码路径</span><span class="sxs-lookup"><span data-stu-id="3061d-209">Resource implementation does not contain hardcoded paths</span></span>

<span data-ttu-id="3061d-210">确保资源实现中没有硬编码路径，特别是如果它们表示语言时 (en-us)，或者当存在可以使用的系统变量时。</span><span class="sxs-lookup"><span data-stu-id="3061d-210">Ensure there are no hardcoded paths in the resource implementation, particularly if they assume language (en-us), or when there are system variables that can be used.</span></span> <span data-ttu-id="3061d-211">如果资源需要访问特定路径，请使用环境变量而非硬编码路径，因为后者在其他计算机上可能有所不同。</span><span class="sxs-lookup"><span data-stu-id="3061d-211">If your resource need to access specific paths, use environment variables instead of hardcoding the path, as it may differ on other machines.</span></span>

<span data-ttu-id="3061d-212">示例：</span><span class="sxs-lookup"><span data-stu-id="3061d-212">Example:</span></span>

<span data-ttu-id="3061d-213">不是：</span><span class="sxs-lookup"><span data-stu-id="3061d-213">Instead of:</span></span>

```powershell
$tempPath = "C:\Users\kkaczma\AppData\Local\Temp\MyResource"
$programFilesPath = "C:\Program Files (x86)"
```

<span data-ttu-id="3061d-214">你可以编写：</span><span class="sxs-lookup"><span data-stu-id="3061d-214">You can write:</span></span>

```powershell
$tempPath = Join-Path $env:temp "MyResource"
$programFilesPath = ${env:ProgramFiles(x86)}
```

## <a name="resource-implementation-does-not-contain-user-information"></a><span data-ttu-id="3061d-215">资源实现不包含用户信息</span><span class="sxs-lookup"><span data-stu-id="3061d-215">Resource implementation does not contain user information</span></span>

<span data-ttu-id="3061d-216">请确保代码中没有电子邮件名称、帐户信息或人员姓名。</span><span class="sxs-lookup"><span data-stu-id="3061d-216">Make sure there are no email names, account information, or names of people in the code.</span></span>

## <a name="resource-was-tested-with-validinvalid-credentials"></a><span data-ttu-id="3061d-217">已使用有效/无效凭据验证了资源</span><span class="sxs-lookup"><span data-stu-id="3061d-217">Resource was tested with valid/invalid credentials</span></span>

<span data-ttu-id="3061d-218">如果资源将凭据作为参数：</span><span class="sxs-lookup"><span data-stu-id="3061d-218">If your resource takes a credential as parameter:</span></span>

- <span data-ttu-id="3061d-219">当本地系统（或远程资源计算机帐户）无访问权限时验证资源是否正常运行。</span><span class="sxs-lookup"><span data-stu-id="3061d-219">Verify the resource works when Local System (or the computer account for remote resources) does not have access.</span></span>
- <span data-ttu-id="3061d-220">使用为 Get、Set 和 Test 指定的凭据验证资源是否正常运行。</span><span class="sxs-lookup"><span data-stu-id="3061d-220">Verify the resource works with a credential specified for Get, Set and Test</span></span>
- <span data-ttu-id="3061d-221">如果资源访问共享，请测试你需要支持的所有变体，例如：</span><span class="sxs-lookup"><span data-stu-id="3061d-221">If your resource accesses shares, test all the variants you need to support, such as:</span></span>
  - <span data-ttu-id="3061d-222">标准 Windows 共享。</span><span class="sxs-lookup"><span data-stu-id="3061d-222">Standard windows shares.</span></span>
  - <span data-ttu-id="3061d-223">DFS 共享。</span><span class="sxs-lookup"><span data-stu-id="3061d-223">DFS shares.</span></span>
  - <span data-ttu-id="3061d-224">SAMBA 共享（如果希望支持 Linux。）</span><span class="sxs-lookup"><span data-stu-id="3061d-224">SAMBA shares (if you want to support Linux.)</span></span>

## <a name="resource-does-not-require-interactive-input"></a><span data-ttu-id="3061d-225">资源不需要交互式输入</span><span class="sxs-lookup"><span data-stu-id="3061d-225">Resource does not require interactive input</span></span>

<span data-ttu-id="3061d-226">应自动执行 `Get/Set/Test-TargetResource` 函数，且不能在任何执行阶段等待用户输入（例如，不能在这些函数中使用 `Get-Credential`）。</span><span class="sxs-lookup"><span data-stu-id="3061d-226">`Get/Set/Test-TargetResource` functions should be executed automatically and must not wait for user's input at any stage of execution (e.g. you should not use `Get-Credential` inside these functions).</span></span> <span data-ttu-id="3061d-227">如果需要提供用户的输入，应在编译阶段期间将它作为参数传递到配置。</span><span class="sxs-lookup"><span data-stu-id="3061d-227">If you need to provide user's input, you should pass it to the configuration as parameter during the compilation phase.</span></span>

## <a name="resource-functionality-was-thoroughly-tested"></a><span data-ttu-id="3061d-228">已全面测试资源功能</span><span class="sxs-lookup"><span data-stu-id="3061d-228">Resource functionality was thoroughly tested</span></span>

<span data-ttu-id="3061d-229">此清单包含要测试的重要项和/或经常丢失的项。</span><span class="sxs-lookup"><span data-stu-id="3061d-229">This checklist contains items which are important to be tested and/or are often missed.</span></span> <span data-ttu-id="3061d-230">提供了一系列测试，主要是特定于你要测试的资源和此处未提及的测试。</span><span class="sxs-lookup"><span data-stu-id="3061d-230">There will be bunch of tests, mainly functional ones which will be specific to the resource you are testing and are not mentioned here.</span></span> <span data-ttu-id="3061d-231">不要忘记负面测试用例。</span><span class="sxs-lookup"><span data-stu-id="3061d-231">Don't forget about negative test cases.</span></span>

## <a name="best-practice-resource-module-contains-tests-folder-with-resourcedesignertestsps1-script"></a><span data-ttu-id="3061d-232">最佳做法：资源模块包含具有 ResourceDesignerTests.ps1 脚本的 Tests 文件夹</span><span class="sxs-lookup"><span data-stu-id="3061d-232">Best practice: Resource module contains Tests folder with ResourceDesignerTests.ps1 script</span></span>

<span data-ttu-id="3061d-233">对于给定模块中的所有资源，最好使用 `Test-xDscResource` 和 `Test-xDscSchema` 在资源模块中创建“Tests”文件夹，创建 `ResourceDesignerTests.ps1` 文件并添加测试。</span><span class="sxs-lookup"><span data-stu-id="3061d-233">It's a good practice to create folder "Tests" inside resource module, create `ResourceDesignerTests.ps1` file and add tests using `Test-xDscResource` and `Test-xDscSchema` for all resources in given module.</span></span> <span data-ttu-id="3061d-234">通过这种方法你可以快速验证给定模块的所有资源的架构，并在发布前执行完整性检查。</span><span class="sxs-lookup"><span data-stu-id="3061d-234">This way you can quickly validate schemas of all resources from the given modules and do a sanity check before publishing.</span></span> <span data-ttu-id="3061d-235">对于 xRemoteFile，`ResourceTests.ps1` 可能和以下情况一样简单：</span><span class="sxs-lookup"><span data-stu-id="3061d-235">For xRemoteFile, `ResourceTests.ps1` could look as simple as:</span></span>

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="best-practice-resource-supports--whatif"></a><span data-ttu-id="3061d-236">最佳做法：资源支持 - WhatIf</span><span class="sxs-lookup"><span data-stu-id="3061d-236">Best practice: Resource supports -WhatIf</span></span>

<span data-ttu-id="3061d-237">如果资源正在执行“危险”操作，最佳做法是实现 `-WhatIf` 功能。</span><span class="sxs-lookup"><span data-stu-id="3061d-237">If your resource is performing "dangerous" operations, it's a good practice to implement `-WhatIf` functionality.</span></span> <span data-ttu-id="3061d-238">完成后，请确保 `-WhatIf` 输出正确地描述了在无 `-WhatIf` 开关情况下执行命令时可能发生的操作。</span><span class="sxs-lookup"><span data-stu-id="3061d-238">After it's done, make sure that `-WhatIf` output correctly describes operations which would happen if command was executed without `-WhatIf` switch.</span></span> <span data-ttu-id="3061d-239">此外，验证当 `–WhatIf` 开关存在时操作是否不会执行（未对节点的状态进行更改）。</span><span class="sxs-lookup"><span data-stu-id="3061d-239">Also, verify that operations does not execute (no changes to the node's state are made) when `–WhatIf` switch is present.</span></span> <span data-ttu-id="3061d-240">例如，假设我们正在测试 File 资源。</span><span class="sxs-lookup"><span data-stu-id="3061d-240">For example, let's assume we are testing File resource.</span></span> <span data-ttu-id="3061d-241">下面是创建 `test.txt` 文件及其“test”内容的简单配置：</span><span class="sxs-lookup"><span data-stu-id="3061d-241">Below is simple configuration which creates file `test.txt` with contents "test":</span></span>

```powershell
configuration config
{
    node localhost
    {
        File file
        {
            Contents="test"
            DestinationPath="C:\test\test.txt"
        }
    }
}
config
```

<span data-ttu-id="3061d-242">如果我们使用 `-WhatIf` 开关进行编译，然后执行配置，则输出将报告运行该配置时具体会发生什么。</span><span class="sxs-lookup"><span data-stu-id="3061d-242">If we compile and then execute the configuration with the `-WhatIf` switch, the output is telling us exactly what would happen when we run the configuration.</span></span> <span data-ttu-id="3061d-243">但是配置本身并没有被执行（没有创建 `test.txt` 文件）。</span><span class="sxs-lookup"><span data-stu-id="3061d-243">The configuration itself however was not executed (`test.txt` file was not created).</span></span>

```powershell
Start-DscConfiguration -Path .\config -ComputerName localhost -Wait -Verbose -WhatIf
```

```Output
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer CHARLESX1 with user sid
S-1-5-21-397955417-626881126-188441444-5179871.
What if: [X]: LCM:  [ Start  Set      ]
What if: [X]: LCM:  [ Start  Resource ]  [[File]file]
What if: [X]: LCM:  [ Start  Test     ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]: LCM:  [ End    Test     ]  [[File]file]  in 0.0270 seconds.
What if: [X]: LCM:  [ Start  Set      ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]:                            [C:\test\test.txt] Creating and writing contents and setting attributes.
What if: [X]: LCM:  [ End    Set      ]  [[File]file]  in 0.0180 seconds.
What if: [X]: LCM:  [ End    Resource ]  [[File]file]
What if: [X]: LCM:  [ End    Set      ]
VERBOSE: [X]: LCM:  [ End    Set      ]    in  0.1050 seconds.
VERBOSE: Operation 'Invoke CimMethod' complete.
```

<span data-ttu-id="3061d-244">此列表并不详尽，但它涵盖了在设计、开发和测试 DSC 资源时会遇到的许多重要问题。</span><span class="sxs-lookup"><span data-stu-id="3061d-244">This list is not exhaustive, but it covers many important issues which can be encountered while designing, developing and testing DSC resources.</span></span>
