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
# <a name="defining-default-methods-for-objects"></a>定义对象的默认方法

扩展.NET Framework 对象时，可以为这些对象中添加代码的方法和脚本方法。 以下各节介绍了用于定义这些方法的 XML。

> [!NOTE]
> 以下各节中的示例是从 Windows PowerShell 安装目录中的 Types.ps1xml 类型文件 (`$pshome`)。

## <a name="code-methods"></a>代码的方法

代码方法引用.NET Framework 对象的静态方法。

在以下示例中， **ConvertLargeIntegerToInt64**方法添加到[System.Xml.Xmlnode？Displayproperty =](/dotnet/api/System.Xml.XmlNode)类型。 [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod)元素中定义的扩展的方法为代码方法。 [名称](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name)元素指定的扩展方法的名称。 并且， [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference)元素指定的静态方法。 (您还可以添加[PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod)元素的成员[PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0)元素。)

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

## <a name="script-methods"></a>脚本方法

脚本方法定义其值是脚本的输出的方法。 在以下示例中， **ConvertToDateTime**方法添加到[System.Management.Managementobject？Displayproperty =](/dotnet/api/System.Management.ManagementObject)类型。 [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0)元素定义的扩展的方法作为脚本方法。 [名称](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name)元素指定的扩展方法的名称。 并且，[脚本](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script)元素指定的脚本的生成方法值。 (您还可以添加[PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0)元素的成员[PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0)元素。)

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

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
