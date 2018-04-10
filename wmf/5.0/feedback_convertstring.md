---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 302a347b0f4c9c322f7701e8d6a721f9ffba9b59
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="convert-string"></a><span data-ttu-id="be34e-102">Convert-String</span><span class="sxs-lookup"><span data-stu-id="be34e-102">Convert-String</span></span>
<span data-ttu-id="be34e-103">**Convert-String** 公开“魔法替换”功能。</span><span class="sxs-lookup"><span data-stu-id="be34e-103">**Convert-String** exposes "replace by magic" functionality.</span></span> <span data-ttu-id="be34e-104">提供所需文本外观的前后对照示例，**Convert-String** 将自动设置文本格式。</span><span class="sxs-lookup"><span data-stu-id="be34e-104">Provide before and after examples of how you want text to look, and **Convert-String** formats your text automatically.</span></span> <span data-ttu-id="be34e-105">以下是一个演示：取某人的名字和姓氏，并替换为其姓氏、逗号、姓氏（拼音）首字母和句点。</span><span class="sxs-lookup"><span data-stu-id="be34e-105">Here's a demo - taking somebody's first and last name, and replacing it with their last name, a comma, the first initial of their last name, and a dot.</span></span> <span data-ttu-id="be34e-106">使用正则表达式进行尝试，并查看所用时间。</span><span class="sxs-lookup"><span data-stu-id="be34e-106">Try it with a regex, and see how long it takes you.</span></span>

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```