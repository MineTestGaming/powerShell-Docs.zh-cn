---
title: ListControl (Format) 的 ListEntry 元素 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d98f0b5215eea7668f866d2733214ade79d748f1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785687"
---
# <a name="listentry-element-for-listcontrol-format"></a><span data-ttu-id="f4784-102">ListEntry Element for ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="f4784-102">ListEntry Element for ListControl (Format)</span></span>

<span data-ttu-id="f4784-103">提供列表视图的定义。</span><span class="sxs-lookup"><span data-stu-id="f4784-103">Provides a definition of the list view.</span></span>

<span data-ttu-id="f4784-104">配置元素 (格式) ViewDefinitions 元素 (格式) View 元素 (格式) ListControl 元素 (格式) ListEntries 元素 (格式) ListEntry 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="f4784-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f4784-105">语法</span><span class="sxs-lookup"><span data-stu-id="f4784-105">Syntax</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f4784-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="f4784-106">Attributes and Elements</span></span>

<span data-ttu-id="f4784-107">以下各节描述了元素的属性、子元素和父元素 `ListEntry` 。</span><span class="sxs-lookup"><span data-stu-id="f4784-107">The following sections describe the attributes, child elements, and the parent element of the `ListEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f4784-108">特性</span><span class="sxs-lookup"><span data-stu-id="f4784-108">Attributes</span></span>

<span data-ttu-id="f4784-109">无。</span><span class="sxs-lookup"><span data-stu-id="f4784-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f4784-110">子元素</span><span class="sxs-lookup"><span data-stu-id="f4784-110">Child Elements</span></span>

|<span data-ttu-id="f4784-111">元素</span><span class="sxs-lookup"><span data-stu-id="f4784-111">Element</span></span>|<span data-ttu-id="f4784-112">说明</span><span class="sxs-lookup"><span data-stu-id="f4784-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f4784-113">ListEntry 的 EntrySelectedBy 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="f4784-113">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="f4784-114">可选元素。</span><span class="sxs-lookup"><span data-stu-id="f4784-114">Optional element.</span></span><br /><br /> <span data-ttu-id="f4784-115">定义使用此列表视图定义的 .NET 对象，或使用此定义必须存在的条件。</span><span class="sxs-lookup"><span data-stu-id="f4784-115">Defines the .NET objects that use this list view definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="f4784-116">ListItems 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="f4784-116">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="f4784-117">必需的元素。</span><span class="sxs-lookup"><span data-stu-id="f4784-117">Required element.</span></span><br /><br /> <span data-ttu-id="f4784-118">定义其值由列表视图显示的属性和脚本。</span><span class="sxs-lookup"><span data-stu-id="f4784-118">Defines the properties and scripts whose values are displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f4784-119">父元素</span><span class="sxs-lookup"><span data-stu-id="f4784-119">Parent Elements</span></span>

|<span data-ttu-id="f4784-120">元素</span><span class="sxs-lookup"><span data-stu-id="f4784-120">Element</span></span>|<span data-ttu-id="f4784-121">说明</span><span class="sxs-lookup"><span data-stu-id="f4784-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f4784-122">ListEntries 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="f4784-122">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="f4784-123">提供列表视图的定义。</span><span class="sxs-lookup"><span data-stu-id="f4784-123">Provides the definitions of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f4784-124">备注</span><span class="sxs-lookup"><span data-stu-id="f4784-124">Remarks</span></span>

<span data-ttu-id="f4784-125">列表视图是显示每个对象的属性值或脚本值的列表格式。</span><span class="sxs-lookup"><span data-stu-id="f4784-125">A list view is a list format that displays property values or script values for each object.</span></span> <span data-ttu-id="f4784-126">有关列表视图的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="f4784-126">For more information about list views, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f4784-127">示例</span><span class="sxs-lookup"><span data-stu-id="f4784-127">Example</span></span>

<span data-ttu-id="f4784-128">此示例显示了为[system.serviceprocess. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController)对象定义列表视图的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="f4784-128">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>...</ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="f4784-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f4784-129">See Also</span></span>

[<span data-ttu-id="f4784-130">创建列表视图</span><span class="sxs-lookup"><span data-stu-id="f4784-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="f4784-131">ListEntry 的 EntrySelectedBy 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="f4784-131">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="f4784-132">ListEntries 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="f4784-132">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="f4784-133">ListItems 元素 (格式) </span><span class="sxs-lookup"><span data-stu-id="f4784-133">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="f4784-134">编写 Windows PowerShell 格式设置和类型文件</span><span class="sxs-lookup"><span data-stu-id="f4784-134">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
