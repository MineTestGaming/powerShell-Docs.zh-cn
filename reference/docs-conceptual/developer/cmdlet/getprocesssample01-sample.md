---
title: GetProcessSample01 示例 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 84956fbafdd58623ca4f332efc940fb93b421c6e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784242"
---
# <a name="getprocesssample01-sample"></a><span data-ttu-id="e4b23-102">GetProcessSample01 示例</span><span class="sxs-lookup"><span data-stu-id="e4b23-102">GetProcessSample01 Sample</span></span>

<span data-ttu-id="e4b23-103">此示例演示如何实现一个用于检索本地计算机上的进程的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e4b23-103">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="e4b23-104">此 cmdlet 是 `Get-Process` Windows PowerShell 2.0 提供的简化版本的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e4b23-104">This cmdlet is a simplified version of the `Get-Process` cmdlet that is provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="e4b23-105">如何使用 Visual Studio 生成示例。</span><span class="sxs-lookup"><span data-stu-id="e4b23-105">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="e4b23-106">安装 Windows PowerShell 2.0 SDK 后，导航到 GetProcessSample01 文件夹。</span><span class="sxs-lookup"><span data-stu-id="e4b23-106">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample01 folder.</span></span> <span data-ttu-id="e4b23-107">默认位置为 C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01。</span><span class="sxs-lookup"><span data-stu-id="e4b23-107">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01.</span></span>

2. <span data-ttu-id="e4b23-108">双击解决方案的图标 ( .sln) 文件。</span><span class="sxs-lookup"><span data-stu-id="e4b23-108">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="e4b23-109">这会在 Microsoft Visual Studio 中打开示例项目。</span><span class="sxs-lookup"><span data-stu-id="e4b23-109">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="e4b23-110">在“生成”菜单中选择“生成解决方案” 。</span><span class="sxs-lookup"><span data-stu-id="e4b23-110">In the **Build** menu, select **Build Solution**.</span></span>

  <span data-ttu-id="e4b23-111">示例库将在默认的 \bin 或 \bin\debug 文件夹中生成。</span><span class="sxs-lookup"><span data-stu-id="e4b23-111">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="e4b23-112">如何运行示例</span><span class="sxs-lookup"><span data-stu-id="e4b23-112">How to run the sample</span></span>

1. <span data-ttu-id="e4b23-113">打开命令提示符窗口。</span><span class="sxs-lookup"><span data-stu-id="e4b23-113">Open a Command Prompt window.</span></span>

2. <span data-ttu-id="e4b23-114">导航到包含示例 .dll 文件的目录。</span><span class="sxs-lookup"><span data-stu-id="e4b23-114">Navigate to the directory containing the sample .dll file.</span></span>

3. <span data-ttu-id="e4b23-115">运行 installutil.exe "GetProcessSample01.dll"。</span><span class="sxs-lookup"><span data-stu-id="e4b23-115">Run installutil "GetProcessSample01.dll".</span></span>

4. <span data-ttu-id="e4b23-116">启动 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="e4b23-116">Start Windows PowerShell.</span></span>

5. <span data-ttu-id="e4b23-117">运行以下命令，将管理单元添加到 shell 中。</span><span class="sxs-lookup"><span data-stu-id="e4b23-117">Run the following command to add the snap-in to the shell.</span></span>

   `Add-PSSnapin GetProcPSSnapIn01`

6. <span data-ttu-id="e4b23-118">输入以下命令以运行 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e4b23-118">Enter the following command to run the cmdlet.</span></span> `get-proc`

   `get-proc`

   <span data-ttu-id="e4b23-119">这是通过以下步骤生成的示例输出。</span><span class="sxs-lookup"><span data-stu-id="e4b23-119">This is a sample output that results from following these steps.</span></span>

   ```output
   Id              Name            State      HasMoreData     Location             Command
   --              ----            -----      -----------     --------             -------
   1               26932870-d3b... NotStarted False                                 Write-Host "A f...

   ```

   ```powershell
   Set-Content $env:temp\test.txt "This is a test file"
   ```

   ```output
   A file was created in the TEMP directory
   ```

## <a name="requirements"></a><span data-ttu-id="e4b23-120">要求</span><span class="sxs-lookup"><span data-stu-id="e4b23-120">Requirements</span></span>

<span data-ttu-id="e4b23-121">此示例需要 Windows PowerShell 1.0 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="e4b23-121">This sample requires Windows PowerShell 1.0 or later.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="e4b23-122">演示</span><span class="sxs-lookup"><span data-stu-id="e4b23-122">Demonstrates</span></span>

<span data-ttu-id="e4b23-123">此示例演示以下各项。</span><span class="sxs-lookup"><span data-stu-id="e4b23-123">This sample demonstrates the following.</span></span>

- <span data-ttu-id="e4b23-124">创建基本的示例 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e4b23-124">Creating a basic sample cmdlet.</span></span>

- <span data-ttu-id="e4b23-125">使用 Cmdlet 特性定义 cmdlet 类。</span><span class="sxs-lookup"><span data-stu-id="e4b23-125">Defining a cmdlet class by using the Cmdlet attribute.</span></span>

- <span data-ttu-id="e4b23-126">创建适用于 Windows PowerShell 1.0 和 Windows PowerShell 2.0 的管理单元。</span><span class="sxs-lookup"><span data-stu-id="e4b23-126">Creating a snap-in that works with both Windows PowerShell 1.0 and Windows PowerShell 2.0.</span></span> <span data-ttu-id="e4b23-127">后续示例使用模块，而不是管理单元，因此它们需要 Windows PowerShell 2.0。</span><span class="sxs-lookup"><span data-stu-id="e4b23-127">Subsequent samples use modules instead of snap-ins so they require Windows PowerShell 2.0.</span></span>

## <a name="example"></a><span data-ttu-id="e4b23-128">示例</span><span class="sxs-lookup"><span data-stu-id="e4b23-128">Example</span></span>

<span data-ttu-id="e4b23-129">此示例演示如何创建一个简单的 cmdlet 及其管理单元。</span><span class="sxs-lookup"><span data-stu-id="e4b23-129">This sample shows how to create a simple cmdlet and its snap-in.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;             //Windows PowerShell namespace
using System.ComponentModel;

namespace Microsoft.Samples.PowerShell.Commands
{

   #region GetProcCommand

   /// <summary>
   /// This class implements the Get-Proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc")]
   public class GetProcCommand : Cmdlet
   {
      #region Cmdlet Overrides

      /// <summary>
      /// The ProcessRecord method calls the Process.GetProcesses
      /// method to retrieve the processes of the local computer.
      /// Then, the WriteObject method writes the associated processes
      /// to the pipeline.
      /// </summary>
      protected override void ProcessRecord()
      {
         // Retrieve the current processes.
         Process[] processes = Process.GetProcesses();

         // Write the processes to the pipeline to make them available
         // to the next cmdlet. The second argument (true) tells Windows
         // PowerShell to enumerate the array and to send one process
         // object at a time to the pipeline.
         WriteObject(processes, true);
      }

      #endregion Overrides

   } //GetProcCommand

   #endregion GetProcCommand

   #region PowerShell snap-in

   /// <summary>
   /// Create this sample as an PowerShell snap-in
   /// </summary>
   [RunInstaller(true)]
   public class GetProcPSSnapIn01 : PSSnapIn
   {
       /// <summary>
       /// Create an instance of the GetProcPSSnapIn01
       /// </summary>
       public GetProcPSSnapIn01()
           : base()
       {
       }

       /// <summary>
       /// Get a name for this PowerShell snap-in. This name will be used in registering
       /// this PowerShell snap-in.
       /// </summary>
       public override string Name
       {
           get
           {
               return "GetProcPSSnapIn01";
           }
       }

       /// <summary>
       /// Vendor information for this PowerShell snap-in.
       /// </summary>
       public override string Vendor
       {
           get
           {
               return "Microsoft";
           }
       }

       /// <summary>
       /// Gets resource information for vendor. This is a string of format:
       /// resourceBaseName,resourceName.
       /// </summary>
       public override string VendorResource
       {
           get
           {
               return "GetProcPSSnapIn01,Microsoft";
           }
       }

       /// <summary>
       /// Description of this PowerShell snap-in.
       /// </summary>
       public override string Description
       {
           get
           {
               return "This is a PowerShell snap-in that includes the get-proc cmdlet.";
           }
       }
   }

   #endregion PowerShell snap-in
}
```

## <a name="see-also"></a><span data-ttu-id="e4b23-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e4b23-130">See Also</span></span>

[<span data-ttu-id="e4b23-131">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e4b23-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
