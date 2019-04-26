---
title: 定义默认成员设置为对象 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 77f94326-8ffe-4d40-bd2a-b79fb0b4a4e5
caps.latest.revision: 8
ms.openlocfilehash: 2d634e7638ec0e0117d65ca0b2d08e68f0068a03
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068243"
---
# <a name="defining-default-member-sets-for-objects"></a>定义对象的默认成员集

Windows PowerShell 使用 PSStandardMembers 成员集来定义对象的默认属性集。 例如格式设置 cmdlet 的命令可以使用默认属性集以仅显示那些属性所定义的属性集。 默认属性集包括 DefaultDisplayProperty、 DefaultDisplayPropertySet 和 DefaultKeyPropertySet。 Windows PowerShell 将忽略所有其他成员集和添加到 PSStandardMembers 成员集的任何其他属性集。

## <a name="member-set-for-systemdiagnosticsprocess"></a>System.Diagnostics.Process 的成员集

在以下示例中，PSStandardMembers 成员集定义 DefaultDisplayPropertySet 属性设置为[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)对象。 设置此属性由[Format-list](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet。

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

下面的输出显示返回的默认属性[Format-list](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet。 仅`Id`， `Handles`， `CPU`，和`Name`对于每个进程对象返回的属性。

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
