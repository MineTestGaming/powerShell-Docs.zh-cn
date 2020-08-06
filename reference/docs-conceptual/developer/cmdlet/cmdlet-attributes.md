---
title: Cmdlet 属性 |Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- attributes [PowerShell SDK]
- attributes [PowerShell SDK], described
ms.openlocfilehash: f22c2882fbe5b2f51ca5ea218b921192b0a7d41f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784514"
---
# <a name="cmdlet-attributes"></a><span data-ttu-id="5c6b9-102">Cmdlet 属性</span><span class="sxs-lookup"><span data-stu-id="5c6b9-102">Cmdlet Attributes</span></span>

<span data-ttu-id="5c6b9-103">Windows PowerShell 定义多个属性，可用于向 cmdlet 添加常见功能，而无需在自己的代码中实现该功能。</span><span class="sxs-lookup"><span data-stu-id="5c6b9-103">Windows PowerShell defines several attributes that you can use to add common functionality to your cmdlets without implementing that functionality within your own code.</span></span> <span data-ttu-id="5c6b9-104">这包括 Cmdlet 属性，该属性用于将 Microsoft .NET 框架类标识为 cmdlet 类、指定 cmdlet 返回的 .NET Framework 类型的 OutputType 属性、用于将公共属性标识为 cmdlet 参数的参数属性等。</span><span class="sxs-lookup"><span data-stu-id="5c6b9-104">This includes the Cmdlet attribute that identifies a Microsoft .NET Framework class as a cmdlet class, the OutputType attribute that specifies the .NET Framework types returned by the cmdlet, the Parameter attribute that identifies public properties as cmdlet parameters, and more.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="5c6b9-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="5c6b9-105">In This Section</span></span>

<span data-ttu-id="5c6b9-106">[Cmdlet 代码中的属性](./attributes-in-cmdlet-code.md)介绍使用 cmdlet 代码中的属性的好处。</span><span class="sxs-lookup"><span data-stu-id="5c6b9-106">[Attributes in Cmdlet Code](./attributes-in-cmdlet-code.md) Describes the benefit of using attributes in cmdlet code.</span></span>

<span data-ttu-id="5c6b9-107">[特性类型](./attribute-types.md)描述可以修饰 cmdlet 类的不同属性。</span><span class="sxs-lookup"><span data-stu-id="5c6b9-107">[Attribute Types](./attribute-types.md) Describes the different attributes that can decorate a cmdlet class.</span></span>

<span data-ttu-id="5c6b9-108">[Alias 特性声明](./alias-attribute-declaration.md)描述如何为 cmdlet 参数名称定义别名。</span><span class="sxs-lookup"><span data-stu-id="5c6b9-108">[Alias Attribute Declaration](./alias-attribute-declaration.md) Describes how to define aliases for a cmdlet parameter name.</span></span>

<span data-ttu-id="5c6b9-109">[Cmdlet 特性声明](./cmdlet-attribute-declaration.md)描述如何将 .NET Framework 类定义为 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5c6b9-109">[Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md) Describes how to define a .NET Framework class as a cmdlet.</span></span>

<span data-ttu-id="5c6b9-110">[Credential 特性声明](./credential-attribute-declaration.md)介绍如何添加对将字符串输入转换为[system.web](/dotnet/api/System.Management.Automation.PSCredential)对象的支持。</span><span class="sxs-lookup"><span data-stu-id="5c6b9-110">[Credential Attribute Declaration](./credential-attribute-declaration.md) Describes how to add support for converting string input into a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span>

<span data-ttu-id="5c6b9-111">[OutputType 特性声明](./outputtype-attribute-declaration.md)描述如何指定 cmdlet 返回的 .NET Framework 类型。</span><span class="sxs-lookup"><span data-stu-id="5c6b9-111">[OutputType attribute Declaration](./outputtype-attribute-declaration.md) Describes how to specify the .NET Framework types returned by the cmdlet.</span></span>

<span data-ttu-id="5c6b9-112">[参数属性声明](./parameter-attribute-declaration.md)描述如何定义 cmdlet 的参数。</span><span class="sxs-lookup"><span data-stu-id="5c6b9-112">[Parameter Attribute Declaration](./parameter-attribute-declaration.md) Describes how to define the parameters of a cmdlet.</span></span>

<span data-ttu-id="5c6b9-113">[ValidateCount 特性声明](./validatecount-attribute-declaration.md)描述如何定义参数允许的参数数量。</span><span class="sxs-lookup"><span data-stu-id="5c6b9-113">[ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md) Describes how to define how many arguments are allowed for a parameter.</span></span>

<span data-ttu-id="5c6b9-114">[ValidateLength 特性声明](./validatelength-attribute-declaration.md)描述如何定义参数参数的长度 (以字符) 。</span><span class="sxs-lookup"><span data-stu-id="5c6b9-114">[ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md) Describes how to define the length (in characters) of a parameter argument.</span></span>

<span data-ttu-id="5c6b9-115">[ValidatePattern 特性声明](./validatepattern-attribute-declaration.md)描述如何定义参数参数的有效模式。</span><span class="sxs-lookup"><span data-stu-id="5c6b9-115">[ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md) Describes how to define the valid patterns for a parameter argument.</span></span>

<span data-ttu-id="5c6b9-116">[ValidateRange 特性声明](./validaterange-attribute-declaration.md)描述如何定义参数参数的有效范围。</span><span class="sxs-lookup"><span data-stu-id="5c6b9-116">[ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md) Describes how to define the valid range for a parameter argument.</span></span>

<span data-ttu-id="5c6b9-117">[ValidateSet 特性声明](./validateset-attribute-declaration.md)描述如何定义参数参数的可能值。</span><span class="sxs-lookup"><span data-stu-id="5c6b9-117">[ValidateSet Attribute Declaration](./validateset-attribute-declaration.md) Describes how to define the possible values for a parameter argument.</span></span>

## <a name="reference"></a><span data-ttu-id="5c6b9-118">参考</span><span class="sxs-lookup"><span data-stu-id="5c6b9-118">Reference</span></span>

[<span data-ttu-id="5c6b9-119">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5c6b9-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
