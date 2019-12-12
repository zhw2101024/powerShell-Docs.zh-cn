---
title: 定义对象的默认成员集 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 77f94326-8ffe-4d40-bd2a-b79fb0b4a4e5
caps.latest.revision: 8
ms.openlocfilehash: 2d634e7638ec0e0117d65ca0b2d08e68f0068a03
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369776"
---
# <a name="defining-default-member-sets-for-objects"></a>定义对象的默认成员集

Windows PowerShell 使用 PSStandardMembers 成员集来定义对象的默认属性集。 诸如格式设置 cmdlet 这样的命令可以使用默认属性集来仅显示由属性集定义的属性。 默认属性集包括 DefaultDisplayProperty、使用 defaultdisplaypropertyset 和 DefaultKeyPropertySet。 Windows PowerShell 将忽略所有其他成员集以及添加到 PSStandardMembers 成员集的任何其他属性集。

## <a name="member-set-for-systemdiagnosticsprocess"></a>用于 system.exception 的成员集

在下面的示例中，PSStandardMembers 成员集定义了使用 defaultdisplaypropertyset 属性[集。](/dotnet/api/System.Diagnostics.Process) 此属性集由[格式列表](/powershell/module/Microsoft.PowerShell.Utility/Format-List)cmdlet 使用。

```xml
<Type>
  <Name>System.Diagnostics.Process</Name>
  <Members>
    <MemberSet>
     <Name>PSStandardMembers</Name>
     <Members>
       <PropertySet>
         <Name>DefaultDisplayPropertySet</Name>
         <ReferencedProperties>
           <Name>Id</Name>
           <Name>Handles</Name>
           <Name>CPU</Name>
           <Name>Name</Name>
         </ReferencedProperties>
      </PropertySet>
    </Members>
  </MemberSet>
```

以下输出显示了由[格式列表](/powershell/module/Microsoft.PowerShell.Utility/Format-List)cmdlet 返回的默认属性。 只为每个进程对象返回 `Id`、`Handles`、`CPU`和 `Name` 属性。

```powershell
Get-Process | format-list
```

```output
Id      : 2036
Handles : 27
CPU     :
Name    : AEADISRV

Id      : 272
Handles : 38
CPU     :
Name    : agrsmsvc
...
```

## <a name="see-also"></a>另请参阅

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
