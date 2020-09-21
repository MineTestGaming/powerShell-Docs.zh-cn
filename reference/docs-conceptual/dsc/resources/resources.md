---
ms.date: 07/23/2020
keywords: dsc,powershell,配置,安装程序
title: DSC 资源
ms.openlocfilehash: 6ab831c9d423c6189951b43bfab92f800366ceca
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2020
ms.locfileid: "87777922"
---
# <a name="dsc-resources"></a><span data-ttu-id="c2733-103">DSC 资源</span><span class="sxs-lookup"><span data-stu-id="c2733-103">DSC Resources</span></span>

> <span data-ttu-id="c2733-104">适用于 Windows PowerShell 4.0 及更高版本。</span><span class="sxs-lookup"><span data-stu-id="c2733-104">Applies to Windows PowerShell 4.0 and up.</span></span>

## <a name="overview"></a><span data-ttu-id="c2733-105">概述</span><span class="sxs-lookup"><span data-stu-id="c2733-105">Overview</span></span>

<span data-ttu-id="c2733-106">Desired State Configuration (DSC) 资源为 DSC 配置提供构建基块。</span><span class="sxs-lookup"><span data-stu-id="c2733-106">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="c2733-107">资源公开可配置的属性（架构），并包含本地配置管理器 (LCM) 调用以“使其如此”的 PowerShell 脚本函数。</span><span class="sxs-lookup"><span data-stu-id="c2733-107">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="c2733-108">资源的建模对象可以是一般的文件或 Windows 进程，也可以是具体的 IIS 服务器设置。</span><span class="sxs-lookup"><span data-stu-id="c2733-108">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span> <span data-ttu-id="c2733-109">资源等组被组合成为 DSC 模块，模块将全部所需文件组织成为一个可移植结构，该结构包含标志资源既定用途的元数据。</span><span class="sxs-lookup"><span data-stu-id="c2733-109">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="c2733-110">每个资源都具有用于确定使用[配置](../configurations/configurations.md)中的资源所需的语法的 \*架构。</span><span class="sxs-lookup"><span data-stu-id="c2733-110">Each resource has a \*schema that determines the syntax needed to use the resource in a [Configuration](../configurations/configurations.md).</span></span>
<span data-ttu-id="c2733-111">可以按以下方式定义资源的架构：</span><span class="sxs-lookup"><span data-stu-id="c2733-111">A resource's schema can be defined in the following ways:</span></span>

- <span data-ttu-id="c2733-112">`Schema.Mof` 文件：大多数资源使用[托管对象格式](/windows/desktop/wmisdk/managed-object-format--mof-)定义它们在 `schema.mof` 文件中的架构。</span><span class="sxs-lookup"><span data-stu-id="c2733-112">`Schema.Mof` file: Most resources define their _schema_ in a `schema.mof` file, using [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>
- <span data-ttu-id="c2733-113">`<Resource Name>.schema.psm1` 文件：[复合资源](../configurations/compositeConfigs.md)使用[参数块](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters)定义其在 `<ResourceName>.schema.psm1` 文件中的架构。</span><span class="sxs-lookup"><span data-stu-id="c2733-113">`<Resource Name>.schema.psm1` file: [Composite Resources](../configurations/compositeConfigs.md) define their _schema_ in a `<ResourceName>.schema.psm1` file using a [Parameter Block](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span></span>
- <span data-ttu-id="c2733-114">`<Resource Name>.psm1` 文件：基于类的 DSC 资源定义它们在类定义中的架构。</span><span class="sxs-lookup"><span data-stu-id="c2733-114">`<Resource Name>.psm1` file: Class based DSC resources define their _schema_ in the class definition.</span></span> <span data-ttu-id="c2733-115">语法项表示为类属性。</span><span class="sxs-lookup"><span data-stu-id="c2733-115">Syntax items are denoted as Class properties.</span></span> <span data-ttu-id="c2733-116">有关详细信息，请参阅 [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc)。</span><span class="sxs-lookup"><span data-stu-id="c2733-116">For more information, see [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span></span>

<span data-ttu-id="c2733-117">若要检索 DSC 资源的语法，请将 [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet 与 Syntax 参数一起使用。</span><span class="sxs-lookup"><span data-stu-id="c2733-117">To retrieve the syntax for a DSC resource, use the [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet with the **Syntax** parameter.</span></span> <span data-ttu-id="c2733-118">此用法类似于将 [Get-Command](/powershell/module/microsoft.powershell.core/get-command) 与 Syntax 参数一起使用以获取 cmdlet 语法。</span><span class="sxs-lookup"><span data-stu-id="c2733-118">This usage is similar to using [Get-Command](/powershell/module/microsoft.powershell.core/get-command) with the **Syntax** parameter to get cmdlet syntax.</span></span> <span data-ttu-id="c2733-119">所看到的输出将显示用于指定资源的资源块的模板。</span><span class="sxs-lookup"><span data-stu-id="c2733-119">The output you see will show the template used for a resource block for the resource you specify.</span></span>

```powershell
Get-DscResource -Syntax Service
```

<span data-ttu-id="c2733-120">所看到的输出应类似于以下输出，尽管此资源的语法在将来可能会发生改变也是如此。</span><span class="sxs-lookup"><span data-stu-id="c2733-120">The output you see should be similar to the output below, though this resource's syntax could change in the future.</span></span> <span data-ttu-id="c2733-121">类似于 cmdlet 语法，方括号中所示的键是可选的。</span><span class="sxs-lookup"><span data-stu-id="c2733-121">Like cmdlet syntax, the _keys_ seen in square brackets, are optional.</span></span> <span data-ttu-id="c2733-122">类型指定每个键所需的数据类型。</span><span class="sxs-lookup"><span data-stu-id="c2733-122">The types specify the type of data each key expects.</span></span>

> [!NOTE]
> <span data-ttu-id="c2733-123">确保键是可选的，因为它默认为“Present”。</span><span class="sxs-lookup"><span data-stu-id="c2733-123">The **Ensure** key is optional because it defaults to "Present".</span></span>

```output
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

> [!NOTE]
> <span data-ttu-id="c2733-124">在低于 7.0 的 PowerShell 版本中，`Get-DscResource` 找不到基于类的 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="c2733-124">In PowerShell versions below 7.0, `Get-DscResource` does not find Class based DSC resources.</span></span>

<span data-ttu-id="c2733-125">在配置内，Service 资源块可能如下所示以确保 Spooler 服务正在运行。</span><span class="sxs-lookup"><span data-stu-id="c2733-125">Inside a Configuration, a **Service** resource block might look like this to **Ensure** that the Spooler service is running.</span></span>

> [!NOTE]
> <span data-ttu-id="c2733-126">在使用配置中的资源之前，必须使用 [Import-DSCResource](../configurations/import-dscresource.md) 导入该资源。</span><span class="sxs-lookup"><span data-stu-id="c2733-126">Before using a resource in a Configuration, you must import it using [Import-DSCResource](../configurations/import-dscresource.md).</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }
    }
}
```

<span data-ttu-id="c2733-127">配置可以包含同一资源类型的多个实例。</span><span class="sxs-lookup"><span data-stu-id="c2733-127">Configurations can contain multiple instances of the same resource type.</span></span> <span data-ttu-id="c2733-128">每个实例必须具有唯一名称。</span><span class="sxs-lookup"><span data-stu-id="c2733-128">Each instance must be uniquely named.</span></span> <span data-ttu-id="c2733-129">在以下示例中，添加了第二个 Service 资源块以配置“DHCP”服务。</span><span class="sxs-lookup"><span data-stu-id="c2733-129">In the following example, a second **Service** resource block is added to configure the "DHCP" service.</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }

        # To configure a second service resource block, add another Service resource block and use a unique name.
        Service "DHCP:Running"
        {
            Name = "DHCP"
            State = "Running"
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="c2733-130">从 PowerShell 5.0 开始，为 DSC 添加了 IntelliSense。</span><span class="sxs-lookup"><span data-stu-id="c2733-130">Beginning in PowerShell 5.0, IntelliSense was added for DSC.</span></span> <span data-ttu-id="c2733-131">借助这一新功能，可以使用 <kbd>TAB</kbd> 和 <kbd>Ctr</kbd>+<kbd>Space</kbd> 自动补全键名称。</span><span class="sxs-lookup"><span data-stu-id="c2733-131">This new feature allows you to use <kbd>TAB</kbd> and <kbd>Ctr</kbd>+<kbd>Space</kbd> to auto-complete key names.</span></span>

![使用 Tab 自动补全的资源 IntelliSense](media/resources/resource-tabcompletion.png)

## <a name="types-of-resources"></a><span data-ttu-id="c2733-133">资源类型</span><span class="sxs-lookup"><span data-stu-id="c2733-133">Types of resources</span></span>

<span data-ttu-id="c2733-134">Windows 附带内置资源，Linux 具有特定于 OS 的资源。</span><span class="sxs-lookup"><span data-stu-id="c2733-134">Windows comes with built in resources and Linux has OS specific resources.</span></span> <span data-ttu-id="c2733-135">提供[跨节点依赖项](../configurations/crossNodeDependencies.md)的资源、包管理资源以及[由社区拥有和维护的资源](https://github.com/dsccommunity)。</span><span class="sxs-lookup"><span data-stu-id="c2733-135">There are resources for [cross-node dependencies](../configurations/crossNodeDependencies.md), package management resources, as well as[community owned and maintained resources](https://github.com/dsccommunity).</span></span> <span data-ttu-id="c2733-136">可以使用上述步骤确定这些资源的语法以及如何使用这些资源。</span><span class="sxs-lookup"><span data-stu-id="c2733-136">You can use the above steps to determine the syntax of these resources and how to use them.</span></span> <span data-ttu-id="c2733-137">已在“参考”下存档提供这些资源的页面。</span><span class="sxs-lookup"><span data-stu-id="c2733-137">The pages that serve these resources have been archived under **Reference**.</span></span>

### <a name="windows-built-in-resources"></a><span data-ttu-id="c2733-138">Windows 内置资源</span><span class="sxs-lookup"><span data-stu-id="c2733-138">Windows built-in resources</span></span>

- [<span data-ttu-id="c2733-139">存档资源</span><span class="sxs-lookup"><span data-stu-id="c2733-139">Archive Resource</span></span>](../reference/resources/windows/archiveResource.md)
- [<span data-ttu-id="c2733-140">环境资源</span><span class="sxs-lookup"><span data-stu-id="c2733-140">Environment Resource</span></span>](../reference/resources/windows/environmentResource.md)
- [<span data-ttu-id="c2733-141">文件资源</span><span class="sxs-lookup"><span data-stu-id="c2733-141">File Resource</span></span>](../reference/resources/windows/fileResource.md)
- [<span data-ttu-id="c2733-142">组资源</span><span class="sxs-lookup"><span data-stu-id="c2733-142">Group Resource</span></span>](../reference/resources/windows/groupResource.md)
- [<span data-ttu-id="c2733-143">GroupSet 资源</span><span class="sxs-lookup"><span data-stu-id="c2733-143">GroupSet Resource</span></span>](../reference/resources/windows/groupSetResource.md)
- [<span data-ttu-id="c2733-144">日志资源</span><span class="sxs-lookup"><span data-stu-id="c2733-144">Log Resource</span></span>](../reference/resources/windows/logResource.md)
- [<span data-ttu-id="c2733-145">包资源</span><span class="sxs-lookup"><span data-stu-id="c2733-145">Package Resource</span></span>](../reference/resources/windows/packageResource.md)
- [<span data-ttu-id="c2733-146">ProcessSet 资源</span><span class="sxs-lookup"><span data-stu-id="c2733-146">ProcessSet Resource</span></span>](../reference/resources/windows/ProcessSetResource.md)
- [<span data-ttu-id="c2733-147">注册表资源</span><span class="sxs-lookup"><span data-stu-id="c2733-147">Registry Resource</span></span>](../reference/resources/windows/registryResource.md)
- [<span data-ttu-id="c2733-148">脚本资源</span><span class="sxs-lookup"><span data-stu-id="c2733-148">Script Resource</span></span>](../reference/resources/windows/scriptResource.md)
- [<span data-ttu-id="c2733-149">服务资源</span><span class="sxs-lookup"><span data-stu-id="c2733-149">Service Resource</span></span>](../reference/resources/windows/serviceResource.md)
- [<span data-ttu-id="c2733-150">ServiceSet 资源</span><span class="sxs-lookup"><span data-stu-id="c2733-150">ServiceSet Resource</span></span>](../reference/resources/windows/serviceSetResource.md)
- [<span data-ttu-id="c2733-151">用户资源</span><span class="sxs-lookup"><span data-stu-id="c2733-151">User Resource</span></span>](../reference/resources/windows/userResource.md)
- [<span data-ttu-id="c2733-152">WindowsFeature 资源</span><span class="sxs-lookup"><span data-stu-id="c2733-152">WindowsFeature Resource</span></span>](../reference/resources/windows/windowsFeatureResource.md)
- [<span data-ttu-id="c2733-153">WindowsFeatureSet 资源</span><span class="sxs-lookup"><span data-stu-id="c2733-153">WindowsFeatureSet Resource</span></span>](../reference/resources/windows/windowsFeatureSetResource.md)
- [<span data-ttu-id="c2733-154">WindowsOptionalFeature 资源</span><span class="sxs-lookup"><span data-stu-id="c2733-154">WindowsOptionalFeature Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureResource.md)
- [<span data-ttu-id="c2733-155">WindowsOptionalFeatureSet 资源</span><span class="sxs-lookup"><span data-stu-id="c2733-155">WindowsOptionalFeatureSet Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
- [<span data-ttu-id="c2733-156">WindowsPackageCabResource 资源</span><span class="sxs-lookup"><span data-stu-id="c2733-156">WindowsPackageCabResource Resource</span></span>](../reference/resources/windows/windowsPackageCabResource.md)
- [<span data-ttu-id="c2733-157">WindowsProcess 资源</span><span class="sxs-lookup"><span data-stu-id="c2733-157">WindowsProcess Resource</span></span>](../reference/resources/windows/windowsProcessResource.md)

### <a name="cross-node-dependency-resources"></a><span data-ttu-id="c2733-158">跨节点依赖项资源</span><span class="sxs-lookup"><span data-stu-id="c2733-158">Cross-Node dependency resources</span></span>

- [<span data-ttu-id="c2733-159">WaitForAll 资源</span><span class="sxs-lookup"><span data-stu-id="c2733-159">WaitForAll Resource</span></span>](../reference/resources/windows/waitForAllResource.md)
- [<span data-ttu-id="c2733-160">WaitForSome 资源</span><span class="sxs-lookup"><span data-stu-id="c2733-160">WaitForSome Resource</span></span>](../reference/resources/windows/waitForSomeResource.md)
- [<span data-ttu-id="c2733-161">WaitForAny 资源</span><span class="sxs-lookup"><span data-stu-id="c2733-161">WaitForAny Resource</span></span>](../reference/resources/windows/waitForAnyResource.md)

### <a name="package-management-resources"></a><span data-ttu-id="c2733-162">包管理资源</span><span class="sxs-lookup"><span data-stu-id="c2733-162">Package Management resources</span></span>

- [<span data-ttu-id="c2733-163">PackageManagement 资源</span><span class="sxs-lookup"><span data-stu-id="c2733-163">PackageManagement Resource</span></span>](../reference/resources/packagemanagement/PackageManagementDscResource.md)
- [<span data-ttu-id="c2733-164">PackageManagementSource 资源</span><span class="sxs-lookup"><span data-stu-id="c2733-164">PackageManagementSource Resource</span></span>](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

#### <a name="linux-resources"></a><span data-ttu-id="c2733-165">Linux 资源</span><span class="sxs-lookup"><span data-stu-id="c2733-165">Linux resources</span></span>

- [<span data-ttu-id="c2733-166">Linux 存档资源</span><span class="sxs-lookup"><span data-stu-id="c2733-166">Linux Archive Resource</span></span>](../reference/resources/linux/lnxArchiveResource.md)
- [<span data-ttu-id="c2733-167">Linux 环境资源</span><span class="sxs-lookup"><span data-stu-id="c2733-167">Linux Environment Resource</span></span>](../reference/resources/linux/lnxEnvironmentResource.md)
- [<span data-ttu-id="c2733-168">Linux FileLine 资源</span><span class="sxs-lookup"><span data-stu-id="c2733-168">Linux FileLine Resource</span></span>](../reference/resources/linux/lnxFileLineResource.md)
- [<span data-ttu-id="c2733-169">Linux 文件资源</span><span class="sxs-lookup"><span data-stu-id="c2733-169">Linux File Resource</span></span>](../reference/resources/linux/lnxFileResource.md)
- [<span data-ttu-id="c2733-170">Linux 组资源</span><span class="sxs-lookup"><span data-stu-id="c2733-170">Linux Group Resource</span></span>](../reference/resources/linux/lnxGroupResource.md)
- [<span data-ttu-id="c2733-171">Linux 包资源</span><span class="sxs-lookup"><span data-stu-id="c2733-171">Linux Package Resource</span></span>](../reference/resources/linux/lnxPackageResource.md)
- [<span data-ttu-id="c2733-172">Linux 脚本资源</span><span class="sxs-lookup"><span data-stu-id="c2733-172">Linux Script Resource</span></span>](../reference/resources/linux/lnxScriptResource.md)
- [<span data-ttu-id="c2733-173">Linux 服务资源</span><span class="sxs-lookup"><span data-stu-id="c2733-173">Linux Service Resource</span></span>](../reference/resources/linux/lnxServiceResource.md)
- [<span data-ttu-id="c2733-174">Linux SshAuthorizedKeys 资源</span><span class="sxs-lookup"><span data-stu-id="c2733-174">Linux SshAuthorizedKeys Resource</span></span>](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
- [<span data-ttu-id="c2733-175">Linux 用户资源</span><span class="sxs-lookup"><span data-stu-id="c2733-175">Linux User Resource</span></span>](../reference/resources/linux/lnxUserResource.md)
