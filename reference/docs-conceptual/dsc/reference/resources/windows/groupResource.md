---
ms.date: 07/16/2020
keywords: dsc,powershell,配置,安装程序
title: DSC Group 资源
ms.openlocfilehash: 5570d46d872e205917eef49bfa869419b20a77b0
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464207"
---
# <a name="dsc-group-resource"></a><span data-ttu-id="11cfc-103">DSC Group 资源</span><span class="sxs-lookup"><span data-stu-id="11cfc-103">DSC Group Resource</span></span>

> <span data-ttu-id="11cfc-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="11cfc-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="11cfc-105">Windows PowerShell Desired State Configuration (DSC) 中的 **Group** 资源提供用于管理目标节点上的本地组的机制。</span><span class="sxs-lookup"><span data-stu-id="11cfc-105">The **Group** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local groups on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="11cfc-106">语法</span><span class="sxs-lookup"><span data-stu-id="11cfc-106">Syntax</span></span>

```Syntax
Group [string] #ResourceName
{
    GroupName = [string]
    [ Credential = [PSCredential] ]
    [ Description = [string[]] ]
    [ Members = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="11cfc-107">属性</span><span class="sxs-lookup"><span data-stu-id="11cfc-107">Properties</span></span>

|<span data-ttu-id="11cfc-108">properties</span><span class="sxs-lookup"><span data-stu-id="11cfc-108">Property</span></span> |<span data-ttu-id="11cfc-109">说明</span><span class="sxs-lookup"><span data-stu-id="11cfc-109">Description</span></span> |
|---|---|
|<span data-ttu-id="11cfc-110">GroupName</span><span class="sxs-lookup"><span data-stu-id="11cfc-110">GroupName</span></span> |<span data-ttu-id="11cfc-111">要确保其处于特定状态的组的名称。</span><span class="sxs-lookup"><span data-stu-id="11cfc-111">The name of the group for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="11cfc-112">凭据</span><span class="sxs-lookup"><span data-stu-id="11cfc-112">Credential</span></span> |<span data-ttu-id="11cfc-113">访问远程资源所需的凭据。</span><span class="sxs-lookup"><span data-stu-id="11cfc-113">The credentials required to access remote resources.</span></span> <span data-ttu-id="11cfc-114">此帐户必须拥有相应的 Active Directory 权限，才能将所有非本地帐户添加到组中；否则，在目标节点上执行配置时会发生错误。</span><span class="sxs-lookup"><span data-stu-id="11cfc-114">This account must have the appropriate Active Directory permissions to add all non-local accounts to the group; otherwise, an error occurs when the configuration is executed on the target node.</span></span>
|<span data-ttu-id="11cfc-115">说明</span><span class="sxs-lookup"><span data-stu-id="11cfc-115">Description</span></span> |<span data-ttu-id="11cfc-116">组的说明。</span><span class="sxs-lookup"><span data-stu-id="11cfc-116">The description of the group.</span></span> |
|<span data-ttu-id="11cfc-117">成员</span><span class="sxs-lookup"><span data-stu-id="11cfc-117">Members</span></span> |<span data-ttu-id="11cfc-118">使用此属性将当前的组成员身份替换为指定成员。</span><span class="sxs-lookup"><span data-stu-id="11cfc-118">Use this property to replace the current group membership with the specified members.</span></span> <span data-ttu-id="11cfc-119">此属性的值是一组形式为 `Domain\UserName` 的字符串。</span><span class="sxs-lookup"><span data-stu-id="11cfc-119">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="11cfc-120">如果你在配置中设置此属性，请勿使用 **MembersToExclude** 或 **MembersToInclude** 属性。</span><span class="sxs-lookup"><span data-stu-id="11cfc-120">If you set this property in a configuration, do not use either the **MembersToExclude** or **MembersToInclude** property.</span></span> <span data-ttu-id="11cfc-121">这样会生成错误。</span><span class="sxs-lookup"><span data-stu-id="11cfc-121">Doing so generates an error.</span></span> |
|<span data-ttu-id="11cfc-122">MembersToExclude</span><span class="sxs-lookup"><span data-stu-id="11cfc-122">MembersToExclude</span></span> |<span data-ttu-id="11cfc-123">使用此属性从现有的组成员身份中删除成员。</span><span class="sxs-lookup"><span data-stu-id="11cfc-123">Use this property to remove members from the existing membership of the group.</span></span> <span data-ttu-id="11cfc-124">此属性的值是一组形式为 `Domain\UserName` 的字符串。</span><span class="sxs-lookup"><span data-stu-id="11cfc-124">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="11cfc-125">如果你在配置中设置此属性，请勿使用 **Members** 属性。</span><span class="sxs-lookup"><span data-stu-id="11cfc-125">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="11cfc-126">这样会生成错误。</span><span class="sxs-lookup"><span data-stu-id="11cfc-126">Doing so generates an error.</span></span> |
|<span data-ttu-id="11cfc-127">MembersToInclude</span><span class="sxs-lookup"><span data-stu-id="11cfc-127">MembersToInclude</span></span> |<span data-ttu-id="11cfc-128">使用此属性将成员添加到组的现有成员资格中。</span><span class="sxs-lookup"><span data-stu-id="11cfc-128">Use this property to add members to the existing membership of the group.</span></span> <span data-ttu-id="11cfc-129">此属性的值是一组形式为 `Domain\UserName` 的字符串。</span><span class="sxs-lookup"><span data-stu-id="11cfc-129">The value of this property is an array of strings of the form `Domain\UserName`.</span></span> <span data-ttu-id="11cfc-130">如果你在配置中设置此属性，请勿使用 **Members** 属性。</span><span class="sxs-lookup"><span data-stu-id="11cfc-130">If you set this property in a configuration, do not use the **Members** property.</span></span> <span data-ttu-id="11cfc-131">这样做会导致错误生成。</span><span class="sxs-lookup"><span data-stu-id="11cfc-131">Doing so will generate an error.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="11cfc-132">公共属性</span><span class="sxs-lookup"><span data-stu-id="11cfc-132">Common properties</span></span>

|<span data-ttu-id="11cfc-133">properties</span><span class="sxs-lookup"><span data-stu-id="11cfc-133">Property</span></span> |<span data-ttu-id="11cfc-134">说明</span><span class="sxs-lookup"><span data-stu-id="11cfc-134">Description</span></span> |
|---|---|
|<span data-ttu-id="11cfc-135">DependsOn</span><span class="sxs-lookup"><span data-stu-id="11cfc-135">DependsOn</span></span> |<span data-ttu-id="11cfc-136">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="11cfc-136">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="11cfc-137">例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="11cfc-137">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="11cfc-138">Ensure</span><span class="sxs-lookup"><span data-stu-id="11cfc-138">Ensure</span></span> |<span data-ttu-id="11cfc-139">指示该组是否存在。</span><span class="sxs-lookup"><span data-stu-id="11cfc-139">Indicates if the group exists.</span></span> <span data-ttu-id="11cfc-140">将此属性设置为 **Absent** 可确保组不存在。</span><span class="sxs-lookup"><span data-stu-id="11cfc-140">Set this property to **Absent** to ensure that the group does not exist.</span></span> <span data-ttu-id="11cfc-141">将其设置为 **Present** 可确保组存在。</span><span class="sxs-lookup"><span data-stu-id="11cfc-141">Setting it to **Present** ensures that the group exists.</span></span> <span data-ttu-id="11cfc-142">默认值为 **Present**。</span><span class="sxs-lookup"><span data-stu-id="11cfc-142">The default value is **Present**.</span></span> |
|<span data-ttu-id="11cfc-143">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="11cfc-143">PsDscRunAsCredential</span></span> |<span data-ttu-id="11cfc-144">设置用于运行整个资源的身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="11cfc-144">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="11cfc-145">在 WMF 5.0 中添加了 **PsDscRunAsCredential** 公共属性，用于允许在其他凭据上下文中运行任何 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="11cfc-145">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="11cfc-146">有关详细信息，请参阅[将凭据与 DSC 资源配合使用](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="11cfc-146">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example-1-ensure-group-is-not-present"></a><span data-ttu-id="11cfc-147">示例 1：确保组不存在</span><span class="sxs-lookup"><span data-stu-id="11cfc-147">Example 1: Ensure group is not present</span></span>

<span data-ttu-id="11cfc-148">下面的示例展示了如何确保名为“TestGroup”的组不存在。</span><span class="sxs-lookup"><span data-stu-id="11cfc-148">The following example shows how to ensure that a group called "TestGroup" is absent.</span></span>

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present"
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```

## <a name="example-2-add-domain-user-to-local-group"></a><span data-ttu-id="11cfc-149">示例 2：将域用户添加到本地组</span><span class="sxs-lookup"><span data-stu-id="11cfc-149">Example 2: Add domain user to local group</span></span>

<span data-ttu-id="11cfc-150">以下示例演示如何将 Active Directory 用户添加到属于多计算机实验室版本（已在其中对本地管理员帐户使用 PSCredential）的本地管理员组。</span><span class="sxs-lookup"><span data-stu-id="11cfc-150">The following example shows how to add an Active Directory User to the local administrators group as part of a Multi-Machine Lab build where you are already using a PSCredential for the Local Administrator account.</span></span> <span data-ttu-id="11cfc-151">由于这也适用于域管理员帐户（在域提升后），因此需要将这个现有 PSCredential 转换为域友好凭据。</span><span class="sxs-lookup"><span data-stu-id="11cfc-151">As this is also used for the Domain Admin Account (after Domain promotion), we then need to convert this existing PSCredential to a Domain Friendly credential.</span></span> <span data-ttu-id="11cfc-152">然后，便可以将域用户添加到成员服务器上的本地管理员组。</span><span class="sxs-lookup"><span data-stu-id="11cfc-152">Then we can add a Domain User to the Local Administrators Group on the Member server.</span></span>

```powershell
@{
    AllNodes = @(
        @{
            NodeName = '*';
            DomainName = 'SubTest.contoso.com';
         }
        @{
            NodeName = 'Box2';
            AdminAccount = 'Admin-Dave_Alexanderson'
        }
    )
}

$domain = $node.DomainName.split('.')[0]
$DCredential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList ("$domain\$($credential.Username)", $Credential.Password)

Group AddADUserToLocalAdminGroup {
    GroupName='Administrators'
    Ensure= 'Present'
    MembersToInclude= "$domain\$($Node.AdminAccount)"
    Credential = $dCredential
    PsDscRunAsCredential = $DCredential
}
```

## <a name="example-3"></a><span data-ttu-id="11cfc-153">示例 3</span><span class="sxs-lookup"><span data-stu-id="11cfc-153">Example 3</span></span>

<span data-ttu-id="11cfc-154">下面的示例展示了如何确保服务器 TigerTeamSource.Contoso.Com 上的本地组 TigerTeamAdmins 不包含特定域帐户 Contoso\JerryG。</span><span class="sxs-lookup"><span data-stu-id="11cfc-154">The following example shows how to ensure a local group, TigerTeamAdmins, on the server TigerTeamSource.Contoso.Com does not contain a particular domain account, Contoso\JerryG.</span></span>

```powershell
Configuration SecureTigerTeamSource {
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node TigerTeamSource.Contoso.Com {
        Group TigerTeamAdmins {
            GroupName        = 'TigerTeamAdmins'
            Ensure           = 'Present'
            MembersToExclude = "Contoso\JerryG"
        }
    }
}
```
