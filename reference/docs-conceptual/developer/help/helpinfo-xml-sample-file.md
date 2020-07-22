---
title: HelpInfo XML 示例文件
ms.date: 09/12/2016
ms.openlocfilehash: ccd1f61d8d40232a3e6d2228d382ef4895e13d3d
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893503"
---
# <a name="helpinfo-xml-sample-file"></a><span data-ttu-id="008bd-102">HelpInfo XML 示例文件</span><span class="sxs-lookup"><span data-stu-id="008bd-102">HelpInfo XML Sample File</span></span>

<span data-ttu-id="008bd-103">本主题显示了格式正确的可更新帮助信息文件（通常称为 "HelpInfo XML 文件"）的示例。</span><span class="sxs-lookup"><span data-stu-id="008bd-103">This topic displays a sample of a well-formed Updatable Help Information file, commonly known as "HelpInfo XML file."</span></span> <span data-ttu-id="008bd-104">在此示例文件中，UI 区域性元素按 UI 区域性名称按字母顺序排列。</span><span class="sxs-lookup"><span data-stu-id="008bd-104">In this sample file, the UI culture elements are arranged in alphabetical order by UI culture name.</span></span> <span data-ttu-id="008bd-105">按字母顺序排序是最佳实践，但这不是必需的。</span><span class="sxs-lookup"><span data-stu-id="008bd-105">Alphabetical ordering is a best practice, but it is not required.</span></span>

## <a name="helpinfo-xml-sample-file"></a><span data-ttu-id="008bd-106">HelpInfo XML 示例文件</span><span class="sxs-lookup"><span data-stu-id="008bd-106">HelpInfo XML Sample File</span></span>

```xml

<?xml version="1.0" encoding="utf-8"?>
<HelpInfo xmlns="https://schemas.microsoft.com/powershell/help/2010/05">
   <HelpContentURI>https://go.microsoft.com/fwlink/?LinkID=141553</HelpContentURI>
   <SupportedUICultures>
    <UICulture>
      <UICultureName>de-DE</UICultureName>
      <UICultureVersion>2.15.0.10</UICultureVersion>
    </UICulture>
    <UICulture>
      <UICultureName>en-US</UICultureName>
      <UICultureVersion>3.2.0.7</UICultureVersion>
    </UICulture>
    <UICulture>
      <UICultureName>it-IT</UICultureName>
      <UICultureVersion>1.1.0.5</UICultureVersion>
    </UICulture>
    <UICulture>
      <UICultureName>ja-JP</UICultureName>
      <UICultureVersion>3.2.0.4</UICultureVersion>
    </UICulture>
   </SupportedUICultures>
</HelpInfo>

```
