---
title: 'GetProc03 (c # ) 示例代码 |Microsoft Docs'
ms.date: 09/13/2016
ms.openlocfilehash: 278c3f36bb975f9ea195978853e6539c0bd15084
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787115"
---
# <a name="getproc03-c-sample-code"></a><span data-ttu-id="569fd-102">GetProc03 (C#) 示例代码</span><span class="sxs-lookup"><span data-stu-id="569fd-102">GetProc03 (C#) Sample Code</span></span>

<span data-ttu-id="569fd-103">下面的代码演示了 `Get-Process` 可以接受流水线输入的 cmdlet 的实现。</span><span class="sxs-lookup"><span data-stu-id="569fd-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="569fd-104">此实现定义了一个 `Name` 参数，该参数接受管道输入，并根据提供的名称从本地计算机检索进程信息，然后使用[WriteObject (system.object) ](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_)方法作为将对象发送到管道的输出机制。</span><span class="sxs-lookup"><span data-stu-id="569fd-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending objects to the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="569fd-105">你可以使用适用于 Windows Vista 的 Microsoft Windows 软件开发工具包和 .NET Framework 3.0 运行时组件 (getprov03.cs cmdlet 下载 c # 源文件) 。</span><span class="sxs-lookup"><span data-stu-id="569fd-105">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="569fd-106">有关下载说明，请参阅[如何安装 Windows powershell 和下载 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="569fd-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="569fd-107">下载的源文件在目录中提供 **\<PowerShell Samples>** 。</span><span class="sxs-lookup"><span data-stu-id="569fd-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="569fd-108">代码示例</span><span class="sxs-lookup"><span data-stu-id="569fd-108">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs" range="11-78":::

## <a name="see-also"></a><span data-ttu-id="569fd-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="569fd-109">See Also</span></span>

[<span data-ttu-id="569fd-110">Windows PowerShell 程序员指南</span><span class="sxs-lookup"><span data-stu-id="569fd-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="569fd-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="569fd-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
