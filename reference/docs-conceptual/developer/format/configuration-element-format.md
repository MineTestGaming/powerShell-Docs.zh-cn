---
title: 配置元素 (格式) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 90be02f8e27c0bd391e01da1a08ecd8eeb29b84c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783834"
---
# <a name="configuration-element-format"></a><span data-ttu-id="c0474-102">Configuration Element (Format)</span><span class="sxs-lookup"><span data-stu-id="c0474-102">Configuration Element (Format)</span></span>

<span data-ttu-id="c0474-103">表示格式设置文件的顶级元素。</span><span class="sxs-lookup"><span data-stu-id="c0474-103">Represents the top-level element of a formatting file.</span></span>

<span data-ttu-id="c0474-104">配置元素</span><span class="sxs-lookup"><span data-stu-id="c0474-104">Configuration Element</span></span>

## <a name="syntax"></a><span data-ttu-id="c0474-105">语法</span><span class="sxs-lookup"><span data-stu-id="c0474-105">Syntax</span></span>

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="c0474-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="c0474-106">Attributes and Elements</span></span>

<span data-ttu-id="c0474-107">以下各节描述了元素的属性、子元素和父元素 `Configuration` 。</span><span class="sxs-lookup"><span data-stu-id="c0474-107">The following sections describe the attributes, child elements, and the parent element of the `Configuration` element.</span></span> <span data-ttu-id="c0474-108">此元素必须是每个格式化文件的根元素，并且此元素必须包含至少一个子元素。</span><span class="sxs-lookup"><span data-stu-id="c0474-108">This element must be the root element for each formatting file, and this element must contain at least one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c0474-109">特性</span><span class="sxs-lookup"><span data-stu-id="c0474-109">Attributes</span></span>

<span data-ttu-id="c0474-110">无。</span><span class="sxs-lookup"><span data-stu-id="c0474-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c0474-111">子元素</span><span class="sxs-lookup"><span data-stu-id="c0474-111">Child Elements</span></span>

|<span data-ttu-id="c0474-112">元素</span><span class="sxs-lookup"><span data-stu-id="c0474-112">Element</span></span>|<span data-ttu-id="c0474-113">描述</span><span class="sxs-lookup"><span data-stu-id="c0474-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c0474-114">Controls Element for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="c0474-114">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="c0474-115">可选元素。</span><span class="sxs-lookup"><span data-stu-id="c0474-115">Optional element.</span></span><br /><br /> <span data-ttu-id="c0474-116">定义可供格式设置文件的所有视图使用的公共控件。</span><span class="sxs-lookup"><span data-stu-id="c0474-116">Defines the common controls that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="c0474-117">DefaultSettings Element (Format)</span><span class="sxs-lookup"><span data-stu-id="c0474-117">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="c0474-118">可选元素。</span><span class="sxs-lookup"><span data-stu-id="c0474-118">Optional element.</span></span><br /><br /> <span data-ttu-id="c0474-119">定义适用于格式设置文件的所有视图的常见设置。</span><span class="sxs-lookup"><span data-stu-id="c0474-119">Defines common settings that apply to all the views of the formatting file.</span></span>|
|[<span data-ttu-id="c0474-120">SelectionSets 元素格式</span><span class="sxs-lookup"><span data-stu-id="c0474-120">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="c0474-121">可选元素。</span><span class="sxs-lookup"><span data-stu-id="c0474-121">Optional element.</span></span><br /><br /> <span data-ttu-id="c0474-122">定义可供格式设置文件的所有视图使用的常用 .NET 对象集。</span><span class="sxs-lookup"><span data-stu-id="c0474-122">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|
|[<span data-ttu-id="c0474-123">ViewDefinitions Element (Format)</span><span class="sxs-lookup"><span data-stu-id="c0474-123">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="c0474-124">可选元素。</span><span class="sxs-lookup"><span data-stu-id="c0474-124">Optional element.</span></span><br /><br /> <span data-ttu-id="c0474-125">定义用于显示对象的视图。</span><span class="sxs-lookup"><span data-stu-id="c0474-125">Defines the views used to display objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c0474-126">父元素</span><span class="sxs-lookup"><span data-stu-id="c0474-126">Parent Elements</span></span>

<span data-ttu-id="c0474-127">无。</span><span class="sxs-lookup"><span data-stu-id="c0474-127">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="c0474-128">备注</span><span class="sxs-lookup"><span data-stu-id="c0474-128">Remarks</span></span>

<span data-ttu-id="c0474-129">格式化文件定义对象的显示方式。</span><span class="sxs-lookup"><span data-stu-id="c0474-129">Formatting files define how objects are displayed.</span></span> <span data-ttu-id="c0474-130">在大多数情况下，此根元素包含一个[ViewDefinitions](./viewdefinitions-element-format.md)元素，该元素定义格式设置文件的表、列表和宽视图。</span><span class="sxs-lookup"><span data-stu-id="c0474-130">In most cases, this root element contains a [ViewDefinitions](./viewdefinitions-element-format.md) element that defines the table, list, and wide views of the formatting file.</span></span> <span data-ttu-id="c0474-131">除了视图定义以外，格式设置文件还可以定义这些视图可以使用的常用选择集、设置和控件。</span><span class="sxs-lookup"><span data-stu-id="c0474-131">In addition to the view definitions, the formatting file can define common selection sets, settings, and controls that those views can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="c0474-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c0474-132">See Also</span></span>

[<span data-ttu-id="c0474-133">Controls Element for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="c0474-133">Controls Element for Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="c0474-134">DefaultSettings Element (Format)</span><span class="sxs-lookup"><span data-stu-id="c0474-134">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="c0474-135">SelectionSets Element (Format)</span><span class="sxs-lookup"><span data-stu-id="c0474-135">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="c0474-136">ViewDefinitions Element (Format)</span><span class="sxs-lookup"><span data-stu-id="c0474-136">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="c0474-137">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="c0474-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
