---
title: 如何创建 Windows PowerShell 管理单元 |Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- snap-ins [PowerShell SDK], examples
ms.openlocfilehash: 4150ba582544d1daa4a898f0ff20b169c24a0ee0
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787319"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a><span data-ttu-id="15394-102">如何创建 Windows PowerShell 管理单元</span><span class="sxs-lookup"><span data-stu-id="15394-102">How to Create a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="15394-103">Windows PowerShell 管理单元提供了一种机制，用于向 shell 注册一组 cmdlet 以及另一个 Windows PowerShell 提供程序，从而扩展了 shell 的功能。</span><span class="sxs-lookup"><span data-stu-id="15394-103">A Windows PowerShell snap-in provides a mechanism for registering sets of cmdlets and another Windows PowerShell provider with the shell, thus extending the functionality of the shell.</span></span> <span data-ttu-id="15394-104">Windows PowerShell 管理单元可以将所有 cmdlet 和提供程序注册到单个程序集中，也可以注册特定的 cmdlet 和提供程序列表。</span><span class="sxs-lookup"><span data-stu-id="15394-104">A Windows PowerShell snap-in can register all the cmdlets and providers in a single assembly, or it can register a specific list of cmdlets and providers.</span></span>

<span data-ttu-id="15394-105">管理单元程序集应安装在受保护的目录中，就像在其他操作系统中一样。</span><span class="sxs-lookup"><span data-stu-id="15394-105">Snap-in assemblies should be installed in a protected directory, just as they would be with other operating systems.</span></span> <span data-ttu-id="15394-106">否则，恶意用户可以将程序集替换为不安全代码。</span><span class="sxs-lookup"><span data-stu-id="15394-106">Otherwise, malicious users can replace an assembly with unsafe code.</span></span>

## <a name="windows-powershell-snap-in-classes"></a><span data-ttu-id="15394-107">Windows PowerShell 管理单元类</span><span class="sxs-lookup"><span data-stu-id="15394-107">Windows PowerShell Snap-in Classes</span></span>

<span data-ttu-id="15394-108">所有 Windows PowerShell 管理单元类均从[add-pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn)或[Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn)类中派生而来的。</span><span class="sxs-lookup"><span data-stu-id="15394-108">All Windows PowerShell snap-in classes derive from the [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) or [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) classes.</span></span>

## <a name="examples"></a><span data-ttu-id="15394-109">示例</span><span class="sxs-lookup"><span data-stu-id="15394-109">Examples</span></span>

<span data-ttu-id="15394-110">[编写 Windows PowerShell 管理单元](./writing-a-windows-powershell-snap-in.md)：此示例演示如何创建用于在程序集中注册所有 cmdlet 和提供程序的管理单元。</span><span class="sxs-lookup"><span data-stu-id="15394-110">[Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md): This example shows how to create a snap-in that is used to register all the cmdlets and providers in an assembly.</span></span>

<span data-ttu-id="15394-111">[编写自定义 Windows PowerShell 管理单元](./writing-a-custom-windows-powershell-snap-in.md)：此示例演示如何创建一个自定义管理单元，该管理单元用于注册一组特定的 cmdlet 和提供程序，它们在单个程序集中可能存在也可能不存在。</span><span class="sxs-lookup"><span data-stu-id="15394-111">[Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md): This example shows how to create a custom snap-in that is used to register a specific set of cmdlets and providers that might or might not exist in a single assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="15394-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="15394-112">See Also</span></span>

[<span data-ttu-id="15394-113">System.web. Add-pssnapin</span><span class="sxs-lookup"><span data-stu-id="15394-113">System.Management.Automation.PSSnapIn</span></span>](/dotnet/api/System.Management.Automation.PSSnapIn)

[<span data-ttu-id="15394-114">System.web. Custompssnapin</span><span class="sxs-lookup"><span data-stu-id="15394-114">System.Management.Automation.Custompssnapin</span></span>](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[<span data-ttu-id="15394-115">注册 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="15394-115">Registering Cmdlets</span></span>](./registering-cmdlets.md)

[<span data-ttu-id="15394-116">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="15394-116">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
