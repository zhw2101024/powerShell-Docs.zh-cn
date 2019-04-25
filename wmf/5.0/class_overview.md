---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 5919a68c87ae8827a1b97befc653bb74713f33fe
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085773"
---
# <a name="creating-custom-types-using-powershell-classes"></a><span data-ttu-id="2d2f1-102">使用 PowerShell 类创建自定义类型</span><span class="sxs-lookup"><span data-stu-id="2d2f1-102">Creating Custom Types using PowerShell Classes</span></span>

<span data-ttu-id="2d2f1-103">我们使用类似于其他面向对象的编程语言的语法和语义改进了用于定义类和其他用户定义的类型的 PowerShell 语言。</span><span class="sxs-lookup"><span data-stu-id="2d2f1-103">We’ve improved the PowerShell language for defining classes and other user-defined types by using formal syntax and semantics that are similar to other object-oriented programming languages.</span></span> <span data-ttu-id="2d2f1-104">目标是使开发人员和 IT 专业人员在更广泛的用例中使用 PowerShell，从而简化 PowerShell 项目开发（如 DSC 资源），并加速覆盖管理面。</span><span class="sxs-lookup"><span data-stu-id="2d2f1-104">The goal is to enable developers and IT professionals to embrace PowerShell for a wider range of use cases, simplify development of PowerShell artifacts (such as DSC resources), and accelerate coverage of management surfaces.</span></span>

## <a name="supported-scenarios-in-this-release"></a><span data-ttu-id="2d2f1-105">此版本中受支持的方案</span><span class="sxs-lookup"><span data-stu-id="2d2f1-105">Supported scenarios in this release</span></span>

-   <span data-ttu-id="2d2f1-106">使用 PowerShell 语言来定义 DSC 资源和与其关联的类型</span><span class="sxs-lookup"><span data-stu-id="2d2f1-106">Define DSC resources and their associated types by using the PowerShell language</span></span>
-   <span data-ttu-id="2d2f1-107">使用熟悉的面向对象的编程构造（例如类、属性、方法等）在 PowerShell 中定义自定义类型。</span><span class="sxs-lookup"><span data-stu-id="2d2f1-107">Define custom types in PowerShell by using familiar object-oriented programming constructs, such as classes, properties, methods, etc.</span></span>
-   <span data-ttu-id="2d2f1-108">使用 PowerShell 中的类和基类 DSC 资源的继承支持</span><span class="sxs-lookup"><span data-stu-id="2d2f1-108">Inheritance support with class in PowerShell and class base DSC resource</span></span>
-   <span data-ttu-id="2d2f1-109">使用 PowerShell 语言调试类型</span><span class="sxs-lookup"><span data-stu-id="2d2f1-109">Debug types by using the PowerShell language</span></span>
-   <span data-ttu-id="2d2f1-110">使用正式的机制以及适当的级别生成和处理异常</span><span class="sxs-lookup"><span data-stu-id="2d2f1-110">Generate and handle exceptions by using formal mechanisms, and at the right level</span></span>
