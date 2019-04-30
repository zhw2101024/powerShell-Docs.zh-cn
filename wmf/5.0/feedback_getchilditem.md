---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: cc5d2d799c1292f68de5fb2360fcba220c2c010b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085259"
---
# <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="174aa-102">Get-ChildItem 具有 -Depth 参数</span><span class="sxs-lookup"><span data-stu-id="174aa-102">Get-ChildItem has -Depth parameter</span></span>
<span data-ttu-id="174aa-103">**Get-ChildItem** 现在具有 **–Depth** 参数，你可以将其与 **–Recurse** 一起使用来限制递归：</span><span class="sxs-lookup"><span data-stu-id="174aa-103">**Get-ChildItem** now has a **–Depth** parameter you use with **–Recurse** to limit the recursion:</span></span>

<span data-ttu-id="174aa-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span><span class="sxs-lookup"><span data-stu-id="174aa-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span></span>

<span data-ttu-id="174aa-105">目录：C:\\Users\\slee\\Downloads\\Example</span><span class="sxs-lookup"><span data-stu-id="174aa-105">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="174aa-106">模式 上次写入时间 长度 名称</span><span class="sxs-lookup"><span data-stu-id="174aa-106">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="174aa-107">d----- 4/14/2015 5:36 PM Depth0</span><span class="sxs-lookup"><span data-stu-id="174aa-107">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="174aa-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="174aa-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="174aa-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="174aa-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="174aa-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="174aa-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="174aa-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span><span class="sxs-lookup"><span data-stu-id="174aa-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span></span>

<span data-ttu-id="174aa-112">目录：C:\\Users\\slee\\Downloads\\Example</span><span class="sxs-lookup"><span data-stu-id="174aa-112">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="174aa-113">模式 上次写入时间 长度 名称</span><span class="sxs-lookup"><span data-stu-id="174aa-113">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="174aa-114">d----- 4/14/2015 5:36 PM Depth0</span><span class="sxs-lookup"><span data-stu-id="174aa-114">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="174aa-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="174aa-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="174aa-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="174aa-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="174aa-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="174aa-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="174aa-118">目录：C:\\Users\\slee\\Downloads\\Example\\Depth0</span><span class="sxs-lookup"><span data-stu-id="174aa-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span></span>

<span data-ttu-id="174aa-119">模式 上次写入时间 长度 名称</span><span class="sxs-lookup"><span data-stu-id="174aa-119">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="174aa-120">d----- 4/14/2015 5:33 PM Depth1</span><span class="sxs-lookup"><span data-stu-id="174aa-120">d----- 4/14/2015 5:33 PM Depth1</span></span>
