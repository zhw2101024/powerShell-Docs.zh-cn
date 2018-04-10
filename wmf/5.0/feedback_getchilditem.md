---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 62cccabd7c63c6ba928fc2bf8addd3d11483e90f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="63e7c-102">Get-ChildItem 具有 -Depth 参数</span><span class="sxs-lookup"><span data-stu-id="63e7c-102">Get-ChildItem has -Depth parameter</span></span>
<span data-ttu-id="63e7c-103">**Get-ChildItem** 现在具有 **–Depth** 参数，你可以将其与 **–Recurse** 一起使用来限制递归：</span><span class="sxs-lookup"><span data-stu-id="63e7c-103">**Get-ChildItem** now has a **–Depth** parameter you use with **–Recurse** to limit the recursion:</span></span>

<span data-ttu-id="63e7c-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span><span class="sxs-lookup"><span data-stu-id="63e7c-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span></span>

<span data-ttu-id="63e7c-105">目录：C:\\Users\\slee\\Downloads\\Example</span><span class="sxs-lookup"><span data-stu-id="63e7c-105">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="63e7c-106">模式 上次写入时间 长度 名称</span><span class="sxs-lookup"><span data-stu-id="63e7c-106">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="63e7c-107">d----- 4/14/2015 5:36 PM Depth0</span><span class="sxs-lookup"><span data-stu-id="63e7c-107">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="63e7c-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="63e7c-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="63e7c-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="63e7c-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="63e7c-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="63e7c-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="63e7c-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span><span class="sxs-lookup"><span data-stu-id="63e7c-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span></span>

<span data-ttu-id="63e7c-112">目录：C:\\Users\\slee\\Downloads\\Example</span><span class="sxs-lookup"><span data-stu-id="63e7c-112">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="63e7c-113">模式 上次写入时间 长度 名称</span><span class="sxs-lookup"><span data-stu-id="63e7c-113">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="63e7c-114">d----- 4/14/2015 5:36 PM Depth0</span><span class="sxs-lookup"><span data-stu-id="63e7c-114">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="63e7c-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="63e7c-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="63e7c-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="63e7c-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="63e7c-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="63e7c-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="63e7c-118">目录：C:\\Users\\slee\\Downloads\\Example\\Depth0</span><span class="sxs-lookup"><span data-stu-id="63e7c-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span></span>

<span data-ttu-id="63e7c-119">模式 上次写入时间 长度 名称</span><span class="sxs-lookup"><span data-stu-id="63e7c-119">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="63e7c-120">d----- 4/14/2015 5:33 PM Depth1</span><span class="sxs-lookup"><span data-stu-id="63e7c-120">d----- 4/14/2015 5:33 PM Depth1</span></span>