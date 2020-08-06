---
title: WideControl (Format) 的 WideEntry 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 13dd1f6ad7ac1e9d8d0524f0a0f18fe80ffaf8e2
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780009"
---
# <a name="wideentry-element-for-widecontrol-format"></a><span data-ttu-id="3569b-102">WideEntry Element for WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="3569b-102">WideEntry Element for WideControl (Format)</span></span>

<span data-ttu-id="3569b-103">提供宽视图的定义。</span><span class="sxs-lookup"><span data-stu-id="3569b-103">Provides a definition of the wide view.</span></span>

<span data-ttu-id="3569b-104">配置元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) WideControl 元素 (格式) WideEntries 元素 (格式) WideEntry 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="3569b-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3569b-105">语法</span><span class="sxs-lookup"><span data-stu-id="3569b-105">Syntax</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3569b-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="3569b-106">Attributes and Elements</span></span>

<span data-ttu-id="3569b-107">以下各节描述了元素的属性、子元素和父元素 `WideEntry` 。</span><span class="sxs-lookup"><span data-stu-id="3569b-107">The following sections describe the attributes, child elements, and the parent element of the `WideEntry` element.</span></span> <span data-ttu-id="3569b-108">您必须指定一个 `WideItem` 子元素。</span><span class="sxs-lookup"><span data-stu-id="3569b-108">You must specify a single `WideItem` child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3569b-109">特性</span><span class="sxs-lookup"><span data-stu-id="3569b-109">Attributes</span></span>

<span data-ttu-id="3569b-110">无。</span><span class="sxs-lookup"><span data-stu-id="3569b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3569b-111">子元素</span><span class="sxs-lookup"><span data-stu-id="3569b-111">Child Elements</span></span>

|<span data-ttu-id="3569b-112">元素</span><span class="sxs-lookup"><span data-stu-id="3569b-112">Element</span></span>|<span data-ttu-id="3569b-113">描述</span><span class="sxs-lookup"><span data-stu-id="3569b-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3569b-114">EntrySelectedBy Element for WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="3569b-114">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="3569b-115">可选元素。</span><span class="sxs-lookup"><span data-stu-id="3569b-115">Optional element.</span></span><br /><br /> <span data-ttu-id="3569b-116">定义使用此宽项定义的 .NET 类型或要使用此定义时必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="3569b-116">Defines the .NET types that use this wide entry definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="3569b-117">WideItem 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="3569b-117">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="3569b-118">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="3569b-118">Required element.</span></span><br /><br /> <span data-ttu-id="3569b-119">定义要显示其值的属性或脚本。</span><span class="sxs-lookup"><span data-stu-id="3569b-119">Defines the property or script whose value is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3569b-120">父元素</span><span class="sxs-lookup"><span data-stu-id="3569b-120">Parent Elements</span></span>

|<span data-ttu-id="3569b-121">元素</span><span class="sxs-lookup"><span data-stu-id="3569b-121">Element</span></span>|<span data-ttu-id="3569b-122">描述</span><span class="sxs-lookup"><span data-stu-id="3569b-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3569b-123">WideEntries 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="3569b-123">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="3569b-124">提供宽视图的定义。</span><span class="sxs-lookup"><span data-stu-id="3569b-124">Provides the definitions of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3569b-125">备注</span><span class="sxs-lookup"><span data-stu-id="3569b-125">Remarks</span></span>

<span data-ttu-id="3569b-126">宽视图是显示每个对象的单个属性值或脚本值的列表格式。</span><span class="sxs-lookup"><span data-stu-id="3569b-126">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="3569b-127">与其他类型的视图不同，每个视图定义只能指定一个 item 元素。</span><span class="sxs-lookup"><span data-stu-id="3569b-127">Unlike other types of views, you can specify only one item element for each view definition.</span></span> <span data-ttu-id="3569b-128">有关大视图的其他组件的详细信息，请参阅[创建宽视图](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="3569b-128">For more information about the other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="3569b-129">示例</span><span class="sxs-lookup"><span data-stu-id="3569b-129">Example</span></span>

<span data-ttu-id="3569b-130">下面的示例演示一个 `WideEntry` 元素，该元素定义单个 `WideItem` 元素。</span><span class="sxs-lookup"><span data-stu-id="3569b-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="3569b-131">`WideItem`元素定义其值在视图中显示的属性。</span><span class="sxs-lookup"><span data-stu-id="3569b-131">The `WideItem` element defines the property whose value is displayed in the view.</span></span>

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

<span data-ttu-id="3569b-132">有关宽视图的完整示例，请参阅[宽视图 (基本) ](./wide-view-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="3569b-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3569b-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3569b-133">See Also</span></span>

[<span data-ttu-id="3569b-134">创建宽视图</span><span class="sxs-lookup"><span data-stu-id="3569b-134">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="3569b-135">WideEntry 的 SelectionCondition 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="3569b-135">SelectionCondition Element for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="3569b-136">WideEntry 的 SelectionSetName 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="3569b-136">SelectionSetName Element for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="3569b-137">WideEntry (格式的 TypeName 元素) </span><span class="sxs-lookup"><span data-stu-id="3569b-137">TypeName Element for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="3569b-138">WideEntries 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="3569b-138">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="3569b-139">WideItem 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="3569b-139">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="3569b-140">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="3569b-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
