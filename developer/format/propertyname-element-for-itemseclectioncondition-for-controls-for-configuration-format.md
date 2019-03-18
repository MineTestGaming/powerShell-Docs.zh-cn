---
title: ItemSeclectionCondition 配置 （格式） 的控件的属性名称元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ad8ab181-c559-492e-a0cf-299e381fdcc3
caps.latest.revision: 6
ms.openlocfilehash: ce25789bdfc2679372ca9e42f99dcc6a30ae2def
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860923"
---
# <a name="propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="0611b-102">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="0611b-102">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="0611b-103">指定触发条件的.NET 属性。</span><span class="sxs-lookup"><span data-stu-id="0611b-103">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="0611b-104">存在此属性时或当计算结果为`true`、 满足该条件，并使用该控件。</span><span class="sxs-lookup"><span data-stu-id="0611b-104">When this property is present or when it evaluates to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="0611b-105">定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。</span><span class="sxs-lookup"><span data-stu-id="0611b-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="0611b-106">配置 （格式） 的配置 （格式） 的配置 （CustomControl CustomEntries 元素的控件的配置 （格式） CustomControl 元素的控件的控件元素的配置元素 （格式） 的 Controls 元素CustomControl CustomEntry 配置 ExpressionBinding CustomItem 配置 （格式） 的控件元素的控件的配置 （格式） CustomItem 元素的控件的格式） CustomEntry 元素ExpressionBinding ItemSeclectionCondition 的 Controls 的配置 （格式） 的配置 （格式） PropertyName 元素的控件的 ItemSelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="0611b-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0611b-107">语法</span><span class="sxs-lookup"><span data-stu-id="0611b-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0611b-108">属性和元素</span><span class="sxs-lookup"><span data-stu-id="0611b-108">Attributes and Elements</span></span>

<span data-ttu-id="0611b-109">以下各节描述了特性、 子元素和父元素的`PropertyName`元素。</span><span class="sxs-lookup"><span data-stu-id="0611b-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0611b-110">特性</span><span class="sxs-lookup"><span data-stu-id="0611b-110">Attributes</span></span>

<span data-ttu-id="0611b-111">无。</span><span class="sxs-lookup"><span data-stu-id="0611b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0611b-112">子元素</span><span class="sxs-lookup"><span data-stu-id="0611b-112">Child Elements</span></span>

<span data-ttu-id="0611b-113">无。</span><span class="sxs-lookup"><span data-stu-id="0611b-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0611b-114">父元素</span><span class="sxs-lookup"><span data-stu-id="0611b-114">Parent Elements</span></span>

|<span data-ttu-id="0611b-115">元素</span><span class="sxs-lookup"><span data-stu-id="0611b-115">Element</span></span>|<span data-ttu-id="0611b-116">描述</span><span class="sxs-lookup"><span data-stu-id="0611b-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0611b-117">配置 （格式） 的控件的 ExpressionBinding 的 ItemSelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="0611b-117">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="0611b-118">定义要在使用此控件中必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="0611b-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="0611b-119">文本值</span><span class="sxs-lookup"><span data-stu-id="0611b-119">Text Value</span></span>

<span data-ttu-id="0611b-120">指定触发条件的.NET 属性的名称。</span><span class="sxs-lookup"><span data-stu-id="0611b-120">Specify the name of the .NET property that triggers the condition.</span></span>

## <a name="remarks"></a><span data-ttu-id="0611b-121">备注</span><span class="sxs-lookup"><span data-stu-id="0611b-121">Remarks</span></span>

<span data-ttu-id="0611b-122">如果使用此元素时，不能指定[ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)元素定义的选择条件时。</span><span class="sxs-lookup"><span data-stu-id="0611b-122">If this element is used, you cannot specify the [ScriptBlock](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="0611b-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0611b-123">See Also</span></span>

[<span data-ttu-id="0611b-124">ItemSeclectionCondition 的 Controls 的配置 （格式） 的脚本块元素</span><span class="sxs-lookup"><span data-stu-id="0611b-124">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="0611b-125">配置 （格式） 的控件的 ExpressionBinding 的 ItemSelectionCondition 元素</span><span class="sxs-lookup"><span data-stu-id="0611b-125">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="0611b-126">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="0611b-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)