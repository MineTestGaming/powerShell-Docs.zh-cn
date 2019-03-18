---
title: RunSpace06 代码示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d71f86d5-eb62-4b16-aa95-5fd3f314ffd3
caps.latest.revision: 6
ms.openlocfilehash: d0330f082262b68486a582ed95c7a520be1e184c
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429527"
---
# <a name="runspace06-code-sample"></a><span data-ttu-id="e0fdc-102">RunSpace06 代码示例</span><span class="sxs-lookup"><span data-stu-id="e0fdc-102">RunSpace06 Code Sample</span></span>

<span data-ttu-id="e0fdc-103">此处是 Runspace06 示例中所述的源代码[配置使用 Windows PowerShell 管理单元的运行空间](http://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83)。</span><span class="sxs-lookup"><span data-stu-id="e0fdc-103">Here is the source code for the Runspace06 sample described in [Configuring a Runspace Using a Windows PowerShell Snap-in](http://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83).</span></span> <span data-ttu-id="e0fdc-104">此示例应用程序创建基于 Windows PowerShell 管理单元中，然后用于使用单个命令运行管道的运行空间。</span><span class="sxs-lookup"><span data-stu-id="e0fdc-104">This sample application creates a runspace based on a Windows PowerShell snap-in, which is then used to run a pipeline with a single command.</span></span> <span data-ttu-id="e0fdc-105">若要执行此操作，应用程序会创建运行空间配置信息，创建一个运行空间，使用单个命令，创建一个管道，然后执行管道。</span><span class="sxs-lookup"><span data-stu-id="e0fdc-105">To do this, the application creates the runspace configuration information, creates a runspace, creates a pipeline with a single command, and then executes the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="e0fdc-106">您可以下载C#通过使用 Windows 软件开发工具包适用于 Windows Vista 和 Microsoft.NET Framework 3.0 运行时组件的源文件 (runspace06.cs)。</span><span class="sxs-lookup"><span data-stu-id="e0fdc-106">You can download the C# source file (runspace06.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="e0fdc-107">有关下载说明，请参阅[如何安装 Windows PowerShell 和下载 Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="e0fdc-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="e0fdc-108">已下载的源文件中有 **\<PowerShell 示例 >** 目录。</span><span class="sxs-lookup"><span data-stu-id="e0fdc-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="e0fdc-109">代码示例</span><span class="sxs-lookup"><span data-stu-id="e0fdc-109">Code Sample</span></span>

[!code-csharp[Runspace06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs#L11-L85 "Runspace06.cs")]

## <a name="see-also"></a><span data-ttu-id="e0fdc-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e0fdc-110">See Also</span></span>

[<span data-ttu-id="e0fdc-111">Windows PowerShell 程序员指南</span><span class="sxs-lookup"><span data-stu-id="e0fdc-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="e0fdc-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e0fdc-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)