---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: DSC Package 资源
ms.openlocfilehash: 9285df71a303c9a53dd50d450272575a64e962e7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "55676939"
---
# <a name="dsc-package-resource"></a><span data-ttu-id="c41cc-103">DSC Package 资源</span><span class="sxs-lookup"><span data-stu-id="c41cc-103">DSC Package Resource</span></span>

<span data-ttu-id="c41cc-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c41cc-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="c41cc-105">Windows PowerShell Desired State Configuration (DSC) 中的 **Package** 资源提供了在目标节点上安装或卸载程序包（如 Windows Installer 和 setup.exe 程序包）的机制。</span><span class="sxs-lookup"><span data-stu-id="c41cc-105">The **Package** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall packages, such as Windows Installer and setup.exe packages, on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="c41cc-106">语法</span><span class="sxs-lookup"><span data-stu-id="c41cc-106">Syntax</span></span>

```
Package [string] #ResourceName
{
    Name = [string]
    Path = [string]
    ProductId = [string]
    [ Arguments = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ ReturnCode = [UInt32[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="c41cc-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="c41cc-107">Properties</span></span>

| <span data-ttu-id="c41cc-108">属性</span><span class="sxs-lookup"><span data-stu-id="c41cc-108">Property</span></span> | <span data-ttu-id="c41cc-109">说明</span><span class="sxs-lookup"><span data-stu-id="c41cc-109">Description</span></span> |
| --- | --- |
| <span data-ttu-id="c41cc-110">名称</span><span class="sxs-lookup"><span data-stu-id="c41cc-110">Name</span></span>| <span data-ttu-id="c41cc-111">指示要确保其特定状态的程序包的名称。</span><span class="sxs-lookup"><span data-stu-id="c41cc-111">Indicates the name of the package for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="c41cc-112">路径</span><span class="sxs-lookup"><span data-stu-id="c41cc-112">Path</span></span>| <span data-ttu-id="c41cc-113">指示程序包所在的路径。</span><span class="sxs-lookup"><span data-stu-id="c41cc-113">Indicates the path where the package resides.</span></span>|
| <span data-ttu-id="c41cc-114">ProductId</span><span class="sxs-lookup"><span data-stu-id="c41cc-114">ProductId</span></span>| <span data-ttu-id="c41cc-115">指示唯一标识程序包的产品 ID。</span><span class="sxs-lookup"><span data-stu-id="c41cc-115">Indicates the product ID that uniquely identifies the package.</span></span>|
| <span data-ttu-id="c41cc-116">参数</span><span class="sxs-lookup"><span data-stu-id="c41cc-116">Arguments</span></span>| <span data-ttu-id="c41cc-117">列出按照原样传输到程序包的参数字符串。</span><span class="sxs-lookup"><span data-stu-id="c41cc-117">Lists a string of arguments that will be passed to the package exactly as provided.</span></span>|
| <span data-ttu-id="c41cc-118">凭据</span><span class="sxs-lookup"><span data-stu-id="c41cc-118">Credential</span></span>| <span data-ttu-id="c41cc-119">提供远程源上程序包的访问权限。</span><span class="sxs-lookup"><span data-stu-id="c41cc-119">Provides access to the package on a remote source.</span></span> <span data-ttu-id="c41cc-120">此属性不用于安装程序包。</span><span class="sxs-lookup"><span data-stu-id="c41cc-120">This property is not used to install the package.</span></span> <span data-ttu-id="c41cc-121">程序包始终安装在本地系统上。</span><span class="sxs-lookup"><span data-stu-id="c41cc-121">The package is always installed on the local system.</span></span>|
| <span data-ttu-id="c41cc-122">Ensure</span><span class="sxs-lookup"><span data-stu-id="c41cc-122">Ensure</span></span>| <span data-ttu-id="c41cc-123">指示程序包是否已安装。</span><span class="sxs-lookup"><span data-stu-id="c41cc-123">Indicates if the package is installed.</span></span> <span data-ttu-id="c41cc-124">将此属性设置为“Absent”以确保未安装程序包（如果已安装则卸载程序包）。</span><span class="sxs-lookup"><span data-stu-id="c41cc-124">Set this property to "Absent" to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="c41cc-125">将其设置为“Present”（默认值）以确保已安装程序包。</span><span class="sxs-lookup"><span data-stu-id="c41cc-125">Set it to "Present" (the default value) to ensure the package is installed.</span></span>|
| <span data-ttu-id="c41cc-126">LogPath</span><span class="sxs-lookup"><span data-stu-id="c41cc-126">LogPath</span></span>| <span data-ttu-id="c41cc-127">指示你希望提供程序用于保存安装或卸载程序包的日志文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="c41cc-127">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span>|
| <span data-ttu-id="c41cc-128">DependsOn</span><span class="sxs-lookup"><span data-stu-id="c41cc-128">DependsOn</span></span> | <span data-ttu-id="c41cc-129">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="c41cc-129">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c41cc-130">例如，如果你想要首先运行 ID 为 **ResourceName**、类型为 **ResourceType** 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="c41cc-130">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="c41cc-131">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="c41cc-131">ReturnCode</span></span>| <span data-ttu-id="c41cc-132">指示预期的返回代码。</span><span class="sxs-lookup"><span data-stu-id="c41cc-132">Indicates the expected return code.</span></span> <span data-ttu-id="c41cc-133">如果实际返回代码与此处提供的预期值不匹配，则配置将返回错误。</span><span class="sxs-lookup"><span data-stu-id="c41cc-133">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span>|

## <a name="example"></a><span data-ttu-id="c41cc-134">示例</span><span class="sxs-lookup"><span data-stu-id="c41cc-134">Example</span></span>

<span data-ttu-id="c41cc-135">此示例将运行位于指定路径且具有指定产品 ID 的 .msi 安装程序。</span><span class="sxs-lookup"><span data-stu-id="c41cc-135">This example runs the .msi installer that is located at the specified path and has the specified product ID.</span></span>

```powershell
Configuration PackageTest
{
    Package PackageExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Path        = "$Env:SystemDrive\TestFolder\TestProject.msi"
        Name        = "TestPackage"
        ProductId   = "ACDDCDAF-80C6-41E6-A1B9-8ABD8A05027E"
    }
}
```