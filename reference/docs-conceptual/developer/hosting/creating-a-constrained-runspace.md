---
title: 创建受限的运行空间 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59125e65-7030-40bb-9926-756120b2d952
caps.latest.revision: 5
ms.openlocfilehash: 20ac1e2af8e047b8b572d86a55439676aa8df25c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367646"
---
# <a name="creating-a-constrained-runspace"></a><span data-ttu-id="cda86-102">创建受限运行空间</span><span class="sxs-lookup"><span data-stu-id="cda86-102">Creating a constrained runspace</span></span>

<span data-ttu-id="cda86-103">出于性能或安全方面的考虑，可能需要限制可用于主机应用程序的 Windows PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="cda86-103">For performance or security reasons, you might want to restrict the Windows PowerShell commands available to your host application.</span></span> <span data-ttu-id="cda86-104">要执行此操作，请通过调用[Initialsessionstate \*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create)方法来创建一个空的[Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) ，然后仅添加所需的命令，然后再添加即可.</span><span class="sxs-lookup"><span data-stu-id="cda86-104">To do this you create an empty [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) by calling the [System.Management.Automation.Runspaces.Initialsessionstate.Create\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) method, and then add only the commands you want available.</span></span>

 <span data-ttu-id="cda86-105">使用仅加载您指定的命令的运行空间可显著提高性能。</span><span class="sxs-lookup"><span data-stu-id="cda86-105">Using a runspace that loads only the commands that you specify provides significantly improved performance.</span></span>

 <span data-ttu-id="cda86-106">你可以使用[Sessionstatecmdletentry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry)类的方法来定义初始会话状态的 cmdlet）。</span><span class="sxs-lookup"><span data-stu-id="cda86-106">You use the methods of the [System.Management.Automation.Runspaces.Sessionstatecmdletentry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) class to define cmdlets for the initial session state.</span></span>

 <span data-ttu-id="cda86-107">你还可以将命令设置为私有。</span><span class="sxs-lookup"><span data-stu-id="cda86-107">You can also make commands private.</span></span> <span data-ttu-id="cda86-108">专用命令可由主机应用程序使用，但不能由应用程序的用户使用。</span><span class="sxs-lookup"><span data-stu-id="cda86-108">Private commands can be used by the host application, but not by users of the application.</span></span>

## <a name="adding-commands-to-an-empty-runspace"></a><span data-ttu-id="cda86-109">将命令添加到空的运行空间</span><span class="sxs-lookup"><span data-stu-id="cda86-109">Adding commands to an empty runspace</span></span>

 <span data-ttu-id="cda86-110">下面的示例演示如何创建一个空的 InitialSessionState 并向其中添加命令。</span><span class="sxs-lookup"><span data-stu-id="cda86-110">The following example demonstrates how to create an empty InitialSessionState and add commands to it.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using Microsoft.PowerShell.Commands;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for the application.
  /// </summary>
  internal class Runspace10b
  {
    /// <summary>
    /// This sample shows how to create an empty initial session state,
    /// how to add commands to the session state, and then how to create a
    /// runspace that has only those two commands. A PowerShell object
    /// is used to run the Get-Command cmdlet to show that only two commands
    /// are available.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    private static void Main(string[] args)
    {
      // Create an empty InitialSessionState and then add two commands.
      InitialSessionState iss = InitialSessionState.Create();

      // Add the Get-Process and Get-Command cmdlets to the session state.
      SessionStateCmdletEntry ssce1 = new SessionStateCmdletEntry(
                                                            "get-process",
                                                            typeof(GetProcessCommand),
                                                            null);
      iss.Commands.Add(ssce1);

      SessionStateCmdletEntry ssce2 = new SessionStateCmdletEntry(
                                                            "get-command",
                                                            typeof(GetCommandCommand),
                                                            null);
      iss.Commands.Add(ssce2);

      // Create a runspace.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunSpace.Open();
        using (PowerShell powershell = PowerShell.Create())
        {
          powershell.Runspace = myRunSpace;

          // Create a pipeline with the Get-Command command.
          powershell.AddCommand("get-command");

          Collection<PSObject> results = powershell.Invoke();

          Console.WriteLine("Verb                 Noun");
          Console.WriteLine("----------------------------");

          // Display each result object.
          foreach (PSObject result in results)
          {
            Console.WriteLine(
                             "{0,-20} {1}",
                             result.Members["verb"].Value,
                             result.Members["Noun"].Value);
          }
        }

        // Close the runspace and release any resources.
        myRunSpace.Close();
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="making-commands-private"></a><span data-ttu-id="cda86-111">使命令私有</span><span class="sxs-lookup"><span data-stu-id="cda86-111">Making commands private</span></span>

 <span data-ttu-id="cda86-112">你还可以通过将命令的[Commandinfo](/dotnet/api/System.Management.Automation.CommandInfo.Visibility)属性设置为 private，使其成为私有命令。 [SessionStateEntryVisibility](/dotnet/api/System.Management.Automation.SessionStateEntryVisibility) **私有**。</span><span class="sxs-lookup"><span data-stu-id="cda86-112">You can also make a command private, by setting it's [System.Management.Automation.Commandinfo.Visibility](/dotnet/api/System.Management.Automation.CommandInfo.Visibility) property to [System.Management.Automation.SessionStateEntryVisibility](/dotnet/api/System.Management.Automation.SessionStateEntryVisibility) **Private**.</span></span> <span data-ttu-id="cda86-113">宿主应用程序和其他命令可以调用该命令，但应用程序的用户不能。</span><span class="sxs-lookup"><span data-stu-id="cda86-113">The host application and other commands can call that command, but the user of the application cannot.</span></span> <span data-ttu-id="cda86-114">在下面的示例中， [get-childitem](/powershell/module/Microsoft.PowerShell.Management/Get-ChildItem)命令是私有的。</span><span class="sxs-lookup"><span data-stu-id="cda86-114">In the following example, the [Get-ChildItem](/powershell/module/Microsoft.PowerShell.Management/Get-ChildItem) command is private.</span></span>

```csharp
defaultSessionState = InitialSessionState.CreateDefault();
commandIndex = GetIndexOfEntry(defaultSessionState.Commands, "get-childitem");
defaultSessionState.Commands[commandIndex].Visibility = SessionStateEntryVisibility.Private;

this.runspace = RunspaceFactory.CreateRunspace(defaultSessionState);
this.runspace.Open();
```

## <a name="see-also"></a><span data-ttu-id="cda86-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cda86-115">See Also</span></span>

 [<span data-ttu-id="cda86-116">创建 InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="cda86-116">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)