---
ms.date: 07/16/2020
keywords: dsc,powershell,配置,安装程序
title: DSC ServiceSet 资源
ms.openlocfilehash: b51cfa86aa6d2114553a0eee681cb88ea93e213f
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464394"
---
# <a name="dsc-serviceset-resource"></a><span data-ttu-id="0ca5e-103">DSC ServiceSet 资源</span><span class="sxs-lookup"><span data-stu-id="0ca5e-103">DSC ServiceSet Resource</span></span>

> <span data-ttu-id="0ca5e-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="0ca5e-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="0ca5e-105">Windows PowerShell Desired State Configuration (DSC) 中的 **ServiceSet** 资源提供了在目标节点上管理服务的机制。</span><span class="sxs-lookup"><span data-stu-id="0ca5e-105">The **ServiceSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage services on the target node.</span></span> <span data-ttu-id="0ca5e-106">此资源是[复合资源](../../../resources/authoringResourceComposite.md)，它会针对 **Name** 属性中指定的每个服务调用 [Service 资源](serviceResource.md)。</span><span class="sxs-lookup"><span data-stu-id="0ca5e-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [Service resource](serviceResource.md) for each service specified in the **Name** property.</span></span>

<span data-ttu-id="0ca5e-107">要将一些服务配置为相同状态时，请使用此资源。</span><span class="sxs-lookup"><span data-stu-id="0ca5e-107">Use this resource when you want to configure a number of services to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="0ca5e-108">语法</span><span class="sxs-lookup"><span data-stu-id="0ca5e-108">Syntax</span></span>

```Syntax
ServiceSet [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="0ca5e-109">属性</span><span class="sxs-lookup"><span data-stu-id="0ca5e-109">Properties</span></span>

|<span data-ttu-id="0ca5e-110">properties</span><span class="sxs-lookup"><span data-stu-id="0ca5e-110">Property</span></span> |<span data-ttu-id="0ca5e-111">说明</span><span class="sxs-lookup"><span data-stu-id="0ca5e-111">Description</span></span> |
|---|---|
|<span data-ttu-id="0ca5e-112">名称</span><span class="sxs-lookup"><span data-stu-id="0ca5e-112">Name</span></span> |<span data-ttu-id="0ca5e-113">指示服务名称。</span><span class="sxs-lookup"><span data-stu-id="0ca5e-113">Indicates the service names.</span></span> <span data-ttu-id="0ca5e-114">请注意，有时它与显示名称不同。</span><span class="sxs-lookup"><span data-stu-id="0ca5e-114">Note that sometimes this is different from the display names.</span></span> <span data-ttu-id="0ca5e-115">可使用 `Get-Service` cmdlet 获取服务及其当前状态的列表。</span><span class="sxs-lookup"><span data-stu-id="0ca5e-115">You can get a list of the services and their current state with the `Get-Service` cmdlet.</span></span> |
|<span data-ttu-id="0ca5e-116">StartupType</span><span class="sxs-lookup"><span data-stu-id="0ca5e-116">StartupType</span></span> |<span data-ttu-id="0ca5e-117">指示服务的启动类型。</span><span class="sxs-lookup"><span data-stu-id="0ca5e-117">Indicates the startup type for the services.</span></span> <span data-ttu-id="0ca5e-118">允许用于此属性的值有：**Automatic**、**Disabled** 和 **Manual**。</span><span class="sxs-lookup"><span data-stu-id="0ca5e-118">The values that are allowed for this property are: **Automatic**, **Disabled**, and **Manual**.</span></span> |
|<span data-ttu-id="0ca5e-119">BuiltInAccount</span><span class="sxs-lookup"><span data-stu-id="0ca5e-119">BuiltInAccount</span></span> |<span data-ttu-id="0ca5e-120">指示要用于服务的登录帐户。</span><span class="sxs-lookup"><span data-stu-id="0ca5e-120">Indicates the sign-in account to use for the services.</span></span> <span data-ttu-id="0ca5e-121">允许用于此属性的值有：LocalService  、LocalSystem  和 NetworkService  。</span><span class="sxs-lookup"><span data-stu-id="0ca5e-121">The values that are allowed for this property are: **LocalService**, **LocalSystem**, and **NetworkService**.</span></span> |
|<span data-ttu-id="0ca5e-122">状态</span><span class="sxs-lookup"><span data-stu-id="0ca5e-122">State</span></span> |<span data-ttu-id="0ca5e-123">指示你想要确保服务所处的状态：Stopped  或 Running  。</span><span class="sxs-lookup"><span data-stu-id="0ca5e-123">Indicates the state you want to ensure for the services: **Stopped** or **Running**.</span></span> |
|<span data-ttu-id="0ca5e-124">凭据</span><span class="sxs-lookup"><span data-stu-id="0ca5e-124">Credential</span></span> |<span data-ttu-id="0ca5e-125">指示服务资源将在其下运行的帐户的凭据。</span><span class="sxs-lookup"><span data-stu-id="0ca5e-125">Indicates credentials for the account that the service resource will run under.</span></span> <span data-ttu-id="0ca5e-126">此属性与 **BuiltinAccount** 属性不能一起使用。</span><span class="sxs-lookup"><span data-stu-id="0ca5e-126">This property and the **BuiltinAccount** property cannot be used together.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="0ca5e-127">公共属性</span><span class="sxs-lookup"><span data-stu-id="0ca5e-127">Common properties</span></span>

|<span data-ttu-id="0ca5e-128">properties</span><span class="sxs-lookup"><span data-stu-id="0ca5e-128">Property</span></span> |<span data-ttu-id="0ca5e-129">说明</span><span class="sxs-lookup"><span data-stu-id="0ca5e-129">Description</span></span> |
|---|---|
|<span data-ttu-id="0ca5e-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="0ca5e-130">DependsOn</span></span> |<span data-ttu-id="0ca5e-131">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="0ca5e-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="0ca5e-132">例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="0ca5e-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="0ca5e-133">Ensure</span><span class="sxs-lookup"><span data-stu-id="0ca5e-133">Ensure</span></span> |<span data-ttu-id="0ca5e-134">指示服务是否在系统中存在。</span><span class="sxs-lookup"><span data-stu-id="0ca5e-134">Indicates whether the services exist on the system.</span></span> <span data-ttu-id="0ca5e-135">将此属性设置为 **Absent** 可确保服务不存在。</span><span class="sxs-lookup"><span data-stu-id="0ca5e-135">Set this property to **Absent** to ensure that the services do not exist.</span></span> <span data-ttu-id="0ca5e-136">将它设置为 **Present** 可确保目标服务存在。</span><span class="sxs-lookup"><span data-stu-id="0ca5e-136">Setting it to **Present** ensures that target services exist.</span></span> <span data-ttu-id="0ca5e-137">默认值为 **Present**。</span><span class="sxs-lookup"><span data-stu-id="0ca5e-137">The default value is **Present**.</span></span> |
|<span data-ttu-id="0ca5e-138">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="0ca5e-138">PsDscRunAsCredential</span></span> |<span data-ttu-id="0ca5e-139">设置用于运行整个资源的身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="0ca5e-139">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="0ca5e-140">在 WMF 5.0 中添加了 **PsDscRunAsCredential** 公共属性，用于允许在其他凭据上下文中运行任何 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="0ca5e-140">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="0ca5e-141">有关详细信息，请参阅[将凭据与 DSC 资源配合使用](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="0ca5e-141">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="0ca5e-142">示例</span><span class="sxs-lookup"><span data-stu-id="0ca5e-142">Example</span></span>

<span data-ttu-id="0ca5e-143">以下配置启动“Windows 音频”和“远程桌面服务”服务。</span><span class="sxs-lookup"><span data-stu-id="0ca5e-143">The following configuration starts the "Windows Audio" and "Remote Desktop Services" services.</span></span>

```powershell
configuration ServiceSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {
        ServiceSet ServiceSetExample
        {
            Name        = @("TermService", "Audiosrv")
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```
