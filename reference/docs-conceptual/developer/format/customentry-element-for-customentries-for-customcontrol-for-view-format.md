---
title: 用于 CustomControl for View (Format) 的 CustomEntries 的 CustomEntry 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a13e83ec941bed80eaab02e40131054432fcce00
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785874"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a><span data-ttu-id="1eb42-102">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span><span class="sxs-lookup"><span data-stu-id="1eb42-102">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>

<span data-ttu-id="1eb42-103">提供自定义控件视图的定义。</span><span class="sxs-lookup"><span data-stu-id="1eb42-103">Provides a definition of the custom control view.</span></span>

<span data-ttu-id="1eb42-104">配置元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) CustomControl 元素 (格式) CustomEntries 元素 (CustomEntry 的 CustomControl 的 CustomEntries 元素)  (格式) </span><span class="sxs-lookup"><span data-stu-id="1eb42-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1eb42-105">语法</span><span class="sxs-lookup"><span data-stu-id="1eb42-105">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1eb42-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="1eb42-106">Attributes and Elements</span></span>

<span data-ttu-id="1eb42-107">以下各节描述了元素的属性、子元素和父元素 `CustomEntry` 。</span><span class="sxs-lookup"><span data-stu-id="1eb42-107">The following sections describe attributes, child elements, and the parent element of the `CustomEntry` element.</span></span> <span data-ttu-id="1eb42-108">您必须指定由定义显示的项。</span><span class="sxs-lookup"><span data-stu-id="1eb42-108">You must specify the items displayed by the definition.</span></span>

### <a name="attributes"></a><span data-ttu-id="1eb42-109">特性</span><span class="sxs-lookup"><span data-stu-id="1eb42-109">Attributes</span></span>

<span data-ttu-id="1eb42-110">无。</span><span class="sxs-lookup"><span data-stu-id="1eb42-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1eb42-111">子元素</span><span class="sxs-lookup"><span data-stu-id="1eb42-111">Child Elements</span></span>

|<span data-ttu-id="1eb42-112">元素</span><span class="sxs-lookup"><span data-stu-id="1eb42-112">Element</span></span>|<span data-ttu-id="1eb42-113">描述</span><span class="sxs-lookup"><span data-stu-id="1eb42-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1eb42-114">View (格式的 CustomEntry 的 EntrySelectedBy 元素) </span><span class="sxs-lookup"><span data-stu-id="1eb42-114">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="1eb42-115">可选元素。</span><span class="sxs-lookup"><span data-stu-id="1eb42-115">Optional element.</span></span><br /><br /> <span data-ttu-id="1eb42-116">定义使用自定义控件视图的定义或要使用此定义必须存在的条件的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="1eb42-116">Defines the .NET types that use the definition of the custom control view or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="1eb42-117">View (格式的 CustomEntry 的 CustomItem 元素) </span><span class="sxs-lookup"><span data-stu-id="1eb42-117">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="1eb42-118">定义自定义控件定义的控件。</span><span class="sxs-lookup"><span data-stu-id="1eb42-118">Defines a control for the custom control definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1eb42-119">父元素</span><span class="sxs-lookup"><span data-stu-id="1eb42-119">Parent Elements</span></span>

|<span data-ttu-id="1eb42-120">元素</span><span class="sxs-lookup"><span data-stu-id="1eb42-120">Element</span></span>|<span data-ttu-id="1eb42-121">描述</span><span class="sxs-lookup"><span data-stu-id="1eb42-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1eb42-122">CustomEntries Element for CustomControl for View (Format)</span><span class="sxs-lookup"><span data-stu-id="1eb42-122">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="1eb42-123">提供自定义控件视图的定义。</span><span class="sxs-lookup"><span data-stu-id="1eb42-123">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="1eb42-124">自定义控件视图必须指定一个或多个定义。</span><span class="sxs-lookup"><span data-stu-id="1eb42-124">The custom control view must specify one or more definitions.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1eb42-125">备注</span><span class="sxs-lookup"><span data-stu-id="1eb42-125">Remarks</span></span>

<span data-ttu-id="1eb42-126">在大多数情况下，每个自定义控件视图只需要一个定义，但如果您希望使用同一视图显示不同的 .NET 对象，则可以有多个定义。</span><span class="sxs-lookup"><span data-stu-id="1eb42-126">In most cases, only one definition is required for each custom control view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="1eb42-127">在这些情况下，可以为每个对象或一组对象提供单独的定义。</span><span class="sxs-lookup"><span data-stu-id="1eb42-127">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="1eb42-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1eb42-128">See Also</span></span>

[<span data-ttu-id="1eb42-129">CustomControl Element for View (Format)</span><span class="sxs-lookup"><span data-stu-id="1eb42-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="1eb42-130">View (格式的 CustomEntry 的 CustomItem 元素) </span><span class="sxs-lookup"><span data-stu-id="1eb42-130">CustomItem Element for CustomEntry for View (Format)</span></span>](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="1eb42-131">View (格式的 CustomEntry 的 EntrySelectedBy 元素) </span><span class="sxs-lookup"><span data-stu-id="1eb42-131">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="1eb42-132">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="1eb42-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
