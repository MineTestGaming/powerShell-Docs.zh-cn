---
title: 配置 （格式） 的控件的控件元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858883"
---
# <a name="control-element-for-controls-for-configuration-format"></a><span data-ttu-id="0ef9b-102">Control Element for Controls for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="0ef9b-102">Control Element for Controls for Configuration (Format)</span></span>

<span data-ttu-id="0ef9b-103">定义可由格式设置文件和名称，用于引用该控件的所有视图的公共控件。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-103">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>

<span data-ttu-id="0ef9b-104">配置 （格式） 的配置 （格式） 的控件的控件元素的配置元素 （格式） 的 Controls 元素</span><span class="sxs-lookup"><span data-stu-id="0ef9b-104">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0ef9b-105">语法</span><span class="sxs-lookup"><span data-stu-id="0ef9b-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0ef9b-106">属性和元素</span><span class="sxs-lookup"><span data-stu-id="0ef9b-106">Attributes and Elements</span></span>

<span data-ttu-id="0ef9b-107">以下各节描述了特性、 子元素和的父元素`Control`元素。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-107">The following sections describe the attributes, child elements, and the parent element for the `Control` element.</span></span> <span data-ttu-id="0ef9b-108">必须指定每个子元素之一。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-108">You must specify only one of each child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0ef9b-109">特性</span><span class="sxs-lookup"><span data-stu-id="0ef9b-109">Attributes</span></span>

<span data-ttu-id="0ef9b-110">无。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0ef9b-111">子元素</span><span class="sxs-lookup"><span data-stu-id="0ef9b-111">Child Elements</span></span>

|<span data-ttu-id="0ef9b-112">元素</span><span class="sxs-lookup"><span data-stu-id="0ef9b-112">Element</span></span>|<span data-ttu-id="0ef9b-113">描述</span><span class="sxs-lookup"><span data-stu-id="0ef9b-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0ef9b-114">配置 （格式） 的控件的控件的 CustomControl 元素</span><span class="sxs-lookup"><span data-stu-id="0ef9b-114">CustomControl Element for Control for Controls for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="0ef9b-115">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-115">Required element.</span></span><br /><br /> <span data-ttu-id="0ef9b-116">定义控件。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-116">Defines the control.</span></span>|
|[<span data-ttu-id="0ef9b-117">配置 （格式） 的控件的名称元素</span><span class="sxs-lookup"><span data-stu-id="0ef9b-117">Name Element for Control for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="0ef9b-118">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-118">Required element.</span></span><br /><br /> <span data-ttu-id="0ef9b-119">指定用来引用该控件的名称。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-119">Specifies the name used to reference the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0ef9b-120">父元素</span><span class="sxs-lookup"><span data-stu-id="0ef9b-120">Parent Elements</span></span>

|<span data-ttu-id="0ef9b-121">元素</span><span class="sxs-lookup"><span data-stu-id="0ef9b-121">Element</span></span>|<span data-ttu-id="0ef9b-122">描述</span><span class="sxs-lookup"><span data-stu-id="0ef9b-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0ef9b-123">控件元素的配置 （格式）</span><span class="sxs-lookup"><span data-stu-id="0ef9b-123">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="0ef9b-124">定义由格式设置文件的所有视图或其他控件可以使用的公共控件。</span><span class="sxs-lookup"><span data-stu-id="0ef9b-124">Defines the common controls that can be used by all views of the formatting file or by other controls.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0ef9b-125">备注</span><span class="sxs-lookup"><span data-stu-id="0ef9b-125">Remarks</span></span>

<span data-ttu-id="0ef9b-126">可以在以下元素中引用提供给此控件的名称：</span><span class="sxs-lookup"><span data-stu-id="0ef9b-126">The name given to this control can be referenced in the following elements:</span></span>

- [<span data-ttu-id="0ef9b-127">ExpressionBinding CustomItem （格式） 的元素</span><span class="sxs-lookup"><span data-stu-id="0ef9b-127">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [<span data-ttu-id="0ef9b-128">View(Format) 的 GroupBy 元素</span><span class="sxs-lookup"><span data-stu-id="0ef9b-128">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="0ef9b-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0ef9b-129">See Also</span></span>

[<span data-ttu-id="0ef9b-130">控件元素的配置 （格式）</span><span class="sxs-lookup"><span data-stu-id="0ef9b-130">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="0ef9b-131">配置 （格式） 的控件的 CustomControl 元素</span><span class="sxs-lookup"><span data-stu-id="0ef9b-131">CustomControl element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="0ef9b-132">ExpressionBinding CustomItem （格式） 的元素</span><span class="sxs-lookup"><span data-stu-id="0ef9b-132">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="0ef9b-133">View(Format) 的 GroupBy 元素</span><span class="sxs-lookup"><span data-stu-id="0ef9b-133">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="0ef9b-134">配置 （格式） 的控件的控件的名称元素</span><span class="sxs-lookup"><span data-stu-id="0ef9b-134">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="0ef9b-135">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="0ef9b-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)