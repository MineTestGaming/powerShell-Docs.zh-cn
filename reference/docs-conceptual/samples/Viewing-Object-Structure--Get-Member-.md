---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 查看对象结构 (Get Member)
description: Get-Member 是一种功能强大的工具，借助它可查看 PowerShell 中对象的类型和结构。
ms.openlocfilehash: 3c294fe47294e2cf8daf125aac55661dd38cf9bb
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501212"
---
# <a name="viewing-object-structure-get-member"></a>查看对象结构 (Get-Member)

由于对象在 Windows PowerShell 中扮演了如此重要的角色，因此存在几个用于处理任意对象类型的本机命令。 最重要的一个是 **Get-Member** 命令。

分析命令返回的对象的最简单方法是通过管道将该命令的输出传递到 **Get-Member** cmdlet。 **Get-Member** cmdlet 向你显示对象类型的正式名称及其成员的完整列表。 有时返回的元素数目可能非常巨大。 例如，一个进程对象可以拥有 100 多个成员。

若要查看进程对象的所有成员并分页显示输出，以便于你可以全部查看，请键入：

```powershell
Get-Process | Get-Member | Out-Host -Paging
```

此命令的输出将如下所示：

```Output
TypeName: System.Diagnostics.Process

Name                           MemberType     Definition
----                           ----------     ----------
Handles                        AliasProperty  Handles = Handlecount
Name                           AliasProperty  Name = ProcessName
NPM                            AliasProperty  NPM = NonpagedSystemMemorySize
PM                             AliasProperty  PM = PagedMemorySize
VM                             AliasProperty  VM = VirtualMemorySize
WS                             AliasProperty  WS = WorkingSet
add_Disposed                   Method         System.Void add_Disposed(Event...
...
```

我们可以通过筛选想要查看的元素，让这个冗长的信息列表更易于使用。 **Get-Member** 命令仅允许你列出属性成员。 属性的形式有数种。 如果将 Get-Member MemberType 参数设置为值属性，则 cmdlet 将显示任何类型的属性  。 生成的列表仍会很长，但较之前更易于管理：

```
PS> Get-Process | Get-Member -MemberType Properties

   TypeName: System.Diagnostics.Process

Name                       MemberType     Definition
----                       ----------     ----------
Handles                    AliasProperty  Handles = Handlecount
Name                       AliasProperty  Name = ProcessName
...
ExitCode                   Property       System.Int32 ExitCode {get;}
...
Handle                     Property       System.IntPtr Handle {get;}
...
CPU                        ScriptProperty System.Object CPU {get=$this.Total...
...
Path                       ScriptProperty System.Object Path {get=$this.Main...
...
```

> [!NOTE]
> MemberType 的允许值有 AliasProperty、CodeProperty、Property、NoteProperty、ScriptProperty、Properties、PropertySet、Method、CodeMethod、ScriptMethod、Methods、ParameterizedProperty、MemberSet 以及 All。

一个进程有 60 多个属性。 对于任何已知的对象，Windows PowerShell 通常仅显示少许属性，这是因为显示所有属性会导致产生无法管理的信息量。

> [!NOTE]
> Windows PowerShell 通过使用存储在以 .format.ps1xml 结尾的 XML 文件中的信息来决定某种类型的对象的显示方式。 进程对象（即 .NET System.Diagnostics.Process 对象）的格式设置数据存储在 DotNetTypes.format.ps1xml 中。

如果需要查看 Windows PowerShell 默认显示的属性之外的属性，则需要自己对输出数据进行格式化。 这可以通过使用格式 cmdlet 实现。
