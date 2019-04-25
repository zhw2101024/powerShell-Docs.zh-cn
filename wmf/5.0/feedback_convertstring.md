---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 27541d903748738675917941dc6b60bc9acdc3f4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057785"
---
# <a name="convert-string"></a><span data-ttu-id="a4fb9-102">Convert-String</span><span class="sxs-lookup"><span data-stu-id="a4fb9-102">Convert-String</span></span>
<span data-ttu-id="a4fb9-103">**Convert-String** 公开“魔法替换”功能。</span><span class="sxs-lookup"><span data-stu-id="a4fb9-103">**Convert-String** exposes "replace by magic" functionality.</span></span> <span data-ttu-id="a4fb9-104">提供所需文本外观的前后对照示例，**Convert-String** 将自动设置文本格式。</span><span class="sxs-lookup"><span data-stu-id="a4fb9-104">Provide before and after examples of how you want text to look, and **Convert-String** formats your text automatically.</span></span> <span data-ttu-id="a4fb9-105">以下是一个演示：取某人的名字和姓氏，并替换为其姓氏、逗号、姓氏（拼音）首字母和句点。</span><span class="sxs-lookup"><span data-stu-id="a4fb9-105">Here's a demo - taking somebody's first and last name, and replacing it with their last name, a comma, the first initial of their last name, and a dot.</span></span> <span data-ttu-id="a4fb9-106">使用正则表达式进行尝试，并查看所用时间。</span><span class="sxs-lookup"><span data-stu-id="a4fb9-106">Try it with a regex, and see how long it takes you.</span></span>

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```
