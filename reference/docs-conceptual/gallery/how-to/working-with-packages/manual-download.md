---
ms.date: 09/11/2018
contributor: JKeithB
keywords: 库, powershell, psgallery
title: 手动包下载
ms.openlocfilehash: 3e29437c4e35e47ab2028a7eea9f408daf1a59e1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782848"
---
# <a name="manual-package-download"></a><span data-ttu-id="bd5f0-103">手动包下载</span><span class="sxs-lookup"><span data-stu-id="bd5f0-103">Manual Package Download</span></span>

<span data-ttu-id="bd5f0-104">PowerShell 库支持直接下载网站中的包而无需使用 PowerShellGet cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-104">The PowerShell Gallery supports downloading a package from the website directly, without using the PowerShellGet cmdlets.</span></span> <span data-ttu-id="bd5f0-105">可以将任何包下载为 NuGet 包 (`.nupkg`) 文件，然后可以将该文件复制到内部存储库。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-105">You can download any package as a NuGet package (`.nupkg`) file, which you can then copy to an internal repository.</span></span>

> [!NOTE]
> <span data-ttu-id="bd5f0-106">手动包下载并非  旨在替代 `Install-Module` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-106">Manual package download is **not** intended as a replacement for the `Install-Module` cmdlet.</span></span>
> <span data-ttu-id="bd5f0-107">下载包不会安装模块或脚本。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-107">Downloading the package doesn't install the module or script.</span></span> <span data-ttu-id="bd5f0-108">下载的 NuGet 包中不包含依赖项。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-108">Dependencies aren't included in the NuGet package downloaded.</span></span> <span data-ttu-id="bd5f0-109">以下说明仅供参考。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-109">The following instructions are provided for reference purposes only.</span></span>

## <a name="using-manual-download-to-acquire-a-package"></a><span data-ttu-id="bd5f0-110">使用手动下载以获取包</span><span class="sxs-lookup"><span data-stu-id="bd5f0-110">Using manual download to acquire a package</span></span>

<span data-ttu-id="bd5f0-111">每个页面都有一个手动下载链接，如下所示：</span><span class="sxs-lookup"><span data-stu-id="bd5f0-111">Each page has a link for Manual Download, as shown here:</span></span>

![包含安装选项的包显示页面](media/manual-download/packagedisplaypagewithpseditions.png)

<span data-ttu-id="bd5f0-113">若要手动下载，请单击“下载原始 nupkg 文件”  。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-113">To download manually, click on **Download the raw nupkg file**.</span></span> <span data-ttu-id="bd5f0-114">将包的副本复制到名称为 `<name>.<version>.nupkg` 的浏览器的下载文件夹中。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-114">A copy of the package is copied to the download folder for your browser with the name `<name>.<version>.nupkg`.</span></span>

<span data-ttu-id="bd5f0-115">NuGet 包是一个 ZIP 存档，其中的额外文件包含有关包内容的信息。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-115">A NuGet package is a ZIP archive with extra files containing information about the contents of the package.</span></span> <span data-ttu-id="bd5f0-116">某些浏览器（如 Internet Explorer）会自动将 `.nupkg` 文件扩展名替换为 `.zip`。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-116">Some browsers, like Internet Explorer, automatically replace the `.nupkg` file extension with `.zip`.</span></span> <span data-ttu-id="bd5f0-117">要展开包，请根据需要将 `.nupkg` 文件重命名为 `.zip`，然后将内容提取到本地文件夹。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-117">To expand the package, rename the `.nupkg` file to `.zip`, if needed, then extract the contents to a local folder.</span></span>

<span data-ttu-id="bd5f0-118">NuGet 包文件包含以下特定于 NuGet  的元素，这些元素不是原始打包代码的一部分：</span><span class="sxs-lookup"><span data-stu-id="bd5f0-118">A NuGet package file includes the following **NuGet-specific elements** that aren't part of the original packaged code:</span></span>

- <span data-ttu-id="bd5f0-119">名为 `_rels` 的文件夹 - 包含列出依赖项的 `.rels` 文件</span><span class="sxs-lookup"><span data-stu-id="bd5f0-119">A folder named `_rels` - contains a `.rels` file that lists the dependencies</span></span>
- <span data-ttu-id="bd5f0-120">名为 `package` 的文件夹 - 包含特定于 NuGet 的数据</span><span class="sxs-lookup"><span data-stu-id="bd5f0-120">A folder named `package` - contains the NuGet-specific data</span></span>
- <span data-ttu-id="bd5f0-121">名为 `[Content_Types].xml` 的文件 - 描述 PowerShellGet 等扩展如何与 NuGet 一起使用</span><span class="sxs-lookup"><span data-stu-id="bd5f0-121">A file named `[Content_Types].xml` - describes how extensions like PowerShellGet work with NuGet</span></span>
- <span data-ttu-id="bd5f0-122">名为 `<name>.nuspec` 的文件 - 包含大量元数据</span><span class="sxs-lookup"><span data-stu-id="bd5f0-122">A file named `<name>.nuspec` - contains the bulk of the metadata</span></span>

## <a name="installing-powershell-modules-from-a-nuget-package"></a><span data-ttu-id="bd5f0-123">从 NuGet 包安装 PowerShell 模块</span><span class="sxs-lookup"><span data-stu-id="bd5f0-123">Installing PowerShell modules from a NuGet package</span></span>

> [!NOTE]
> <span data-ttu-id="bd5f0-124">这些说明并未给出与运行 `Install-Module` 相同的结果。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-124">These instructions **DO NOT** give the same result as running `Install-Module`.</span></span> <span data-ttu-id="bd5f0-125">这些说明满足最低要求。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-125">These instructions fulfill the minimum requirements.</span></span> <span data-ttu-id="bd5f0-126">它们并非 `Install-Module` 的替代品。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-126">They aren't intended to be a replacement for `Install-Module`.</span></span>
> <span data-ttu-id="bd5f0-127">`Install-Module` 执行的某些步骤不包括在内。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-127">Some steps performed by `Install-Module` aren't included.</span></span>

<span data-ttu-id="bd5f0-128">最简单的方法是从文件夹中删除特定于 NuGet 的元素。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-128">The easiest approach is to remove the NuGet-specific elements from the folder.</span></span> <span data-ttu-id="bd5f0-129">删除元素将保留由包创建者创建的 PowerShell 代码。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-129">Removing the elements leaves the PowerShell code created by the package author.</span></span>
<span data-ttu-id="bd5f0-130">有关特定于 NuGet 的元素的列表，请参阅[使用手动下载以获取包](#using-manual-download-to-acquire-a-package)。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-130">For the list of NuGet-specific elements, see [Using manual download to acquire a package](#using-manual-download-to-acquire-a-package).</span></span>

<span data-ttu-id="bd5f0-131">步骤如下：</span><span class="sxs-lookup"><span data-stu-id="bd5f0-131">The steps are as follows:</span></span>

1. <span data-ttu-id="bd5f0-132">取消阻止 Internet 下载的 NuGet 包 (`.nupkg`) 文件，例如使用 `Unblock-File -Path C:\Downloads\module.nupkg` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-132">Unblock the Internet-downloaded NuGet package (`.nupkg`) file, for example using `Unblock-File -Path C:\Downloads\module.nupkg` cmdlet.</span></span>
2. <span data-ttu-id="bd5f0-133">将 NuGet 包的内容提取到本地文件夹。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-133">Extract the contents of the NuGet package to a local folder.</span></span>
2. <span data-ttu-id="bd5f0-134">从文件夹中删除特定于 NuGet 的元素。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-134">Delete the NuGet-specific elements from the folder.</span></span>
3. <span data-ttu-id="bd5f0-135">重命名文件夹。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-135">Rename the folder.</span></span> <span data-ttu-id="bd5f0-136">默认文件夹名称通常是 `<name>.<version>`。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-136">The default folder name is usually `<name>.<version>`.</span></span> <span data-ttu-id="bd5f0-137">若将模块标记为预发布版本，则版本可包含 `-prerelease`。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-137">The version can include `-prerelease` if the module is tagged as a prerelease version.</span></span> <span data-ttu-id="bd5f0-138">将文件夹重命名为模块名称。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-138">Rename the folder to just the module name.</span></span> <span data-ttu-id="bd5f0-139">例如，`azurerm.storage.5.0.4-preview` 重命名为 `azurerm.storage`。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-139">For example, `azurerm.storage.5.0.4-preview` becomes `azurerm.storage`.</span></span>
4. <span data-ttu-id="bd5f0-140">将文件夹复制到 `$env:PSModulePath value` 中的一个文件夹。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-140">Copy the folder to one of the folders in the `$env:PSModulePath value`.</span></span> <span data-ttu-id="bd5f0-141">`$env:PSModulePath` 是以分号分隔的一组路径，PowerShell 应在这些路径中查找模块。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-141">`$env:PSModulePath` is a semicolon-delimited set of paths in which PowerShell should look for modules.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bd5f0-142">手动下载不包括模块所需的任何依赖项。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-142">The manual download doesn't include any dependencies required by the module.</span></span> <span data-ttu-id="bd5f0-143">若包具有依赖项，则必须在系统上安装它们才能使此模块正常工作。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-143">If the package has dependencies, they must be installed on the system for this module to work correctly.</span></span> <span data-ttu-id="bd5f0-144">PowerShell 库显示包所需的所有依赖项。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-144">The PowerShell Gallery shows all dependencies required by the package.</span></span>

## <a name="installing-powershell-scripts-from-a-nuget-package"></a><span data-ttu-id="bd5f0-145">在 NuGet 包安装 PowerShell 脚本</span><span class="sxs-lookup"><span data-stu-id="bd5f0-145">Installing PowerShell scripts from a NuGet package</span></span>

> [!NOTE]
> <span data-ttu-id="bd5f0-146">这些说明并未给出与运行 `Install-Script` 相同的结果。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-146">These instructions **DO NOT** give the same result as running `Install-Script`.</span></span> <span data-ttu-id="bd5f0-147">这些说明满足最低要求。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-147">These instructions fulfill the minimum requirements.</span></span> <span data-ttu-id="bd5f0-148">它们并非 `Install-Script` 的替代品。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-148">They aren't intended to be a replacement for `Install-Script`.</span></span>

<span data-ttu-id="bd5f0-149">最简单的方法是提取 NuGet 包，然后直接使用脚本。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-149">The easiest approach is to extract the NuGet package, then use the script directly.</span></span>

<span data-ttu-id="bd5f0-150">步骤如下：</span><span class="sxs-lookup"><span data-stu-id="bd5f0-150">The steps are as follows:</span></span>

1. <span data-ttu-id="bd5f0-151">取消阻止 Internet 下载的 NuGet 包 (`.nupkg`) 文件，例如使用 `Unblock-File -Path C:\Downloads\package.nupkg` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-151">Unblock the Internet-downloaded NuGet package (`.nupkg`) file, for example using `Unblock-File -Path C:\Downloads\package.nupkg` cmdlet.</span></span>
2. <span data-ttu-id="bd5f0-152">提取 NuGet 包的内容。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-152">Extract the contents of the NuGet package.</span></span>
2. <span data-ttu-id="bd5f0-153">文件夹中的 `.PS1` 文件可直接从此位置使用。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-153">The `.PS1` file in the folder can be used directly from this location.</span></span>
3. <span data-ttu-id="bd5f0-154">可删除文件夹中特定于 NuGet 的元素。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-154">You may delete the NuGet-specific elements in the folder.</span></span>

<span data-ttu-id="bd5f0-155">有关特定于 NuGet 的元素的列表，请参阅[使用手动下载以获取包](#using-manual-download-to-acquire-a-package)。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-155">For the list of NuGet-specific elements, see [Using manual download to acquire a package](#using-manual-download-to-acquire-a-package).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bd5f0-156">手动下载不包括模块所需的任何依赖项。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-156">The manual download doesn't include any dependencies required by the module.</span></span> <span data-ttu-id="bd5f0-157">若包具有依赖项，则必须在系统上安装它们才能使此模块正常工作。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-157">If the package has dependencies, they must be installed on the system for this module to work correctly.</span></span> <span data-ttu-id="bd5f0-158">PowerShell 库显示包所需的所有依赖项。</span><span class="sxs-lookup"><span data-stu-id="bd5f0-158">The PowerShell Gallery shows all dependencies required by the package.</span></span>
