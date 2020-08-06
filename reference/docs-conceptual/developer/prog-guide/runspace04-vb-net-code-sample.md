---
title: RunSpace04 (VB.NET) 代码示例 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 853e3d223843fb39b2e6a08a21d041a5e696ce2c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784752"
---
# <a name="runspace04--vbnet-code-sample"></a><span data-ttu-id="ca455-102">RunSpace04 (VB.NET) 代码示例</span><span class="sxs-lookup"><span data-stu-id="ca455-102">RunSpace04  (VB.NET) Code Sample</span></span>

<span data-ttu-id="ca455-103">下面是 Runspace04 示例的 VB.NET 源代码。</span><span class="sxs-lookup"><span data-stu-id="ca455-103">Here is the VB.NET source code for the Runspace04 sample.</span></span> <span data-ttu-id="ca455-104">此示例使用[Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke)类来执行生成终止错误的脚本。</span><span class="sxs-lookup"><span data-stu-id="ca455-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that generates a terminating error.</span></span> <span data-ttu-id="ca455-105">宿主应用程序负责捕获错误并解释错误记录。</span><span class="sxs-lookup"><span data-stu-id="ca455-105">The host application is responsible for catching the error and interpreting the error record.</span></span>

> [!NOTE]
> <span data-ttu-id="ca455-106">您可以使用适用于 Windows Vista 的 Windows 软件开发工具包和 Microsoft .NET Framework 3.0 运行时组件) 为此示例下载 VB.NET (源文件。</span><span class="sxs-lookup"><span data-stu-id="ca455-106">You can download the VB.NET source file (runspace02.vb) for this sample by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="ca455-107">有关下载说明，请参阅[如何安装 Windows powershell 和下载 Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk)。</span><span class="sxs-lookup"><span data-stu-id="ca455-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="ca455-108">下载的源文件在目录中提供 **\<PowerShell Samples>** 。</span><span class="sxs-lookup"><span data-stu-id="ca455-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="ca455-109">代码示例</span><span class="sxs-lookup"><span data-stu-id="ca455-109">Code Sample</span></span>

```vb
Imports System
Imports System.Collections
Imports System.Collections.Generic
Imports System.Collections.ObjectModel
Imports System.Text
Imports Microsoft.VisualBasic
Imports System.Management.Automation
Imports System.Management.Automation.Host
Imports System.Management.Automation.Runspaces

Namespace Microsoft.Samples.PowerShell.Runspaces

    Class Runspace04

        ''' <summary>
        ''' This sample uses the RunspaceInvoke class to execute
        ''' a script. This script will generate a terminating
        ''' exception that the caller should catch and process.
        ''' </summary>
        ''' <param name="args">Unused</param>
        ''' <remarks>
        ''' This sample demonstrates the following:
        ''' 1. Creating an instance of the RunspaceInvoke class.
        ''' 2. Using this instance to execute a string as a PowerShell script.
        ''' 3. Passing input objects to the script from the calling program.
        ''' 4. Using PSObject to extract and display properties from the objects
        '''    returned by this command.
        ''' 5. Retrieving and displaying error records that may be generated
        '''    during the execution of that script.
        ''' 6. Catching and displaying terminating exceptions generated
        '''    by the script being run.
        ''' </remarks>
        Shared Sub Main(ByVal args() As String)
            ' Define a list of patterns to use in matching
            ' Note that the fourth pattern is not a valid regular
            ' expression so it will cause a terminating exception to
            ' be thrown when used in select-string.
            Dim patterns() As String = {"aa", "bc", "ab*c", "*", "abc"}

            ' The script to run to use the patterns. Input passed
            ' to the script will be available in the $input variable.
            Dim script As String = "$input | where {" & _
                " select-string $_ -inputobject 'abc' }"

            ' Create an instance of the RunspaceInvoke class.
            Dim invoker As New RunspaceInvoke()

            ' Invoke the runspace. Because of the bad regular expression,
            ' no objects will be returned. Instead, an exception will be
            ' thrown.
            Try
                Dim errors As System.Collections.IList = Nothing
                Dim result As PSObject
                For Each result In invoker.Invoke(script, patterns, errors)
                    Console.WriteLine("'{0}'", result.ToString())
                Next result

                ' Now process any error records that were generated
                ' while running the script.
                Console.WriteLine(vbCrLf & _
                    "The following non-terminating errors occurred:" & vbCrLf)
                If Not (errors Is Nothing) AndAlso errors.Count > 0 Then
                    Dim err As PSObject
                    For Each err In errors
                        System.Console.WriteLine("    error: {0}", err.ToString())
                    Next err
                End If
            Catch runtimeException As RuntimeException
                ' Trap any exception generated by the script. These exceptions
                ' will all be derived from RuntimeException.
                System.Console.WriteLine("Runtime exception: {0}: {1}" & _
                   vbCrLf + "{2}", _
                   runtimeException.ErrorRecord.InvocationInfo.InvocationName, _
                   runtimeException.Message, _
                   runtimeException.ErrorRecord.InvocationInfo.PositionMessage)
            End Try

            System.Console.WriteLine(vbCrLf + "Hit any key to exit...")
            System.Console.ReadKey()

        End Sub 'Main
    End Class 'Runspace04

End Namespace
```

<!-- TODO!!!: [!code-csharp[Runspace04.vb](../../powershell-sdk-samples/SDK-2.0/vb/Runspace01/Runspace04.vb#L09-L92 "Runspace04.vb")] -->

## <a name="see-also"></a><span data-ttu-id="ca455-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ca455-110">See Also</span></span>

[<span data-ttu-id="ca455-111">Windows PowerShell 程序员指南</span><span class="sxs-lookup"><span data-stu-id="ca455-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="ca455-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ca455-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
