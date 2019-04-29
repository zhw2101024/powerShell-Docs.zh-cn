---
title: Cmdlet 动态参数 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ae2196d-d6c8-4101-8805-4190d293af51
caps.latest.revision: 13
ms.openlocfilehash: 2fc73b6ef5a862fafb7a3c8fe3da19ac71bafc05
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068532"
---
# <a name="cmdlet-dynamic-parameters"></a><span data-ttu-id="7dfd8-102">Cmdlet 动态参数</span><span class="sxs-lookup"><span data-stu-id="7dfd8-102">Cmdlet Dynamic Parameters</span></span>

<span data-ttu-id="7dfd8-103">Cmdlet 可以定义可供用户使用特殊情况下，例如，当另一个参数的参数为特定值的参数。</span><span class="sxs-lookup"><span data-stu-id="7dfd8-103">Cmdlets can define parameters that are available to the user under special conditions, such as when the argument of another parameter is a specific value.</span></span> <span data-ttu-id="7dfd8-104">这些参数在运行时添加和*动态参数*因为仅在需要时添加它们。</span><span class="sxs-lookup"><span data-stu-id="7dfd8-104">These parameters are added at runtime and are referred to as *dynamic parameters* because they are added only when they are needed.</span></span> <span data-ttu-id="7dfd8-105">例如，您可以设计添加几个参数，仅当指定一个特定的开关参数的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7dfd8-105">For example, you can design a cmdlet that adds several parameters only when a specific switch parameter is specified.</span></span>

> [!NOTE]
> <span data-ttu-id="7dfd8-106">提供程序和 Windows PowerShell 函数还可以定义动态参数。</span><span class="sxs-lookup"><span data-stu-id="7dfd8-106">Providers and Windows PowerShell functions can also define dynamic parameters.</span></span>

## <a name="dynamic-parameters-in-windows-powershell-cmdlets"></a><span data-ttu-id="7dfd8-107">在 Windows PowerShell Cmdlet 的动态参数</span><span class="sxs-lookup"><span data-stu-id="7dfd8-107">Dynamic Parameters in Windows PowerShell Cmdlets</span></span>

<span data-ttu-id="7dfd8-108">Windows PowerShell 在多个提供程序 cmdlet 中使用动态参数。</span><span class="sxs-lookup"><span data-stu-id="7dfd8-108">Windows PowerShell uses dynamic parameters in several of its provider cmdlets.</span></span> <span data-ttu-id="7dfd8-109">例如，`Get-Item`并`Get-ChildItem`cmdlet 添加`CodeSigningCert`在运行时参数时`Path`cmdlet 参数指定的证书提供程序路径。</span><span class="sxs-lookup"><span data-stu-id="7dfd8-109">For example, the `Get-Item` and `Get-ChildItem` cmdlets add a `CodeSigningCert` parameter at runtime when the `Path` parameter of the cmdlet specifies the Certificate provider path.</span></span> <span data-ttu-id="7dfd8-110">如果`Path`cmdlet 参数指定的路径不同的提供程序，`CodeSigningCert`参数不可用。</span><span class="sxs-lookup"><span data-stu-id="7dfd8-110">If the `Path` parameter of the cmdlet specifies a path for a different provider, the `CodeSigningCert` parameter is not available.</span></span>

<span data-ttu-id="7dfd8-111">下面的示例演示如何`CodeSigningCert`在运行时添加参数时`Get-Item`运行 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7dfd8-111">The following examples show how the `CodeSigningCert` parameter is added at runtime when the `Get-Item` cmdlet is run.</span></span>

<span data-ttu-id="7dfd8-112">在第一个示例中，Windows PowerShell 运行时已添加了参数，并且该 cmdlet 成功。</span><span class="sxs-lookup"><span data-stu-id="7dfd8-112">In the first example, the Windows PowerShell runtime has added the parameter, and the cmdlet is successful.</span></span>

```powershell
Get-Item -Path cert:\CurrentUser -codesigningcert
```

```output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

<span data-ttu-id="7dfd8-113">在第二个示例中，指定文件系统驱动器，并返回错误。</span><span class="sxs-lookup"><span data-stu-id="7dfd8-113">In the second example, a FileSystem drive is specified, and an error is returned.</span></span> <span data-ttu-id="7dfd8-114">错误消息指示`CodeSigningCert`找不到参数。</span><span class="sxs-lookup"><span data-stu-id="7dfd8-114">The error message indicates that the `CodeSigningCert` parameter cannot be found.</span></span>

```powershell
Get-Item -Path C:\ -codesigningcert
```

```output
Get-Item : A parameter cannot be found that matches parameter name 'codesigningcert'.
At line:1 char:37
+  get-item -path C:\ -codesigningcert <<<<
--------
    CategoryInfo          : InvalidArgument: (:) [Get-Item], ParameterBindingException
    FullyQualifiedErrorId : NamedParameterNotFound,Microsoft.PowerShell.Commands.GetItemCommand
```

## <a name="support-for-dynamic-parameters"></a><span data-ttu-id="7dfd8-115">对动态参数的支持</span><span class="sxs-lookup"><span data-stu-id="7dfd8-115">Support for Dynamic Parameters</span></span>

<span data-ttu-id="7dfd8-116">若要支持动态参数，cmdlet 代码必须包含以下元素。</span><span class="sxs-lookup"><span data-stu-id="7dfd8-116">To support dynamic parameters, the cmdlet code must include the following elements.</span></span>

<span data-ttu-id="7dfd8-117">[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters)此接口提供用于检索动态参数的方法。</span><span class="sxs-lookup"><span data-stu-id="7dfd8-117">[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) This interface provides the method that retrieves the dynamic parameters.</span></span>

<span data-ttu-id="7dfd8-118">例如：</span><span class="sxs-lookup"><span data-stu-id="7dfd8-118">Example:</span></span>

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

<span data-ttu-id="7dfd8-119">[System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)此方法检索包含的动态参数定义的对象。</span><span class="sxs-lookup"><span data-stu-id="7dfd8-119">[System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) This method retrieves the object that contains the dynamic parameter definitions.</span></span>

<span data-ttu-id="7dfd8-120">例如：</span><span class="sxs-lookup"><span data-stu-id="7dfd8-120">Example:</span></span>

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

<span data-ttu-id="7dfd8-121">动态参数类此类定义要添加的参数。</span><span class="sxs-lookup"><span data-stu-id="7dfd8-121">Dynamic Parameter class This class defines the parameters to be added.</span></span> <span data-ttu-id="7dfd8-122">此类必须包含每个参数和所需 cmdlet 的任何可选别名和验证属性的参数属性。</span><span class="sxs-lookup"><span data-stu-id="7dfd8-122">This class must include a Parameter attribute for each parameter and any optional Alias and Validation attributes that are needed by the cmdlet.</span></span>

<span data-ttu-id="7dfd8-123">例如：</span><span class="sxs-lookup"><span data-stu-id="7dfd8-123">Example:</span></span>

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

<span data-ttu-id="7dfd8-124">支持动态参数的 cmdlet 的完整示例，请参阅[如何声明动态参数](./how-to-declare-dynamic-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="7dfd8-124">For a complete example of a cmdlet that supports dynamic parameters, see [How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7dfd8-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7dfd8-125">See Also</span></span>

[<span data-ttu-id="7dfd8-126">System.Management.Automation.Idynamicparameters</span><span class="sxs-lookup"><span data-stu-id="7dfd8-126">System.Management.Automation.Idynamicparameters</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters)

[<span data-ttu-id="7dfd8-127">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span><span class="sxs-lookup"><span data-stu-id="7dfd8-127">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[<span data-ttu-id="7dfd8-128">如何声明动态参数</span><span class="sxs-lookup"><span data-stu-id="7dfd8-128">How to Declare Dynamic Parameters</span></span>](./how-to-declare-dynamic-parameters.md)

[<span data-ttu-id="7dfd8-129">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7dfd8-129">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
