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
ms.openlocfilehash: e8185eb7221a3be0445eddc537dbca89478c74f2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859793"
---
# <a name="defining-default-member-sets-for-objects"></a><span data-ttu-id="64f83-102">定义对象的默认成员集</span><span class="sxs-lookup"><span data-stu-id="64f83-102">Defining Default Member Sets for Objects</span></span>

<span data-ttu-id="64f83-103">Windows PowerShell 使用 PSStandardMembers 成员集来定义对象的默认属性集。</span><span class="sxs-lookup"><span data-stu-id="64f83-103">The PSStandardMembers member set is used by Windows PowerShell to define the default property sets for an object.</span></span> <span data-ttu-id="64f83-104">例如格式设置 cmdlet 的命令可以使用默认属性集以仅显示那些属性所定义的属性集。</span><span class="sxs-lookup"><span data-stu-id="64f83-104">The default property sets can be used by commands such as the formatting cmdlets to display only those properties that are defined by the property set.</span></span> <span data-ttu-id="64f83-105">默认属性集包括 DefaultDisplayProperty、 DefaultDisplayPropertySet 和 DefaultKeyPropertySet。</span><span class="sxs-lookup"><span data-stu-id="64f83-105">The default property sets include DefaultDisplayProperty, DefaultDisplayPropertySet, and DefaultKeyPropertySet.</span></span> <span data-ttu-id="64f83-106">Windows PowerShell 将忽略所有其他成员集和添加到 PSStandardMembers 成员集的任何其他属性集。</span><span class="sxs-lookup"><span data-stu-id="64f83-106">Windows PowerShell ignores all other member sets and any other property sets added to the PSStandardMembers member set.</span></span>

## <a name="member-set-for-systemdiagnosticsprocess"></a><span data-ttu-id="64f83-107">System.Diagnostics.Process 的成员集</span><span class="sxs-lookup"><span data-stu-id="64f83-107">Member Set for System.Diagnostics.Process</span></span>

<span data-ttu-id="64f83-108">在以下示例中，PSStandardMembers 成员集定义 DefaultDisplayPropertySet 属性设置为[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)对象。</span><span class="sxs-lookup"><span data-stu-id="64f83-108">In the following example, the PSStandardMembers member set defines the DefaultDisplayPropertySet property set for [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects.</span></span> <span data-ttu-id="64f83-109">设置此属性由[Format-list](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="64f83-109">This property set is used by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span>
<span data-ttu-id="64f83-110">在以下示例中，PSStandardMembers 成员集定义 DefaultDisplayPropertySet 属性设置为[System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process)对象。</span><span class="sxs-lookup"><span data-stu-id="64f83-110">In the following example, the PSStandardMembers member set defines the DefaultDisplayPropertySet property set for [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects.</span></span> <span data-ttu-id="64f83-111">设置此属性由[Format-list](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="64f83-111">This property set is used by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span>

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

<span data-ttu-id="64f83-112">下面的输出显示返回的默认属性[Format-list](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="64f83-112">The following output shows the default properties returned by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span> <span data-ttu-id="64f83-113">仅`Id`， `Handles`， `CPU`，和`Name`对于每个进程对象返回的属性。</span><span class="sxs-lookup"><span data-stu-id="64f83-113">Only the `Id`, `Handles`, `CPU`, and `Name` properties are returned for each process object.</span></span>
<span data-ttu-id="64f83-114">下面的输出显示返回的默认属性[Format-list](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="64f83-114">The following output shows the default properties returned by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span> <span data-ttu-id="64f83-115">仅`Id`， `Handles`， `CPU`，和`Name`对于每个进程对象返回的属性。</span><span class="sxs-lookup"><span data-stu-id="64f83-115">Only the `Id`, `Handles`, `CPU`, and `Name` properties are returned for each process object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="64f83-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="64f83-116">See Also</span></span>

[<span data-ttu-id="64f83-117">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="64f83-117">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
