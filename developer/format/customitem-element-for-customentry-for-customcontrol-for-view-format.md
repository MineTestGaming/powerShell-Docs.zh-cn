---
title: CustomItem 元素的视图 （格式） 的 CustomControl CustomEntry |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98708c1d-6f39-4a76-b454-31153a6ade8c
caps.latest.revision: 12
ms.openlocfilehash: 3c110bd5fe3ef2f790ef136556afa7c29d0b5b29
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856183"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="3c6b7-102">CustomItem Element for CustomEntry for CustomControl for View (Format)</span><span class="sxs-lookup"><span data-stu-id="3c6b7-102">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="3c6b7-103">定义由自定义控件视图中显示的数据和显示方式。</span><span class="sxs-lookup"><span data-stu-id="3c6b7-103">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="3c6b7-104">定义自定义控件视图时，将使用此元素。</span><span class="sxs-lookup"><span data-stu-id="3c6b7-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="3c6b7-105">配置元素 （格式） ViewDefinitions 元素 （格式） 视图元素 （格式） CustomControl 元素 （格式） CustomEntries 元素 CustomControl 视图 （格式） 的视图 （格式） CustomItem 元素 CustomEntries CustomEntry 元素CustomEntry 视图 （格式）</span><span class="sxs-lookup"><span data-stu-id="3c6b7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3c6b7-106">语法</span><span class="sxs-lookup"><span data-stu-id="3c6b7-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3c6b7-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="3c6b7-107">Attributes and Elements</span></span>

<span data-ttu-id="3c6b7-108">以下各节描述了特性、 子元素和父元素的`CustomItem`元素。</span><span class="sxs-lookup"><span data-stu-id="3c6b7-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3c6b7-109">特性</span><span class="sxs-lookup"><span data-stu-id="3c6b7-109">Attributes</span></span>

<span data-ttu-id="3c6b7-110">无。</span><span class="sxs-lookup"><span data-stu-id="3c6b7-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3c6b7-111">子元素</span><span class="sxs-lookup"><span data-stu-id="3c6b7-111">Child Elements</span></span>

|<span data-ttu-id="3c6b7-112">元素</span><span class="sxs-lookup"><span data-stu-id="3c6b7-112">Element</span></span>|<span data-ttu-id="3c6b7-113">描述</span><span class="sxs-lookup"><span data-stu-id="3c6b7-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3c6b7-114">为视图 （格式） 的 CustomControl CustomItem ExpressionBinding 元素</span><span class="sxs-lookup"><span data-stu-id="3c6b7-114">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="3c6b7-115">可选元素。</span><span class="sxs-lookup"><span data-stu-id="3c6b7-115">Optional element.</span></span><br /><br /> <span data-ttu-id="3c6b7-116">定义由控件显示的数据。</span><span class="sxs-lookup"><span data-stu-id="3c6b7-116">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="3c6b7-117">为视图 （格式） 的 CustomControl CustomItem 的框架元素</span><span class="sxs-lookup"><span data-stu-id="3c6b7-117">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="3c6b7-118">可选元素。</span><span class="sxs-lookup"><span data-stu-id="3c6b7-118">Optional element.</span></span><br /><br /> <span data-ttu-id="3c6b7-119">定义由自定义控件视图中显示的数据和显示方式。</span><span class="sxs-lookup"><span data-stu-id="3c6b7-119">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="3c6b7-120">CustomItem 视图 （格式） 的自定义控件的新行元素</span><span class="sxs-lookup"><span data-stu-id="3c6b7-120">NewLine Element for CustomItem for Custom Control for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="3c6b7-121">可选元素。</span><span class="sxs-lookup"><span data-stu-id="3c6b7-121">Optional element.</span></span><br /><br /> <span data-ttu-id="3c6b7-122">将空白的行添加到控件的显示。</span><span class="sxs-lookup"><span data-stu-id="3c6b7-122">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="3c6b7-123">为视图 （格式） 的 CustomControl CustomItem 的文本元素</span><span class="sxs-lookup"><span data-stu-id="3c6b7-123">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)|<span data-ttu-id="3c6b7-124">可选元素。</span><span class="sxs-lookup"><span data-stu-id="3c6b7-124">Optional element.</span></span><br /><br /> <span data-ttu-id="3c6b7-125">指定由控件显示的数据的其他文本。</span><span class="sxs-lookup"><span data-stu-id="3c6b7-125">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3c6b7-126">父元素</span><span class="sxs-lookup"><span data-stu-id="3c6b7-126">Parent Elements</span></span>

|<span data-ttu-id="3c6b7-127">元素</span><span class="sxs-lookup"><span data-stu-id="3c6b7-127">Element</span></span>|<span data-ttu-id="3c6b7-128">描述</span><span class="sxs-lookup"><span data-stu-id="3c6b7-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3c6b7-129">为视图 （格式） 的 CustomControl CustomEntries CustomEntry 元素</span><span class="sxs-lookup"><span data-stu-id="3c6b7-129">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="3c6b7-130">提供自定义控件视图的定义。</span><span class="sxs-lookup"><span data-stu-id="3c6b7-130">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3c6b7-131">备注</span><span class="sxs-lookup"><span data-stu-id="3c6b7-131">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="3c6b7-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3c6b7-132">See Also</span></span>

[<span data-ttu-id="3c6b7-133">视图 （格式） 的 CustomEntries CustomEntry 元素</span><span class="sxs-lookup"><span data-stu-id="3c6b7-133">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3c6b7-134">为视图 （格式） 的 CustomControl CustomItem ExpressionBinding 元素</span><span class="sxs-lookup"><span data-stu-id="3c6b7-134">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3c6b7-135">为视图 （格式） 的 CustomControl CustomItem 的框架元素</span><span class="sxs-lookup"><span data-stu-id="3c6b7-135">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3c6b7-136">为视图 （格式） 的 CustomControl CustomItem 的换行元素</span><span class="sxs-lookup"><span data-stu-id="3c6b7-136">NewLine Element for CustomItem for CustomControl for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3c6b7-137">为视图 （格式） 的 CustomControl CustomItem 的文本元素</span><span class="sxs-lookup"><span data-stu-id="3c6b7-137">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)

[<span data-ttu-id="3c6b7-138">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="3c6b7-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)