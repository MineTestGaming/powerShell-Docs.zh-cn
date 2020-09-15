---
ms.date: 07/17/2020
keywords: dsc,powershell,配置,安装程序
title: 适用于 Linux 的 DSC nxService 资源
ms.openlocfilehash: 2aec8b943d386fad33dfc1cfdd916c5e18039eaa
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463629"
---
# <a name="dsc-for-linux-nxservice-resource"></a><span data-ttu-id="c6f9d-103">适用于 Linux 的 DSC nxService 资源</span><span class="sxs-lookup"><span data-stu-id="c6f9d-103">DSC for Linux nxService Resource</span></span>

<span data-ttu-id="c6f9d-104">PowerShell Desired State Configuration (DSC) 中的 **nxService** 资源提供了在 Linux 节点上管理服务的机制。</span><span class="sxs-lookup"><span data-stu-id="c6f9d-104">The **nxService** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="c6f9d-105">语法</span><span class="sxs-lookup"><span data-stu-id="c6f9d-105">Syntax</span></span>

```Syntax
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd } ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a><span data-ttu-id="c6f9d-106">属性</span><span class="sxs-lookup"><span data-stu-id="c6f9d-106">Properties</span></span>

|<span data-ttu-id="c6f9d-107">properties</span><span class="sxs-lookup"><span data-stu-id="c6f9d-107">Property</span></span> |<span data-ttu-id="c6f9d-108">说明</span><span class="sxs-lookup"><span data-stu-id="c6f9d-108">Description</span></span> |
|---|---|
|<span data-ttu-id="c6f9d-109">名称</span><span class="sxs-lookup"><span data-stu-id="c6f9d-109">Name</span></span> |<span data-ttu-id="c6f9d-110">要配置的服务/守护程序的名称。</span><span class="sxs-lookup"><span data-stu-id="c6f9d-110">The name of the service/daemon to configure.</span></span> |
|<span data-ttu-id="c6f9d-111">控制器</span><span class="sxs-lookup"><span data-stu-id="c6f9d-111">Controller</span></span> |<span data-ttu-id="c6f9d-112">配置服务时使用的服务控制器类型。</span><span class="sxs-lookup"><span data-stu-id="c6f9d-112">The type of service controller to use when configuring the service.</span></span> |
|<span data-ttu-id="c6f9d-113">已启用</span><span class="sxs-lookup"><span data-stu-id="c6f9d-113">Enabled</span></span> |<span data-ttu-id="c6f9d-114">指示服务是否开机启动。</span><span class="sxs-lookup"><span data-stu-id="c6f9d-114">Indicates whether the service starts on boot.</span></span> |
|<span data-ttu-id="c6f9d-115">状态</span><span class="sxs-lookup"><span data-stu-id="c6f9d-115">State</span></span> |<span data-ttu-id="c6f9d-116">指示服务是否正在运行。</span><span class="sxs-lookup"><span data-stu-id="c6f9d-116">Indicates whether the service is running.</span></span> <span data-ttu-id="c6f9d-117">将此属性设置为 **Stopped** 可确保服务不在运行。</span><span class="sxs-lookup"><span data-stu-id="c6f9d-117">Set this property to **Stopped** to ensure that the service is not running.</span></span> <span data-ttu-id="c6f9d-118">将其设置为 **Running** 可确保服务正在运行。</span><span class="sxs-lookup"><span data-stu-id="c6f9d-118">Set it to **Running** to ensure that the service is running.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="c6f9d-119">公共属性</span><span class="sxs-lookup"><span data-stu-id="c6f9d-119">Common properties</span></span>

|<span data-ttu-id="c6f9d-120">properties</span><span class="sxs-lookup"><span data-stu-id="c6f9d-120">Property</span></span> |<span data-ttu-id="c6f9d-121">说明</span><span class="sxs-lookup"><span data-stu-id="c6f9d-121">Description</span></span> |
|---|---|
|<span data-ttu-id="c6f9d-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="c6f9d-122">DependsOn</span></span> |<span data-ttu-id="c6f9d-123">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="c6f9d-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c6f9d-124">例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="c6f9d-124">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |

## <a name="additional-information"></a><span data-ttu-id="c6f9d-125">其他信息</span><span class="sxs-lookup"><span data-stu-id="c6f9d-125">Additional Information</span></span>

<span data-ttu-id="c6f9d-126">**nxService** 资源不会为不存在的服务创建服务定义或脚本。</span><span class="sxs-lookup"><span data-stu-id="c6f9d-126">The **nxService** resource will not create a service definition or script for the service if it does not exist.</span></span> <span data-ttu-id="c6f9d-127">你可使用 PowerShell Desired State Configuration **nxFile** 资源管理服务定义文件或脚本是否存在或管理其内容。</span><span class="sxs-lookup"><span data-stu-id="c6f9d-127">You can use the PowerShell Desired State Configuration **nxFile** Resource resource to manage the existence or contents of the service definition file or script.</span></span>

## <a name="example"></a><span data-ttu-id="c6f9d-128">示例</span><span class="sxs-lookup"><span data-stu-id="c6f9d-128">Example</span></span>

<span data-ttu-id="c6f9d-129">下面的示例展示了已向 SystemD  服务控制器注册的“httpd”服务（适用于 Apache HTTP 服务器）的配置。</span><span class="sxs-lookup"><span data-stu-id="c6f9d-129">The following example shows configuration of the 'httpd' service (for Apache HTTP Server), registered with the **SystemD** service controller.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
    #Apache Service
    nxService ApacheService {
        Name = 'httpd'
        State = 'running'
        Enabled = $true
        Controller = 'systemd'
    }
}
```
