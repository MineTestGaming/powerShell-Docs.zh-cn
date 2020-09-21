---
ms.date: 07/16/2020
keywords: dsc,powershell,配置,安装程序
title: DSC Environment 资源
ms.openlocfilehash: d8519a66d457767dcbc0e08b01a69a9264997479
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464411"
---
# <a name="dsc-environment-resource"></a>DSC Environment 资源

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.x

Windows PowerShell Desired State Configuration (DSC) 中的 **Environment** 资源提供了管理系统环境变量的机制。

## <a name="syntax"></a>语法

```Syntax
Environment [string] #ResourceName
{
    Name = [string]
    [ Path = [bool] ]
    [ Target = [string] { Process | Machine } ]
    [ Value = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>属性

|properties |说明 |
|---|---|
|名称 |指示指示你想要确保其特定状态的环境变量的名称。 |
|路径 |定义正在配置的环境变量。 如果变量是 **Path**，则将此属性设置为 `$true`；否则将其设置为 `$false`。 默认为 `$false`。 如果正在配置的变量是 **Path**，则通过 **Value** 属性提供的值将被附加到现有值。 |
|目标| 指示检索变量的位置：计算机或进程。 如果同时指示了这两个位置，则仅返回计算机的值。 默认值为这两者的值，因为这是其余资源的默认值。 |
|Value |要分配给环境变量的值。 |

## <a name="common-properties"></a>公共属性

|properties |说明 |
|---|---|
|DependsOn |指示必须先运行其他资源的配置，再配置此资源。 例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。 |
|Ensure |指示变量是否存在。 如果不存在此变量，将此属性设置为 **Present** 以创建环境变量；如果已存在此变量，则确保其值与通过 **Value** 属性提供的值相匹配。 如果存在该变量，将其设置为 **Absent** 可将其删除。 |
|PsDscRunAsCredential |设置用于运行整个资源的身份的凭据。 |

> [!NOTE]
> 在 WMF 5.0 中添加了 **PsDscRunAsCredential** 公共属性，用于允许在其他凭据上下文中运行任何 DSC 资源。 有关详细信息，请参阅[将凭据与 DSC 资源配合使用](../../../configurations/runasuser.md)。

## <a name="example"></a>示例

以下示例可确保 TestEnvironmentVariable 存在且具有值 _TestValue_。 如果不存在，则创建它。

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```
