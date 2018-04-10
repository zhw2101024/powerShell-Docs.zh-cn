---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 3b2c268cd10d7c421b3d1fc73a7bbeaa4714f5fc
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="authoring-improvements-using-powershell-ise"></a><span data-ttu-id="344b5-102">使用 PowerShell ISE 创作改进</span><span class="sxs-lookup"><span data-stu-id="344b5-102">Authoring Improvements using PowerShell ISE</span></span>

<span data-ttu-id="344b5-103">由于以下改进，现在在 Windows PowerShell ISE 中创作 DSC 配置的操作要容易得多：</span><span class="sxs-lookup"><span data-stu-id="344b5-103">Authoring DSC configurations in Windows PowerShell ISE is much easier, thanks to the following improvements:</span></span>

- <span data-ttu-id="344b5-104">在其中的某个空行上输入 **Ctrl+Space**，列出**配置**块或**节点**块中的 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="344b5-104">List all DSC resources within a **configuration** block or **node** block by entering **Ctrl+Space** on a blank line within it.</span></span>
- <span data-ttu-id="344b5-105">属于**枚举**类型的资源属性的自动完成。</span><span class="sxs-lookup"><span data-stu-id="344b5-105">Automatic completion on resource properties that are of the **enumeration** type.</span></span>
- <span data-ttu-id="344b5-106">DSC 资源的 **DependsOn** 属性的自动完成基于配置中的其他资源实例。</span><span class="sxs-lookup"><span data-stu-id="344b5-106">Automatic completion on the **DependsOn** property of DSC resources, based on other resource instances in the configuration.</span></span>
- <span data-ttu-id="344b5-107">使用“Tab”更好地完成资源属性值。</span><span class="sxs-lookup"><span data-stu-id="344b5-107">Better tab completion of resource property values.</span></span>

<span data-ttu-id="344b5-108">**注意：**在你可以使用“Ctrl+Space”列出选项之前，资源属性值必须为空字符串。</span><span class="sxs-lookup"><span data-stu-id="344b5-108">**Note:** You must have an empty string for resource property values before you can use Ctrl+Space to list the options.</span></span> <span data-ttu-id="344b5-109">按 **Tab** 循环显示选项。</span><span class="sxs-lookup"><span data-stu-id="344b5-109">Pressing **Tab** cycles through options.</span></span>