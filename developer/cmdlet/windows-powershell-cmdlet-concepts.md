---
title: Windows PowerShell Cmdlet 概念 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b3ef3f4-c626-4679-884f-406a37412b3e
caps.latest.revision: 16
ms.openlocfilehash: 2f84c57da7429462c69b2a020d9f8ac04f8d0f35
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855783"
---
# <a name="windows-powershell-cmdlet-concepts"></a><span data-ttu-id="2cab7-102">Windows PowerShell Cmdlet 概念</span><span class="sxs-lookup"><span data-stu-id="2cab7-102">Windows PowerShell Cmdlet Concepts</span></span>

<span data-ttu-id="2cab7-103">本部分介绍 cmdlet 如何工作。</span><span class="sxs-lookup"><span data-stu-id="2cab7-103">This section describes how cmdlets work.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="2cab7-104">本节内容</span><span class="sxs-lookup"><span data-stu-id="2cab7-104">In This Section</span></span>

<span data-ttu-id="2cab7-105">本部分包括以下主题。</span><span class="sxs-lookup"><span data-stu-id="2cab7-105">This section includes the following topics.</span></span>

<span data-ttu-id="2cab7-106">[Cmdlet 开发指导原则](./cmdlet-development-guidelines.md)本主题提供可用于生成格式正确的 cmdlet 的开发指南。</span><span class="sxs-lookup"><span data-stu-id="2cab7-106">[Cmdlet Development Guidelines](./cmdlet-development-guidelines.md) This topic provides development guidelines that can be used to produce well-formed cmdlets.</span></span>

<span data-ttu-id="2cab7-107">[Cmdlet 类声明](./cmdlet-class-declaration.md)本主题介绍 cmdlet 类声明。</span><span class="sxs-lookup"><span data-stu-id="2cab7-107">[Cmdlet Class Declaration](./cmdlet-class-declaration.md) This topic describes cmdlet class declaration.</span></span>

<span data-ttu-id="2cab7-108">[批准用于 Windows PowerShell 命令的动词](./approved-verbs-for-windows-powershell-commands.md)本主题列出了你在声明 cmdlet 类时，可以使用的预定义的 cmdlet 谓词。</span><span class="sxs-lookup"><span data-stu-id="2cab7-108">[Approved Verbs for Windows PowerShell Commands](./approved-verbs-for-windows-powershell-commands.md) This topic lists the predefined cmdlet verbs that you can use when you declare a cmdlet class.</span></span>

<span data-ttu-id="2cab7-109">[Cmdlet 输入处理方法](./cmdlet-input-processing-methods.md)本主题介绍允许 cmdlet 来执行预处理操作、 输入处理操作和发布的处理操作的方法。</span><span class="sxs-lookup"><span data-stu-id="2cab7-109">[Cmdlet Input Processing Methods](./cmdlet-input-processing-methods.md) This topic describes the methods that allow a cmdlet to perform preprocessing operations, input processing operations, and post processing operations.</span></span>

<span data-ttu-id="2cab7-110">[Cmdlet 参数](./cmdlet-parameters.md)本部分介绍了不同类型的参数，可以将添加到 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2cab7-110">[Cmdlet Parameters](./cmdlet-parameters.md) This section describes the different types of parameters that you can add to cmdlets.</span></span>

<span data-ttu-id="2cab7-111">[Cmdlet 属性](./cmdlet-attributes.md)本部分介绍用于将.NET Framework 类声明为 cmdlet，来声明作为 cmdlet 参数的字段和声明参数的输入的验证规则的属性。</span><span class="sxs-lookup"><span data-stu-id="2cab7-111">[Cmdlet Attributes](./cmdlet-attributes.md) This section describes the attributes that are used to declare .NET Framework classes as cmdlets, to declare fields as cmdlet parameters, and to declare input validation rules for parameters.</span></span>

<span data-ttu-id="2cab7-112">[Cmdlet 别名](./cmdlet-aliases.md)本主题介绍了 cmdlet 的别名。</span><span class="sxs-lookup"><span data-stu-id="2cab7-112">[Cmdlet Aliases](./cmdlet-aliases.md) This topic describes cmdlet aliases.</span></span>

<span data-ttu-id="2cab7-113">[Cmdlet 输出](./cmdlet-output.md)本部分介绍的 cmdlet 可以返回的输出以及如何定义和显示由 cmdlet 返回的对象的类型。</span><span class="sxs-lookup"><span data-stu-id="2cab7-113">[Cmdlet Output](./cmdlet-output.md) This section describes the type of output that cmdlets can return and how to define and display the objects that are returned by cmdlets.</span></span>

<span data-ttu-id="2cab7-114">[注册 Cmdlet](./modules-and-snap-ins.md)本部分介绍如何通过使用模块和管理单元注册 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2cab7-114">[Registering Cmdlets](./modules-and-snap-ins.md) This section describes how to register cmdlets by using modules and snap-ins.</span></span>

<span data-ttu-id="2cab7-115">[请求确认](./requesting-confirmation-from-cmdlets.md)本部分介绍它们对系统进行更改之前，cmdlet 如何请求来自用户的确认。</span><span class="sxs-lookup"><span data-stu-id="2cab7-115">[Requesting Confirmation](./requesting-confirmation-from-cmdlets.md) This section describes how cmdlets request confirmation from a user before they make a change to the system.</span></span>

<span data-ttu-id="2cab7-116">[Windows PowerShell 错误报告](./error-reporting-concepts.md)本部分介绍 cmdlet 如何报告的终止错误和非终止性错误，并介绍了如何解释错误记录。</span><span class="sxs-lookup"><span data-stu-id="2cab7-116">[Windows PowerShell Error Reporting](./error-reporting-concepts.md) This section describes how cmdlets report terminating errors and non-terminating errors, and it describes how to interpret error records.</span></span>

<span data-ttu-id="2cab7-117">[后台作业](./background-jobs.md)本主题说明了如何 cmdlet 可以执行其工作中不会干扰当前会话中执行的命令的后台作业。</span><span class="sxs-lookup"><span data-stu-id="2cab7-117">[Background Jobs](./background-jobs.md) This topic describes how cmdlets can perform their work within background jobs that do not interfere with the commands that are executing in the current session.</span></span>

<span data-ttu-id="2cab7-118">[调用 Cmdlet 和脚本内 Cmdlet](./invoking-cmdlets-and-scripts-within-a-cmdlet.md)本主题描述如何 cmdlet 可以调用其他 cmdlet 和脚本从其输入处理方法。</span><span class="sxs-lookup"><span data-stu-id="2cab7-118">[Invoking Cmdlets and Scripts Within a Cmdlet](./invoking-cmdlets-and-scripts-within-a-cmdlet.md) This topic describes how cmdlets can invoke other cmdlets and scripts from within their input processing methods.</span></span>

<span data-ttu-id="2cab7-119">[Cmdlet 可设置](./cmdlet-sets.md)本主题介绍如何使用基类，这些类创建的 cmdlet 集。</span><span class="sxs-lookup"><span data-stu-id="2cab7-119">[Cmdlet Sets](./cmdlet-sets.md) This topic describes using base classes to create sets of cmdlets.</span></span>

<span data-ttu-id="2cab7-120">[Windows PowerShell 会话状态](./windows-powershell-session-state.md)本主题介绍 Windows PowerShell 会话状态。</span><span class="sxs-lookup"><span data-stu-id="2cab7-120">[Windows PowerShell Session State](./windows-powershell-session-state.md) This topic describes Windows PowerShell session state.</span></span>
