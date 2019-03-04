---
title: Cmdlet 开发指南 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- development guidelines [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], development guidelines
ms.assetid: c30cc3c0-e958-4a8f-b81f-1e38de772f13
caps.latest.revision: 14
ms.openlocfilehash: 89c7682e87fa6f389349fc44275be0d2ffc83957
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857603"
---
# <a name="cmdlet-development-guidelines"></a><span data-ttu-id="2d099-102">Cmdlet 开发指南</span><span class="sxs-lookup"><span data-stu-id="2d099-102">Cmdlet Development Guidelines</span></span>

<span data-ttu-id="2d099-103">在本部分中的主题提供可用于生成格式正确的 cmdlet 的开发指南。</span><span class="sxs-lookup"><span data-stu-id="2d099-103">The topics in this section provide development guidelines that you can use to produce well-formed cmdlets.</span></span> <span data-ttu-id="2d099-104">通过利用提供通过 Windows PowerShell 运行时并遵循以下准则的常见功能，可以开发可靠 cmdlet 最小的工作量，并向用户提供一致的体验。</span><span class="sxs-lookup"><span data-stu-id="2d099-104">By leveraging the common functionality provided by the Windows PowerShell runtime and by following these guidelines, you can develop robust cmdlets with minimal effort and provide the user with a consistent experience.</span></span> <span data-ttu-id="2d099-105">此外，您将降低测试负担，因为常见功能不需要重新测试。</span><span class="sxs-lookup"><span data-stu-id="2d099-105">Additionally, you will reduce the test burden because common functionality does not require retesting.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="2d099-106">本节内容</span><span class="sxs-lookup"><span data-stu-id="2d099-106">In This Section</span></span>

- [<span data-ttu-id="2d099-107">所需的开发指导原则</span><span class="sxs-lookup"><span data-stu-id="2d099-107">Required Development Guidelines</span></span>](./required-development-guidelines.md)

- [<span data-ttu-id="2d099-108">强烈建议的开发指导原则</span><span class="sxs-lookup"><span data-stu-id="2d099-108">Strongly Encouraged Development Guidelines</span></span>](./strongly-encouraged-development-guidelines.md)

- [<span data-ttu-id="2d099-109">咨询开发指导原则</span><span class="sxs-lookup"><span data-stu-id="2d099-109">Advisory Development Guidelines</span></span>](./advisory-development-guidelines.md)

## <a name="see-also"></a><span data-ttu-id="2d099-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2d099-110">See Also</span></span>

[<span data-ttu-id="2d099-111">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2d099-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="2d099-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="2d099-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)