---
title: 关于 PSCustomObject 的各项须知内容
description: PSCustomObject 是创建结构化数据的一种简单方法。
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: fbc8b5b6d2cfafaa75fa820f420762a1804074ac
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149490"
---
# <a name="everything-you-wanted-to-know-about-pscustomobject"></a><span data-ttu-id="b009c-103">关于 PSCustomObject 的各项须知内容</span><span class="sxs-lookup"><span data-stu-id="b009c-103">Everything you wanted to know about PSCustomObject</span></span>

<span data-ttu-id="b009c-104">`PSCustomObject` 是可添加到 PowerShell 工具包中的绝佳工具。</span><span class="sxs-lookup"><span data-stu-id="b009c-104">`PSCustomObject`s are a great tool to add into your PowerShell tool belt.</span></span> <span data-ttu-id="b009c-105">让我们从基本功能开始，然后深入了解更高级的功能。</span><span class="sxs-lookup"><span data-stu-id="b009c-105">Let's start with the basics and work our way into the more advanced features.</span></span> <span data-ttu-id="b009c-106">使用 `PSCustomObject` 背后的理念是，使用一种简单的方法来创建结构化数据。</span><span class="sxs-lookup"><span data-stu-id="b009c-106">The idea behind using a `PSCustomObject` is to have a simple way to create structured data.</span></span> <span data-ttu-id="b009c-107">查看第一个示例，可以更好地了解其含义。</span><span class="sxs-lookup"><span data-stu-id="b009c-107">Take a look at the first example and you'll have a better idea of what that means.</span></span>

> [!NOTE]
> <span data-ttu-id="b009c-108">本文的[原始版本][]发布在 [@KevinMarquette][] 撰写的博客上。</span><span class="sxs-lookup"><span data-stu-id="b009c-108">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="b009c-109">PowerShell 团队感谢 Kevin 与我们分享这篇文章。</span><span class="sxs-lookup"><span data-stu-id="b009c-109">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="b009c-110">请前往 [PowerShellExplained.com][] 访问他的博客。</span><span class="sxs-lookup"><span data-stu-id="b009c-110">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="creating-a-pscustomobject"></a><span data-ttu-id="b009c-111">创建 PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="b009c-111">Creating a PSCustomObject</span></span>

<span data-ttu-id="b009c-112">我喜欢在 PowerShell 中使用 `[PSCustomObject]`。</span><span class="sxs-lookup"><span data-stu-id="b009c-112">I love using `[PSCustomObject]` in PowerShell.</span></span> <span data-ttu-id="b009c-113">创建可用对象变得前所未有的容易。</span><span class="sxs-lookup"><span data-stu-id="b009c-113">Creating a usable object has never been easier.</span></span>
<span data-ttu-id="b009c-114">因此，我将跳过所有其他创建对象的方法，但需要注意的是，大多数示例都采用 PowerShell 3.0 和更高版本。</span><span class="sxs-lookup"><span data-stu-id="b009c-114">Because of that, I'm going to skip over all the other ways you can create an object but I need to mention that most of these examples are PowerShell v3.0 and newer.</span></span>

```powershell
$myObject = [PSCustomObject]@{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}
```

<span data-ttu-id="b009c-115">这种方法非常适合我，因为我几乎对所有事项都使用哈希表。</span><span class="sxs-lookup"><span data-stu-id="b009c-115">This method works well for me because I use hashtables for just about everything.</span></span> <span data-ttu-id="b009c-116">但有时，我更希望 PowerShell 将哈希表视为一个对象。</span><span class="sxs-lookup"><span data-stu-id="b009c-116">But there are times when I would like PowerShell to treat hashtables more like an object.</span></span> <span data-ttu-id="b009c-117">当你想要使用 `Format-Table` 或 `Export-CSV` 并且意识到哈希表只是键/值对的集合时，你首先会注意到这种差异。</span><span class="sxs-lookup"><span data-stu-id="b009c-117">The first place you notice the difference is when you want to use `Format-Table` or `Export-CSV` and you realize that a hashtable is just a collection of key/value pairs.</span></span>

<span data-ttu-id="b009c-118">然后，你可以像访问普通对象一样访问和使用这些值。</span><span class="sxs-lookup"><span data-stu-id="b009c-118">You can then access and use the values like you would a normal object.</span></span>

```powershell
$myObject.Name
```

### <a name="converting-a-hashtable"></a><span data-ttu-id="b009c-119">转换哈希表</span><span class="sxs-lookup"><span data-stu-id="b009c-119">Converting a hashtable</span></span>

<span data-ttu-id="b009c-120">在谈到这个主题时，你是否知道你可以这样做：</span><span class="sxs-lookup"><span data-stu-id="b009c-120">While I am on the topic, did you know you could do this:</span></span>

```powershell
$myHashtable = @{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}
$myObject = [pscustomobject]$myHashtable
```

<span data-ttu-id="b009c-121">我确实想从头开始创建对象，但有时你必须先使用哈希表。</span><span class="sxs-lookup"><span data-stu-id="b009c-121">I do prefer to create the object from the start but there are times you have to work with a hashtable first.</span></span> <span data-ttu-id="b009c-122">此示例能工作的原因是，构造函数为对象属性采用了哈希表。</span><span class="sxs-lookup"><span data-stu-id="b009c-122">This example works because the constructor takes a hashtable for the object properties.</span></span> <span data-ttu-id="b009c-123">一个重要的注意事项是，虽然此方法有效，但并不是完全等价的。</span><span class="sxs-lookup"><span data-stu-id="b009c-123">One important note is that while this method works, it isn't an exact equivalent.</span></span> <span data-ttu-id="b009c-124">最大的区别在于属性的顺序不会被保留。</span><span class="sxs-lookup"><span data-stu-id="b009c-124">The biggest difference is that the order of the properties isn't preserved.</span></span>

### <a name="legacy-approach"></a><span data-ttu-id="b009c-125">传统方法</span><span class="sxs-lookup"><span data-stu-id="b009c-125">Legacy approach</span></span>

<span data-ttu-id="b009c-126">你可能见过人们使用 `New-Object` 来创建自定义对象。</span><span class="sxs-lookup"><span data-stu-id="b009c-126">You may have seen people use `New-Object` to create custom objects.</span></span>

```powershell
$myHashtable = @{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}

$myObject = New-Object -TypeName PSObject -Property $myHashtable
```

<span data-ttu-id="b009c-127">这种方式比较慢，但可能是 PowerShell 早期版本的最佳选择。</span><span class="sxs-lookup"><span data-stu-id="b009c-127">This way is quite a bit slower but it may be your best option on early versions of PowerShell.</span></span>

### <a name="saving-to-a-file"></a><span data-ttu-id="b009c-128">保存到文件</span><span class="sxs-lookup"><span data-stu-id="b009c-128">Saving to a file</span></span>

<span data-ttu-id="b009c-129">我发现将哈希表保存到文件的最佳方法是将其保存为 JSON。</span><span class="sxs-lookup"><span data-stu-id="b009c-129">I find the best way to save a hashtable to a file is to save it as JSON.</span></span> <span data-ttu-id="b009c-130">可以将其导入回 `[PSCusomObject]`</span><span class="sxs-lookup"><span data-stu-id="b009c-130">You can import it back into a `[PSCusomObject]`</span></span>

```powershell
$myObject | ConvertTo-Json -depth 1- | Set-Content -Path $Path
$myObject = Get-Content -Path $Path | ConvertFrom-Json
```

<span data-ttu-id="b009c-131">我在[读取和写入文件的多种方式][]一文中介绍了将对象保存到文件的更多方法。</span><span class="sxs-lookup"><span data-stu-id="b009c-131">I cover more ways to save objects to a file in my article on [The many ways to read and write to files][].</span></span>

## <a name="working-with-properties"></a><span data-ttu-id="b009c-132">使用属性</span><span class="sxs-lookup"><span data-stu-id="b009c-132">Working with properties</span></span>

### <a name="adding-properties"></a><span data-ttu-id="b009c-133">添加属性</span><span class="sxs-lookup"><span data-stu-id="b009c-133">Adding properties</span></span>

<span data-ttu-id="b009c-134">你仍可以使用 `Add-Member` 将新属性添加到 `PSCustomObject`。</span><span class="sxs-lookup"><span data-stu-id="b009c-134">You can still add new properties to your `PSCustomObject` with `Add-Member`.</span></span>

```powershell
$myObject | Add-Member -MemberType NoteProperty -Name `ID` -Value 'KevinMarquette'

$myObject.ID
```

### <a name="remove-properties"></a><span data-ttu-id="b009c-135">删除属性</span><span class="sxs-lookup"><span data-stu-id="b009c-135">Remove properties</span></span>

<span data-ttu-id="b009c-136">你还可以从对象中删除属性。</span><span class="sxs-lookup"><span data-stu-id="b009c-136">You can also remove properties off of an object.</span></span>

```powershell
$myObject.psobject.properties.remove('ID')
```

<span data-ttu-id="b009c-137">`psobject` 是隐藏属性，它允许你访问基对象元数据。</span><span class="sxs-lookup"><span data-stu-id="b009c-137">The `psobject` is a hidden property that gives you access to base object metadata.</span></span>

### <a name="enumerating-property-names"></a><span data-ttu-id="b009c-138">枚举属性名称</span><span class="sxs-lookup"><span data-stu-id="b009c-138">Enumerating property names</span></span>

<span data-ttu-id="b009c-139">有时需要对象上所有属性名称的列表。</span><span class="sxs-lookup"><span data-stu-id="b009c-139">Sometimes you need a list of all the property names on an object.</span></span>

```powershell
$myObject | Get-Member -MemberType NoteProperty | Select -ExpandProperty Name
```

<span data-ttu-id="b009c-140">我们也可以从 `psobject` 属性获取此列表。</span><span class="sxs-lookup"><span data-stu-id="b009c-140">We can get this same list off of the `psobject` property too.</span></span>

```powershell
$myobject.psobject.properties.name
```

### <a name="dynamically-accessing-properties"></a><span data-ttu-id="b009c-141">动态访问属性</span><span class="sxs-lookup"><span data-stu-id="b009c-141">Dynamically accessing properties</span></span>

<span data-ttu-id="b009c-142">我曾提到过，你可以直接访问属性值。</span><span class="sxs-lookup"><span data-stu-id="b009c-142">I already mentioned that you can access property values directly.</span></span>

```powershell
$myObject.Name
```

<span data-ttu-id="b009c-143">你可以使用字符串作为属性名称，它仍可正常工作。</span><span class="sxs-lookup"><span data-stu-id="b009c-143">You can use a string for the property name and it will still work.</span></span>

```powershell
$myObject.'Name'
```

<span data-ttu-id="b009c-144">我们可以再执行一步，并使用变量作为属性名称。</span><span class="sxs-lookup"><span data-stu-id="b009c-144">We can take this one more step and use a variable for the property name.</span></span>

```powershell
$property = 'Name'
$myObject.$property
```

<span data-ttu-id="b009c-145">我知道这看起来很奇怪，但它很有效。</span><span class="sxs-lookup"><span data-stu-id="b009c-145">I know that looks strange, but it works.</span></span>

### <a name="convert-pscustomboject-into-a-hashtable"></a><span data-ttu-id="b009c-146">将 pscustomboject 转换为哈希表</span><span class="sxs-lookup"><span data-stu-id="b009c-146">Convert pscustomboject into a hashtable</span></span>

<span data-ttu-id="b009c-147">要从上一节继续操作，可以动态地遍历属性并从中创建一个哈希表。</span><span class="sxs-lookup"><span data-stu-id="b009c-147">To continue on from the last section, you can dynamically walk the properties and create a hashtable from them.</span></span>

```powershell
$hashtable = @{}
foreach( $property in $myobject.psobject.properties.name )
{
    $hashtable[$property] = $myObject.$property
}
```

### <a name="testing-for-properties"></a><span data-ttu-id="b009c-148">测试属性</span><span class="sxs-lookup"><span data-stu-id="b009c-148">Testing for properties</span></span>

<span data-ttu-id="b009c-149">如果需要知道属性是否存在，只需检查该属性是否有值。</span><span class="sxs-lookup"><span data-stu-id="b009c-149">If you need to know if a property exists, you could just check for that property to have a value.</span></span>

```powershell
if( $null -ne $myObject.ID )
```

<span data-ttu-id="b009c-150">但是，如果该值可以为 `$null`，并且仍需要检查该值，则可以检查 `psobject.properties` 是否具有该值。</span><span class="sxs-lookup"><span data-stu-id="b009c-150">But if the value could be `$null` and you still need to check for it, you can check the `psobject.properties` for it.</span></span>

```powershell
if( $myobject.psobject.properties.match('ID') )
```

## <a name="adding-object-methods"></a><span data-ttu-id="b009c-151">添加对象方法</span><span class="sxs-lookup"><span data-stu-id="b009c-151">Adding object methods</span></span>

<span data-ttu-id="b009c-152">如果需要将脚本方法添加到对象，则可以使用 `Add-Member` 和 `ScriptBlock` 执行此操作。</span><span class="sxs-lookup"><span data-stu-id="b009c-152">If you need to add a script method to an object, you can do it with `Add-Member` and a `ScriptBlock`.</span></span> <span data-ttu-id="b009c-153">必须使用 `this` 自动变量引用当前对象。</span><span class="sxs-lookup"><span data-stu-id="b009c-153">You have to use the `this` automatic variable reference the current object.</span></span> <span data-ttu-id="b009c-154">下面是将对象转换为哈希表的 `scriptblock`。</span><span class="sxs-lookup"><span data-stu-id="b009c-154">Here is a `scriptblock` to turn an object into a hashtable.</span></span> <span data-ttu-id="b009c-155">（上一个示例中的相同代码）</span><span class="sxs-lookup"><span data-stu-id="b009c-155">(same code form the last example)</span></span>

```powershell
$ScriptBlock = {
    $hashtable = @{}
    foreach( $property in $this.psobject.properties.name )
    {
        $hashtable[$property] = $this.$property
    }
    return $hashtable
}
```

<span data-ttu-id="b009c-156">然后，将其作为脚本属性添加到对象。</span><span class="sxs-lookup"><span data-stu-id="b009c-156">Then we add it to our object as a script property.</span></span>

```powershell
$memberParam = @{
    MemberType = "ScriptMethod"
    InputObject = $myobject
    Name = "ToHashtable"
    Value = $scriptBlock
}
Add-Member @memberParam
```

<span data-ttu-id="b009c-157">接下来，我们可以调用函数，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b009c-157">Then we can call our function like this:</span></span>

```powershell
$myObject.ToHashtable()
```

### <a name="objects-vs-value-types"></a><span data-ttu-id="b009c-158">对象与值类型</span><span class="sxs-lookup"><span data-stu-id="b009c-158">Objects vs Value types</span></span>

<span data-ttu-id="b009c-159">对象和值类型不会以相同的方式处理变量赋值。</span><span class="sxs-lookup"><span data-stu-id="b009c-159">Objects and value types don't handle variable assignments the same way.</span></span> <span data-ttu-id="b009c-160">如果互相分配值类型，则只有值会复制到新变量。</span><span class="sxs-lookup"><span data-stu-id="b009c-160">If you assign value types to each other, only the value get copied to the new variable.</span></span>

```powershell
$first = 1
$second = $first
$second = 2
```

<span data-ttu-id="b009c-161">在这种情况下，`$first` 为 1，`$second` 为 2。</span><span class="sxs-lookup"><span data-stu-id="b009c-161">In this case, `$first` is 1 and `$second` is 2.</span></span>

<span data-ttu-id="b009c-162">对象变量具有对实际对象的引用。</span><span class="sxs-lookup"><span data-stu-id="b009c-162">Object variables hold a reference to the actual object.</span></span> <span data-ttu-id="b009c-163">将一个对象分配给新变量时，它们仍引用相同的对象。</span><span class="sxs-lookup"><span data-stu-id="b009c-163">When you assign one object to a new variable, they still reference the same object.</span></span>

```powershell
$third = [PSCustomObject]@{Key=3}
$fourth = $third
$fourth.Key = 4
```

<span data-ttu-id="b009c-164">由于 `$third` 和 `$fourth` 引用对象的同一实例，`$third.key` 和 `$fourth.Key` 均为 4。</span><span class="sxs-lookup"><span data-stu-id="b009c-164">Because `$third` and `$fourth` reference the same instance of an object, both `$third.key` and `$fourth.Key` are 4.</span></span>

### <a name="psobjectcopy"></a><span data-ttu-id="b009c-165">psobject.copy()</span><span class="sxs-lookup"><span data-stu-id="b009c-165">psobject.copy()</span></span>

<span data-ttu-id="b009c-166">如果需要对象的真正副本，可以对其进行克隆。</span><span class="sxs-lookup"><span data-stu-id="b009c-166">If you need a true copy of an object, you can clone it.</span></span>

```powershell
$third = [PSCustomObject]@{Key=3}
$fourth = $third.psobject.copy()
$fourth.Key = 4
```

<span data-ttu-id="b009c-167">通过克隆可创建对象的卷影副本。</span><span class="sxs-lookup"><span data-stu-id="b009c-167">Clone creates a shallow copy of the object.</span></span> <span data-ttu-id="b009c-168">它们现在具有不同的实例，在本示例中，`$third.key` 为 3，`$fourth.Key` 为 4。</span><span class="sxs-lookup"><span data-stu-id="b009c-168">They have different instances now and `$third.key` is 3 and `$fourth.Key` is 4 in this example.</span></span>

<span data-ttu-id="b009c-169">由于嵌套了对象，我将其称为卷影副本。</span><span class="sxs-lookup"><span data-stu-id="b009c-169">I call this a shallow copy because if you have nested objects.</span></span> <span data-ttu-id="b009c-170">（其中，属性包含其他对象）。</span><span class="sxs-lookup"><span data-stu-id="b009c-170">(where the properties contain other objects).</span></span> <span data-ttu-id="b009c-171">仅复制顶级值。</span><span class="sxs-lookup"><span data-stu-id="b009c-171">Only the top-level values are copied.</span></span> <span data-ttu-id="b009c-172">子对象将相互引用。</span><span class="sxs-lookup"><span data-stu-id="b009c-172">The child objects will reference each other.</span></span>

### <a name="pstypename-for-custom-object-types"></a><span data-ttu-id="b009c-173">自定义对象类型的 PSTypeName</span><span class="sxs-lookup"><span data-stu-id="b009c-173">PSTypeName for custom object types</span></span>

<span data-ttu-id="b009c-174">既然我们有了一个对象，我们还可以用它做一些可能不那么明显的事情。</span><span class="sxs-lookup"><span data-stu-id="b009c-174">Now that we have an object, there are a few more things we can do with it that may not be nearly as obvious.</span></span> <span data-ttu-id="b009c-175">要做的第一件事就是为它指定 `PSTypeName`。</span><span class="sxs-lookup"><span data-stu-id="b009c-175">First thing we need to do is give it a `PSTypeName`.</span></span> <span data-ttu-id="b009c-176">以下是我看到的最常用的方法：</span><span class="sxs-lookup"><span data-stu-id="b009c-176">This is the most common way I see people do it:</span></span>

```powershell
$myObject.PSObject.TypeNames.Insert(0,"My.Object")
```

<span data-ttu-id="b009c-177">我最近从 [/u/markekraus 的这篇文章][]中发现了执行此操作的另一种方法。</span><span class="sxs-lookup"><span data-stu-id="b009c-177">I recently discovered another way to do this from this [post by /u/markekraus][].</span></span> <span data-ttu-id="b009c-178">我对 [Adam Bertram][] 和 [Mike Shepard][] 的观点做了更深入的研究，阅读了更多关于此内联定义方法的文章。</span><span class="sxs-lookup"><span data-stu-id="b009c-178">I did a little digging and more posts about the idea from [Adam Bertram][] and [Mike Shepard][] where they talk about this approach that allows you to define it inline.</span></span>

```powershell
$myObject = [PSCustomObject]@{
    PSTypeName = 'My.Object'
    Name       = 'Kevin'
    Language   = 'PowerShell'
    State      = 'Texas'
}
```

<span data-ttu-id="b009c-179">这刚好适用于这种语言，我很喜欢。</span><span class="sxs-lookup"><span data-stu-id="b009c-179">I love how nicely this just fits into the language.</span></span> <span data-ttu-id="b009c-180">现在，我们有了一个具有正确类型名称的对象，接下来可以执行更多操作。</span><span class="sxs-lookup"><span data-stu-id="b009c-180">Now that we have an object with a proper type name, we can do some more things.</span></span>

## <a name="using-defaultpropertyset-the-long-way"></a><span data-ttu-id="b009c-181">使用 DefaultPropertySet（长期）</span><span class="sxs-lookup"><span data-stu-id="b009c-181">Using DefaultPropertySet (the long way)</span></span>

<span data-ttu-id="b009c-182">PowerShell 为我们决定默认情况下显示哪些属性。</span><span class="sxs-lookup"><span data-stu-id="b009c-182">PowerShell decides for us what properties to display by default.</span></span> <span data-ttu-id="b009c-183">很多本机命令都有一个可以完成所有繁重工作的 `.ps1xml`[格式化文件][]。</span><span class="sxs-lookup"><span data-stu-id="b009c-183">A lot of the native commands have a `.ps1xml` [formatting file][] that does all the heavy lifting.</span></span> <span data-ttu-id="b009c-184">[Boe Prox 的文章][]中提供了另外一种方法，只需使用 PowerShell 即可在自定义对象上执行此操作。</span><span class="sxs-lookup"><span data-stu-id="b009c-184">From this [post by Boe Prox][], there's another way for us to do this on our custom object using just PowerShell.</span></span> <span data-ttu-id="b009c-185">我们可以提供一个 `MemberSet` 供其使用。</span><span class="sxs-lookup"><span data-stu-id="b009c-185">We can give it a `MemberSet` for it to use.</span></span>

```powershell
$defaultDisplaySet = 'Name','Language'
$defaultDisplayPropertySet = New-Object System.Management.Automation.PSPropertySet(‘DefaultDisplayPropertySet’,[string[]]$defaultDisplaySet)
$PSStandardMembers = [System.Management.Automation.PSMemberInfo[]]@($defaultDisplayPropertySet)
$MyObject | Add-Member MemberSet PSStandardMembers $PSStandardMembers
```

<span data-ttu-id="b009c-186">现在，当我的对象刚好落到 shell 上时，默认情况下它将仅显示这些属性。</span><span class="sxs-lookup"><span data-stu-id="b009c-186">Now when my object just falls to the shell, it will only show those properties by default.</span></span>

### <a name="update-typedata-with-defaultpropertyset"></a><span data-ttu-id="b009c-187">带有 DefaultPropertySet 的 Update-TypeData</span><span class="sxs-lookup"><span data-stu-id="b009c-187">Update-TypeData with DefaultPropertySet</span></span>

<span data-ttu-id="b009c-188">这很好，但我最近在观看 [PowerShell unplugged 2016 with Jeffrey Snover & Don Jones][psunplugged] 时，发现了一种更好的方法。</span><span class="sxs-lookup"><span data-stu-id="b009c-188">This is nice but I recently saw a better way when watching [PowerShell unplugged 2016 with Jeffrey Snover & Don Jones][psunplugged].</span></span> <span data-ttu-id="b009c-189">Jeffrey 使用 [Update-TypeData][] 来指定默认属性。</span><span class="sxs-lookup"><span data-stu-id="b009c-189">Jeffrey was using [Update-TypeData][] to specify the default properties.</span></span>

```powershell
$TypeData = @{
    TypeName = 'My.Object'
    DefaultDisplayPropertySet = 'Name','Language'
}
Update-TypeData @TypeData
```

<span data-ttu-id="b009c-190">这非常简单，即使我没有此文章作为快速参考，也差不多能记住它。</span><span class="sxs-lookup"><span data-stu-id="b009c-190">That is simple enough that I could almost remember it if I didn't have this post as a quick reference.</span></span> <span data-ttu-id="b009c-191">现在，我可以轻松地创建具有很多属性的对象，并在从 shell 中查看时，为其提供一个不错的干净视图。</span><span class="sxs-lookup"><span data-stu-id="b009c-191">Now I can easily create objects with lots of properties and still give it a nice clean view when looking at it from the shell.</span></span> <span data-ttu-id="b009c-192">如果需要访问或查看其他属性，它们仍在那里。</span><span class="sxs-lookup"><span data-stu-id="b009c-192">If I need to access or see those other properties, they're still there.</span></span>

```powershell
$myObject | Format-List *
```

### <a name="update-typedata-with-scriptproperty"></a><span data-ttu-id="b009c-193">带有 ScriptProperty 的 Update-TypeData</span><span class="sxs-lookup"><span data-stu-id="b009c-193">Update-TypeData with ScriptProperty</span></span>

<span data-ttu-id="b009c-194">我从该视频中还学习到了如何为你的对象创建脚本属性。</span><span class="sxs-lookup"><span data-stu-id="b009c-194">Something else I got out of that video was creating script properties for your objects.</span></span> <span data-ttu-id="b009c-195">现在可以说，这也适用于现有对象。</span><span class="sxs-lookup"><span data-stu-id="b009c-195">This would be a good time to point out that this works for existing objects too.</span></span>

```powershell
$TypeData = @{
    TypeName = 'My.Object'
    MemberType = 'ScriptProperty'
    MemberName = 'UpperCaseName'
    Value = {$this.Name.toUpper()}
}
Update-TypeData @TypeData
```

<span data-ttu-id="b009c-196">你可以在创建对象之前或之后执行此操作，它仍可正常工作。</span><span class="sxs-lookup"><span data-stu-id="b009c-196">You can do this before your object is created or after and it will still work.</span></span> <span data-ttu-id="b009c-197">这就是将 `Add-Member` 与脚本属性一起使用的不同之处。</span><span class="sxs-lookup"><span data-stu-id="b009c-197">This is what makes this different then using `Add-Member` with a script property.</span></span> <span data-ttu-id="b009c-198">当你通过我前面提及的方式使用 `Add-Member` 时，它只存在于对象的特定实例上。</span><span class="sxs-lookup"><span data-stu-id="b009c-198">When you use `Add-Member` the way I referenced earlier, it only exists on that specific instance of the object.</span></span> <span data-ttu-id="b009c-199">此项适用于具有此 `TypeName` 的所有对象。</span><span class="sxs-lookup"><span data-stu-id="b009c-199">This one applies to all objects with this `TypeName`.</span></span>

## <a name="function-parameters"></a><span data-ttu-id="b009c-200">函数参数</span><span class="sxs-lookup"><span data-stu-id="b009c-200">Function parameters</span></span>

<span data-ttu-id="b009c-201">你现在可以在函数和脚本中对参数使用这些自定义类型。</span><span class="sxs-lookup"><span data-stu-id="b009c-201">You can now use these custom types for parameters in your functions and scripts.</span></span> <span data-ttu-id="b009c-202">可以让一个函数创建这些自定义对象，然后将它们传递到其他函数。</span><span class="sxs-lookup"><span data-stu-id="b009c-202">You can have one function create these custom objects and then pass them into other functions.</span></span>

```powershell
param( [PSTypeName('My.Object')]$Data )
```

<span data-ttu-id="b009c-203">PowerShell 要求对象是你指定的类型。</span><span class="sxs-lookup"><span data-stu-id="b009c-203">PowerShell requires that the object is the type you specified.</span></span> <span data-ttu-id="b009c-204">如果该类型不能自动匹配，则会引发验证错误，从而省去你在代码中执行测试的步骤。</span><span class="sxs-lookup"><span data-stu-id="b009c-204">It throws a validation error if the type doesn't match automatically to save you the step of testing for it in your code.</span></span> <span data-ttu-id="b009c-205">这是让 PowerShell 实现最佳性能的一个优秀示例。</span><span class="sxs-lookup"><span data-stu-id="b009c-205">A great example of letting PowerShell do what it does best.</span></span>

### <a name="function-outputtype"></a><span data-ttu-id="b009c-206">函数 OutputType</span><span class="sxs-lookup"><span data-stu-id="b009c-206">Function OutputType</span></span>

<span data-ttu-id="b009c-207">你还可以为高级函数定义 `OutputType`。</span><span class="sxs-lookup"><span data-stu-id="b009c-207">You can also define an `OutputType` for your advanced functions.</span></span>

```powershell
function Get-MyObject
{
    [OutputType('My.Object')]
    [CmdletBinding()]
        param
        (
            ...
```

<span data-ttu-id="b009c-208">OutputType 属性值只是一个文档说明。</span><span class="sxs-lookup"><span data-stu-id="b009c-208">The **OutputType** attribute value is only a documentation note.</span></span> <span data-ttu-id="b009c-209">它不是从函数代码派生，也不与实际函数输出进行比较。</span><span class="sxs-lookup"><span data-stu-id="b009c-209">It isn't derived from the function code or compared to the actual function output.</span></span>

<span data-ttu-id="b009c-210">使用输出类型的主要原因是，关于函数的元信息反映了你的意图。</span><span class="sxs-lookup"><span data-stu-id="b009c-210">The main reason you would use an output type is so that meta information about your function reflects your intentions.</span></span> <span data-ttu-id="b009c-211">例如，你的开发环境可以利用的 `Get-Command` 和 `Get-Help`。</span><span class="sxs-lookup"><span data-stu-id="b009c-211">Things like `Get-Command` and `Get-Help` that your development environment can take advantage of.</span></span> <span data-ttu-id="b009c-212">如果需要详细信息，请查看其帮助：[about_Functions_OutputTypeAttribute][]。</span><span class="sxs-lookup"><span data-stu-id="b009c-212">If you want more information, then take a look at the help for it: [about_Functions_OutputTypeAttribute][].</span></span>

<span data-ttu-id="b009c-213">也就是说，如果使用 Pester 对函数进行单元测试，最好验证输出对象与 OutputType 是否匹配。</span><span class="sxs-lookup"><span data-stu-id="b009c-213">With that said, if you're using Pester to unit test your functions then it would be a good idea to validate the output objects match your **OutputType**.</span></span> <span data-ttu-id="b009c-214">这可能会捕获那些不应该落入管道的变量。</span><span class="sxs-lookup"><span data-stu-id="b009c-214">This could catch variables that just fall to the pipe when they shouldn't.</span></span>

## <a name="closing-thoughts"></a><span data-ttu-id="b009c-215">结语</span><span class="sxs-lookup"><span data-stu-id="b009c-215">Closing thoughts</span></span>

<span data-ttu-id="b009c-216">本文的上下文都是关于 `[PSCustomObject]` 的，但许多信息都适用于一般对象。</span><span class="sxs-lookup"><span data-stu-id="b009c-216">The context of this was all about `[PSCustomObject]`, but a lot of this information applies to objects in general.</span></span>

<span data-ttu-id="b009c-217">我以前看到过其中的大部分功能，但从未见过它们作为 `PSCustomObject` 上的信息集合呈现。</span><span class="sxs-lookup"><span data-stu-id="b009c-217">I have seen most of these features in passing before but never saw them presented as a collection of information on `PSCustomObject`.</span></span> <span data-ttu-id="b009c-218">就在上周，我偶然看到另一个才吃惊地发现之前从未见过。</span><span class="sxs-lookup"><span data-stu-id="b009c-218">Just this last week I stumbled upon another one and was surprised that I had not seen it before.</span></span> <span data-ttu-id="b009c-219">我希望将所有这些想法集中在一起，让你有更全面的了解，并在有机会用到它们时能想起来。</span><span class="sxs-lookup"><span data-stu-id="b009c-219">I wanted to pull all these ideas together so you can hopefully see the bigger picture and be aware of them when you have an opportunity to use them.</span></span> <span data-ttu-id="b009c-220">希望你学有所获，并能够找到一种方法将其用在自己的脚本中。</span><span class="sxs-lookup"><span data-stu-id="b009c-220">I hope you learned something and can find a way to work this into your scripts.</span></span>

<!-- link references -->
[原始版本]: https://powershellexplained.com/2016-10-28-powershell-everything-you-wanted-to-know-about-pscustomobject/
[original version]: https://powershellexplained.com/2016-10-28-powershell-everything-you-wanted-to-know-about-pscustomobject/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Boe Prox 的文章]: https://learn-PowerShell.net/2013/08/03/quick-hits-set-the-default-property-display-in-PowerShell-on-custom-objects/
[post by Boe Prox]: https://learn-PowerShell.net/2013/08/03/quick-hits-set-the-default-property-display-in-PowerShell-on-custom-objects/
[格式化文件]: https://mcpmag.com/articles/2014/05/13/PowerShell-properties-part-3.aspx
[formatting file]: https://mcpmag.com/articles/2014/05/13/PowerShell-properties-part-3.aspx
[about_Functions_OutputTypeAttribute]: /powershell/module/microsoft.powershell.core/about/about_functions_outputtypeattribute
[读取和写入文件的多种方式]: https://powershellexplained.com/2017-03-18-Powershell-reading-and-saving-data-to-files
[The many ways to read and write to files]: https://powershellexplained.com/2017-03-18-Powershell-reading-and-saving-data-to-files
[/u/markekraus 的这篇文章]: https://www.reddit.com/r/PowerShell/comments/590awc/is_it_possible_to_initialize_a_pscustoobject_with/
[post by /u/markekraus]: https://www.reddit.com/r/PowerShell/comments/590awc/is_it_possible_to_initialize_a_pscustoobject_with/
[Adam Bertram]: http://www.adamtheautomator.com/building-custom-object-types-PowerShell-pstypename/
[Mike Shepard]: https://powershellstation.com/2016/05/22/custom-objects-and-pstypename/
[psunplugged]: https://www.youtube.com/watch?v=Ab46gHXNm8Q
[Update-TypeData]: /powershell/module/microsoft.powershell.utility/update-typedata