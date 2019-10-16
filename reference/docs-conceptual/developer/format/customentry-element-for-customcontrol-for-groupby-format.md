---
title: GroupBy （Format）的 CustomControl 的 CustomEntry 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2987cb45-f646-45d4-b81b-7871e77af36f
caps.latest.revision: 5
ms.openlocfilehash: dcf4f8b2bbd422067ffdf9b3b4972e279e91edf9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364056"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="5cb71-102">CustomEntry Element for CustomControl for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="5cb71-102">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="5cb71-103">提供控件的定义。</span><span class="sxs-lookup"><span data-stu-id="5cb71-103">Provides a definition of the control.</span></span> <span data-ttu-id="5cb71-104">此元素在定义如何显示新的对象组时使用。</span><span class="sxs-lookup"><span data-stu-id="5cb71-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="5cb71-105">配置元素（格式） ViewDefinitions 元素（格式） View 元素（format）对于 GroupBy （format） CustomEntries 元素，用于元素的 CustomControl 元素（format）CustomControl for GroupBy （Format）</span><span class="sxs-lookup"><span data-stu-id="5cb71-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5cb71-106">语法</span><span class="sxs-lookup"><span data-stu-id="5cb71-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5cb71-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="5cb71-107">Attributes and Elements</span></span>

<span data-ttu-id="5cb71-108">以下各节介绍了 `CustomEntry` 元素的属性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5cb71-108">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5cb71-109">属性</span><span class="sxs-lookup"><span data-stu-id="5cb71-109">Attributes</span></span>

<span data-ttu-id="5cb71-110">无。</span><span class="sxs-lookup"><span data-stu-id="5cb71-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5cb71-111">子元素</span><span class="sxs-lookup"><span data-stu-id="5cb71-111">Child Elements</span></span>

|<span data-ttu-id="5cb71-112">元素</span><span class="sxs-lookup"><span data-stu-id="5cb71-112">Element</span></span>|<span data-ttu-id="5cb71-113">描述</span><span class="sxs-lookup"><span data-stu-id="5cb71-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5cb71-114">GroupBy 的 CustomEntry 的 EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5cb71-114">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="5cb71-115">可选元素。</span><span class="sxs-lookup"><span data-stu-id="5cb71-115">Optional element.</span></span><br /><br /> <span data-ttu-id="5cb71-116">定义使用此控件定义的 .NET 类型或要使用此定义时必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="5cb71-116">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="5cb71-117">GroupBy 的 CustomEntry 的 CustomItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5cb71-117">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="5cb71-118">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="5cb71-118">Required element.</span></span><br /><br /> <span data-ttu-id="5cb71-119">定义控件显示数据的方式。</span><span class="sxs-lookup"><span data-stu-id="5cb71-119">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5cb71-120">父元素</span><span class="sxs-lookup"><span data-stu-id="5cb71-120">Parent Elements</span></span>

|<span data-ttu-id="5cb71-121">元素</span><span class="sxs-lookup"><span data-stu-id="5cb71-121">Element</span></span>|<span data-ttu-id="5cb71-122">描述</span><span class="sxs-lookup"><span data-stu-id="5cb71-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5cb71-123">GroupBy 的 CustomControl 的 CustomEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5cb71-123">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="5cb71-124">提供控件的定义。</span><span class="sxs-lookup"><span data-stu-id="5cb71-124">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5cb71-125">备注</span><span class="sxs-lookup"><span data-stu-id="5cb71-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="5cb71-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5cb71-126">See Also</span></span>

[<span data-ttu-id="5cb71-127">GroupBy 的 CustomEntry 的 EntrySelectedBy 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5cb71-127">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="5cb71-128">GroupBy 的 CustomEntry 的 CustomItem 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5cb71-128">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>](./customitem-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="5cb71-129">GroupBy 的 CustomControl 的 CustomEntries 元素（格式）</span><span class="sxs-lookup"><span data-stu-id="5cb71-129">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>](./customentries-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="5cb71-130">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="5cb71-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)