---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 使用文件和文件夹
description: 本文介绍如何使用 PowerShell 处理特定文件和文件夹操作任务。
ms.openlocfilehash: c0c3abb082b05296daa480ac06bcbfa3a784e0c9
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500022"
---
# <a name="working-with-files-and-folders"></a>使用文件和文件夹

在 Windows PowerShell 驱动器中导航和操作其上面的项类似于操作 Windows 物理磁盘驱动器上的文件和文件夹。 本文介绍如何使用 PowerShell 处理特定文件和文件夹操作任务。

## <a name="listing-all-the-files-and-folders-within-a-folder"></a>列出某个文件夹内的所有文件和文件夹

可以使用 `Get-ChildItem` 来直接获取文件夹中的所有项。 添加可选的 **Force** 参数以显示隐藏项或系统项。 例如，此命令将显示 Windows PowerShell 驱动器 C（它与 Windows 物理驱动器 C 相同）的直观内容：

```powershell
Get-ChildItem -Path C:\ -Force
```

此命令只列出直接包含的项，很像使用 `Cmd.exe` 的 `DIR` 命令或 UNIX shell 中的 `ls`。 为了显示包含的项，还需要指定 `-Recurse` 参数。 （这可能需要相当长的时间才能完成。）列出 C 驱动器上的所有内容：

```powershell
Get-ChildItem -Path C:\ -Force -Recurse
```

`Get-ChildItem` 可以使用 Path  、Filter  、Include  和 Exclude  参数来筛选项，但这些通常只以名称为依据。 使用 `Where-Object`，还可以执行基于项的其他属性的复杂筛选。

下面的命令用于查找上次于 2005 年 10 月 1 日之后修改，并且不小于 1 兆字节，也不大于 10 兆字节的 Program Files 文件夹中的所有可执行文件：

```powershell
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt '2005-10-01') -and ($_.Length -ge 1mb) -and ($_.Length -le 10mb)}
```

## <a name="copying-files-and-folders"></a>复制文件和文件夹

复制通过 `Copy-Item` 完成。 以下命令用于将 C:\\boot.ini 备份到 C:\\boot.bak：

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak
```

如果目标文件已存在，则复制尝试失败。 若要覆盖预先存在的目标，请使用 Force 参数  ：

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak -Force
```

即使当目标为只读时，该命令也有效。

复制文件夹的操作方式与此相同。 以下命令以递归方式将文件夹 `C:\temp\test1` 复制到新文件夹 `C:\temp\DeleteMe`：

```powershell
Copy-Item C:\temp\test1 -Recurse C:\temp\DeleteMe
```

还可以复制选定的项。 以下命令将 `C:\data` 中任意位置包含的所有 .txt 文件都复制到 `C:\temp\text`：

```powershell
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination C:\temp\text
```

你仍然可以使用其他工具执行文件系统复制。 XCOPY、ROBOCOPY 和 COM 对象（如 **Scripting.FileSystemObject** ）都适用于 Windows PowerShell。 例如，可以使用 Windows 脚本宿主 Scripting.FileSystem COM  类将 `C:\boot.ini` 备份到 `C:\boot.bak`：

```powershell
(New-Object -ComObject Scripting.FileSystemObject).CopyFile('C:\boot.ini', 'C:\boot.bak')
```

## <a name="creating-files-and-folders"></a>创建文件和文件夹

创建新项的操作方式在所有 Windows PowerShell 提供程序上都相同。 如果某个 Windows PowerShell 提供程序具有多个类型的项（例如，用于区分目录和文件的 FileSystem Windows PowerShell 提供程序），则需要指定项类型。

以下命令新建文件夹 `C:\temp\New Folder`：

```powershell
New-Item -Path 'C:\temp\New Folder' -ItemType Directory
```

以下命令新建空的文件 `C:\temp\New Folder\file.txt`

```powershell
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType File
```

> [!IMPORTANT]
> 结合使用 Force  开关与 `New-Item` 命令来创建文件夹时，如果文件夹已存在，则不会  覆盖或替换此文件夹。 它会直接返回现有的文件夹对象。 不过，如果对已存在的文件使用 `New-Item -Force`，此文件  会被完全覆盖。

## <a name="removing-all-files-and-folders-within-a-folder"></a>删除某个文件夹内的所有文件和文件夹

可以使用 `Remove-Item` 来删除包含的项，但如果项包含其他任何内容，系统就会提示你确认是否要删除。 例如，如果尝试删除包含其他项的文件夹 `C:\temp\DeleteMe`，则在删除此文件夹前，Windows PowerShell 会提示你确认是否要删除：

```
Remove-Item -Path C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the Recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

如果不希望系统针对每个包含的项都提示你，则指定 **Recurse** 参数：

```powershell
Remove-Item -Path C:\temp\DeleteMe -Recurse
```

## <a name="mapping-a-local-folder-as-a-drive"></a>将本地文件夹映射为驱动器

还可以使用 `New-PSDrive` 命令来映射本地文件夹。 以下命令在本地 Program Files 目录中的根位置创建本地驱动器 `P:`（只在 PowerShell 会话中可见）：

```powershell
New-PSDrive -Name P -Root $env:ProgramFiles -PSProvider FileSystem
```

正如网络驱动器一样，在 Windows PowerShell 内映射的驱动器将对 Windows PowerShell shell 立即可见。 若要创建在文件资源管理器中可见的映射驱动器，需要使用参数 `-Persist`。 但是，只有远程路径才能与 Persist 一起使用。

## <a name="reading-a-text-file-into-an-array"></a>将文本文件数据读取到数组中

文本数据更常见的存储格式之一是采用文件形式，其中单独的行被视为不同的数据元素。 `Get-Content` cmdlet 可用于一步读取整个文件，如下所示：

```
PS> Get-Content -Path C:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"
 /noexecute=AlwaysOff /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS=" Microsoft Windows XP Professional
with Data Execution Prevention" /noexecute=optin /fastdetect
```

`Get-Content` 已将从文件读取的数据视为数组，其中每行文件内容为一个元素。 可以通过检查返回的内容的 **长度** 来确认此点：

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

此命令对于直接从 Windows PowerShell 获取列表信息最为有用。 例如，你可能会在文件 `C:\temp\domainMembers.txt` 中存储计算机名或 IP 地址的列表，文件的每一行上都有一个名称。 可以使用 `Get-Content` 来检索文件内容，并将它们放置在变量 `$Computers` 中：

```powershell
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

`$Computers` 现在是数组，其中每个元素包含一个计算机名。
