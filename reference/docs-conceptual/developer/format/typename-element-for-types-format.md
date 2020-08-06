---
title: " (Format) 类型的类型名称元素 |Microsoft Docs"
ms.date: 09/13/2016
ms.openlocfilehash: 40fad73c66124d6c3b0d969b4268713a492c963a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772529"
---
# <a name="typename-element-for-types-format"></a><span data-ttu-id="5fdd6-102">TypeName Element for Types (Format)</span><span class="sxs-lookup"><span data-stu-id="5fdd6-102">TypeName Element for Types (Format)</span></span>

<span data-ttu-id="5fdd6-103">指定属于选择集的对象的 .NET 类型。</span><span class="sxs-lookup"><span data-stu-id="5fdd6-103">Specifies the .NET type of an object that belongs to the selection set.</span></span>

<span data-ttu-id="5fdd6-104">配置元素 (格式) SelectionSets 元素 (格式) SelectionSet 元素 (格式) 格式 (格式) 类型 () 格式的 TypeName 元素</span><span class="sxs-lookup"><span data-stu-id="5fdd6-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format) TypeName Element of Types (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5fdd6-105">语法</span><span class="sxs-lookup"><span data-stu-id="5fdd6-105">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5fdd6-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="5fdd6-106">Attributes and Elements</span></span>

<span data-ttu-id="5fdd6-107">以下各节描述了元素的属性、子元素和父元素 `TypeName` 。</span><span class="sxs-lookup"><span data-stu-id="5fdd6-107">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span> <span data-ttu-id="5fdd6-108">`TypeName`选择集中必须至少包含一个元素。</span><span class="sxs-lookup"><span data-stu-id="5fdd6-108">At least one `TypeName` element must be included in the selection set.</span></span>

### <a name="attributes"></a><span data-ttu-id="5fdd6-109">特性</span><span class="sxs-lookup"><span data-stu-id="5fdd6-109">Attributes</span></span>

<span data-ttu-id="5fdd6-110">无。</span><span class="sxs-lookup"><span data-stu-id="5fdd6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5fdd6-111">子元素</span><span class="sxs-lookup"><span data-stu-id="5fdd6-111">Child Elements</span></span>

<span data-ttu-id="5fdd6-112">无。</span><span class="sxs-lookup"><span data-stu-id="5fdd6-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5fdd6-113">父元素</span><span class="sxs-lookup"><span data-stu-id="5fdd6-113">Parent Elements</span></span>

|<span data-ttu-id="5fdd6-114">元素</span><span class="sxs-lookup"><span data-stu-id="5fdd6-114">Element</span></span>|<span data-ttu-id="5fdd6-115">描述</span><span class="sxs-lookup"><span data-stu-id="5fdd6-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5fdd6-116">类型元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="5fdd6-116">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="5fdd6-117">定义选择集中的 .NET 对象。</span><span class="sxs-lookup"><span data-stu-id="5fdd6-117">Defines the .NET objects that are in the selection set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5fdd6-118">文本值</span><span class="sxs-lookup"><span data-stu-id="5fdd6-118">Text Value</span></span>

<span data-ttu-id="5fdd6-119">指定 .NET 类型的完全限定名称。</span><span class="sxs-lookup"><span data-stu-id="5fdd6-119">Specify the fully qualified name for the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="5fdd6-120">备注</span><span class="sxs-lookup"><span data-stu-id="5fdd6-120">Remarks</span></span>

<span data-ttu-id="5fdd6-121">如果你有一组要通过使用单个名称引用的相关对象（例如通过继承相关的一组对象），则可以使用选择集。</span><span class="sxs-lookup"><span data-stu-id="5fdd6-121">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="5fdd6-122">定义视图时，可以使用选择集的名称（而不是列出每个视图中的所有对象）来指定对象集。</span><span class="sxs-lookup"><span data-stu-id="5fdd6-122">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="5fdd6-123">常用选择集在定义格式设置文件的视图时由其名称指定。</span><span class="sxs-lookup"><span data-stu-id="5fdd6-123">Common selection sets are specified by their name when defining the views of the formatting file.</span></span> <span data-ttu-id="5fdd6-124">在这些情况下， `SelectionSetName` 视图的元素的子元素 `ViewSelectedBy` 指定了集。</span><span class="sxs-lookup"><span data-stu-id="5fdd6-124">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` element for the view specifies the set.</span></span> <span data-ttu-id="5fdd6-125">但是，视图的不同项还可以指定仅适用于该视图项的选择集。</span><span class="sxs-lookup"><span data-stu-id="5fdd6-125">However, different entries of a view can also specify a selection set that applies to only that entry of the view.</span></span> <span data-ttu-id="5fdd6-126">有关选择集的详细信息，请参阅[定义对象集](./defining-selection-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="5fdd6-126">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="5fdd6-127">示例</span><span class="sxs-lookup"><span data-stu-id="5fdd6-127">Example</span></span>

<span data-ttu-id="5fdd6-128">下面的示例演示 `SelectionSet` 定义四个 .net 类型的元素。</span><span class="sxs-lookup"><span data-stu-id="5fdd6-128">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

```
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

## <a name="see-also"></a><span data-ttu-id="5fdd6-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5fdd6-129">See Also</span></span>

[<span data-ttu-id="5fdd6-130">定义选项集</span><span class="sxs-lookup"><span data-stu-id="5fdd6-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="5fdd6-131">SelectionSet Element (Format)</span><span class="sxs-lookup"><span data-stu-id="5fdd6-131">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="5fdd6-132">SelectionSets Element (Format)</span><span class="sxs-lookup"><span data-stu-id="5fdd6-132">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="5fdd6-133">类型元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="5fdd6-133">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="5fdd6-134">编写 Windows PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="5fdd6-134">Writing a Windows PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
