---
title: Alias 属性声明 |Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- Alias attribute
- attributes, Alias
- Alias attribute, described
ms.openlocfilehash: 4c1ff34a244611173ca919a44d6598189b19dc98
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782406"
---
# <a name="alias-attribute-declaration"></a><span data-ttu-id="2099e-102">别名属性声明</span><span class="sxs-lookup"><span data-stu-id="2099e-102">Alias Attribute Declaration</span></span>

<span data-ttu-id="2099e-103">Alias 属性允许用户为 cmdlet 参数指定不同的名称。</span><span class="sxs-lookup"><span data-stu-id="2099e-103">The Alias attribute allows the user to specify different names for a cmdlet parameter.</span></span> <span data-ttu-id="2099e-104">可以使用别名提供参数名称的快捷方式，也可以提供适用于不同方案的不同名称。</span><span class="sxs-lookup"><span data-stu-id="2099e-104">Aliases can be used to provide shortcuts for a parameter name, or they can provide different names that are appropriate for different scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="2099e-105">语法</span><span class="sxs-lookup"><span data-stu-id="2099e-105">Syntax</span></span>

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a><span data-ttu-id="2099e-106">参数</span><span class="sxs-lookup"><span data-stu-id="2099e-106">Parameters</span></span>

<span data-ttu-id="2099e-107">`aliasName`需要 (String [] ) 。</span><span class="sxs-lookup"><span data-stu-id="2099e-107">`aliasName` (String[]) Required.</span></span> <span data-ttu-id="2099e-108">指定 cmdlet 参数的一组以逗号分隔的别名。</span><span class="sxs-lookup"><span data-stu-id="2099e-108">Specifies a set of comma-separated alias names for the cmdlet parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="2099e-109">备注</span><span class="sxs-lookup"><span data-stu-id="2099e-109">Remarks</span></span>

- <span data-ttu-id="2099e-110">当指定 cmdlet 参数时，会将 Alias 特性与参数特性一起使用。</span><span class="sxs-lookup"><span data-stu-id="2099e-110">The Alias attribute is used with the Parameter attribute when you specify a cmdlet parameter.</span></span> <span data-ttu-id="2099e-111">有关如何声明这些属性的详细信息，请参阅[如何声明 Cmdlet 参数](./how-to-declare-cmdlet-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="2099e-111">For more information about how to declare these attributes, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="2099e-112">每个别名在 cmdlet 中必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="2099e-112">Each alias name must be unique within a cmdlet.</span></span> <span data-ttu-id="2099e-113">Windows PowerShell 不会检查是否存在重复的别名。</span><span class="sxs-lookup"><span data-stu-id="2099e-113">Windows PowerShell does not check for duplicate alias names.</span></span>

- <span data-ttu-id="2099e-114">为 cmdlet 中的每个参数使用一次 Alias 特性。</span><span class="sxs-lookup"><span data-stu-id="2099e-114">The Alias attribute is used once for each parameter in a cmdlet.</span></span>

- <span data-ttu-id="2099e-115">Alias 特性是由[Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute)类定义的。</span><span class="sxs-lookup"><span data-stu-id="2099e-115">The Alias attribute is defined by the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="2099e-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2099e-116">See Also</span></span>

[<span data-ttu-id="2099e-117">参数别名</span><span class="sxs-lookup"><span data-stu-id="2099e-117">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="2099e-118">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2099e-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
