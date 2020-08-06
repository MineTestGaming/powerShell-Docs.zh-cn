---
title: 列表视图 (GroupBy) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 7956d13e196454a3f6da185e9be74f9d3cb8ef63
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773396"
---
# <a name="list-view-groupby"></a><span data-ttu-id="8ef8b-102">列表视图 (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="8ef8b-102">List View (GroupBy)</span></span>

<span data-ttu-id="8ef8b-103">此示例演示如何实现将列表行分为多个组的列表视图。</span><span class="sxs-lookup"><span data-stu-id="8ef8b-103">This example shows how to implement a list view that separates the rows of the list into groups.</span></span> <span data-ttu-id="8ef8b-104">此列表视图显示[system.serviceprocess. Servicecontroller 的属性？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)由[get-help](/powershell/module/Microsoft.PowerShell.Management/Get-Service) Cmdlet 返回的 Fullname 对象。</span><span class="sxs-lookup"><span data-stu-id="8ef8b-104">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="8ef8b-105">有关列表视图组件的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="8ef8b-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="8ef8b-106">加载此格式设置文件</span><span class="sxs-lookup"><span data-stu-id="8ef8b-106">To load this formatting file</span></span>

1. <span data-ttu-id="8ef8b-107">将本主题的 "示例" 部分中的 XML 复制到一个文本文件中。</span><span class="sxs-lookup"><span data-stu-id="8ef8b-107">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="8ef8b-108">保存文本文件。</span><span class="sxs-lookup"><span data-stu-id="8ef8b-108">Save the text file.</span></span> <span data-ttu-id="8ef8b-109">请确保将扩展名添加 `format.ps1xml` 到文件，以将其标识为格式化文件。</span><span class="sxs-lookup"><span data-stu-id="8ef8b-109">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="8ef8b-110">打开 Windows PowerShell 并运行以下命令，将格式化文件加载到当前会话中： `Update-formatdata -prependpath PathToFormattingFile` 。</span><span class="sxs-lookup"><span data-stu-id="8ef8b-110">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="8ef8b-111">此格式化文件定义已由 Windows PowerShell 格式设置文件定义的对象的显示。</span><span class="sxs-lookup"><span data-stu-id="8ef8b-111">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="8ef8b-112">在 `prependPath` 运行 cmdlet 时，必须使用参数，并且不能将此格式化文件作为模块加载。</span><span class="sxs-lookup"><span data-stu-id="8ef8b-112">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="8ef8b-113">演示</span><span class="sxs-lookup"><span data-stu-id="8ef8b-113">Demonstrates</span></span>

<span data-ttu-id="8ef8b-114">此格式化文件演示了以下 XML 元素：</span><span class="sxs-lookup"><span data-stu-id="8ef8b-114">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="8ef8b-115">视图的[名称](./name-element-for-view-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="8ef8b-115">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="8ef8b-116">定义视图要显示的对象的[ViewSelectedBy](./viewselectedby-element-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="8ef8b-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="8ef8b-117">定义新的对象组显示方式的[GroupBy](./viewselectedby-element-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="8ef8b-117">The [GroupBy](./viewselectedby-element-format.md) element that defines how a new group of objects is displayed.</span></span>

- <span data-ttu-id="8ef8b-118">定义视图显示的属性的[ListControl](./listcontrol-element-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="8ef8b-118">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="8ef8b-119">定义在列表视图的行中显示的[内容的包含项元素。](./listitem-element-for-listitems-for-listcontrol-format.md)</span><span class="sxs-lookup"><span data-stu-id="8ef8b-119">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="8ef8b-120">定义要显示的属性的[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="8ef8b-120">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="8ef8b-121">示例</span><span class="sxs-lookup"><span data-stu-id="8ef8b-121">Example</span></span>

<span data-ttu-id="8ef8b-122">下面的 XML 定义一个列表视图，当[system.serviceprocess](/dotnet/api/System.ServiceProcess.ServiceController.Status)属性的值发生更改时，它将启动一个新组。</span><span class="sxs-lookup"><span data-stu-id="8ef8b-122">The following XML defines a list view that starts a new group whenever the value of the [System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status) property changes.</span></span> <span data-ttu-id="8ef8b-123">每个组启动时，将显示自定义标签，其中包含属性的新值。</span><span class="sxs-lookup"><span data-stu-id="8ef8b-123">When each group is started, a custom label is displayed that includes the new value of the property.</span></span>

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <Name>System.ServiceProcess.ServiceController</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <PropertyName>Status</PropertyName>
        <Label>New Service Status</Label>
      </GroupBy>
      <ListControl>
        <ListEntries>
          <ListEntry>
            <ListItems>
              <ListItem>
                <PropertyName>Name</PropertyName>
              </ListItem>
              <ListItem>
                <PropertyName>DisplayName</PropertyName>
              </ListItem>
              <ListItem>
                <PropertyName>ServiceType</PropertyName>
              </ListItem>
            </ListItems>
          </ListEntry>
        </ListEntries>
      </ListControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

<span data-ttu-id="8ef8b-124">下面的示例演示 Windows PowerShell 如何显示[system.serviceprocess. Servicecontroller？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)加载此格式化文件之后的 Fullname 对象。</span><span class="sxs-lookup"><span data-stu-id="8ef8b-124">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span> <span data-ttu-id="8ef8b-125">Windows PowerShell 将自动添加组标签之前和之后添加的空白行。</span><span class="sxs-lookup"><span data-stu-id="8ef8b-125">The blank lines added before and after the group label are automatically added by Windows PowerShell.</span></span>

```powershell
Get-Service f*
```

```output
   New Service Status: Stopped

Name        : Fax
DisplayName : Fax
ServiceType : Win32OwnProcess

   New Service Status: Running

Name        : FCSAM
DisplayName : Microsoft Antimalware Service
ServiceType : Win32OwnProcess

   New Service Status: Stopped

Name        : fdPHost
DisplayName : Function Discovery Provider Host
ServiceType : Win32ShareProcess

   New Service Status: Running

Name        : FDResPub
DisplayName : Function Discovery Resource Publication
ServiceType : Win32ShareProcess

Name        : FontCache
DisplayName : Windows Font Cache Service
ServiceType : Win32ShareProcess

   New Service Status: Stopped

Name        : FontCache3.0.0.0
DisplayName : Windows Presentation Foundation Font Cache 3.0.0.0
ServiceType : Win32OwnProcess

   New Service Status: Running

Name        : FSysAgent
DisplayName : Microsoft Forefront System Agent
ServiceType : Win32OwnProcess

Name        : FwcAgent
DisplayName : Firewall Client Agent
ServiceType : Win32OwnProcess
```

## <a name="see-also"></a><span data-ttu-id="8ef8b-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8ef8b-126">See Also</span></span>

[<span data-ttu-id="8ef8b-127">格式设置文件示例</span><span class="sxs-lookup"><span data-stu-id="8ef8b-127">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="8ef8b-128">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="8ef8b-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
