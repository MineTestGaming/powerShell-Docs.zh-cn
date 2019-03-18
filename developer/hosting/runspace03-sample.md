---
title: Runspace03 示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 31df99d7-6954-4fdc-b6f5-06ecba094f43
caps.latest.revision: 8
ms.openlocfilehash: 39495f7813aecf5d0210866fc11f94557fdb0cd9
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058991"
---
# <a name="runspace03-sample"></a><span data-ttu-id="e27d4-102">Runspace03 示例</span><span class="sxs-lookup"><span data-stu-id="e27d4-102">Runspace03 Sample</span></span>

<span data-ttu-id="e27d4-103">此示例演示如何使用[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)类来运行脚本以同步方式，以及如何处理非终止性错误。</span><span class="sxs-lookup"><span data-stu-id="e27d4-103">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run a script synchronously, and how to handle non-terminating errors.</span></span> <span data-ttu-id="e27d4-104">该脚本可接收一系列进程名称，然后检索这些进程。</span><span class="sxs-lookup"><span data-stu-id="e27d4-104">The script receives a list of process names and then retrieves those processes.</span></span> <span data-ttu-id="e27d4-105">脚本的结果（包括运行脚本时生成的非终止错误）显示在控制台窗口中。</span><span class="sxs-lookup"><span data-stu-id="e27d4-105">The results of the script, including any non-terminating errors that were generated when running the script, are displayed in a console window.</span></span>

## <a name="requirements"></a><span data-ttu-id="e27d4-106">要求</span><span class="sxs-lookup"><span data-stu-id="e27d4-106">Requirements</span></span>

<span data-ttu-id="e27d4-107">此示例要求 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="e27d4-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="e27d4-108">说明</span><span class="sxs-lookup"><span data-stu-id="e27d4-108">Demonstrates</span></span>

<span data-ttu-id="e27d4-109">此示例将演示如下。</span><span class="sxs-lookup"><span data-stu-id="e27d4-109">This sample demonstrates the following.</span></span>

- <span data-ttu-id="e27d4-110">创建[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)对象运行脚本。</span><span class="sxs-lookup"><span data-stu-id="e27d4-110">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to run a script.</span></span>

- <span data-ttu-id="e27d4-111">将脚本添加到的管道[System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell)对象。</span><span class="sxs-lookup"><span data-stu-id="e27d4-111">Adding a script to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="e27d4-112">输入将对象传递给该脚本从调用程序。</span><span class="sxs-lookup"><span data-stu-id="e27d4-112">Passing input objects to the script from the calling program.</span></span>

- <span data-ttu-id="e27d4-113">以同步方式运行脚本。</span><span class="sxs-lookup"><span data-stu-id="e27d4-113">Running the script synchronously.</span></span>

- <span data-ttu-id="e27d4-114">使用[System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject)对象以提取和显示从脚本返回的对象的属性。</span><span class="sxs-lookup"><span data-stu-id="e27d4-114">Using [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects to extract and display properties from the objects returned by the script.</span></span>

- <span data-ttu-id="e27d4-115">检索和显示运行该脚本时生成的错误记录。</span><span class="sxs-lookup"><span data-stu-id="e27d4-115">Retrieving and displaying error records that were generated when the script was run.</span></span>

## <a name="example"></a><span data-ttu-id="e27d4-116">示例</span><span class="sxs-lookup"><span data-stu-id="e27d4-116">Example</span></span>

<span data-ttu-id="e27d4-117">此示例中提供的 Windows PowerShell 的默认运行空间以同步方式运行脚本。</span><span class="sxs-lookup"><span data-stu-id="e27d4-117">This sample runs a script synchronously in the default runspace provided by Windows PowerShell.</span></span> <span data-ttu-id="e27d4-118">在控制台窗口中显示的脚本和生成的任何非终止错误输出。</span><span class="sxs-lookup"><span data-stu-id="e27d4-118">The output of the script and any non-terminating errors that were generated are displayed in a console window.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace03
  {
    /// <summary>
    /// This sample shows how to use the PowerShell class to run a
    /// script that retrieves process information for the list of
    /// process names passed to the script. It shows how to pass input
    /// objects to a script and how to retrieve error objects as well
    /// as the output objects.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerSHell object to run a script.
    /// 2. Adding a script to the pipeline of the PowerShell object.
    /// 3. Passing input objects to the script from the calling program.
    /// 4. Running the script synchronously.
    /// 5. Using PSObject objects to extract and display properties from
    ///    the objects returned by the script.
    /// 6. Retrieving and displaying error records that were generated
    ///    when the script was run.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Define a list of processes to look for.
      string[] processNames = new string[]
      {
        "lsass", "nosuchprocess", "services", "nosuchprocess2"
      };

      // The script to run to get these processes. Input passed
      // to the script will be available in the $input variable.
      string script = "$input | get-process -name {$_}";

      // Create a PowerShell object. Creating this object takes care of
      // building all of the other data structures needed to run the script.
      using (PowerShell powershell = PowerShell.Create())
      {
        powershell.AddScript(script);

        Console.WriteLine("Process              HandleCount");
        Console.WriteLine("--------------------------------");

        // Invoke the script synchronously and display the
        // ProcessName and HandleCount properties of the
        // objects that are returned.
        foreach (PSObject result in powershell.Invoke(processNames))
        {
          Console.WriteLine(
                            "{0,-20} {1}",
                            result.Members["ProcessName"].Value,
                            result.Members["HandleCount"].Value);
        }

        // Process any error records that were generated while running
        //  the script.
        Console.WriteLine("\nThe following non-terminating errors occurred:\n");
        PSDataCollection<ErrorRecord> errors = powershell.Streams.Error;
        if (errors != null && errors.Count > 0)
        {
          foreach (ErrorRecord err in errors)
          {
            System.Console.WriteLine("    error: {0}", err.ToString());
          }
        }
      }

      System.Console.WriteLine("\nHit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="e27d4-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e27d4-119">See Also</span></span>

[<span data-ttu-id="e27d4-120">编写 Windows PowerShell 主机应用程序</span><span class="sxs-lookup"><span data-stu-id="e27d4-120">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)