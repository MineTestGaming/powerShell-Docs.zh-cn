---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 适用于 Linux nxFile 资源的 DSC
ms.openlocfilehash: 80969ba2ea6247fcd616a301d951403a840c851d
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047218"
---
# <a name="dsc-for-linux-nxfile-resource"></a><span data-ttu-id="dd4ef-103">适用于 Linux nxFile 资源的 DSC</span><span class="sxs-lookup"><span data-stu-id="dd4ef-103">DSC for Linux nxFile Resource</span></span>

<span data-ttu-id="dd4ef-104">PowerShell Desired State Configuration (DSC) 中的 nxFile 资源提供了管理 Linux 节点上的文件和目录的机制。</span><span class="sxs-lookup"><span data-stu-id="dd4ef-104">The **nxFile** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and directories on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="dd4ef-105">语法</span><span class="sxs-lookup"><span data-stu-id="dd4ef-105">Syntax</span></span>

```
nxFile <string> #ResourceName
{
    DestinationPath = <string>
    [ SourcePath = <string> ]
    [ Ensure = <string> { Absent | Present }  ]
    [ Type = <string> { directory | file | link } ]
    [ Contents = <string> ]
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Recurse = <bool> ]
    [ Force = <bool> ]
    [ Links = <string> { follow | manage } ]
    [ Group = <string> ]
    [ Mode = <string> ]
    [ Owner = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="dd4ef-106">“属性”</span><span class="sxs-lookup"><span data-stu-id="dd4ef-106">Properties</span></span>

|  <span data-ttu-id="dd4ef-107">属性</span><span class="sxs-lookup"><span data-stu-id="dd4ef-107">Property</span></span> |  <span data-ttu-id="dd4ef-108">说明</span><span class="sxs-lookup"><span data-stu-id="dd4ef-108">Description</span></span> |
|---|---|
| <span data-ttu-id="dd4ef-109">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="dd4ef-109">DestinationPath</span></span>| <span data-ttu-id="dd4ef-110">指定你想确保其中文件或目录状态的位置。</span><span class="sxs-lookup"><span data-stu-id="dd4ef-110">Specifies the location where you want to ensure the state for a file or directory.</span></span>|
| <span data-ttu-id="dd4ef-111">SourcePath</span><span class="sxs-lookup"><span data-stu-id="dd4ef-111">SourcePath</span></span>| <span data-ttu-id="dd4ef-112">指定要从其中复制文件或文件夹资源的路径。</span><span class="sxs-lookup"><span data-stu-id="dd4ef-112">Specifies the path from which to copy the file or folder resource.</span></span> <span data-ttu-id="dd4ef-113">此路径可以是本地路径，或者 `http/https/ftp` URL。</span><span class="sxs-lookup"><span data-stu-id="dd4ef-113">This path may be a local path, or an `http/https/ftp` URL.</span></span> <span data-ttu-id="dd4ef-114">只有在 **Type** 属性的值为文件时，才支持远程 `http/https/ftp` URL。</span><span class="sxs-lookup"><span data-stu-id="dd4ef-114">Remote `http/https/ftp` URLs are only supported when the value of the **Type** property is file.</span></span>|
| <span data-ttu-id="dd4ef-115">Ensure</span><span class="sxs-lookup"><span data-stu-id="dd4ef-115">Ensure</span></span>| <span data-ttu-id="dd4ef-116">确定是否要检查该文件是否存在。</span><span class="sxs-lookup"><span data-stu-id="dd4ef-116">Determines whether to check if the file exists.</span></span> <span data-ttu-id="dd4ef-117">将此属性设置为“Present”可确保该文件存在。</span><span class="sxs-lookup"><span data-stu-id="dd4ef-117">Set this property to "Present" to ensure the file exists.</span></span> <span data-ttu-id="dd4ef-118">将其设置为“Absent”可确保该文件不存在。</span><span class="sxs-lookup"><span data-stu-id="dd4ef-118">Set it to "Absent" to ensure the file does not exist.</span></span> <span data-ttu-id="dd4ef-119">默认值为“Present”。</span><span class="sxs-lookup"><span data-stu-id="dd4ef-119">The default value is "Present".</span></span>|
| <span data-ttu-id="dd4ef-120">类型</span><span class="sxs-lookup"><span data-stu-id="dd4ef-120">Type</span></span>| <span data-ttu-id="dd4ef-121">指定正在配置的资源是目录还是文件。</span><span class="sxs-lookup"><span data-stu-id="dd4ef-121">Specifies whether the resource being configured is a directory or a file.</span></span> <span data-ttu-id="dd4ef-122">将此属性设置为“directory”可指示该资源是一个目录。</span><span class="sxs-lookup"><span data-stu-id="dd4ef-122">Set this property to "directory" to indicate that the resource is a directory.</span></span> <span data-ttu-id="dd4ef-123">将其设置为“file”可指示该资源是一个文件。</span><span class="sxs-lookup"><span data-stu-id="dd4ef-123">Set it to "file" to indicate that the resource is a file.</span></span> <span data-ttu-id="dd4ef-124">默认值为“file”。</span><span class="sxs-lookup"><span data-stu-id="dd4ef-124">The default value is "file"</span></span>|
| <span data-ttu-id="dd4ef-125">目录</span><span class="sxs-lookup"><span data-stu-id="dd4ef-125">Contents</span></span>| <span data-ttu-id="dd4ef-126">指定文件的内容，例如特定字符串。</span><span class="sxs-lookup"><span data-stu-id="dd4ef-126">Specifies the contents of a file, such as a particular string.</span></span>|
| <span data-ttu-id="dd4ef-127">校验和</span><span class="sxs-lookup"><span data-stu-id="dd4ef-127">Checksum</span></span>| <span data-ttu-id="dd4ef-128">定义当确定两个文件是否相同时使用的类型。</span><span class="sxs-lookup"><span data-stu-id="dd4ef-128">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="dd4ef-129">如果未指定**校验和**，则只是文件或目录名用于比较。</span><span class="sxs-lookup"><span data-stu-id="dd4ef-129">If **Checksum** is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="dd4ef-130">值为：“ctime”、“mtime”或“md5”。</span><span class="sxs-lookup"><span data-stu-id="dd4ef-130">Values are: "ctime", "mtime", or "md5".</span></span>|
| <span data-ttu-id="dd4ef-131">Recurse</span><span class="sxs-lookup"><span data-stu-id="dd4ef-131">Recurse</span></span>| <span data-ttu-id="dd4ef-132">指示是否包含子目录。</span><span class="sxs-lookup"><span data-stu-id="dd4ef-132">Indicates if subdirectories are included.</span></span> <span data-ttu-id="dd4ef-133">将此属性设置为 **$true** 以指示你想要包含子目录。</span><span class="sxs-lookup"><span data-stu-id="dd4ef-133">Set this property to **$true** to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="dd4ef-134">默认值为 **$false**。</span><span class="sxs-lookup"><span data-stu-id="dd4ef-134">The default is **$false**.</span></span> <span data-ttu-id="dd4ef-135">**注意：** 此属性才有效**类型**属性设置为目录。</span><span class="sxs-lookup"><span data-stu-id="dd4ef-135">**Note:** This property is only valid when the **Type** property is set to directory.</span></span>|
| <span data-ttu-id="dd4ef-136">Force</span><span class="sxs-lookup"><span data-stu-id="dd4ef-136">Force</span></span>| <span data-ttu-id="dd4ef-137">某些文件操作（如覆盖文件或删除不为空的目录）将导致错误。</span><span class="sxs-lookup"><span data-stu-id="dd4ef-137">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="dd4ef-138">使用 **Force** 属性覆盖此类错误。</span><span class="sxs-lookup"><span data-stu-id="dd4ef-138">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="dd4ef-139">默认值为 **$false**。</span><span class="sxs-lookup"><span data-stu-id="dd4ef-139">The default value is **$false**.</span></span>|
| <span data-ttu-id="dd4ef-140">链接</span><span class="sxs-lookup"><span data-stu-id="dd4ef-140">Links</span></span>| <span data-ttu-id="dd4ef-141">指定符号链接的所需行为。</span><span class="sxs-lookup"><span data-stu-id="dd4ef-141">Specifies the desired behavior for symbolic links.</span></span> <span data-ttu-id="dd4ef-142">将此属性设置为“follow”可跟随符号链接，并对链接目标进行操作（例如</span><span class="sxs-lookup"><span data-stu-id="dd4ef-142">Set this property to "follow" to follow symbolic links and act on the links target (for example.</span></span> <span data-ttu-id="dd4ef-143">复制文件而不是链接）。</span><span class="sxs-lookup"><span data-stu-id="dd4ef-143">copy the file instead of the link).</span></span> <span data-ttu-id="dd4ef-144">将此属性设置为“manage”可对此链接进行操作（例如</span><span class="sxs-lookup"><span data-stu-id="dd4ef-144">Set this property to "manage" to act on the link (for example.</span></span> <span data-ttu-id="dd4ef-145">复制链接本身）。</span><span class="sxs-lookup"><span data-stu-id="dd4ef-145">copy the link itself).</span></span> <span data-ttu-id="dd4ef-146">将此属性设置为“ignore”可忽略符号链接。</span><span class="sxs-lookup"><span data-stu-id="dd4ef-146">Set this property to "ignore" to ignore symbolic links.</span></span>|
| <span data-ttu-id="dd4ef-147">组</span><span class="sxs-lookup"><span data-stu-id="dd4ef-147">Group</span></span>| <span data-ttu-id="dd4ef-148">拥有此文件或目录的**组**名称。</span><span class="sxs-lookup"><span data-stu-id="dd4ef-148">The name of the **Group** to own the file or directory.</span></span>|
| <span data-ttu-id="dd4ef-149">模式</span><span class="sxs-lookup"><span data-stu-id="dd4ef-149">Mode</span></span>| <span data-ttu-id="dd4ef-150">以八进制或符号表示法指定资源的所需权限。</span><span class="sxs-lookup"><span data-stu-id="dd4ef-150">Specifies the desired permissions for the resource, in octal or symbolic notation.</span></span> <span data-ttu-id="dd4ef-151">（例如，777 或 rwxrwxrwx）。</span><span class="sxs-lookup"><span data-stu-id="dd4ef-151">(for example, 777 or rwxrwxrwx).</span></span> <span data-ttu-id="dd4ef-152">如果使用符号表示法，不需提供指示文件或目录的第一个字符。</span><span class="sxs-lookup"><span data-stu-id="dd4ef-152">If using symbolic notation, do not provide the first character which indicates directory or file.</span></span>|
| <span data-ttu-id="dd4ef-153">DependsOn</span><span class="sxs-lookup"><span data-stu-id="dd4ef-153">DependsOn</span></span> | <span data-ttu-id="dd4ef-154">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="dd4ef-154">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="dd4ef-155">例如，如果你想要首先运行 **ID** 为 **ResourceName**、类型为 **ResourceType** 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="dd4ef-155">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="additional-information"></a><span data-ttu-id="dd4ef-156">其他信息</span><span class="sxs-lookup"><span data-stu-id="dd4ef-156">Additional Information</span></span>


<span data-ttu-id="dd4ef-157">Linux 和 Windows 在文本文件中默认使用不同的换行符，这可能会导致在 Linux 计算机上使用 __nxFile__ 配置某些文件时产生意外结果。</span><span class="sxs-lookup"><span data-stu-id="dd4ef-157">Linux and Windows use different line break characters in text files by default, and this can cause unexpected results when configuring some files on a Linux computer with __nxFile__.</span></span> <span data-ttu-id="dd4ef-158">有多种管理 Linux 文件内容，同时避免由意外换行符引起问题的方法：</span><span class="sxs-lookup"><span data-stu-id="dd4ef-158">There are multiple ways to manage the content of a Linux file while avoiding issues caused by unexpected line break characters:</span></span>

<span data-ttu-id="dd4ef-159">步骤 1：从远程源（http、https 或 ftp）中复制文件：使用所需内容在 Linux 上创建一个文件，并将其暂存于能够访问将配置节点的网页或 ftp 服务器上。</span><span class="sxs-lookup"><span data-stu-id="dd4ef-159">Step 1: Copy the file from a remote source (http, https, or ftp): create a file on Linux with the desired contents, and stage it on a web or ftp server accessible the node(s) you will configure.</span></span> <span data-ttu-id="dd4ef-160">然后使用该文件的 Web 或 ftp URL 在 __nxFile__ 资源中定义 __SourcePath__ 属性。</span><span class="sxs-lookup"><span data-stu-id="dd4ef-160">Define the __SourcePath__ property in the __nxFile__ resource with the web or ftp URL to the file.</span></span>

```
Import-DSCResource -Module nx
Node $Node
{
nxFile resolvConf
{
    SourcePath = "http://10.185.85.11/conf/resolv.conf"
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"
    Type = "file"

}

}
```


<span data-ttu-id="dd4ef-161">步骤 2：设置 __$OFS__ 属性以使用 Linux 换行符后，通过 [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) 来读取 PowerShell 脚本的内容。</span><span class="sxs-lookup"><span data-stu-id="dd4ef-161">Step 2: Read the file contents in the PowerShell script with [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) after setting the __$OFS__ property to use the Linux line-break character.</span></span>


```
Import-DSCResource -Module nx
Node $Node
{
$OFS = "`n"
$Contents = Get-Content C:\temp\resolv.conf

nxFile resolvConf
{
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"
    Type = "file"
    Contents = "$Contents"
}

}
```


<span data-ttu-id="dd4ef-162">步骤 3：使用 PowerShell 函数替换为的 Windows 与 Linux 换行字符的换行符。</span><span class="sxs-lookup"><span data-stu-id="dd4ef-162">Step 3: Use a PowerShell function to replace Windows line breaks with Linux line-break characters.</span></span>

```
Function LinuxString($inputStr){
    $outputStr = $inputStr.Replace("`r`n","`n")
    $ouputStr += "`n"
    Return $outputStr
}

Import-DSCResource -Module nx
Node $Node
{

$Contents = @'
search contoso.com
domain contoso.com
nameserver 10.185.85.11
'@

$Contents = LinuxString $Contents

nxFile resolvConf
{
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"
    Type = "file"
    Contents = $Contents

}
}
```

## <a name="example"></a><span data-ttu-id="dd4ef-163">示例</span><span class="sxs-lookup"><span data-stu-id="dd4ef-163">Example</span></span>

<span data-ttu-id="dd4ef-164">以下示例可确保目录 `/opt/mydir` 存在，并且具有指定内容的文件存在于此目录中。</span><span class="sxs-lookup"><span data-stu-id="dd4ef-164">The following example ensures that the directory `/opt/mydir` exists, and that a file with specified contents exists this directory.</span></span>

```
Import-DSCResource -Module nx

Node $node {
nxFile DirectoryExample
{
   Ensure = "Present"
   DestinationPath = "/opt/mydir"
   Type = "Directory"
}

nxFile FileExample
{
    Ensure = "Present"
    Destinationpath = "/opt/mydir/myfile"
    Contents=@"
#!/bin/bash`necho "hello world"`n
"@
    Mode = “755”
    DependsOn = "[nxFile]DirectoryExample"
}
}
```