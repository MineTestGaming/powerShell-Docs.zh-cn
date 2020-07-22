---
title: 如何向提供程序帮助主题添加“另请参阅”部分
ms.date: 09/12/2016
ms.openlocfilehash: 54adf4bb941888583eb749b7b5322b27d84c7af7
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893469"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a>如何向提供程序帮助主题添加“另请参阅”部分

本部分介绍如何填充提供程序帮助主题的 "**另请参阅**" 部分。

"**另请参阅**" 部分包含与提供程序相关的主题列表，或可帮助用户更好地了解和使用该提供程序。 主题列表可以包含 Windows PowerShell 中的 cmdlet 帮助、提供程序帮助和概念（"关于"）帮助主题。 它还可以包括对书籍、纸张和联机主题的引用，包括当前提供程序帮助主题的联机版本。

请参阅联机主题，以纯文本形式提供 URI 或搜索词。 `Get-Help`Cmdlet 不会链接或重定向到列表中的任何主题。 此外， `Online` cmdlet 的参数不适 `Get-Help` 用于提供程序帮助。

"**另请参见**" 部分从 `RelatedLinks` 元素及其包含的标记创建。
下面的 XML 演示如何添加标记。

### <a name="to-add-see-also-topics"></a>要添加的另请参阅主题

1. 在 `<AssemblyName>.dll-help.xml` 文件中，在 `providerHelp` 元素中添加一个 `RelatedLinks` 元素。 `RelatedLinks`元素应为元素中的最后一个元素 `providerHelp` 。 `RelatedLinks`每个提供程序帮助主题中只允许有一个元素。

   例如：

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

1. 对于 "**另请参见**" 部分中的每个主题，在 `RelatedLinks` 元素中添加一个 `navigationLink` 元素。 然后，在每个 `navigationLink` 元素中添加一个 `linkText` 元素和一个 `uri` 元素。 如果不使用 `uri` 元素，则可以将其添加为空元素（ \<uri/> ）。

   例如：

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> </linkText>
                <uri> </uri>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```

1. 键入标记之间的主题名称 `linkText` 。 如果要提供 URI，请在标记之间键入 `uri` 。 若要指示当前提供程序帮助主题的联机版本，请在 `linkText` 标记之间键入 "online 版本："，而不是主题名称。 通常，"Online 版本：" 链接是 "另请参见" 主题列表中的第一个主题。

   下面的示例包括三个 "另请参阅" 主题。 第一个引用当前主题的联机版本。 第二个引用 Windows PowerShell cmdlet 帮助主题。 第三个引用其他联机主题。

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> Online version: </linkText>
                <uri>http://www.fabrikam.com/help/myFunction.htm</uri>
            </navigationLink>
            <navigationLink>
                <linkText> about_functions </linkText>
                <uri/>
            </navigationLink>
            <navigationLink>
                <linkText> Windows PowerShell Getting Started Guide </linkText>
                <uri>https://go.microsoft.com/fwlink/?LinkID=89597<uri/>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```
