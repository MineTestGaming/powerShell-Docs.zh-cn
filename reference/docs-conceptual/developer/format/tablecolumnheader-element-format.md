---
title: " (格式) 的 TableColumnHeader 元素 |Microsoft Docs"
ms.date: 09/13/2016
ms.openlocfilehash: 6296aea5c567663b1c3c0a2cf0a57b21aa5394de
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785177"
---
# <a name="tablecolumnheader-element-format"></a><span data-ttu-id="94b46-102">TableColumnHeader Element (Format)</span><span class="sxs-lookup"><span data-stu-id="94b46-102">TableColumnHeader Element (Format)</span></span>

<span data-ttu-id="94b46-103">定义标签、列的宽度和表中某一列的标签对齐方式。</span><span class="sxs-lookup"><span data-stu-id="94b46-103">Defines the label, the width of the column, and the alignment of the label for a column of the table.</span></span>

<span data-ttu-id="94b46-104">配置元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) TableControl 元素 (格式) TableHeaders 元素 (TableColumnHeader) 格式 (TableHeaders 元素) </span><span class="sxs-lookup"><span data-stu-id="94b46-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="94b46-105">语法</span><span class="sxs-lookup"><span data-stu-id="94b46-105">Syntax</span></span>

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="94b46-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="94b46-106">Attributes and Elements</span></span>

<span data-ttu-id="94b46-107">以下各节描述了元素的属性、子元素和父元素 `TableColumnHeader` 。</span><span class="sxs-lookup"><span data-stu-id="94b46-107">The following sections describe attributes, child elements, and the parent element of the `TableColumnHeader` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="94b46-108">特性</span><span class="sxs-lookup"><span data-stu-id="94b46-108">Attributes</span></span>

<span data-ttu-id="94b46-109">无。</span><span class="sxs-lookup"><span data-stu-id="94b46-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="94b46-110">子元素</span><span class="sxs-lookup"><span data-stu-id="94b46-110">Child Elements</span></span>

|<span data-ttu-id="94b46-111">元素</span><span class="sxs-lookup"><span data-stu-id="94b46-111">Element</span></span>|<span data-ttu-id="94b46-112">描述</span><span class="sxs-lookup"><span data-stu-id="94b46-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="94b46-113">TableControl 的 TableColumnHeader 的 Label 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="94b46-113">Label Element For TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="94b46-114">可选元素。</span><span class="sxs-lookup"><span data-stu-id="94b46-114">Optional element.</span></span><br /><br /> <span data-ttu-id="94b46-115">定义在列顶部显示的标签。</span><span class="sxs-lookup"><span data-stu-id="94b46-115">Defines the label that is displayed at the top of the column.</span></span> <span data-ttu-id="94b46-116">如果未指定标签，则使用在行中显示其值的属性的名称。</span><span class="sxs-lookup"><span data-stu-id="94b46-116">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>|
|[<span data-ttu-id="94b46-117">Width Element for TableColumnHeader for TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="94b46-117">Width Element for TableColumnHeader for TableControl (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="94b46-118">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="94b46-118">Required element.</span></span><br /><br /> <span data-ttu-id="94b46-119">指定列的字符)  (宽度。</span><span class="sxs-lookup"><span data-stu-id="94b46-119">Specifies the width (in characters) of the column.</span></span>|
|[<span data-ttu-id="94b46-120">Alignment Element for TableColumnHeader for TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="94b46-120">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="94b46-121">可选元素。</span><span class="sxs-lookup"><span data-stu-id="94b46-121">Optional element.</span></span><br /><br /> <span data-ttu-id="94b46-122">指定列的标签的显示方式。</span><span class="sxs-lookup"><span data-stu-id="94b46-122">Specifies how the label of the column is displayed.</span></span> <span data-ttu-id="94b46-123">如果未指定对齐方式，则在左侧对齐标签。</span><span class="sxs-lookup"><span data-stu-id="94b46-123">If no alignment is specified, the label is aligned on the left.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="94b46-124">父元素</span><span class="sxs-lookup"><span data-stu-id="94b46-124">Parent Elements</span></span>

|<span data-ttu-id="94b46-125">元素</span><span class="sxs-lookup"><span data-stu-id="94b46-125">Element</span></span>|<span data-ttu-id="94b46-126">描述</span><span class="sxs-lookup"><span data-stu-id="94b46-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="94b46-127">TableHeaders Element (Format)</span><span class="sxs-lookup"><span data-stu-id="94b46-127">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="94b46-128">定义表视图的列。</span><span class="sxs-lookup"><span data-stu-id="94b46-128">Defines the columns of a table view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="94b46-129">备注</span><span class="sxs-lookup"><span data-stu-id="94b46-129">Remarks</span></span>

<span data-ttu-id="94b46-130">为表的每个列指定标题。</span><span class="sxs-lookup"><span data-stu-id="94b46-130">Specify a header for each column of the table.</span></span> <span data-ttu-id="94b46-131">列按定义元素的顺序显示 `TableColumnHeader` 。</span><span class="sxs-lookup"><span data-stu-id="94b46-131">The columns are displayed in the order in which the `TableColumnHeader` elements are defined.</span></span>

<span data-ttu-id="94b46-132">表必须与元素具有相同数量的 `TableColumnHeader` 元素 `TableRowEntry` 。</span><span class="sxs-lookup"><span data-stu-id="94b46-132">A table must have the same number of `TableColumnHeader` elements as `TableRowEntry` elements.</span></span> <span data-ttu-id="94b46-133">列标题定义表顶部的文本的显示方式。</span><span class="sxs-lookup"><span data-stu-id="94b46-133">The column header defines how the text at the top of the table is displayed.</span></span> <span data-ttu-id="94b46-134">行条目定义在表的行中显示的数据。</span><span class="sxs-lookup"><span data-stu-id="94b46-134">The row entries define what data is displayed in the rows of the table.</span></span>

<span data-ttu-id="94b46-135">有关表视图的组件的详细信息，请参阅[表视图](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="94b46-135">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="94b46-136">示例</span><span class="sxs-lookup"><span data-stu-id="94b46-136">Example</span></span>

<span data-ttu-id="94b46-137">下面的示例演示两个 `TableColumnHeader` 元素。</span><span class="sxs-lookup"><span data-stu-id="94b46-137">The following example shows two `TableColumnHeader` elements.</span></span> <span data-ttu-id="94b46-138">第一个元素定义其标签为 "列 1" 的列，宽度为16个字符，其标签在左侧对齐。</span><span class="sxs-lookup"><span data-stu-id="94b46-138">The first element defines a column whose label is "Column 1", has a width of 16 characters, and whose label is aligned on the left.</span></span> <span data-ttu-id="94b46-139">第二个元素定义标签为 "Column 2" 的列，其宽度为10个字符，标签在列中居中。</span><span class="sxs-lookup"><span data-stu-id="94b46-139">The second element defines a column whose label is "Column 2", has a width of 10 characters, and whose label is centered in the column.</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>
    <Label>Column 1</Label)
    <Width>16</Width>
    <Alignment>Left</Alignment>
  </TableColumnHeader>
    <TableColumnHeader>
    <Label>Column 2</Label)
    <Width>10</Width>
    <Alignment>Centered</Alignment>
  </TableColumnHeader>
</TableHeaders>
```

## <a name="see-also"></a><span data-ttu-id="94b46-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="94b46-140">See Also</span></span>

[<span data-ttu-id="94b46-141">Alignment Element for TableColumnHeader for TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="94b46-141">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="94b46-142">创建表视图</span><span class="sxs-lookup"><span data-stu-id="94b46-142">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="94b46-143">Label Element for TableColumnHeader for TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="94b46-143">Label Element for TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="94b46-144">TableControl 的 TableHeaders 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="94b46-144">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="94b46-145">TableControl 元素的 TableColumnHeader 宽度 (格式) </span><span class="sxs-lookup"><span data-stu-id="94b46-145">Width for TableColumnHeader for TableControl Element (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="94b46-146">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="94b46-146">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
