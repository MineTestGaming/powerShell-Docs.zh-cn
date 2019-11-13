---
title: 使用 Windows PowerShell 脚本创建工作流 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70532e7e-9cac-43c3-9687-e77011ecc878
caps.latest.revision: 4
ms.openlocfilehash: 5eb2186cbceee21f8b4a8c88b812e9c71f15e0af
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366026"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a><span data-ttu-id="48f43-102">使用 Windows PowerShell 脚本创建工作流</span><span class="sxs-lookup"><span data-stu-id="48f43-102">Creating a Workflow by Using a Windows PowerShell Script</span></span>

<span data-ttu-id="48f43-103">可以通过编写 Windows PowerShell 脚本来创建工作流。</span><span class="sxs-lookup"><span data-stu-id="48f43-103">You can create a workflow by writing a Windows PowerShell script.</span></span> <span data-ttu-id="48f43-104">若要创建工作流，请在脚本正文前使用工作流关键字，后跟工作流的名称。</span><span class="sxs-lookup"><span data-stu-id="48f43-104">To create a workflow, use the workflow keyword followed by a name for the workflow before the body of the script.</span></span> <span data-ttu-id="48f43-105">例如：</span><span class="sxs-lookup"><span data-stu-id="48f43-105">For example:</span></span>

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

<span data-ttu-id="48f43-106">查找工作流的方式与处理任何其他 Windows PowerShell 命令的方式相同。</span><span class="sxs-lookup"><span data-stu-id="48f43-106">You find the workflow in the same way you would any other Windows PowerShell command.</span></span>

## <a name="implementing-parallel-and-sequence"></a><span data-ttu-id="48f43-107">实现并行和序列</span><span class="sxs-lookup"><span data-stu-id="48f43-107">Implementing Parallel and Sequence</span></span>

<span data-ttu-id="48f43-108">[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx)支持并行执行活动。</span><span class="sxs-lookup"><span data-stu-id="48f43-108">[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx) supports execution of activities in parallel.</span></span> <span data-ttu-id="48f43-109">若要在 Windows PowerShell 脚本中实现此功能，请使用脚本块前面的 `parallel` 关键字。</span><span class="sxs-lookup"><span data-stu-id="48f43-109">To implement this capability in a Windows PowerShell script, use the `parallel` keyword in front of a script block.</span></span> <span data-ttu-id="48f43-110">你还可以使用 `foreach -parallel` 构造以并行方式循环访问对象的集合。</span><span class="sxs-lookup"><span data-stu-id="48f43-110">You can also use the `foreach -parallel` construction to iterate through a collection of objects in parallel.</span></span> <span data-ttu-id="48f43-111">若要按顺序在并行块中按顺序执行一组活动，请将该活动组括在脚本块中，并在块前面加上 sequence 关键字。</span><span class="sxs-lookup"><span data-stu-id="48f43-111">To execute a group of activities in sequential order within a parallel block, enclose that group of activities in a script block and precede the block with the sequence keyword.</span></span>

## <a name="joining-computers-to-a-domain"></a><span data-ttu-id="48f43-112">将计算机加入域</span><span class="sxs-lookup"><span data-stu-id="48f43-112">Joining Computers to a Domain</span></span>

<span data-ttu-id="48f43-113">下面的脚本创建一个工作流，该工作流检查一组用户指定的计算机的域状态，将它们加入域（如果尚未加入域），然后再次检查状态。</span><span class="sxs-lookup"><span data-stu-id="48f43-113">The following script creates a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span> <span data-ttu-id="48f43-114">这是在[使用 Windows PowerShell 活动创建工作流](./creating-a-workflow-with-windows-powershell-activities.md)中说明的 XAML 工作流的脚本版本。</span><span class="sxs-lookup"><span data-stu-id="48f43-114">This is a script version of the XAML workflow explained in [Creating a Workflow with Windows PowerShell Activities](./creating-a-workflow-with-windows-powershell-activities.md).</span></span>

```powershell
workflow Join-Domain
{
    param([string[]] $ComputerName, [PSCredential] $DomainCred, [PsCredential] $MachineCred)

    foreach -parallel($Computer in $ComputerName)
    {
        sequence {
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        Add-Computer -PSComputerName $Computer -PSCredential $DomainCred
        Restart-Computer -ComputerName $Computer -Credential $MachineCred -For PowerShell -Force -Wait -PSComputerName ""
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        }
    }
 }

```