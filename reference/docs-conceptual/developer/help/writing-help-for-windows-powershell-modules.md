---
title: 编写 PowerShell 模块的帮助
ms.date: 04/10/2020
ms.openlocfilehash: 2c6450c03fb9847de331605fb6b9bfb203af3d89
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811456"
---
# <a name="writing-help-for-powershell-modules"></a><span data-ttu-id="6db92-102">编写 PowerShell 模块的帮助</span><span class="sxs-lookup"><span data-stu-id="6db92-102">Writing Help for PowerShell Modules</span></span>

<span data-ttu-id="6db92-103">PowerShell 模块可以包含有关模块和模块成员（例如 cmdlet、提供程序、函数和脚本）的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="6db92-103">PowerShell modules can include Help topics about the module and about the module members, such as cmdlets, providers, functions and scripts.</span></span> <span data-ttu-id="6db92-104">Cmdlet 以与 `Get-Help` 显示其他 PowerShell 项的帮助相同的格式显示模块帮助主题，用户使用标准 `Get-Help` 命令来获取帮助主题。</span><span class="sxs-lookup"><span data-stu-id="6db92-104">The `Get-Help` cmdlet displays the module Help topics in the same format as it displays Help for other PowerShell items, and users use standard `Get-Help` commands to get the Help topics.</span></span>

<span data-ttu-id="6db92-105">本文档说明了模块帮助主题的格式和正确位置，并建议了模块帮助内容的准则。</span><span class="sxs-lookup"><span data-stu-id="6db92-105">This document explains the format and correct placement of module Help topics, and it suggests guidelines for module Help content.</span></span>

## <a name="types-of-module-help"></a><span data-ttu-id="6db92-106">模块的类型帮助</span><span class="sxs-lookup"><span data-stu-id="6db92-106">Types of Module Help</span></span>

<span data-ttu-id="6db92-107">模块可以包含以下类型的帮助。</span><span class="sxs-lookup"><span data-stu-id="6db92-107">A module can include the following types of Help.</span></span>

- <span data-ttu-id="6db92-108">**Cmdlet 帮助**。</span><span class="sxs-lookup"><span data-stu-id="6db92-108">**Cmdlet Help**.</span></span> <span data-ttu-id="6db92-109">描述模块中的 cmdlet 的帮助主题是使用 command Help 架构的 XML 文件</span><span class="sxs-lookup"><span data-stu-id="6db92-109">The Help topics that describe cmdlets in a module are XML files that use the command help schema</span></span>

- <span data-ttu-id="6db92-110">**提供程序帮助**。</span><span class="sxs-lookup"><span data-stu-id="6db92-110">**Provider Help**.</span></span> <span data-ttu-id="6db92-111">在模块中描述提供程序的帮助主题是使用提供程序帮助架构的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="6db92-111">The Help topics that describe providers in a module are XML files that use the provider help schema.</span></span>

- <span data-ttu-id="6db92-112">**函数帮助**。</span><span class="sxs-lookup"><span data-stu-id="6db92-112">**Function Help**.</span></span> <span data-ttu-id="6db92-113">描述模块中的函数的帮助主题可以是 XML 文件，这些文件使用命令帮助架构或在函数中使用基于注释的帮助主题，或者脚本或脚本模块</span><span class="sxs-lookup"><span data-stu-id="6db92-113">The Help topics that describe functions in a module can be XML files that use the command help schema or comment-based Help topics within the function, or the script or script module</span></span>

- <span data-ttu-id="6db92-114">**脚本帮助**。</span><span class="sxs-lookup"><span data-stu-id="6db92-114">**Script Help**.</span></span> <span data-ttu-id="6db92-115">描述模块中的脚本的帮助主题可以是 XML 文件，这些文件使用命令帮助架构或脚本模块中的基于注释的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="6db92-115">The Help topics that describe scripts in a module can be XML files that use the command help schema or comment-based Help topics in the script or script module.</span></span>

- <span data-ttu-id="6db92-116">**概念（"关于"）帮助**。</span><span class="sxs-lookup"><span data-stu-id="6db92-116">**Conceptual ("About") Help**.</span></span> <span data-ttu-id="6db92-117">您可以使用概念（"关于"）帮助主题描述模块及其成员，并说明如何将成员一起用于执行任务。</span><span class="sxs-lookup"><span data-stu-id="6db92-117">You can use a conceptual ("about") Help topic to describe the module and its members and to explain how the members can be used together to perform tasks.</span></span>
  <span data-ttu-id="6db92-118">概念性帮助主题是带有 Unicode （UTF-8）编码的文本文件。</span><span class="sxs-lookup"><span data-stu-id="6db92-118">Conceptual Help topics are text files with Unicode (UTF-8) encoding.</span></span> <span data-ttu-id="6db92-119">文件名必须使用 `about_<name>.help.txt` 格式，如 `about_MyModule.help.txt` 。</span><span class="sxs-lookup"><span data-stu-id="6db92-119">The file name must use the `about_<name>.help.txt` format, such as `about_MyModule.help.txt`.</span></span> <span data-ttu-id="6db92-120">默认情况下，PowerShell 包括超过100的有关 "帮助" 主题的概念，它们的格式与以下示例类似。</span><span class="sxs-lookup"><span data-stu-id="6db92-120">By default, PowerShell includes over 100 of these conceptual About Help topics, and they are formatted like the following example.</span></span>

  ```
  TOPIC
      about_<subject or module name>

  SHORT DESCRIPTION
      A short, one-line description of the topic contents.

  LONG DESCRIPTION
      A detailed, full description of the subject or purpose of the module.

  EXAMPLES
      Examples of how to use the module or how the subject feature works in practice.

  KEYWORDS
      Terms or titles on which you might expect your users to search for the information in this topic.

  SEE ALSO
      Text-only references for further reading. Hyperlinks cannot work in the PowerShell console.

  ```

<span data-ttu-id="6db92-121">所有架构文件都可以在文件夹中找到 `$PSHOME\Schemas\PSMaml` 。</span><span class="sxs-lookup"><span data-stu-id="6db92-121">All of the schema files can be found in the `$PSHOME\Schemas\PSMaml` folder.</span></span>

## <a name="placement-of-module-help"></a><span data-ttu-id="6db92-122">模块的位置帮助</span><span class="sxs-lookup"><span data-stu-id="6db92-122">Placement of Module Help</span></span>

<span data-ttu-id="6db92-123">该 `Get-Help` cmdlet 将在模块目录的特定于语言的子目录中查找模块帮助主题文件。</span><span class="sxs-lookup"><span data-stu-id="6db92-123">The `Get-Help` cmdlet looks for module Help topic files in language-specific subdirectories of the module directory.</span></span>

<span data-ttu-id="6db92-124">例如，下面的目录结构关系图显示了 SampleModule 模块的帮助主题的位置。</span><span class="sxs-lookup"><span data-stu-id="6db92-124">For example, the following directory structure diagram shows the location of the Help topics for the SampleModule module.</span></span>

```
<ModulePath>
         \SampleModule
               \<en-US>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml
               \<fr-FR>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml

```

> [!NOTE]
> <span data-ttu-id="6db92-125">在此示例中， `<ModulePath>` 占位符表示环境变量中的路径之一 `PSModulePath` ，例如 `$HOME\Documents\Modules` 、 `$PSHOME\Modules` 或用户指定的自定义路径。</span><span class="sxs-lookup"><span data-stu-id="6db92-125">In the example, the `<ModulePath>` placeholder represents one of the paths in the `PSModulePath` environment variable, such as `$HOME\Documents\Modules`, `$PSHOME\Modules`, or a custom path that the user specifies.</span></span>

## <a name="getting-module-help"></a><span data-ttu-id="6db92-126">获取模块帮助</span><span class="sxs-lookup"><span data-stu-id="6db92-126">Getting Module Help</span></span>

<span data-ttu-id="6db92-127">当用户将模块导入到会话中时，该模块的帮助主题将与模块一起导入到会话中。</span><span class="sxs-lookup"><span data-stu-id="6db92-127">When a user imports a module into a session, the Help topics for that module are imported into the session along with the module.</span></span> <span data-ttu-id="6db92-128">可以在模块清单中的 FileList 键的值中列出帮助主题文件，但帮助主题不受 cmdlet 的影响 `Export-ModuleMember` 。</span><span class="sxs-lookup"><span data-stu-id="6db92-128">You can list the Help topic files in the value of the FileList key in the module manifest, but Help topics are not affected by the `Export-ModuleMember` cmdlet.</span></span>

<span data-ttu-id="6db92-129">可以用不同的语言提供模块帮助主题。</span><span class="sxs-lookup"><span data-stu-id="6db92-129">You can provide module Help topics in different languages.</span></span> <span data-ttu-id="6db92-130">该 `Get-Help` cmdlet 会自动以 "控制面板" 的 "区域和语言选项" 项中为当前用户指定的语言显示模块帮助主题。</span><span class="sxs-lookup"><span data-stu-id="6db92-130">The `Get-Help` cmdlet automatically displays module Help topics in the language that is specified for the current user in the Regional and Language Options item in Control Panel.</span></span> <span data-ttu-id="6db92-131">在 Windows Vista 和更高版本的 Windows 中，在 `Get-Help` 模块目录的特定于语言的子目录中按照为 Windows 建立的语言回退标准搜索帮助主题。</span><span class="sxs-lookup"><span data-stu-id="6db92-131">In Windows Vista and later versions of Windows, `Get-Help` searches for the Help topics in language-specific subdirectories of the module directory in accordance with the language fallback standards established for Windows.</span></span>

<span data-ttu-id="6db92-132">从 PowerShell 3.0 开始，运行 `Get-Help` cmdlet 或函数命令会触发模块的自动导入。</span><span class="sxs-lookup"><span data-stu-id="6db92-132">Beginning in PowerShell 3.0, running a `Get-Help` command for a cmdlet or function triggers automatic importing of the module.</span></span> <span data-ttu-id="6db92-133">`Get-Help`Cmdlet 立即显示模块中帮助主题的内容。</span><span class="sxs-lookup"><span data-stu-id="6db92-133">The `Get-Help` cmdlet immediately displays the contents of the help topics in the module.</span></span>

<span data-ttu-id="6db92-134">如果该模块不包含帮助主题，并且用户计算机上的模块中没有相关命令的帮助主题，将 `Get-Help` 显示自动生成的帮助。</span><span class="sxs-lookup"><span data-stu-id="6db92-134">If the module does not contain help topics and there are no help topics for the commands in the module on the user's computer, `Get-Help` displays auto-generated help.</span></span> <span data-ttu-id="6db92-135">自动生成的帮助包括命令语法、参数、输入和输出类型，但不包含任何说明。</span><span class="sxs-lookup"><span data-stu-id="6db92-135">The auto-generated help includes the command syntax, parameters, and input and output types, but does not include any descriptions.</span></span> <span data-ttu-id="6db92-136">自动生成的帮助包括文本，该文本指示用户尝试使用 `Update-Help` cmdlet 从 Internet 或文件共享下载命令的帮助。</span><span class="sxs-lookup"><span data-stu-id="6db92-136">The auto-generated help includes text that directs the user to try to use the `Update-Help` cmdlet to download help for the command from the Internet or a file share.</span></span> <span data-ttu-id="6db92-137">它还建议使用 cmdlet 的**online**参数 `Get-Help` 获取帮助主题的联机版本。</span><span class="sxs-lookup"><span data-stu-id="6db92-137">It also recommends using the **Online** parameter of the `Get-Help` cmdlet to get the online version of the help topic.</span></span>

## <a name="supporting-updatable-help"></a><span data-ttu-id="6db92-138">支持可更新帮助</span><span class="sxs-lookup"><span data-stu-id="6db92-138">Supporting Updatable Help</span></span>

<span data-ttu-id="6db92-139">PowerShell 3.0 和更高版本的 PowerShell 的用户可以从 Internet 或本地文件共享下载和安装模块的更新帮助文件。</span><span class="sxs-lookup"><span data-stu-id="6db92-139">Users of PowerShell 3.0 and later versions of PowerShell can download and install updated help files for a module from the Internet or from a local file share.</span></span> <span data-ttu-id="6db92-140">`Update-Help`和 `Save-Help` cmdlet 将隐藏用户的管理详细信息。</span><span class="sxs-lookup"><span data-stu-id="6db92-140">The `Update-Help` and `Save-Help` cmdlets hide the management details from the user.</span></span> <span data-ttu-id="6db92-141">用户运行 `Update-Help` cmdlet，然后 `Get-Help` 在 PowerShell 命令提示符处使用 cmdlet 读取模块的最新帮助文件。</span><span class="sxs-lookup"><span data-stu-id="6db92-141">Users run the `Update-Help` cmdlet and then use the `Get-Help` cmdlet to read the newest help files for the module at the PowerShell command prompt.</span></span>
<span data-ttu-id="6db92-142">用户无需重启 Windows 或 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="6db92-142">Users do not need to restart Windows or PowerShell.</span></span>

<span data-ttu-id="6db92-143">防火墙之后的用户和无 Internet 访问权限的用户也可以使用可更新的帮助。</span><span class="sxs-lookup"><span data-stu-id="6db92-143">Users behind firewalls and those without Internet access can use Updatable Help, as well.</span></span>
<span data-ttu-id="6db92-144">具有 Internet 访问权限的管理员可以使用 `Save-Help` cmdlet 下载最新的帮助文件并将其安装到文件共享。</span><span class="sxs-lookup"><span data-stu-id="6db92-144">Administrators with Internet access use the `Save-Help` cmdlet to download and install the newest help files to a file share.</span></span> <span data-ttu-id="6db92-145">然后，用户使用该 cmdlet 的**Path**参数 `Update-Help` 从文件共享中获取最新的帮助文件。</span><span class="sxs-lookup"><span data-stu-id="6db92-145">Then, users use the **Path** parameter of the `Update-Help` cmdlet to get the newest help files from the file share.</span></span>

<span data-ttu-id="6db92-146">模块作者可将帮助文件包含在模块中，并使用可更新的帮助来更新帮助文件，或从模块中忽略帮助文件，并使用可更新的帮助来安装和更新这些文件。</span><span class="sxs-lookup"><span data-stu-id="6db92-146">Module authors can include help files in the module and use Updatable Help to update the help files, or omit help files from the module and use Updatable Help both to install and to update them.</span></span>

<span data-ttu-id="6db92-147">有关可更新帮助的详细信息，请参阅[支持可更新帮助](./supporting-updatable-help.md)。</span><span class="sxs-lookup"><span data-stu-id="6db92-147">For more information about Updatable Help, see [Supporting Updatable Help](./supporting-updatable-help.md).</span></span>

## <a name="supporting-online-help"></a><span data-ttu-id="6db92-148">支持联机帮助</span><span class="sxs-lookup"><span data-stu-id="6db92-148">Supporting Online Help</span></span>

<span data-ttu-id="6db92-149">不能或不在其计算机上安装更新的帮助文件的用户通常依赖于模块帮助主题的联机版本。</span><span class="sxs-lookup"><span data-stu-id="6db92-149">Users who cannot or do not install updated help files on their computers often rely on the online version of module help topics.</span></span> <span data-ttu-id="6db92-150">此 cmdlet 的**online**参数 `Get-Help` 会在其默认的 Internet 浏览器中打开 cmdlet 或高级函数帮助主题的联机版本。</span><span class="sxs-lookup"><span data-stu-id="6db92-150">The **Online** parameter of the `Get-Help` cmdlet opens the online version of a cmdlet or advanced function help topic for the user in their default Internet browser.</span></span>

<span data-ttu-id="6db92-151">`Get-Help`Cmdlet 使用 cmdlet 或函数的**HelpUri**属性的值查找帮助主题的联机版本。</span><span class="sxs-lookup"><span data-stu-id="6db92-151">The `Get-Help` cmdlet uses the value of the **HelpUri** property of the cmdlet or function to find the online version of the help topic.</span></span>

<span data-ttu-id="6db92-152">从 PowerShell 3.0 开始，你可以通过在 cmdlet 类上定义 HelpUri 属性或**CmdletBinding**属性的**HelpUri**属性，帮助用户找到 cmdlet 和函数帮助主题的联机版本。</span><span class="sxs-lookup"><span data-stu-id="6db92-152">Beginning in PowerShell 3.0, you can help users find the online version of cmdlet and function help topics by defining the HelpUri attribute on the cmdlet class or the **HelpUri** property of the **CmdletBinding** attribute.</span></span> <span data-ttu-id="6db92-153">该属性的值为 cmdlet 或函数的**HelpUri**属性的值。</span><span class="sxs-lookup"><span data-stu-id="6db92-153">The value of the attribute is the value of the **HelpUri** property of the cmdlet or function.</span></span>

<span data-ttu-id="6db92-154">有关详细信息，请参阅[支持联机帮助](./supporting-online-help.md)。</span><span class="sxs-lookup"><span data-stu-id="6db92-154">For more information, see [Supporting Online Help](./supporting-online-help.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6db92-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6db92-155">See Also</span></span>

[<span data-ttu-id="6db92-156">编写 PowerShell 模块</span><span class="sxs-lookup"><span data-stu-id="6db92-156">Writing a PowerShell Module</span></span>](../module/writing-a-windows-powershell-module.md)

[<span data-ttu-id="6db92-157">支持可更新帮助</span><span class="sxs-lookup"><span data-stu-id="6db92-157">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)

[<span data-ttu-id="6db92-158">支持联机帮助</span><span class="sxs-lookup"><span data-stu-id="6db92-158">Supporting Online Help</span></span>](./supporting-online-help.md)