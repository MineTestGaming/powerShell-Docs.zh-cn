---
title: 配置 （格式） 的控件的 CustomControl CustomEntries 元素 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80fc4de2-208f-4506-9a6a-c2675bb83be4
caps.latest.revision: 11
ms.openlocfilehash: abef6c91500f665c2366f221496d4cfd6444f5c9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856303"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="36d0b-102">CustomEntries Element for CustomControl for Controls for Configuration (Format)</span><span class="sxs-lookup"><span data-stu-id="36d0b-102">CustomEntries Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="36d0b-103">提供了公共控件的定义。</span><span class="sxs-lookup"><span data-stu-id="36d0b-103">Provides the definitions of a common control.</span></span> <span data-ttu-id="36d0b-104">定义可由格式设置文件中的所有视图的公共控件时，将都使用此元素。</span><span class="sxs-lookup"><span data-stu-id="36d0b-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="36d0b-105">配置 （格式） 的配置 （格式） 的配置 （CustomControl CustomEntries 元素的控件的配置 （格式） CustomControl 元素的控件的控件元素的配置元素 （格式） 的 Controls 元素格式）</span><span class="sxs-lookup"><span data-stu-id="36d0b-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="36d0b-106">语法</span><span class="sxs-lookup"><span data-stu-id="36d0b-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="36d0b-107">属性和元素</span><span class="sxs-lookup"><span data-stu-id="36d0b-107">Attributes and Elements</span></span>

<span data-ttu-id="36d0b-108">以下各节描述了特性、 子元素和父元素的`CustomEntries`元素。</span><span class="sxs-lookup"><span data-stu-id="36d0b-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntries` element.</span></span> <span data-ttu-id="36d0b-109">必须指定一个或多个子元素。</span><span class="sxs-lookup"><span data-stu-id="36d0b-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="36d0b-110">特性</span><span class="sxs-lookup"><span data-stu-id="36d0b-110">Attributes</span></span>

<span data-ttu-id="36d0b-111">无。</span><span class="sxs-lookup"><span data-stu-id="36d0b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="36d0b-112">子元素</span><span class="sxs-lookup"><span data-stu-id="36d0b-112">Child Elements</span></span>

|<span data-ttu-id="36d0b-113">元素</span><span class="sxs-lookup"><span data-stu-id="36d0b-113">Element</span></span>|<span data-ttu-id="36d0b-114">描述</span><span class="sxs-lookup"><span data-stu-id="36d0b-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="36d0b-115">配置 （格式） 的控件的 CustomControl CustomEntry 元素</span><span class="sxs-lookup"><span data-stu-id="36d0b-115">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="36d0b-116">提供了一个常用的控件的定义。</span><span class="sxs-lookup"><span data-stu-id="36d0b-116">Provides a definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="36d0b-117">父元素</span><span class="sxs-lookup"><span data-stu-id="36d0b-117">Parent Elements</span></span>

|<span data-ttu-id="36d0b-118">元素</span><span class="sxs-lookup"><span data-stu-id="36d0b-118">Element</span></span>|<span data-ttu-id="36d0b-119">描述</span><span class="sxs-lookup"><span data-stu-id="36d0b-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="36d0b-120">配置 （格式） 的控件的 CustomControl 元素</span><span class="sxs-lookup"><span data-stu-id="36d0b-120">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="36d0b-121">定义公共控件。</span><span class="sxs-lookup"><span data-stu-id="36d0b-121">Defines a common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="36d0b-122">备注</span><span class="sxs-lookup"><span data-stu-id="36d0b-122">Remarks</span></span>

<span data-ttu-id="36d0b-123">在大多数情况下，控件具有只有一个定义，在单个定义`CustomEntry`元素。</span><span class="sxs-lookup"><span data-stu-id="36d0b-123">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="36d0b-124">但是很可能有多个定义，如果你想要使用相同的控件来显示不同的.NET 对象。</span><span class="sxs-lookup"><span data-stu-id="36d0b-124">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="36d0b-125">在这些情况下，你可以定义`CustomEntry`元素为每个对象或对象集。</span><span class="sxs-lookup"><span data-stu-id="36d0b-125">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="36d0b-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="36d0b-126">See Also</span></span>

[<span data-ttu-id="36d0b-127">配置 （格式） 的控件的 CustomControl 元素</span><span class="sxs-lookup"><span data-stu-id="36d0b-127">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="36d0b-128">配置 （格式） 的控件的 CustomControl CustomEntry 元素</span><span class="sxs-lookup"><span data-stu-id="36d0b-128">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="36d0b-129">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="36d0b-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)