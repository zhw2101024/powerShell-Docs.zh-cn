---
title: 如何创建一个 Windows PowerShell 管理单元 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], examples
ms.assetid: 71bd9b2c-5f2e-4aa8-b5fe-08c956540d37
caps.latest.revision: 10
ms.openlocfilehash: 73834cea1d90943cf954728d6295d8eb33e14f57
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859753"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a><span data-ttu-id="980a6-102">如何创建 Windows PowerShell 管理单元</span><span class="sxs-lookup"><span data-stu-id="980a6-102">How to Create a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="980a6-103">Windows PowerShell 管理单元提供了一种机制，用于注册的 shell，从而将扩展的 shell 功能的 cmdlet 和另一个 Windows PowerShell 提供程序集。</span><span class="sxs-lookup"><span data-stu-id="980a6-103">A Windows PowerShell snap-in provides a mechanism for registering sets of cmdlets and another Windows PowerShell provider with the shell, thus extending the functionality of the shell.</span></span> <span data-ttu-id="980a6-104">Windows PowerShell 管理单元可以所有 cmdlet 和提供程序中都注册一个程序集，或者它可以都注册一个特定的 cmdlet 和提供程序列表。</span><span class="sxs-lookup"><span data-stu-id="980a6-104">A Windows PowerShell snap-in can register all the cmdlets and providers in a single assembly, or it can register a specific list of cmdlets and providers.</span></span>

<span data-ttu-id="980a6-105">管理单元中的程序集应安装在受保护的目录，就像使用其他操作系统。</span><span class="sxs-lookup"><span data-stu-id="980a6-105">Snap-in assemblies should be installed in a protected directory, just as they would be with other operating systems.</span></span> <span data-ttu-id="980a6-106">否则，恶意用户可以使用不安全代码替换程序集。</span><span class="sxs-lookup"><span data-stu-id="980a6-106">Otherwise, malicious users can replace an assembly with unsafe code.</span></span>

## <a name="windows-powershell-snap-in-classes"></a><span data-ttu-id="980a6-107">Windows PowerShell 管理单元类</span><span class="sxs-lookup"><span data-stu-id="980a6-107">Windows PowerShell Snap-in Classes</span></span>

<span data-ttu-id="980a6-108">所有 Windows PowerShell 管理单元类都派生自[System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn)或[System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn)类。</span><span class="sxs-lookup"><span data-stu-id="980a6-108">All Windows PowerShell snap-in classes derive from the [System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) or [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) classes.</span></span>

## <a name="examples"></a><span data-ttu-id="980a6-109">示例</span><span class="sxs-lookup"><span data-stu-id="980a6-109">Examples</span></span>

<span data-ttu-id="980a6-110">[编写一个 Windows PowerShell 管理单元](./writing-a-windows-powershell-snap-in.md):此示例演示如何，若要创建用于注册的程序集中的所有 cmdlet 和提供程序的管理单元。</span><span class="sxs-lookup"><span data-stu-id="980a6-110">[Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md): This example shows how to create a snap-in that is used to register all the cmdlets and providers in an assembly.</span></span>

<span data-ttu-id="980a6-111">[编写自定义 Windows PowerShell 管理单元中](./writing-a-custom-windows-powershell-snap-in.md):此示例演示如何创建自定义管理单元，用于在单个程序集注册一组特定的 cmdlet 和提供程序可能会或可能不存在。</span><span class="sxs-lookup"><span data-stu-id="980a6-111">[Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md): This example shows how to create a custom snap-in that is used to register a specific set of cmdlets and providers that might or might not exist in a single assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="980a6-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="980a6-112">See Also</span></span>

[<span data-ttu-id="980a6-113">System.Management.Automation.Pssnapin</span><span class="sxs-lookup"><span data-stu-id="980a6-113">System.Management.Automation.Pssnapin</span></span>](/dotnet/api/System.Management.Automation.PSSnapIn)

[<span data-ttu-id="980a6-114">System.Management.Automation.Custompssnapin</span><span class="sxs-lookup"><span data-stu-id="980a6-114">System.Management.Automation.Custompssnapin</span></span>](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[<span data-ttu-id="980a6-115">注册 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="980a6-115">Registering Cmdlets</span></span>](./registering-cmdlets.md)

[<span data-ttu-id="980a6-116">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="980a6-116">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
