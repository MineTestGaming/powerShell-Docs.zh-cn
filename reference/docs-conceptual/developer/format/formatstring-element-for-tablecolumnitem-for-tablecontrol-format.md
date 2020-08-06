---
title: TableControl (格式的 TableColumnItem 的格式字符串元素) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 848583e697d0ab7bd5b017c14c47aba3c51a3c17
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781539"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="7ba8c-102">FormatString Element for TableColumnItem for TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7ba8c-102">FormatString Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="7ba8c-103">指定一种格式模式，用于定义表的属性或脚本值的显示方式。</span><span class="sxs-lookup"><span data-stu-id="7ba8c-103">Specifies a format pattern that defines how the property or script value of the table is displayed.</span></span>

<span data-ttu-id="7ba8c-104">配置元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) TableControl 元素 (格式) TableRowEntries 元素 (格式) TableRowEntry 元素 (格式) TableColumnItems 元素 (格式) TableColumnItem (格式) </span><span class="sxs-lookup"><span data-stu-id="7ba8c-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) FormatString Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7ba8c-105">语法</span><span class="sxs-lookup"><span data-stu-id="7ba8c-105">Syntax</span></span>

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7ba8c-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="7ba8c-106">Attributes and Elements</span></span>

<span data-ttu-id="7ba8c-107">以下各节描述了元素的属性、子元素和父元素 `FormatString` 。</span><span class="sxs-lookup"><span data-stu-id="7ba8c-107">The following sections describe attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7ba8c-108">特性</span><span class="sxs-lookup"><span data-stu-id="7ba8c-108">Attributes</span></span>

<span data-ttu-id="7ba8c-109">无。</span><span class="sxs-lookup"><span data-stu-id="7ba8c-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7ba8c-110">子元素</span><span class="sxs-lookup"><span data-stu-id="7ba8c-110">Child Elements</span></span>

<span data-ttu-id="7ba8c-111">无。</span><span class="sxs-lookup"><span data-stu-id="7ba8c-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7ba8c-112">父元素</span><span class="sxs-lookup"><span data-stu-id="7ba8c-112">Parent Elements</span></span>

|<span data-ttu-id="7ba8c-113">元素</span><span class="sxs-lookup"><span data-stu-id="7ba8c-113">Element</span></span>|<span data-ttu-id="7ba8c-114">描述</span><span class="sxs-lookup"><span data-stu-id="7ba8c-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7ba8c-115">TableColumnItem 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="7ba8c-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="7ba8c-116">定义其值显示在行的列中的属性或脚本。</span><span class="sxs-lookup"><span data-stu-id="7ba8c-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7ba8c-117">文本值</span><span class="sxs-lookup"><span data-stu-id="7ba8c-117">Text Value</span></span>

<span data-ttu-id="7ba8c-118">指定用于设置数据格式的模式。</span><span class="sxs-lookup"><span data-stu-id="7ba8c-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="7ba8c-119">例如，可使用此模式设置类型为[system.object](/dotnet/api/System.TimeSpan)： {0： MMM} {0： dd} {0： HH}： {0： mm} 的任何属性的值的格式。</span><span class="sxs-lookup"><span data-stu-id="7ba8c-119">For example, this pattern can be used to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="7ba8c-120">备注</span><span class="sxs-lookup"><span data-stu-id="7ba8c-120">Remarks</span></span>

<span data-ttu-id="7ba8c-121">创建表视图、列表视图、宽视图或自定义视图时，可以使用格式字符串。</span><span class="sxs-lookup"><span data-stu-id="7ba8c-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="7ba8c-122">有关设置视图中显示的值的格式的详细信息，请参阅[设置显示的数据的格式](./formatting-displayed-data.md)。</span><span class="sxs-lookup"><span data-stu-id="7ba8c-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="7ba8c-123">有关表视图的组件的详细信息，请参阅[表视图](./creating-a-table-view.md)。</span><span class="sxs-lookup"><span data-stu-id="7ba8c-123">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="7ba8c-124">示例</span><span class="sxs-lookup"><span data-stu-id="7ba8c-124">Example</span></span>

<span data-ttu-id="7ba8c-125">下面的示例演示如何为属性的值定义格式字符串 `StartTime` 。</span><span class="sxs-lookup"><span data-stu-id="7ba8c-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a><span data-ttu-id="7ba8c-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7ba8c-126">See Also</span></span>

[<span data-ttu-id="7ba8c-127">创建表视图</span><span class="sxs-lookup"><span data-stu-id="7ba8c-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="7ba8c-128">设置显示数据的格式</span><span class="sxs-lookup"><span data-stu-id="7ba8c-128">Formatting Displayed Data</span></span>](./formatting-displayed-data.md)

[<span data-ttu-id="7ba8c-129">TableColumnItem 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="7ba8c-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="7ba8c-130">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="7ba8c-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
