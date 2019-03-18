---
title: StopProcessSample01 Sample | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7bed607-369b-4507-87fa-f6011c2f1970
caps.latest.revision: 9
ms.openlocfilehash: 2ce146df05ef876d9c17f560628ebac2c39e57bf
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059195"
---
# <a name="stopprocesssample01-sample"></a><span data-ttu-id="5b4b4-102">StopProcessSample01 示例</span><span class="sxs-lookup"><span data-stu-id="5b4b4-102">StopProcessSample01 Sample</span></span>

<span data-ttu-id="5b4b4-103">此示例演示如何编写一个 cmdlet，它会尝试停止进程之前, 请求用户反馈以及如何实现`PassThru`参数，该值指示用户想该 cmdlet 返回的对象。</span><span class="sxs-lookup"><span data-stu-id="5b4b4-103">This sample shows how to write a cmdlet that requests feedback from the user before it attempts to stop a process, and how to implement a `PassThru` parameter indicating that the user wants the cmdlet to return an object.</span></span> <span data-ttu-id="5b4b4-104">此 cmdlet 类似于是`Stop-Process`cmdlet 提供的 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="5b4b4-104">This cmdlet is similar to the `Stop-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

### <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="5b4b4-105">如何通过使用 Visual Studio 生成该示例。</span><span class="sxs-lookup"><span data-stu-id="5b4b4-105">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="5b4b4-106">安装了 Windows PowerShell 2.0 sdk，导航到 StopProcessSample01 文件夹。</span><span class="sxs-lookup"><span data-stu-id="5b4b4-106">With the Windows PowerShell 2.0 SDK installed, navigate to the StopProcessSample01 folder.</span></span> <span data-ttu-id="5b4b4-107">默认位置为 C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\StopProcessSample01。</span><span class="sxs-lookup"><span data-stu-id="5b4b4-107">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\StopProcessSample01.</span></span>

2. <span data-ttu-id="5b4b4-108">双击解决方案 (.sln) 文件的图标。</span><span class="sxs-lookup"><span data-stu-id="5b4b4-108">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="5b4b4-109">这将在 Microsoft Visual Studio 中打开示例项目。</span><span class="sxs-lookup"><span data-stu-id="5b4b4-109">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="5b4b4-110">在中**构建**菜单中，选择**生成解决方案**。</span><span class="sxs-lookup"><span data-stu-id="5b4b4-110">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="5b4b4-111">将默认 \bin 或 \bin\debug 文件夹中生成的示例库。</span><span class="sxs-lookup"><span data-stu-id="5b4b4-111">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="5b4b4-112">如何运行示例</span><span class="sxs-lookup"><span data-stu-id="5b4b4-112">How to run the sample</span></span>

1. <span data-ttu-id="5b4b4-113">创建以下模块文件夹：</span><span class="sxs-lookup"><span data-stu-id="5b4b4-113">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/StopProcessSample01`

2. <span data-ttu-id="5b4b4-114">将示例程序集复制到模块文件夹中。</span><span class="sxs-lookup"><span data-stu-id="5b4b4-114">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="5b4b4-115">启动 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="5b4b4-115">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="5b4b4-116">运行以下命令以将该程序集加载到 Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="5b4b4-116">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `import-module stopprossessample01`

5. <span data-ttu-id="5b4b4-117">运行以下命令以运行该 cmdlet:</span><span class="sxs-lookup"><span data-stu-id="5b4b4-117">Run the following command to run the cmdlet:</span></span>

    `stop-proc`

## <a name="requirements"></a><span data-ttu-id="5b4b4-118">要求</span><span class="sxs-lookup"><span data-stu-id="5b4b4-118">Requirements</span></span>

<span data-ttu-id="5b4b4-119">此示例要求 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="5b4b4-119">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="5b4b4-120">说明</span><span class="sxs-lookup"><span data-stu-id="5b4b4-120">Demonstrates</span></span>

<span data-ttu-id="5b4b4-121">此示例将演示如下。</span><span class="sxs-lookup"><span data-stu-id="5b4b4-121">This sample demonstrates the following.</span></span>

- <span data-ttu-id="5b4b4-122">通过使用 Cmdlet 属性声明 cmdlet 类。</span><span class="sxs-lookup"><span data-stu-id="5b4b4-122">Declaring a cmdlet class by using the Cmdlet attribute.</span></span>

- <span data-ttu-id="5b4b4-123">声明一个 cmdlet 参数使用参数属性。</span><span class="sxs-lookup"><span data-stu-id="5b4b4-123">Declaring a cmdlet parameters by using the Parameter attribute.</span></span>

- <span data-ttu-id="5b4b4-124">调用 ShouldProcess 方法来请求确认。</span><span class="sxs-lookup"><span data-stu-id="5b4b4-124">Calling the ShouldProcess method to request confirmation.</span></span>

- <span data-ttu-id="5b4b4-125">实现`PassThru`参数，指示是否用户想要 cmdlet 可返回一个对象。</span><span class="sxs-lookup"><span data-stu-id="5b4b4-125">Implementing a `PassThru` parameter that indicates if the user wants the cmdlet to return an object.</span></span> <span data-ttu-id="5b4b4-126">默认情况下，此 cmdlet 不返回到管道的对象。</span><span class="sxs-lookup"><span data-stu-id="5b4b4-126">By default, this cmdlet does not return an object to the pipeline.</span></span>

## <a name="example"></a><span data-ttu-id="5b4b4-127">示例</span><span class="sxs-lookup"><span data-stu-id="5b4b4-127">Example</span></span>

<span data-ttu-id="5b4b4-128">此示例演示如何实现`PassThru`参数，指示用户想要 cmdlet 可返回一个对象，以及如何请求用户反馈，通过调用`ShouldProcess`和`ShouldContinue`方法。</span><span class="sxs-lookup"><span data-stu-id="5b4b4-128">This sample shows how to implement a `PassThru` parameter that indicates that the user wants the cmdlet to return an object, and how to request user feedback by calls to the `ShouldProcess` and `ShouldContinue` methods.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Collections;
using Win32Exception = System.ComponentModel.Win32Exception;
using System.Management.Automation;    // Windows PowerShell namespace
using System.Globalization;

namespace Microsoft.Samples.PowerShell.Commands
{
   #region StopProcCommand

    /// <summary>
   /// This class implements the stop-proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsLifecycle.Stop, "Proc",
       SupportsShouldProcess = true)]
   public class StopProcCommand : Cmdlet
   {
       #region Parameters

      /// <summary>
      /// This parameter provides the list of process names on
      /// which the Stop-Proc cmdlet will work.
      /// </summary>
       [Parameter(
          Position = 0,
          Mandatory = true,
          ValueFromPipeline = true,
          ValueFromPipelineByPropertyName = true
       )]
       public string[] Name
       {
           get { return processNames; }
           set { processNames = value; }
       }
       private string[] processNames;

       /// <summary>
       /// This parameter overrides the ShouldContinue call to force
       /// the cmdlet to stop its operation. This parameter should always
       /// be used with caution.
       /// </summary>
       [Parameter]
       public SwitchParameter Force
       {
           get { return force; }
           set { force = value; }
       }
       private bool force;

       /// <summary>
       /// This parameter indicates that the cmdlet should return
       /// an object to the pipeline after the processing has been
       /// completed.
       /// </summary>
       [Parameter]
       public SwitchParameter PassThru
       {
           get { return passThru; }
           set { passThru = value; }
       }
       private bool passThru;

       #endregion Parameters

       #region Cmdlet Overrides

       /// <summary>
       /// The ProcessRecord method does the following for each of the
       /// requested process names:
       /// 1) Check that the process is not a critical process.
       /// 2) Attempt to stop that process.
       /// If no process is requested then nothing occurs.
       /// </summary>
       protected override void ProcessRecord()
       {
           foreach (string name in processNames)
           {
               // For every process name passed to the cmdlet, get the associated
               // processes.
               // Write a nonterminating error for failure to retrieve
               // a process.
               Process[] processes;

               try
               {
                   processes = Process.GetProcessesByName(name);
               }
               catch (InvalidOperationException ioe)
               {
                   WriteError(new ErrorRecord(ioe,"UnableToAccessProcessByName",
                       ErrorCategory.InvalidOperation, name));

                   continue;
               }

               // Try to stop the processes that have been retrieved.
               foreach (Process process in processes)
               {
                   string processName;

                   try
                   {
                       processName = process.ProcessName;
                   }
                   catch (Win32Exception e)
                   {
                      WriteError(new ErrorRecord(e, "ProcessNameNotFound",
                                           ErrorCategory.ReadError, process));
                      continue;
                   }

                   // Confirm the operation with the user first.
                   // This is always false if the WhatIf parameter is set.
                   if (!ShouldProcess(string.Format(CultureInfo.CurrentCulture,"{0} ({1})", processName,
                               process.Id)))
                   {
                       continue;
                   }

                   // Make sure that the user really wants to stop a critical
                   // process that could possibly stop the computer.
                   bool criticalProcess =
                       criticalProcessNames.Contains(processName.ToLower(CultureInfo.CurrentCulture));

                   if (criticalProcess &&!force)
                   {
                       string message = String.Format
                           (CultureInfo.CurrentCulture,
                                "The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
                                    processName);

                       // It is possible that the ProcessRecord method is called
                       // multiple times when objects are received as inputs from
                       // the pipeline. So to retain YesToAll and NoToAll input that
                       // the user may enter across multiple calls to this function,
                       // they are stored as private members of the cmdlet.
                       if (!ShouldContinue(message, "Warning!",
                                               ref yesToAll, ref noToAll))
                       {
                           continue;
                       }
                   } // if (criticalProcess...

                   // Stop the named process.
                   try
                   {
                       process.Kill();
                   }
                   catch (Exception e)
                   {
                       if ((e is Win32Exception) || (e is SystemException) ||
                          (e is InvalidOperationException))
                       {
                           // This process could not be stopped so write
                           // a nonterminating error.
                           WriteError(new ErrorRecord(e, "CouldNotStopProcess",
                                           ErrorCategory.CloseError, process));
                           continue;
                       } // if ((e is...
                       else throw;
                   } // catch

                   // If the PassThru parameter is
                   // specified, return the terminated process.
                   if (passThru)
                   {
                       WriteObject(process);
                   }
               } // foreach (Process...
           } // foreach (string...
       } // ProcessRecord

       #endregion Cmdlet Overrides

       #region Private Data

       private bool yesToAll, noToAll;

       /// <summary>
       /// Partial list of critical processes that should not be
       /// stopped.  Lower case is used for case insensitive matching.
       /// </summary>
       private ArrayList criticalProcessNames = new ArrayList(
          new string[] { "system", "winlogon", "spoolsv" }
       );

       #endregion Private Data

   } // StopProcCommand

   #endregion StopProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="5b4b4-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5b4b4-129">See Also</span></span>

[<span data-ttu-id="5b4b4-130">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5b4b4-130">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)