---
title: Runspace01 (C#) 代码示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d59f8b7c-e800-4633-aa5b-74d4c57e2706
caps.latest.revision: 6
ms.openlocfilehash: 59320365c4a35c3d71af10273eb21b1ce01e5c0c
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429697"
---
# <a name="runspace01-c-code-sample"></a><span data-ttu-id="a11c1-102">Runspace01 (C#) 代码示例</span><span class="sxs-lookup"><span data-stu-id="a11c1-102">Runspace01 (C#) Code Sample</span></span>

<span data-ttu-id="a11c1-103">以下是代码示例的运行空间中所述[创建控制台应用程序，运行指定命令](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e)。</span><span class="sxs-lookup"><span data-stu-id="a11c1-103">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e).</span></span> <span data-ttu-id="a11c1-104">若要执行此操作，该应用程序调用一个运行空间，并调用命令。</span><span class="sxs-lookup"><span data-stu-id="a11c1-104">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="a11c1-105">（请注意，此应用程序未指定的运行空间配置信息，也不它不会显式创建的管道。）</span><span class="sxs-lookup"><span data-stu-id="a11c1-105">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline).</span></span> <span data-ttu-id="a11c1-106">调用的命令是`Get-Process`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a11c1-106">The command that is invoked is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="a11c1-107">您可以下载C#使用 Microsoft Windows 软件开发工具包适用于 Windows Vista 和 Microsoft.NET Framework 3.0 运行时组件的此运行空间的源文件 (runspace01.cs)。</span><span class="sxs-lookup"><span data-stu-id="a11c1-107">You can download the C# source file (runspace01.cs) for this runspace using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="a11c1-108">有关下载说明，请参阅[如何安装 Windows PowerShell 和下载 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="a11c1-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="a11c1-109">已下载的源文件中有 **\<PowerShell 示例 >** 目录。</span><span class="sxs-lookup"><span data-stu-id="a11c1-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="a11c1-110">代码示例</span><span class="sxs-lookup"><span data-stu-id="a11c1-110">Code Sample</span></span>

[!code-csharp[Runspace01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs#L11-L62 "Runspace01.cs")]

## <a name="see-also"></a><span data-ttu-id="a11c1-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a11c1-111">See Also</span></span>

[<span data-ttu-id="a11c1-112">Windows PowerShell 程序员指南</span><span class="sxs-lookup"><span data-stu-id="a11c1-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="a11c1-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="a11c1-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)