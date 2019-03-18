---
title: 配置 （格式） 的控件的 ExpressionBinding 的 ItemSelectionCondition 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd3ddc33-b21c-4464-b3f2-a78dbe0062a8
caps.latest.revision: 8
ms.openlocfilehash: 4865d716ebe0460b662253a3019e93e82428b882
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861683"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format"></a><span data-ttu-id="fcb1f-102">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="fcb1f-102">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

<span data-ttu-id="fcb1f-103">定义要在使用此控件中必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="fcb1f-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="fcb1f-104">定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。</span><span class="sxs-lookup"><span data-stu-id="fcb1f-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="fcb1f-105">配置 （格式） 的配置 （格式） 的配置 （CustomControl CustomEntries 元素的控件的配置 （格式） CustomControl 元素的控件的控件元素的配置元素 （格式） 的 Controls 元素CustomControl CustomEntry 配置 ExpressionBinding CustomItem 配置 （格式） 的控件元素的控件的配置 （格式） CustomItem 元素的控件的格式） CustomEntry 元素配置 （格式） 的控件的 ExpressionBinding 的 ItemSelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="fcb1f-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="fcb1f-106">语法</span><span class="sxs-lookup"><span data-stu-id="fcb1f-106">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fcb1f-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="fcb1f-107">Attributes and Elements</span></span>

<span data-ttu-id="fcb1f-108">以下各节描述了特性、 子元素和父元素的`ItemSelectionCondition`元素。</span><span class="sxs-lookup"><span data-stu-id="fcb1f-108">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="fcb1f-109">特性</span><span class="sxs-lookup"><span data-stu-id="fcb1f-109">Attributes</span></span>

<span data-ttu-id="fcb1f-110">无。</span><span class="sxs-lookup"><span data-stu-id="fcb1f-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="fcb1f-111">子元素</span><span class="sxs-lookup"><span data-stu-id="fcb1f-111">Child Elements</span></span>

|<span data-ttu-id="fcb1f-112">元素</span><span class="sxs-lookup"><span data-stu-id="fcb1f-112">Element</span></span>|<span data-ttu-id="fcb1f-113">描述</span><span class="sxs-lookup"><span data-stu-id="fcb1f-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fcb1f-114">ItemSelectionCondition 配置 （格式） 的控件的属性名称元素</span><span class="sxs-lookup"><span data-stu-id="fcb1f-114">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="fcb1f-115">可选元素。</span><span class="sxs-lookup"><span data-stu-id="fcb1f-115">Optional element.</span></span><br /><br /> <span data-ttu-id="fcb1f-116">指定触发条件的.NET 属性。</span><span class="sxs-lookup"><span data-stu-id="fcb1f-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="fcb1f-117">ItemSelectionCondition 的 Controls 的配置 （格式） 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="fcb1f-117">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="fcb1f-118">可选元素。</span><span class="sxs-lookup"><span data-stu-id="fcb1f-118">Optional element.</span></span><br /><br /> <span data-ttu-id="fcb1f-119">指定触发条件的脚本。</span><span class="sxs-lookup"><span data-stu-id="fcb1f-119">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="fcb1f-120">父元素</span><span class="sxs-lookup"><span data-stu-id="fcb1f-120">Parent Elements</span></span>

|<span data-ttu-id="fcb1f-121">元素</span><span class="sxs-lookup"><span data-stu-id="fcb1f-121">Element</span></span>|<span data-ttu-id="fcb1f-122">描述</span><span class="sxs-lookup"><span data-stu-id="fcb1f-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="fcb1f-123">配置 （格式） 的控件的 CustomItem ExpressionBinding 元素</span><span class="sxs-lookup"><span data-stu-id="fcb1f-123">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="fcb1f-124">定义由控件显示的数据。</span><span class="sxs-lookup"><span data-stu-id="fcb1f-124">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fcb1f-125">备注</span><span class="sxs-lookup"><span data-stu-id="fcb1f-125">Remarks</span></span>

<span data-ttu-id="fcb1f-126">您可以指定一个属性名称或用于这种情况的脚本，但不能同时指定。</span><span class="sxs-lookup"><span data-stu-id="fcb1f-126">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="fcb1f-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fcb1f-127">See Also</span></span>

[<span data-ttu-id="fcb1f-128">ItemSelectionCondition 配置 （格式） 的控件的属性名称元素</span><span class="sxs-lookup"><span data-stu-id="fcb1f-128">PropertyName Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="fcb1f-129">ItemSelectionCondition 的 Controls 的配置 （格式） 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="fcb1f-129">ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="fcb1f-130">配置 （格式） 的控件的 CustomItem ExpressionBinding 元素</span><span class="sxs-lookup"><span data-stu-id="fcb1f-130">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="fcb1f-131">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="fcb1f-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)