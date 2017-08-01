---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "限制命令时的注意事项"
ms.technology: powershell
ms.openlocfilehash: 0b4396ee130d99c42f613c1b79193c236ad472e7
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: zh-CN
---
### <a name="considerations-when-limiting-commands"></a><span data-ttu-id="25780-103">限制命令时的注意事项</span><span class="sxs-lookup"><span data-stu-id="25780-103">Considerations When Limiting Commands</span></span>
<span data-ttu-id="25780-104">执行此步骤时有一个重点。</span><span class="sxs-lookup"><span data-stu-id="25780-104">There is one important point to make about this step.</span></span>
<span data-ttu-id="25780-105">将通过 JEA 公开的所有功能置于仅限管理员的区域，这至关重要。</span><span class="sxs-lookup"><span data-stu-id="25780-105">It is critical that all capabilities exposed through JEA are located in administrator-restricted areas.</span></span>
<span data-ttu-id="25780-106">非管理员用户应不能修改通过 JEA 终结点使用的脚本。</span><span class="sxs-lookup"><span data-stu-id="25780-106">Non-administrator users should not have the capability to modify the scripts used through JEA endpoints.</span></span>

<span data-ttu-id="25780-107">关于这一点请注意，切勿允许 JEA 用户覆盖 JEA 配置和其 JEA 会话中已列入白名单的脚本。</span><span class="sxs-lookup"><span data-stu-id="25780-107">On a related note, it is critical that you do not give JEA users the ability to overwrite JEA configurations and whitelisted scripts within their JEA sessions.</span></span>
<span data-ttu-id="25780-108">公开 `Copy-Item` 等命令时请格外小心！</span><span class="sxs-lookup"><span data-stu-id="25780-108">Be extremely careful when exposing commands like `Copy-Item`!</span></span>

