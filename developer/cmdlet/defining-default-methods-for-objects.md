---
title: 为对象定义的默认方法 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53fe744a-485f-4c21-9623-1cb546372211
caps.latest.revision: 9
ms.openlocfilehash: af554cde5e888f2a008028010332caa473151622
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733976"
---
# <a name="defining-default-methods-for-objects"></a><span data-ttu-id="e42a7-102">定义对象的默认方法</span><span class="sxs-lookup"><span data-stu-id="e42a7-102">Defining Default Methods for Objects</span></span>

<span data-ttu-id="e42a7-103">扩展.NET Framework 对象时，可以为这些对象中添加代码的方法和脚本方法。</span><span class="sxs-lookup"><span data-stu-id="e42a7-103">When you extend .NET Framework objects, you can add code methods and script methods to the objects.</span></span> <span data-ttu-id="e42a7-104">以下各节介绍了用于定义这些方法的 XML。</span><span class="sxs-lookup"><span data-stu-id="e42a7-104">The XML that is used to define these methods is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="e42a7-105">以下各节中的示例是从 Windows PowerShell 安装目录中的 Types.ps1xml 类型文件 (`$pshome`)。</span><span class="sxs-lookup"><span data-stu-id="e42a7-105">The examples in the following sections are from the Types.ps1xml types file in the Windows PowerShell installation directory (`$pshome`).</span></span>

## <a name="code-methods"></a><span data-ttu-id="e42a7-106">代码的方法</span><span class="sxs-lookup"><span data-stu-id="e42a7-106">Code Methods</span></span>

<span data-ttu-id="e42a7-107">代码方法引用.NET Framework 对象的静态方法。</span><span class="sxs-lookup"><span data-stu-id="e42a7-107">A code method references a static method of a .NET Framework object.</span></span>

<span data-ttu-id="e42a7-108">在以下示例中， **ConvertLargeIntegerToInt64**方法添加到[System.Xml.Xmlnode？Displayproperty =](/dotnet/api/System.Xml.XmlNode)类型。</span><span class="sxs-lookup"><span data-stu-id="e42a7-108">In the following example, the **ConvertLargeIntegerToInt64** method is added to the [System.Xml.Xmlnode?Displayproperty=Fullname](/dotnet/api/System.Xml.XmlNode) type.</span></span> <span data-ttu-id="e42a7-109">[PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod)元素中定义的扩展的方法为代码方法。</span><span class="sxs-lookup"><span data-stu-id="e42a7-109">The [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element defines the extended method as a code method.</span></span> <span data-ttu-id="e42a7-110">[名称](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name)元素指定的扩展方法的名称。</span><span class="sxs-lookup"><span data-stu-id="e42a7-110">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="e42a7-111">并且， [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference)元素指定的静态方法。</span><span class="sxs-lookup"><span data-stu-id="e42a7-111">And, the [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) element specifies the static method.</span></span> <span data-ttu-id="e42a7-112">(您还可以添加[PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod)元素的成员[PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0)元素。)</span><span class="sxs-lookup"><span data-stu-id="e42a7-112">(You can also add the [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.)</span></span>

```xml
<Type>
  <Name>System.Xml.XmlNode</Name>
  <Members>
    <CodeMethod>
      <Name>ToString</Name>
      <CodeReference>
        <TypeName>Microsoft.PowerShell.ToStringCodemethods</TypeName>
        <MethodName>XmlNode</MethodName>
      </CodeReference>
    </CodeMethod>
  </Members>
</Type>
```

## <a name="script-methods"></a><span data-ttu-id="e42a7-113">脚本方法</span><span class="sxs-lookup"><span data-stu-id="e42a7-113">Script Methods</span></span>

<span data-ttu-id="e42a7-114">脚本方法定义其值是脚本的输出的方法。</span><span class="sxs-lookup"><span data-stu-id="e42a7-114">A script method defines a method whose value is the output of a script.</span></span> <span data-ttu-id="e42a7-115">在以下示例中， **ConvertToDateTime**方法添加到[System.Management.Managementobject？Displayproperty =](/dotnet/api/System.Management.ManagementObject)类型。</span><span class="sxs-lookup"><span data-stu-id="e42a7-115">In the following example, the **ConvertToDateTime** method is added to the [System.Management.Managementobject?Displayproperty=Fullname](/dotnet/api/System.Management.ManagementObject) type.</span></span> <span data-ttu-id="e42a7-116">[PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0)元素定义的扩展的方法作为脚本方法。</span><span class="sxs-lookup"><span data-stu-id="e42a7-116">The [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element defines the extended method as a script method.</span></span> <span data-ttu-id="e42a7-117">[名称](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name)元素指定的扩展方法的名称。</span><span class="sxs-lookup"><span data-stu-id="e42a7-117">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="e42a7-118">并且，[脚本](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script)元素指定的脚本的生成方法值。</span><span class="sxs-lookup"><span data-stu-id="e42a7-118">And, the [Script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) element specifies the script that generates the method value.</span></span> <span data-ttu-id="e42a7-119">(您还可以添加[PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0)元素的成员[PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0)元素。)</span><span class="sxs-lookup"><span data-stu-id="e42a7-119">(You can also add the [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.)</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e42a7-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e42a7-120">See Also</span></span>

[<span data-ttu-id="e42a7-121">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e42a7-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
