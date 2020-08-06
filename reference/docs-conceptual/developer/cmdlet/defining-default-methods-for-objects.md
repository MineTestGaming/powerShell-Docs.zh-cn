---
title: 定义对象的默认方法 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 10917de9e897fc1eed362430d63ff5b9cb7e813d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774586"
---
# <a name="defining-default-methods-for-objects"></a><span data-ttu-id="7afa9-102">定义对象的默认方法</span><span class="sxs-lookup"><span data-stu-id="7afa9-102">Defining Default Methods for Objects</span></span>

<span data-ttu-id="7afa9-103">扩展 .NET Framework 对象时，可以将代码方法和脚本方法添加到对象。</span><span class="sxs-lookup"><span data-stu-id="7afa9-103">When you extend .NET Framework objects, you can add code methods and script methods to the objects.</span></span>
<span data-ttu-id="7afa9-104">以下各节介绍了用于定义这些方法的 XML。</span><span class="sxs-lookup"><span data-stu-id="7afa9-104">The XML that is used to define these methods is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="7afa9-105">以下部分中的示例来自 `Types.ps1xml` Windows PowerShell 安装目录中的类型文件 (`$PSHOME`) 。</span><span class="sxs-lookup"><span data-stu-id="7afa9-105">The examples in the following sections are from the `Types.ps1xml` types file in the Windows PowerShell installation directory (`$PSHOME`).</span></span> <span data-ttu-id="7afa9-106">有关详细信息，请参阅[关于 Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)。</span><span class="sxs-lookup"><span data-stu-id="7afa9-106">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span></span>

## <a name="code-methods"></a><span data-ttu-id="7afa9-107">代码方法</span><span class="sxs-lookup"><span data-stu-id="7afa9-107">Code methods</span></span>

<span data-ttu-id="7afa9-108">代码方法引用 .NET Framework 对象的静态方法。</span><span class="sxs-lookup"><span data-stu-id="7afa9-108">A code method references a static method of a .NET Framework object.</span></span>

<span data-ttu-id="7afa9-109">在下面的示例中，将**ToString**方法添加到[System.Xml.Xml节点](/dotnet/api/System.Xml.XmlNode)类型。</span><span class="sxs-lookup"><span data-stu-id="7afa9-109">In the following example, the **ToString** method is added to the [System.Xml.XmlNode](/dotnet/api/System.Xml.XmlNode) type.</span></span> <span data-ttu-id="7afa9-110">[PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod)元素将扩展方法定义为代码方法。</span><span class="sxs-lookup"><span data-stu-id="7afa9-110">The [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element defines the extended method as a code method.</span></span> <span data-ttu-id="7afa9-111">[Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name)元素指定扩展方法的名称。</span><span class="sxs-lookup"><span data-stu-id="7afa9-111">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="7afa9-112">[CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference)元素指定静态方法。</span><span class="sxs-lookup"><span data-stu-id="7afa9-112">And, the [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) element specifies the static method.</span></span> <span data-ttu-id="7afa9-113">还可以将[PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod)元素添加到[PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0)元素的成员。</span><span class="sxs-lookup"><span data-stu-id="7afa9-113">You can also add the [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.</span></span>

```xml
<Type>
  <Name>System.Xml.XmlNode</Name>
  <Members>
    <CodeMethod>
      <Name>ToString</Name>
      <CodeReference>
        <TypeName>Microsoft.PowerShell.ToStringCodeMethods</TypeName>
        <MethodName>XmlNode</MethodName>
      </CodeReference>
    </CodeMethod>
  </Members>
</Type>
```

## <a name="script-methods"></a><span data-ttu-id="7afa9-114">脚本方法</span><span class="sxs-lookup"><span data-stu-id="7afa9-114">Script methods</span></span>

<span data-ttu-id="7afa9-115">脚本方法定义一个方法，其值为脚本的输出。</span><span class="sxs-lookup"><span data-stu-id="7afa9-115">A script method defines a method whose value is the output of a script.</span></span> <span data-ttu-id="7afa9-116">在下面的示例中，将**ConvertToDateTime**方法添加到[system.management.managementobject](/dotnet/api/System.Management.ManagementObject)类型。</span><span class="sxs-lookup"><span data-stu-id="7afa9-116">In the following example, the **ConvertToDateTime** method is added to the [System.Management.ManagementObject](/dotnet/api/System.Management.ManagementObject) type.</span></span> <span data-ttu-id="7afa9-117">[PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0)元素将扩展方法定义为脚本方法。</span><span class="sxs-lookup"><span data-stu-id="7afa9-117">The [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element defines the extended method as a script method.</span></span> <span data-ttu-id="7afa9-118">[Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name)元素指定扩展方法的名称。</span><span class="sxs-lookup"><span data-stu-id="7afa9-118">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="7afa9-119">[脚本](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script)元素指定生成方法值的脚本。</span><span class="sxs-lookup"><span data-stu-id="7afa9-119">And, the [Script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) element specifies the script that generates the method value.</span></span> <span data-ttu-id="7afa9-120">还可以将[PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0)元素添加到[PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0)元素的成员。</span><span class="sxs-lookup"><span data-stu-id="7afa9-120">You can also add the [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.</span></span>

```xml
<Type>
  <Name>System.Management.ManagementObject</Name>
  <Members>
    <ScriptMethod>
      <Name>ConvertToDateTime</Name>
      <Script>
        [System.Management.ManagementDateTimeConverter]::ToDateTime($args[0])
      </Script>
    </ScriptMethod>
  </Members>
</Type>
```

## <a name="see-also"></a><span data-ttu-id="7afa9-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7afa9-121">See also</span></span>

[<span data-ttu-id="7afa9-122">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7afa9-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
