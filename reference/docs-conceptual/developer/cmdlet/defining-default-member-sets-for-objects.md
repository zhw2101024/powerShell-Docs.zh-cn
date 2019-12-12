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
# <a name="defining-default-member-sets-for-objects"></a><span data-ttu-id="7e4eb-102">定义对象的默认成员集</span><span class="sxs-lookup"><span data-stu-id="7e4eb-102">Defining Default Member Sets for Objects</span></span>

<span data-ttu-id="7e4eb-103">Windows PowerShell 使用 PSStandardMembers 成员集来定义对象的默认属性集。</span><span class="sxs-lookup"><span data-stu-id="7e4eb-103">The PSStandardMembers member set is used by Windows PowerShell to define the default property sets for an object.</span></span> <span data-ttu-id="7e4eb-104">诸如格式设置 cmdlet 这样的命令可以使用默认属性集来仅显示由属性集定义的属性。</span><span class="sxs-lookup"><span data-stu-id="7e4eb-104">The default property sets can be used by commands such as the formatting cmdlets to display only those properties that are defined by the property set.</span></span> <span data-ttu-id="7e4eb-105">默认属性集包括 DefaultDisplayProperty、使用 defaultdisplaypropertyset 和 DefaultKeyPropertySet。</span><span class="sxs-lookup"><span data-stu-id="7e4eb-105">The default property sets include DefaultDisplayProperty, DefaultDisplayPropertySet, and DefaultKeyPropertySet.</span></span> <span data-ttu-id="7e4eb-106">Windows PowerShell 将忽略所有其他成员集以及添加到 PSStandardMembers 成员集的任何其他属性集。</span><span class="sxs-lookup"><span data-stu-id="7e4eb-106">Windows PowerShell ignores all other member sets and any other property sets added to the PSStandardMembers member set.</span></span>

## <a name="member-set-for-systemdiagnosticsprocess"></a><span data-ttu-id="7e4eb-107">用于 system.exception 的成员集</span><span class="sxs-lookup"><span data-stu-id="7e4eb-107">Member Set for System.Diagnostics.Process</span></span>

<span data-ttu-id="7e4eb-108">在下面的示例中，PSStandardMembers 成员集定义了使用 defaultdisplaypropertyset 属性[集。](/dotnet/api/System.Diagnostics.Process)</span><span class="sxs-lookup"><span data-stu-id="7e4eb-108">In the following example, the PSStandardMembers member set defines the DefaultDisplayPropertySet property set for [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects.</span></span> <span data-ttu-id="7e4eb-109">此属性集由[格式列表](/powershell/module/Microsoft.PowerShell.Utility/Format-List)cmdlet 使用。</span><span class="sxs-lookup"><span data-stu-id="7e4eb-109">This property set is used by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span>

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

<span data-ttu-id="7e4eb-110">以下输出显示了由[格式列表](/powershell/module/Microsoft.PowerShell.Utility/Format-List)cmdlet 返回的默认属性。</span><span class="sxs-lookup"><span data-stu-id="7e4eb-110">The following output shows the default properties returned by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span> <span data-ttu-id="7e4eb-111">只为每个进程对象返回 `Id`、`Handles`、`CPU`和 `Name` 属性。</span><span class="sxs-lookup"><span data-stu-id="7e4eb-111">Only the `Id`, `Handles`, `CPU`, and `Name` properties are returned for each process object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7e4eb-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7e4eb-112">See Also</span></span>

[<span data-ttu-id="7e4eb-113">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7e4eb-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
