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
ms.openlocfilehash: fa0f0371856d8723af7ec17a4306de209a481a18
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861403"
---
# <a name="defining-default-methods-for-objects"></a><span data-ttu-id="4cdc7-102">定义对象的默认方法</span><span class="sxs-lookup"><span data-stu-id="4cdc7-102">Defining Default Methods for Objects</span></span>

<span data-ttu-id="4cdc7-103">扩展.NET Framework 对象时，可以为这些对象中添加代码的方法和脚本方法。</span><span class="sxs-lookup"><span data-stu-id="4cdc7-103">When you extend .NET Framework objects, you can add code methods and script methods to the objects.</span></span> <span data-ttu-id="4cdc7-104">以下各节介绍了用于定义这些方法的 XML。</span><span class="sxs-lookup"><span data-stu-id="4cdc7-104">The XML that is used to define these methods is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="4cdc7-105">以下各节中的示例是从 Windows PowerShell 安装目录中的 Types.ps1xml 类型文件 (`$pshome`)。</span><span class="sxs-lookup"><span data-stu-id="4cdc7-105">The examples in the following sections are from the Types.ps1xml types file in the Windows PowerShell installation directory (`$pshome`).</span></span>

## <a name="code-methods"></a><span data-ttu-id="4cdc7-106">代码的方法</span><span class="sxs-lookup"><span data-stu-id="4cdc7-106">Code Methods</span></span>

<span data-ttu-id="4cdc7-107">代码方法引用.NET Framework 对象的静态方法。</span><span class="sxs-lookup"><span data-stu-id="4cdc7-107">A code method references a static method of a .NET Framework object.</span></span>

<span data-ttu-id="4cdc7-108">在以下示例中， **ConvertLargeIntegerToInt64**方法添加到[System.Xml.Xmlnode？Displayproperty =](/dotnet/api/System.Xml.XmlNode)类型。</span><span class="sxs-lookup"><span data-stu-id="4cdc7-108">In the following example, the **ConvertLargeIntegerToInt64** method is added to the [System.Xml.Xmlnode?Displayproperty=Fullname](/dotnet/api/System.Xml.XmlNode) type.</span></span> <span data-ttu-id="4cdc7-109">[CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05)元素中定义的扩展的方法为代码方法。</span><span class="sxs-lookup"><span data-stu-id="4cdc7-109">The [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) element defines the extended method as a code method.</span></span> <span data-ttu-id="4cdc7-110">[名称](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873)元素指定的扩展方法的名称。</span><span class="sxs-lookup"><span data-stu-id="4cdc7-110">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended method.</span></span> <span data-ttu-id="4cdc7-111">并且， [CodeReference](http://msdn.microsoft.com/en-us/70017b85-18d2-4f55-8357-92f309d5618b)元素指定的静态方法。</span><span class="sxs-lookup"><span data-stu-id="4cdc7-111">And, the [CodeReference](http://msdn.microsoft.com/en-us/70017b85-18d2-4f55-8357-92f309d5618b) element specifies the static method.</span></span> <span data-ttu-id="4cdc7-112">(您还可以添加[CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05)元素的成员[成员集](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3)元素。)</span><span class="sxs-lookup"><span data-stu-id="4cdc7-112">(You can also add the [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="script-methods"></a><span data-ttu-id="4cdc7-113">脚本方法</span><span class="sxs-lookup"><span data-stu-id="4cdc7-113">Script Methods</span></span>

<span data-ttu-id="4cdc7-114">脚本方法定义其值是脚本的输出的方法。</span><span class="sxs-lookup"><span data-stu-id="4cdc7-114">A script method defines a method whose value is the output of a script.</span></span> <span data-ttu-id="4cdc7-115">在以下示例中， **ConvertToDateTime**方法添加到[System.Management.Managementobject？Displayproperty =](/dotnet/api/System.Management.ManagementObject)类型。</span><span class="sxs-lookup"><span data-stu-id="4cdc7-115">In the following example, the **ConvertToDateTime** method is added to the [System.Management.Managementobject?Displayproperty=Fullname](/dotnet/api/System.Management.ManagementObject) type.</span></span> <span data-ttu-id="4cdc7-116">[ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c)元素定义的扩展的方法作为脚本方法。</span><span class="sxs-lookup"><span data-stu-id="4cdc7-116">The [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) element defines the extended method as a script method.</span></span> <span data-ttu-id="4cdc7-117">[名称](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873)元素指定的扩展方法的名称。</span><span class="sxs-lookup"><span data-stu-id="4cdc7-117">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended method.</span></span> <span data-ttu-id="4cdc7-118">并且，[脚本](http://msdn.microsoft.com/en-us/1937ad1b-bb2b-4512-9864-01fc0767d46f)元素指定的脚本的生成方法值。</span><span class="sxs-lookup"><span data-stu-id="4cdc7-118">And, the [Script](http://msdn.microsoft.com/en-us/1937ad1b-bb2b-4512-9864-01fc0767d46f) element specifies the script that generates the method value.</span></span> <span data-ttu-id="4cdc7-119">(您还可以添加[ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c)元素的成员[成员集](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3)元素。)</span><span class="sxs-lookup"><span data-stu-id="4cdc7-119">(You can also add the [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4cdc7-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="4cdc7-120">See Also</span></span>

[<span data-ttu-id="4cdc7-121">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4cdc7-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)