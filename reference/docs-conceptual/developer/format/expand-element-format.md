---
title: " (格式) 展开元素 |Microsoft Docs"
ms.date: 09/13/2016
ms.openlocfilehash: deee832254bb8a774ee2c1f5bd451d3ced1bd47a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783647"
---
# <a name="expand-element-format"></a>Expand Element (Format)

指定为此定义扩展集合对象的方式。

配置元素 (格式) DefaultSettings 元素 (格式) EnumerableExpansions 元素 (格式) EnumerableExpansion 元素 (格式) Expand 元素 (格式) 

## <a name="syntax"></a>语法

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a>特性和元素

以下各节描述了元素的属性、子元素和父元素 `Expand` 。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

无。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[EnumerableExpansion Element (Format)](./enumerableexpansion-element-format.md)|定义特定 .NET 集合对象在视图中显示的方式。|

## <a name="text-value"></a>文本值

指定以下值之一：

- EnumOnly：仅显示集合中对象的属性。

- CoreOnly：仅显示集合对象的属性。

- Both：显示集合中的对象的属性和集合对象的属性。

## <a name="remarks"></a>备注

此元素用于定义集合对象和集合中的对象的显示方式。 在这种情况下，集合对象引用支持**system.object**接口的任何对象。

默认行为是只显示集合中对象的属性。

## <a name="see-also"></a>另请参阅

[编写 PowerShell 格式设置文件](./writing-a-powershell-formatting-file.md)
