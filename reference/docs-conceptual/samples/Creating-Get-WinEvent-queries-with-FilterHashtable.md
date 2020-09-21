---
ms.date: 09/13/2019
title: 使用 FilterHashtable 创建 Get-WinEvent 查询
ms.openlocfilehash: 002d84515368663e0e807f48ffe883bd533be1d9
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786639"
---
# <a name="creating-get-winevent-queries-with-filterhashtable"></a><span data-ttu-id="ccea7-102">使用 FilterHashtable 创建 Get-WinEvent 查询</span><span class="sxs-lookup"><span data-stu-id="ccea7-102">Creating Get-WinEvent queries with FilterHashtable</span></span>

<span data-ttu-id="ccea7-103">请参阅[通过 PowerShell 使用 FilterHashTable 筛选事件日志](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/)，以查看 2014 年 6 月 3 日的原创“脚本专家”博客文章。</span><span class="sxs-lookup"><span data-stu-id="ccea7-103">To read the original June 3, 2014 **Scripting Guy** blog post, see [Use FilterHashTable to Filter Event Log with PowerShell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/).</span></span>

<span data-ttu-id="ccea7-104">本文摘录自此原创博客文章，并说明了如何使用 `Get-WinEvent` cmdlet 的 FilterHashtable 参数筛选事件日志。</span><span class="sxs-lookup"><span data-stu-id="ccea7-104">This article is an excerpt of the original blog post and explains how to use the `Get-WinEvent` cmdlet's **FilterHashtable** parameter to filter event logs.</span></span> <span data-ttu-id="ccea7-105">PowerShell 的 `Get-WinEvent` cmdlet 是一种功能强大的方法，可用于筛选 Windows 事件和诊断日志。</span><span class="sxs-lookup"><span data-stu-id="ccea7-105">PowerShell's `Get-WinEvent` cmdlet is a powerful method to filter Windows event and diagnostic logs.</span></span> <span data-ttu-id="ccea7-106">`Get-WinEvent` 查询使用 FilterHashtable 参数时，性能将得到改进。</span><span class="sxs-lookup"><span data-stu-id="ccea7-106">Performance improves when a `Get-WinEvent` query uses the **FilterHashtable** parameter.</span></span>

<span data-ttu-id="ccea7-107">处理大型事件日志时，如果将对象沿管道下发到 `Where-Object` 命令，效率将较低。</span><span class="sxs-lookup"><span data-stu-id="ccea7-107">When you work with large event logs, it's not efficient to send objects down the pipeline to a `Where-Object` command.</span></span> <span data-ttu-id="ccea7-108">在 PowerShell 6 之前，`Get-EventLog` cmdlet 曾是另一个用于获取日志数据的方法。</span><span class="sxs-lookup"><span data-stu-id="ccea7-108">Prior to PowerShell 6, the `Get-EventLog` cmdlet was another option to get log data.</span></span> <span data-ttu-id="ccea7-109">例如，使用下面的命令筛选 Microsoft-Windows-Defrag 日志时，效率较低：</span><span class="sxs-lookup"><span data-stu-id="ccea7-109">For example, the following commands are inefficient to filter the **Microsoft-Windows-Defrag** logs:</span></span>

```powershell
Get-EventLog -LogName Application | Where-Object Source -Match defrag

Get-WinEvent -LogName Application | Where-Object { $_.ProviderName -Match 'defrag' }
```

<span data-ttu-id="ccea7-110">下面的命令使用了可提升性能的哈希表：</span><span class="sxs-lookup"><span data-stu-id="ccea7-110">The following command uses a hash table that improves the performance:</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='*defrag'
}
```

## <a name="blog-posts-about-enumeration"></a><span data-ttu-id="ccea7-111">关于枚举的博客文章</span><span class="sxs-lookup"><span data-stu-id="ccea7-111">Blog posts about enumeration</span></span>

<span data-ttu-id="ccea7-112">本文提供了如何在哈希表中使用枚举值的相关信息。</span><span class="sxs-lookup"><span data-stu-id="ccea7-112">This article presents information about how to use enumerated values in a hash table.</span></span> <span data-ttu-id="ccea7-113">有关枚举的详细信息，请参阅“脚本专家”博客文章。</span><span class="sxs-lookup"><span data-stu-id="ccea7-113">For more information about enumeration, read these **Scripting Guy** blog posts.</span></span> <span data-ttu-id="ccea7-114">若要创建用于返回枚举值的函数，请参阅[枚举和值](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values)。</span><span class="sxs-lookup"><span data-stu-id="ccea7-114">To create a function that returns the enumerated values, see [Enumerations and Values](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values).</span></span>
<span data-ttu-id="ccea7-115">有关详细信息，请参阅[关于枚举的“脚本专家”系列博客文章](https://devblogs.microsoft.com/scripting/?s=about+enumeration)。</span><span class="sxs-lookup"><span data-stu-id="ccea7-115">For more information, see the [Scripting Guy series of blog posts about enumeration](https://devblogs.microsoft.com/scripting/?s=about+enumeration).</span></span>

## <a name="hash-table-key-value-pairs"></a><span data-ttu-id="ccea7-116">哈希表键值对</span><span class="sxs-lookup"><span data-stu-id="ccea7-116">Hash table key-value pairs</span></span>

<span data-ttu-id="ccea7-117">若要生成高效查询，请将 `Get-WinEvent` cmdlet 和 FilterHashtable 参数结合使用。</span><span class="sxs-lookup"><span data-stu-id="ccea7-117">To build efficient queries, use the `Get-WinEvent` cmdlet with the **FilterHashtable** parameter.</span></span>
<span data-ttu-id="ccea7-118">FilterHashtable 允许哈希表作为筛选器，以从 Windows 事件日志获取特定信息。</span><span class="sxs-lookup"><span data-stu-id="ccea7-118">**FilterHashtable** accepts a hash table as a filter to get specific information from Windows event logs.</span></span> <span data-ttu-id="ccea7-119">哈希表将使用键值对。</span><span class="sxs-lookup"><span data-stu-id="ccea7-119">A hash table uses **key-value** pairs.</span></span> <span data-ttu-id="ccea7-120">有关哈希表的详细信息，请参阅 [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables)。</span><span class="sxs-lookup"><span data-stu-id="ccea7-120">For more information about hash tables, see [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span>

<span data-ttu-id="ccea7-121">键值对均位于同一行时，必须使用分号将它们分隔开来。</span><span class="sxs-lookup"><span data-stu-id="ccea7-121">If the **key-value** pairs are on the same line, they must be separated by a semicolon.</span></span> <span data-ttu-id="ccea7-122">每个键值对位于单独的行时，则无需使用分号。</span><span class="sxs-lookup"><span data-stu-id="ccea7-122">If each **key-value** pair is on a separate line, the semicolon isn't needed.</span></span> <span data-ttu-id="ccea7-123">例如，本文将键值对均放置在单独的行上，因此未使用分号。</span><span class="sxs-lookup"><span data-stu-id="ccea7-123">For example, this article places **key-value** pairs on separate lines and doesn't use semicolons.</span></span>

<span data-ttu-id="ccea7-124">本示例使用多个 FilterHashtable 参数的键值对。 </span><span class="sxs-lookup"><span data-stu-id="ccea7-124">This sample uses several of the **FilterHashtable** parameter's **key-value** pairs.</span></span> <span data-ttu-id="ccea7-125">完成的查询包括 LogName、ProviderName、Keywords、ID 和 Level。    </span><span class="sxs-lookup"><span data-stu-id="ccea7-125">The completed query includes **LogName**, **ProviderName**, **Keywords**, **ID**, and **Level**.</span></span>

<span data-ttu-id="ccea7-126">下表显示了允许的键值对，关于 [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
FilterHashtable 参数的文档也包含这些键值对。</span><span class="sxs-lookup"><span data-stu-id="ccea7-126">The accepted **key-value** pairs are shown in the following table and are included in the documentation for the [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable** parameter.</span></span>

<span data-ttu-id="ccea7-127">下表显示了键名称、数据类型以及数据值是否接受通配符。</span><span class="sxs-lookup"><span data-stu-id="ccea7-127">The following table displays the key names, data types, and whether wildcard characters are accepted for a data value.</span></span>

|    <span data-ttu-id="ccea7-128">项名</span><span class="sxs-lookup"><span data-stu-id="ccea7-128">Key name</span></span>    | <span data-ttu-id="ccea7-129">值数据类型</span><span class="sxs-lookup"><span data-stu-id="ccea7-129">Value data type</span></span> | <span data-ttu-id="ccea7-130">是否接受通配符？</span><span class="sxs-lookup"><span data-stu-id="ccea7-130">Accepts wildcard characters?</span></span> |
| -------------- | --------------- | ---------------------------- |
| <span data-ttu-id="ccea7-131">LogName</span><span class="sxs-lookup"><span data-stu-id="ccea7-131">LogName</span></span>        | `<String[]>`    | <span data-ttu-id="ccea7-132">是</span><span class="sxs-lookup"><span data-stu-id="ccea7-132">Yes</span></span>                          |
| <span data-ttu-id="ccea7-133">ProviderName</span><span class="sxs-lookup"><span data-stu-id="ccea7-133">ProviderName</span></span>   | `<String[]>`    | <span data-ttu-id="ccea7-134">是</span><span class="sxs-lookup"><span data-stu-id="ccea7-134">Yes</span></span>                          |
| <span data-ttu-id="ccea7-135">路径</span><span class="sxs-lookup"><span data-stu-id="ccea7-135">Path</span></span>           | `<String[]>`    | <span data-ttu-id="ccea7-136">否</span><span class="sxs-lookup"><span data-stu-id="ccea7-136">No</span></span>                           |
| <span data-ttu-id="ccea7-137">Keywords</span><span class="sxs-lookup"><span data-stu-id="ccea7-137">Keywords</span></span>       | `<Long[]>`      | <span data-ttu-id="ccea7-138">否</span><span class="sxs-lookup"><span data-stu-id="ccea7-138">No</span></span>                           |
| <span data-ttu-id="ccea7-139">ID</span><span class="sxs-lookup"><span data-stu-id="ccea7-139">ID</span></span>             | `<Int32[]>`     | <span data-ttu-id="ccea7-140">否</span><span class="sxs-lookup"><span data-stu-id="ccea7-140">No</span></span>                           |
| <span data-ttu-id="ccea7-141">级别</span><span class="sxs-lookup"><span data-stu-id="ccea7-141">Level</span></span>          | `<Int32[]>`     | <span data-ttu-id="ccea7-142">否</span><span class="sxs-lookup"><span data-stu-id="ccea7-142">No</span></span>                           |
| <span data-ttu-id="ccea7-143">StartTime</span><span class="sxs-lookup"><span data-stu-id="ccea7-143">StartTime</span></span>      | `<DateTime>`    | <span data-ttu-id="ccea7-144">否</span><span class="sxs-lookup"><span data-stu-id="ccea7-144">No</span></span>                           |
| <span data-ttu-id="ccea7-145">EndTime</span><span class="sxs-lookup"><span data-stu-id="ccea7-145">EndTime</span></span>        | `<DateTime>`    | <span data-ttu-id="ccea7-146">否</span><span class="sxs-lookup"><span data-stu-id="ccea7-146">No</span></span>                           |
| <span data-ttu-id="ccea7-147">UserID</span><span class="sxs-lookup"><span data-stu-id="ccea7-147">UserID</span></span>         | `<SID>`         | <span data-ttu-id="ccea7-148">否</span><span class="sxs-lookup"><span data-stu-id="ccea7-148">No</span></span>                           |
| <span data-ttu-id="ccea7-149">数据</span><span class="sxs-lookup"><span data-stu-id="ccea7-149">Data</span></span>           | `<String[]>`    | <span data-ttu-id="ccea7-150">否</span><span class="sxs-lookup"><span data-stu-id="ccea7-150">No</span></span>                           |
| `<named-data>` | `<String[]>`    | <span data-ttu-id="ccea7-151">否</span><span class="sxs-lookup"><span data-stu-id="ccea7-151">No</span></span>                           |

<span data-ttu-id="ccea7-152">`<named-data>` 键表示命名事件数据字段。</span><span class="sxs-lookup"><span data-stu-id="ccea7-152">The `<named-data>` key represents a named event data field.</span></span> <span data-ttu-id="ccea7-153">例如，Perflib 事件 1008 可以包含以下事件数据：</span><span class="sxs-lookup"><span data-stu-id="ccea7-153">For example, the Perflib event 1008 can contain the following event data:</span></span>

```xml
<EventData>
  <Data Name="Service">BITS</Data>
  <Data Name="Library">C:\Windows\System32\bitsperf.dll</Data>
  <Data Name="Win32Error">2</Data>
</EventData>
```

<span data-ttu-id="ccea7-154">可以使用以下命令查询这些事件：</span><span class="sxs-lookup"><span data-stu-id="ccea7-154">You can query for these events using the following command:</span></span>

```powershell
Get-WinEvent -FilterHashtable @{LogName='Application'; 'Service'='Bits'}
```

> [!NOTE]
> <span data-ttu-id="ccea7-155">PowerShell 6 中添加了查询 `<named-data>` 的功能。</span><span class="sxs-lookup"><span data-stu-id="ccea7-155">The ability to query for `<named-data>` was added in PowerShell 6.</span></span>

## <a name="building-a-query-with-a-hash-table"></a><span data-ttu-id="ccea7-156">使用哈希表生成查询</span><span class="sxs-lookup"><span data-stu-id="ccea7-156">Building a query with a hash table</span></span>

<span data-ttu-id="ccea7-157">若要验证结果并解决问题，它帮助生成一次包含一个键值对的哈希表。</span><span class="sxs-lookup"><span data-stu-id="ccea7-157">To verify results and troubleshoot problems, it helps to build the hash table one **key-value** pair at a time.</span></span> <span data-ttu-id="ccea7-158">查询从“Application”日志获取数据。</span><span class="sxs-lookup"><span data-stu-id="ccea7-158">The query gets data from the **Application** log.</span></span> <span data-ttu-id="ccea7-159">哈希表等效于 `Get-WinEvent –LogName Application`。</span><span class="sxs-lookup"><span data-stu-id="ccea7-159">The hash table is equivalent to `Get-WinEvent –LogName Application`.</span></span>

<span data-ttu-id="ccea7-160">首先创建 `Get-WinEvent` 查询。</span><span class="sxs-lookup"><span data-stu-id="ccea7-160">To begin, create the `Get-WinEvent` query.</span></span> <span data-ttu-id="ccea7-161">使用 FilterHashtable 参数的键值对，其中键为“LogName”，值为“Application”。   </span><span class="sxs-lookup"><span data-stu-id="ccea7-161">Use the **FilterHashtable** parameter's **key-value** pair with the key, **LogName**, and the value, **Application**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
}
```

<span data-ttu-id="ccea7-162">继续使用 ProviderName 键生成哈希表。</span><span class="sxs-lookup"><span data-stu-id="ccea7-162">Continue to build the hash table with the **ProviderName** key.</span></span> <span data-ttu-id="ccea7-163">ProviderName 是在“Windows 事件查看器”的“源”字段中显示的名称。  </span><span class="sxs-lookup"><span data-stu-id="ccea7-163">The **ProviderName** is the name that appears in the **Source** field in the **Windows Event Viewer**.</span></span> <span data-ttu-id="ccea7-164">例如，下面的屏幕截图中的“.NET 运行时”：</span><span class="sxs-lookup"><span data-stu-id="ccea7-164">For example, **.NET Runtime** in the following screenshot:</span></span>

![“Windows 事件查看器”源的图片](./media/creating-get-winEvent-queries-with-filterhashtable/providername.png)

<span data-ttu-id="ccea7-166">更新哈希表，并包含键为 ProviderName、值为“.NET 运行时”的键值对  。</span><span class="sxs-lookup"><span data-stu-id="ccea7-166">Update the hash table and include the **key-value** pair with the key, **ProviderName**, and the value, **.NET Runtime**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
}
```

<span data-ttu-id="ccea7-167">若查询需要从存档的事件日志获取数据，请使用 Path 键。</span><span class="sxs-lookup"><span data-stu-id="ccea7-167">If your query needs to get data from archived event logs, use the **Path** key.</span></span> <span data-ttu-id="ccea7-168">Path 值指定日志文件的完整路径。</span><span class="sxs-lookup"><span data-stu-id="ccea7-168">The **Path** value specifies the full path to the log file.</span></span> <span data-ttu-id="ccea7-169">有关详细信息，请参阅“脚本专家”博客文章[使用 PowerShell 分析保存的事件日志以查找错误](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors)。</span><span class="sxs-lookup"><span data-stu-id="ccea7-169">For more information, see the **Scripting Guy** blog post, [Use PowerShell to Parse Saved Event Logs for Errors](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors).</span></span>

## <a name="using-enumerated-values-in-a-hash-table"></a><span data-ttu-id="ccea7-170">在哈希表中使用枚举值</span><span class="sxs-lookup"><span data-stu-id="ccea7-170">Using enumerated values in a hash table</span></span>

<span data-ttu-id="ccea7-171">Keywords 是哈希表中的下一个键。</span><span class="sxs-lookup"><span data-stu-id="ccea7-171">**Keywords** is the next key in the hash table.</span></span> <span data-ttu-id="ccea7-172">Keywords 数据类型是一个包含大量数字的 `[long]` 值类型的数组。</span><span class="sxs-lookup"><span data-stu-id="ccea7-172">The **Keywords** data type is an array of the `[long]` value type that holds a large number.</span></span> <span data-ttu-id="ccea7-173">使用下面的命令查找 `[long]` 的最大值：</span><span class="sxs-lookup"><span data-stu-id="ccea7-173">Use the following command to find the maximum value of `[long]`:</span></span>

```powershell
[long]::MaxValue
```

```Output
9223372036854775807
```

<span data-ttu-id="ccea7-174">对于 Keywords 键，PowerShell 使用数字，而不是字符串（如 Security）。 </span><span class="sxs-lookup"><span data-stu-id="ccea7-174">For the **Keywords** key, PowerShell uses a number, not a string such as **Security**.</span></span> <span data-ttu-id="ccea7-175">“Windows 事件查看器”将 Keywords 显示为字符串，但它们是枚举值。 </span><span class="sxs-lookup"><span data-stu-id="ccea7-175">**Windows Event Viewer** displays the **Keywords** as strings, but they are enumerated values.</span></span> <span data-ttu-id="ccea7-176">在哈希表中使用包含字符串值的 Keywords 键时，将显示错误消息。</span><span class="sxs-lookup"><span data-stu-id="ccea7-176">In the hash table, if you use the **Keywords** key with a string value, an error message is displayed.</span></span>

<span data-ttu-id="ccea7-177">打开“Windows 事件查看器”，从“操作”窗格单击“筛选当前日志”。  </span><span class="sxs-lookup"><span data-stu-id="ccea7-177">Open the **Windows Event Viewer** and from the **Actions** pane, click on **Filter current log**.</span></span>
<span data-ttu-id="ccea7-178">“关键字”下拉菜单将显示可用的关键字，如下面的屏幕截图所示：</span><span class="sxs-lookup"><span data-stu-id="ccea7-178">The **Keywords** drop-down menu displays the available keywords, as shown in the following screenshot:</span></span>

![“Windows 事件查看器”关键字的图片](./media/creating-get-winEvent-queries-with-filterhashtable/keywords.png)

<span data-ttu-id="ccea7-180">使用下面的命令显示 `StandardEventKeywords` 属性名称。</span><span class="sxs-lookup"><span data-stu-id="ccea7-180">Use the following command to display the `StandardEventKeywords` property names.</span></span>

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventKeywords] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventKeywords
Name             MemberType Definition
—-             ———- ———-
AuditFailure     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
AuditSuccess     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint2 Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
EventLogClassic  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
None             Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
ResponseTime     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
Sqm              Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiContext       Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiDiagnostic    Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
```

<span data-ttu-id="ccea7-181">枚举值将记录在 .NET Framework 中。</span><span class="sxs-lookup"><span data-stu-id="ccea7-181">The enumerated values are documented in the **.NET Framework**.</span></span> <span data-ttu-id="ccea7-182">有关详细信息，请参阅 [StandardEventKeywords 枚举](/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2)。</span><span class="sxs-lookup"><span data-stu-id="ccea7-182">For more information, see [StandardEventKeywords Enumeration](/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2).</span></span>

<span data-ttu-id="ccea7-183">Keywords 名称和枚举值如下所示：</span><span class="sxs-lookup"><span data-stu-id="ccea7-183">The **Keywords** names and enumerated values are as follows:</span></span>

| <span data-ttu-id="ccea7-184">名称</span><span class="sxs-lookup"><span data-stu-id="ccea7-184">Name</span></span>             |  <span data-ttu-id="ccea7-185">值</span><span class="sxs-lookup"><span data-stu-id="ccea7-185">Value</span></span>            |
| ---------------- | ------------------|
| <span data-ttu-id="ccea7-186">AuditFailure</span><span class="sxs-lookup"><span data-stu-id="ccea7-186">AuditFailure</span></span>     | <span data-ttu-id="ccea7-187">4503599627370496</span><span class="sxs-lookup"><span data-stu-id="ccea7-187">4503599627370496</span></span>  |
| <span data-ttu-id="ccea7-188">AuditSuccess</span><span class="sxs-lookup"><span data-stu-id="ccea7-188">AuditSuccess</span></span>     | <span data-ttu-id="ccea7-189">9007199254740992</span><span class="sxs-lookup"><span data-stu-id="ccea7-189">9007199254740992</span></span>  |
| <span data-ttu-id="ccea7-190">CorrelationHint2</span><span class="sxs-lookup"><span data-stu-id="ccea7-190">CorrelationHint2</span></span> | <span data-ttu-id="ccea7-191">18014398509481984</span><span class="sxs-lookup"><span data-stu-id="ccea7-191">18014398509481984</span></span> |
| <span data-ttu-id="ccea7-192">EventLogClassic</span><span class="sxs-lookup"><span data-stu-id="ccea7-192">EventLogClassic</span></span>  | <span data-ttu-id="ccea7-193">36028797018963968</span><span class="sxs-lookup"><span data-stu-id="ccea7-193">36028797018963968</span></span> |
| <span data-ttu-id="ccea7-194">Sqm</span><span class="sxs-lookup"><span data-stu-id="ccea7-194">Sqm</span></span>              | <span data-ttu-id="ccea7-195">2251799813685248</span><span class="sxs-lookup"><span data-stu-id="ccea7-195">2251799813685248</span></span>  |
| <span data-ttu-id="ccea7-196">WdiDiagnostic</span><span class="sxs-lookup"><span data-stu-id="ccea7-196">WdiDiagnostic</span></span>    | <span data-ttu-id="ccea7-197">1125899906842624</span><span class="sxs-lookup"><span data-stu-id="ccea7-197">1125899906842624</span></span>  |
| <span data-ttu-id="ccea7-198">WdiContext</span><span class="sxs-lookup"><span data-stu-id="ccea7-198">WdiContext</span></span>       | <span data-ttu-id="ccea7-199">562949953421312</span><span class="sxs-lookup"><span data-stu-id="ccea7-199">562949953421312</span></span>   |
| <span data-ttu-id="ccea7-200">ResponseTime</span><span class="sxs-lookup"><span data-stu-id="ccea7-200">ResponseTime</span></span>     | <span data-ttu-id="ccea7-201">281474976710656</span><span class="sxs-lookup"><span data-stu-id="ccea7-201">281474976710656</span></span>   |
| <span data-ttu-id="ccea7-202">无</span><span class="sxs-lookup"><span data-stu-id="ccea7-202">None</span></span>             | <span data-ttu-id="ccea7-203">0</span><span class="sxs-lookup"><span data-stu-id="ccea7-203">0</span></span>                 |

<span data-ttu-id="ccea7-204">更新哈希表，并包含键为 Keywords 且 EventLogClassic 枚举值为 36028797018963968 的键值对。   </span><span class="sxs-lookup"><span data-stu-id="ccea7-204">Update the hash table and include the **key-value** pair with the key, **Keywords**, and the **EventLogClassic** enumeration value, **36028797018963968**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
}
```

### <a name="keywords-static-property-value-optional"></a><span data-ttu-id="ccea7-205">Keywords 静态属性值（可选）</span><span class="sxs-lookup"><span data-stu-id="ccea7-205">Keywords static property value (optional)</span></span>

<span data-ttu-id="ccea7-206">枚举 Keywords 键，但可以在哈希表查询中使用静态属性名称。</span><span class="sxs-lookup"><span data-stu-id="ccea7-206">The **Keywords** key is enumerated, but you can use a static property name in the hash table query.</span></span>
<span data-ttu-id="ccea7-207">必须使用 Value__ 属性将属性名称转换为值，而非使用返回值。</span><span class="sxs-lookup"><span data-stu-id="ccea7-207">Rather than using the returned string, the property name must be converted to a value with the **Value__** property.</span></span>

<span data-ttu-id="ccea7-208">例如，下面的脚本就使用了 Value__ 属性。</span><span class="sxs-lookup"><span data-stu-id="ccea7-208">For example, the following script uses the **Value__** property.</span></span>

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventKeywords]::EventLogClassic
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=$C.Value__
}
```

## <a name="filtering-by-event-id"></a><span data-ttu-id="ccea7-209">按事件 ID 筛选</span><span class="sxs-lookup"><span data-stu-id="ccea7-209">Filtering by Event Id</span></span>

<span data-ttu-id="ccea7-210">若要获取更多特定数据，请按事件 ID 筛选查询的结果。哈希表将“事件 ID”引用为键 ID，其值为特定的“事件 ID”。  “Windows 事件查看器”将显示“事件 ID”。 此示例使用“事件 ID 1023”。</span><span class="sxs-lookup"><span data-stu-id="ccea7-210">To get more specific data, the query's results are filtered by **Event Id**. The **Event Id** is referenced in the hash table as the key **ID** and the value is a specific **Event Id**. The **Windows Event Viewer** displays the **Event Id**. This example uses **Event Id 1023**.</span></span>

<span data-ttu-id="ccea7-211">更新哈希表，并包含键为 ID 且值为 1023 的键值对。  </span><span class="sxs-lookup"><span data-stu-id="ccea7-211">Update the hash table and include the **key-value** pair with the key, **ID** and the value, **1023**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
}
```

## <a name="filtering-by-level"></a><span data-ttu-id="ccea7-212">按级别筛选</span><span class="sxs-lookup"><span data-stu-id="ccea7-212">Filtering by Level</span></span>

<span data-ttu-id="ccea7-213">若要进一步优化结果并仅包含属于错误的事件，请使用 Level 键。</span><span class="sxs-lookup"><span data-stu-id="ccea7-213">To further refine the results and include only events that are errors, use the **Level** key.</span></span>
<span data-ttu-id="ccea7-214">“Windows 事件查看器”将 Level 显示为字符串值，但它们是枚举值。 </span><span class="sxs-lookup"><span data-stu-id="ccea7-214">**Windows Event Viewer** displays the **Level** as string values, but they are enumerated values.</span></span> <span data-ttu-id="ccea7-215">在哈希表中使用包含字符串值的 Level 键时，将显示错误消息。</span><span class="sxs-lookup"><span data-stu-id="ccea7-215">In the hash table, if you use the **Level** key with a string value, an error message is displayed.</span></span>

<span data-ttu-id="ccea7-216">Level 包含诸如“错误”、“警告”或“信息性”等值。   </span><span class="sxs-lookup"><span data-stu-id="ccea7-216">**Level** has values such as **Error**, **Warning**, or **Informational**.</span></span> <span data-ttu-id="ccea7-217">使用下面的命令显示 `StandardEventLevel` 属性名称。</span><span class="sxs-lookup"><span data-stu-id="ccea7-217">Use the following command to display the `StandardEventLevel` property names.</span></span>

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventLevel] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventLevel

Name          MemberType Definition
----          ---------- ----------
Critical      Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Critical {get;}
Error         Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Error {get;}
Informational Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Informational {get;}
LogAlways     Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel LogAlways {get;}
Verbose       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Verbose {get;}
Warning       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Warning {get;}
```

<span data-ttu-id="ccea7-218">枚举值将记录在 .NET Framework 中。</span><span class="sxs-lookup"><span data-stu-id="ccea7-218">The enumerated values are documented in the **.NET Framework**.</span></span> <span data-ttu-id="ccea7-219">有关详细信息，请参阅 [StandardEventLevel 枚举](/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2)。</span><span class="sxs-lookup"><span data-stu-id="ccea7-219">For more information, see [StandardEventLevel Enumeration](/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2).</span></span>

<span data-ttu-id="ccea7-220">Level 键的名称和枚举值如下所示：</span><span class="sxs-lookup"><span data-stu-id="ccea7-220">The **Level** key's names and enumerated values are as follows:</span></span>

| <span data-ttu-id="ccea7-221">名称</span><span class="sxs-lookup"><span data-stu-id="ccea7-221">Name</span></span>           | <span data-ttu-id="ccea7-222">值</span><span class="sxs-lookup"><span data-stu-id="ccea7-222">Value</span></span> |
| -------------- | ----- |
| <span data-ttu-id="ccea7-223">“详细”</span><span class="sxs-lookup"><span data-stu-id="ccea7-223">Verbose</span></span>        |   <span data-ttu-id="ccea7-224">5</span><span class="sxs-lookup"><span data-stu-id="ccea7-224">5</span></span>   |
| <span data-ttu-id="ccea7-225">信息</span><span class="sxs-lookup"><span data-stu-id="ccea7-225">Informational</span></span>  |   <span data-ttu-id="ccea7-226">4</span><span class="sxs-lookup"><span data-stu-id="ccea7-226">4</span></span>   |
| <span data-ttu-id="ccea7-227">警告</span><span class="sxs-lookup"><span data-stu-id="ccea7-227">Warning</span></span>        |   <span data-ttu-id="ccea7-228">3</span><span class="sxs-lookup"><span data-stu-id="ccea7-228">3</span></span>   |
| <span data-ttu-id="ccea7-229">错误</span><span class="sxs-lookup"><span data-stu-id="ccea7-229">Error</span></span>          |   <span data-ttu-id="ccea7-230">2</span><span class="sxs-lookup"><span data-stu-id="ccea7-230">2</span></span>   |
| <span data-ttu-id="ccea7-231">严重</span><span class="sxs-lookup"><span data-stu-id="ccea7-231">Critical</span></span>       |   <span data-ttu-id="ccea7-232">1</span><span class="sxs-lookup"><span data-stu-id="ccea7-232">1</span></span>   |
| <span data-ttu-id="ccea7-233">LogAlways</span><span class="sxs-lookup"><span data-stu-id="ccea7-233">LogAlways</span></span>      |   <span data-ttu-id="ccea7-234">0</span><span class="sxs-lookup"><span data-stu-id="ccea7-234">0</span></span>   |

<span data-ttu-id="ccea7-235">完成的查询的哈希表包括 Level 键和值 2。 </span><span class="sxs-lookup"><span data-stu-id="ccea7-235">The hash table for the completed query includes the key, **Level**, and the value, **2**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=2
}
```

### <a name="level-static-property-in-enumeration-optional"></a><span data-ttu-id="ccea7-236">枚举中的 Level 静态属性（可选）</span><span class="sxs-lookup"><span data-stu-id="ccea7-236">Level static property in enumeration (optional)</span></span>

<span data-ttu-id="ccea7-237">枚举 Level 键，但可以在哈希表查询中使用静态属性名称。</span><span class="sxs-lookup"><span data-stu-id="ccea7-237">The **Level** key is enumerated, but you can use a static property name in the hash table query.</span></span>
<span data-ttu-id="ccea7-238">必须使用 Value__ 属性将属性名称转换为值，而非使用返回值。</span><span class="sxs-lookup"><span data-stu-id="ccea7-238">Rather than using the returned string, the property name must be converted to a value with the **Value__** property.</span></span>

<span data-ttu-id="ccea7-239">例如，下面的脚本就使用了 Value__ 属性。</span><span class="sxs-lookup"><span data-stu-id="ccea7-239">For example, the following script uses the **Value__** property.</span></span>

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventLevel]::Informational
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=$C.Value__
}
```
