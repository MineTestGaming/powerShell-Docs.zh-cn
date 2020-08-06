---
title: 如何声明动态参数 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c8839aa8841bf94a9b7f8f930ca315fe0ccedb30
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784174"
---
# <a name="how-to-declare-dynamic-parameters"></a><span data-ttu-id="1b481-102">如何声明动态参数</span><span class="sxs-lookup"><span data-stu-id="1b481-102">How to Declare Dynamic Parameters</span></span>

<span data-ttu-id="1b481-103">此示例演示如何定义在运行时添加到 cmdlet 的动态参数。</span><span class="sxs-lookup"><span data-stu-id="1b481-103">This example shows how to define dynamic parameters that are added to the cmdlet at runtime.</span></span> <span data-ttu-id="1b481-104">在此示例中， `Department` 只要用户指定开关参数，就会将参数添加到 cmdlet `Employee` 。</span><span class="sxs-lookup"><span data-stu-id="1b481-104">In this example, the `Department` parameter is added to the cmdlet whenever the user specifies the `Employee` switch parameter.</span></span> <span data-ttu-id="1b481-105">有关动态参数的详细信息，请参阅[Cmdlet 动态参数](./cmdlet-dynamic-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="1b481-105">For more information about dynamic parameters, see [Cmdlet Dynamic Parameters](./cmdlet-dynamic-parameters.md).</span></span>

## <a name="to-define-dynamic-parameters"></a><span data-ttu-id="1b481-106">定义动态参数</span><span class="sxs-lookup"><span data-stu-id="1b481-106">To define dynamic parameters</span></span>

1. <span data-ttu-id="1b481-107">在 cmdlet 类声明中，按如下所示添加[Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters)接口。</span><span class="sxs-lookup"><span data-stu-id="1b481-107">In the cmdlet class declaration, add the [System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) interface as shown.</span></span>

   ```csharp
   public class SendGreetingCommand : Cmdlet, IDynamicParameters
   ```

2. <span data-ttu-id="1b481-108">调用[Idynamicparameters. Getdynamicparameters \*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)方法，该方法返回在其中定义动态参数的对象。</span><span class="sxs-lookup"><span data-stu-id="1b481-108">Call the [System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) method, which returns the object in which the dynamic parameters are defined.</span></span> <span data-ttu-id="1b481-109">在此示例中，当指定了参数时，将调用方法 `Employee` 。</span><span class="sxs-lookup"><span data-stu-id="1b481-109">In this example, the method is called when the `Employee` parameter is specified.</span></span>

   ```csharp
   public object GetDynamicParameters()
   {
       if (employee)
       {
         context= new SendGreetingCommandDynamicParameters();
         return context;
       }
       return null;
   }
   private SendGreetingCommandDynamicParameters context;
   ```

3. <span data-ttu-id="1b481-110">声明一个定义要添加的动态参数的类。</span><span class="sxs-lookup"><span data-stu-id="1b481-110">Declare a class that defines the dynamic parameters to be added.</span></span> <span data-ttu-id="1b481-111">你可以使用用于声明静态 cmdlet 参数的属性来声明动态参数。</span><span class="sxs-lookup"><span data-stu-id="1b481-111">You can use the attributes that you used to declare the static cmdlet parameters to declare the dynamic parameters.</span></span>

   ```csharp
   public class SendGreetingCommandDynamicParameters
   {
     [Parameter]
     [ValidateSet ("Marketing", "Sales", "Development")]
     public string Department
     {
       get { return department; }
       set { department = value; }
     }
     private string department;
   }
   ```

## <a name="example"></a><span data-ttu-id="1b481-112">示例</span><span class="sxs-lookup"><span data-stu-id="1b481-112">Example</span></span>

<span data-ttu-id="1b481-113">在此示例中， `Department` 只要用户指定参数，就会添加参数 `Employee` 。</span><span class="sxs-lookup"><span data-stu-id="1b481-113">In this example, the `Department` parameter is added whenever the user specifies the `Employee` parameter.</span></span> <span data-ttu-id="1b481-114">`Department`参数是一个可选参数，ValidateSet 属性用于指定允许的参数。</span><span class="sxs-lookup"><span data-stu-id="1b481-114">The `Department` parameter is an optional parameter, and the ValidateSet attribute is used to specify the allowed arguments.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;     // PowerShell assembly.

namespace SendGreeting
{
  // Declare the cmdlet class that supports the
  // IDynamicParameters interface.
  [Cmdlet(VerbsCommunications.Send, "Greeting")]
  public class SendGreetingCommand : Cmdlet, IDynamicParameters
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory = true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    [Parameter]
    [Alias ("FTE")]
    public SwitchParameter Employee
    {
      get { return employee; }
      set { employee = value; }
    }
    private Boolean employee;

    // Implement GetDynamicParameters to
    // retrieve the dynamic parameter.
    public object GetDynamicParameters()
    {
      if (employee)
      {
        context= new SendGreetingCommandDynamicParameters();
        return context;
      }
      return null;
   }
   private SendGreetingCommandDynamicParameters context;

    // Overide the ProcessRecord method to process the
    // supplied user name and write out a greeting to
    // the user by calling the WriteObject method.
    protected override void ProcessRecord()
    {
      WriteObject("Hello " + name + "! ");
      if (employee)
      {
        WriteObject("Department: " + context.Department);
      }
    }
  }

  // Define the dynamic parameters to be added
  public class SendGreetingCommandDynamicParameters
  {
    [Parameter]
    [ValidateSet ("Marketing", "Sales", "Development")]
    public string Department
    {
      get { return department; }
      set { department = value; }
    }
    private string department;
  }
}
```

## <a name="see-also"></a><span data-ttu-id="1b481-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1b481-115">See Also</span></span>

[<span data-ttu-id="1b481-116">System.web. Runtimedefinedparameterdictionary</span><span class="sxs-lookup"><span data-stu-id="1b481-116">System.Management.Automation.Runtimedefinedparameterdictionary</span></span>](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)

[<span data-ttu-id="1b481-117">Idynamicparameters. Getdynamicparameters \*</span><span class="sxs-lookup"><span data-stu-id="1b481-117">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[<span data-ttu-id="1b481-118">Cmdlet 动态参数</span><span class="sxs-lookup"><span data-stu-id="1b481-118">Cmdlet Dynamic Parameters</span></span>](./cmdlet-dynamic-parameters.md)

[<span data-ttu-id="1b481-119">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="1b481-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
