---
title: HelpInfo XML 架构
ms.date: 09/12/2016
ms.openlocfilehash: f94d053b8fc558d9efc13e6b9fbd597287970e38
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86953244"
---
# <a name="helpinfo-xml-schema"></a><span data-ttu-id="08a36-102">HelpInfo XML 架构</span><span class="sxs-lookup"><span data-stu-id="08a36-102">HelpInfo XML Schema</span></span>

<span data-ttu-id="08a36-103">本主题包含可更新帮助信息文件（通常称为 "HelpInfo XML 文件"）的 XML 架构。</span><span class="sxs-lookup"><span data-stu-id="08a36-103">This topic contains the XML schema for Updatable Help Information files, commonly known as "HelpInfo XML files."</span></span>

## <a name="helpinfo-xml-schema"></a><span data-ttu-id="08a36-104">HelpInfo XML 架构</span><span class="sxs-lookup"><span data-stu-id="08a36-104">HelpInfo XML Schema</span></span>

<span data-ttu-id="08a36-105">HelpInfo XML 文件基于以下 XML 架构。</span><span class="sxs-lookup"><span data-stu-id="08a36-105">HelpInfo XML files are based on the following XML schema.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<schema targetNamespace="http://schemas.microsoft.com/powershell/help/2010/05" xmlns="http://www.w3.org/2001/XMLSchema">
  <element name="HelpInfo">
    <complexType>
      <sequence>
        <element name="HelpContentURI" type="anyURI" minOccurs="1" maxOccurs="1" />
        <element name="SupportedUICultures" minOccurs="1" maxOccurs="1">
          <complexType>
            <sequence>
              <element name="UICulture" minOccurs="1" maxOccurs="unbounded">
                <complexType>
                  <sequence>
                    <element name="UICultureName" type="language" minOccurs="1" maxOccurs="1" />
                    <element name="UICultureVersion" type="string" minOccurs="1" maxOccurs="1" />
                  </sequence>
                </complexType>
              </element>
            </sequence>
          </complexType>
        </element>
      </sequence>
    </complexType>
  </element>
</schema>
```

## <a name="helpinfo-xml-elements"></a><span data-ttu-id="08a36-106">HelpInfo XML 元素</span><span class="sxs-lookup"><span data-stu-id="08a36-106">HelpInfo XML Elements</span></span>

<span data-ttu-id="08a36-107">HelpInfo XML 文件包含以下元素。</span><span class="sxs-lookup"><span data-stu-id="08a36-107">The HelpInfo XML file includes the following elements.</span></span>

- <span data-ttu-id="08a36-108">**HelpContentURI** -包含模块的帮助 CAB 文件位置的 URI。</span><span class="sxs-lookup"><span data-stu-id="08a36-108">**HelpContentURI** - Contains the URI of the location of the help CAB files for the module.</span></span> <span data-ttu-id="08a36-109">URI 必须以 "http" 或 "https" 开头。</span><span class="sxs-lookup"><span data-stu-id="08a36-109">The URI must begin with "http" or "https".</span></span> <span data-ttu-id="08a36-110">URI 应指定 internet 位置，但不得包含 CAB 文件名。</span><span class="sxs-lookup"><span data-stu-id="08a36-110">The URI should specify an internet location, but must not include the CAB filename.</span></span> <span data-ttu-id="08a36-111">**HelpContentURI**值可以与**HelpInfoURI**值相同或不同。</span><span class="sxs-lookup"><span data-stu-id="08a36-111">The **HelpContentURI** value can be the same or different from the **HelpInfoURI** value.</span></span>

- <span data-ttu-id="08a36-112">**SupportedUICultures** -表示所有 UI 区域性中的模块帮助文件。</span><span class="sxs-lookup"><span data-stu-id="08a36-112">**SupportedUICultures** - Represents the module help files in all UI cultures.</span></span> <span data-ttu-id="08a36-113">包含**UICulture**元素，其中每个元素都表示一组指定 UI 区域性中的模块的帮助文件。</span><span class="sxs-lookup"><span data-stu-id="08a36-113">Contains **UICulture** elements, each of which represents a set of help files for the module in a specified UI culture.</span></span>

- <span data-ttu-id="08a36-114">**UICulture** -表示指定 UI 区域性中的模块的一组帮助文件。</span><span class="sxs-lookup"><span data-stu-id="08a36-114">**UICulture** - Represents a set of help files for the module in a specified UI culture.</span></span> <span data-ttu-id="08a36-115">为在其中编写帮助文件的每个 UI 区域性添加一个**UICulture**元素。</span><span class="sxs-lookup"><span data-stu-id="08a36-115">Add a **UICulture** element for each UI culture in which the help files are written.</span></span>

- <span data-ttu-id="08a36-116">**UICultureName** -包含在其中编写帮助文件的 UI 区域性的语言代码。</span><span class="sxs-lookup"><span data-stu-id="08a36-116">**UICultureName** - Contains the language code for the UI culture in which the help files are written.</span></span>

- <span data-ttu-id="08a36-117">**UICultureVersion** -在 "N1。N2.N3.N4 "格式，表示 UI 区域性中 help CAB 文件的版本。</span><span class="sxs-lookup"><span data-stu-id="08a36-117">**UICultureVersion** - Contains a 4-part version number in "N1.N2.N3.N4" format that represents the version of the help CAB file in the UI culture.</span></span> <span data-ttu-id="08a36-118">每次上传**UICultureName**指定的 UI 区域性中的新帮助 CAB 文件时，请递增此版本号。</span><span class="sxs-lookup"><span data-stu-id="08a36-118">Increment this version number whenever you upload new help CAB files in the UI culture that is specified by **UICultureName**.</span></span> <span data-ttu-id="08a36-119">有关此值的详细信息，请参阅[版本类](/dotnet/api/system.version)。</span><span class="sxs-lookup"><span data-stu-id="08a36-119">For more information about this value, see [Version Class](/dotnet/api/system.version).</span></span>
