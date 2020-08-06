---
title: GroupBy (Format) 的 CustomControl 的 CustomEntries 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2221d1bb94159697ff10466e4606d6d54e117e30
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785942"
---
# <a name="customentries-element-for-customcontrol-for-groupby-format"></a><span data-ttu-id="92eb9-102">CustomEntries Element for CustomControl for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="92eb9-102">CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

<span data-ttu-id="92eb9-103">提供控件的定义。</span><span class="sxs-lookup"><span data-stu-id="92eb9-103">Provides the definitions for the control.</span></span> <span data-ttu-id="92eb9-104">此元素在定义如何显示新的对象组时使用。</span><span class="sxs-lookup"><span data-stu-id="92eb9-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="92eb9-105">配置元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) CustomEntries 元素 for 元素 for CustomControl for GroupBy (格式) CustomControl 元素 (</span><span class="sxs-lookup"><span data-stu-id="92eb9-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="92eb9-106">语法</span><span class="sxs-lookup"><span data-stu-id="92eb9-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="92eb9-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="92eb9-107">Attributes and Elements</span></span>

<span data-ttu-id="92eb9-108">以下各节描述了元素的属性、子元素和父元素 `CustomEntries` 。</span><span class="sxs-lookup"><span data-stu-id="92eb9-108">The following sections describe attributes, child elements, and parent elements of the `CustomEntries` element.</span></span> <span data-ttu-id="92eb9-109">对于可指定的子元素数没有最大限制。</span><span class="sxs-lookup"><span data-stu-id="92eb9-109">There is no maximum limit to the number of child elements that can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="92eb9-110">特性</span><span class="sxs-lookup"><span data-stu-id="92eb9-110">Attributes</span></span>

<span data-ttu-id="92eb9-111">无。</span><span class="sxs-lookup"><span data-stu-id="92eb9-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="92eb9-112">子元素</span><span class="sxs-lookup"><span data-stu-id="92eb9-112">Child Elements</span></span>

|<span data-ttu-id="92eb9-113">元素</span><span class="sxs-lookup"><span data-stu-id="92eb9-113">Element</span></span>|<span data-ttu-id="92eb9-114">说明</span><span class="sxs-lookup"><span data-stu-id="92eb9-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="92eb9-115">CustomEntry Element for CustomControl for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="92eb9-115">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="92eb9-116">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="92eb9-116">Required element.</span></span><br /><br /> <span data-ttu-id="92eb9-117">提供控件的定义。</span><span class="sxs-lookup"><span data-stu-id="92eb9-117">Provides a definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="92eb9-118">父元素</span><span class="sxs-lookup"><span data-stu-id="92eb9-118">Parent Elements</span></span>

|<span data-ttu-id="92eb9-119">元素</span><span class="sxs-lookup"><span data-stu-id="92eb9-119">Element</span></span>|<span data-ttu-id="92eb9-120">说明</span><span class="sxs-lookup"><span data-stu-id="92eb9-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="92eb9-121">CustomControl Element for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="92eb9-121">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="92eb9-122">定义显示新组的自定义控件。</span><span class="sxs-lookup"><span data-stu-id="92eb9-122">Defines the custom control that displays the new group.</span></span>|

## <a name="remarks"></a><span data-ttu-id="92eb9-123">备注</span><span class="sxs-lookup"><span data-stu-id="92eb9-123">Remarks</span></span>

<span data-ttu-id="92eb9-124">在大多数情况下，控件只有一个定义，该定义是在单个元素中指定的 `CustomEntry` 。</span><span class="sxs-lookup"><span data-stu-id="92eb9-124">In most cases, a control has only one definition, which is specified in a single `CustomEntry` element.</span></span> <span data-ttu-id="92eb9-125">但是，如果要使用相同的控件来显示不同的组，则可以提供多个定义。</span><span class="sxs-lookup"><span data-stu-id="92eb9-125">However, it is possible to provide multiple definitions if you want to use the same control to display different groups.</span></span> <span data-ttu-id="92eb9-126">在这些情况下，可以 `CustomEntry` 为组定义元素。</span><span class="sxs-lookup"><span data-stu-id="92eb9-126">In those cases, you can define a `CustomEntry` element for a group.</span></span>

## <a name="see-also"></a><span data-ttu-id="92eb9-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="92eb9-127">See Also</span></span>

[<span data-ttu-id="92eb9-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span><span class="sxs-lookup"><span data-stu-id="92eb9-128">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="92eb9-129">CustomControl Element for GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="92eb9-129">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="92eb9-130">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="92eb9-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
