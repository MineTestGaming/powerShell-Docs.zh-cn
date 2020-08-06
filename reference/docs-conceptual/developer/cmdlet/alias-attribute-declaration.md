---
title: Alias 属性声明 |Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- Alias attribute
- attributes, Alias
- Alias attribute, described
ms.openlocfilehash: 4c1ff34a244611173ca919a44d6598189b19dc98
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782406"
---
# <a name="alias-attribute-declaration"></a>别名属性声明

Alias 属性允许用户为 cmdlet 参数指定不同的名称。 可以使用别名提供参数名称的快捷方式，也可以提供适用于不同方案的不同名称。

## <a name="syntax"></a>语法

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a>参数

`aliasName`需要 (String [] ) 。 指定 cmdlet 参数的一组以逗号分隔的别名。

## <a name="remarks"></a>备注

- 当指定 cmdlet 参数时，会将 Alias 特性与参数特性一起使用。 有关如何声明这些属性的详细信息，请参阅[如何声明 Cmdlet 参数](./how-to-declare-cmdlet-parameters.md)。

- 每个别名在 cmdlet 中必须是唯一的。 Windows PowerShell 不会检查是否存在重复的别名。

- 为 cmdlet 中的每个参数使用一次 Alias 特性。

- Alias 特性是由[Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute)类定义的。

## <a name="see-also"></a>另请参阅

[参数别名](./parameter-aliases.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
