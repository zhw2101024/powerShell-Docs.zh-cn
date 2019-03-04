---
title: Cmdlet 类声明 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], declaring
- declaring cmdlets [PowerShell SDK]
ms.assetid: 1fcc4c5e-0c75-496c-a712-5f844e310576
caps.latest.revision: 14
ms.openlocfilehash: 3e410087438ac99526049f99e5c768c017a29848
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854443"
---
# <a name="cmdlet-class-declaration"></a><span data-ttu-id="3cc50-102">Cmdlet 类声明</span><span class="sxs-lookup"><span data-stu-id="3cc50-102">Cmdlet Class Declaration</span></span>

<span data-ttu-id="3cc50-103">通过指定 Microsoft.NET Framework 类声明为 cmdlet **Cmdlet**作为元数据类的属性。</span><span class="sxs-lookup"><span data-stu-id="3cc50-103">A Microsoft .NET Framework class is declared as a cmdlet by specifying the **Cmdlet** attribute as metadata for the class.</span></span> <span data-ttu-id="3cc50-104">( **Cmdlet**属性是唯一的必需的属性的所有 cmdlet 为)。</span><span class="sxs-lookup"><span data-stu-id="3cc50-104">(The **Cmdlet** attribute is the only required attribute for all cmdlets).</span></span> <span data-ttu-id="3cc50-105">当指定**Cmdlet**属性，则必须指定标识向用户 cmdlet 的动词-名词对。</span><span class="sxs-lookup"><span data-stu-id="3cc50-105">When you specify the **Cmdlet** attribute, you must specify the verb-and-noun pair that identifies the cmdlet to the user.</span></span> <span data-ttu-id="3cc50-106">并且，必须说明该 cmdlet 支持的 Windows PowerShell 功能。</span><span class="sxs-lookup"><span data-stu-id="3cc50-106">And, you must describe the Windows PowerShell functionality that the cmdlet supports.</span></span> <span data-ttu-id="3cc50-107">详细了解用于指定的声明语法**Cmdlet**属性，请参阅[Cmdlet 特性声明](./cmdlet-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="3cc50-107">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

> [!NOTE]
> <span data-ttu-id="3cc50-108">**Cmdlet**属性定义由[System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute)类。</span><span class="sxs-lookup"><span data-stu-id="3cc50-108">The **Cmdlet** attribute is defined by the [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) class.</span></span> <span data-ttu-id="3cc50-109">此类的属性对应于声明属性时，将使用的声明参数。</span><span class="sxs-lookup"><span data-stu-id="3cc50-109">The properties of this class correspond to the declaration parameters that are used when you declare the attribute.</span></span>

## <a name="nouns"></a><span data-ttu-id="3cc50-110">名词</span><span class="sxs-lookup"><span data-stu-id="3cc50-110">Nouns</span></span>

<span data-ttu-id="3cc50-111">该 cmdlet 的名词指定 cmdlet 作用的资源。</span><span class="sxs-lookup"><span data-stu-id="3cc50-111">The noun of the cmdlet specifies the resources upon which the cmdlet acts.</span></span> <span data-ttu-id="3cc50-112">（） 名词，用于 cmdlet 与其他 cmdlet 区分开来。</span><span class="sxs-lookup"><span data-stu-id="3cc50-112">The noun differentiates your cmdlets from other cmdlets.</span></span>

<span data-ttu-id="3cc50-113">Cmdlet 名称中的名词必须是具体而言，对于泛型名词，如*server*，最好是添加一个短前缀，用于你的资源与其他类似资源区分开来。</span><span class="sxs-lookup"><span data-stu-id="3cc50-113">Nouns in cmdlet names must be specific, and in the case of generic nouns, such as *server*, it is best to add a short prefix that differentiates your resource from other similar resources.</span></span> <span data-ttu-id="3cc50-114">例如，包括带前缀的名词的 cmdlet 名称是`Get-SQLServer`。</span><span class="sxs-lookup"><span data-stu-id="3cc50-114">For example, a cmdlet name that includes a noun with a prefix is `Get-SQLServer`.</span></span> <span data-ttu-id="3cc50-115">特定名词具有更多常规谓词的组合使用户能够快速找到该 cmdlet 通过其操作，然后按资源标识该 cmdlet，同时避免不必要的 cmdlet 名称重复。</span><span class="sxs-lookup"><span data-stu-id="3cc50-115">The combination of a specific noun with a more general verb enables the user to quickly locate the cmdlet by its action and then identify the cmdlet by its resource while avoiding unnecessary cmdlet name duplication.</span></span>

<span data-ttu-id="3cc50-116">不能在 cmdlet 名称中使用的特殊字符的列表，请参阅[所需开发指导原则](./required-development-guidelines.md)。</span><span class="sxs-lookup"><span data-stu-id="3cc50-116">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="verbs"></a><span data-ttu-id="3cc50-117">谓词</span><span class="sxs-lookup"><span data-stu-id="3cc50-117">Verbs</span></span>

<span data-ttu-id="3cc50-118">如果指定一个谓词，开发指导原则将要求你使用某一 Windows PowerShell 提供的预定义的谓词。</span><span class="sxs-lookup"><span data-stu-id="3cc50-118">When you specify a verb, the development guidelines require you to use one of the predefined verbs provided by Windows PowerShell.</span></span> <span data-ttu-id="3cc50-119">通过使用这些预定义的谓词之一，您需要确保您编写的 cmdlet 和由 Microsoft 和其他人编写的 cmdlet 之间的一致性。</span><span class="sxs-lookup"><span data-stu-id="3cc50-119">By using one of these predefined verbs, you will ensure consistency between the cmdlets that you write and the cmdlets that are written by Microsoft and by others.</span></span> <span data-ttu-id="3cc50-120">例如，"Get"谓词用于检索数据的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3cc50-120">For example, the "Get" verb is used for cmdlets that retrieve data.</span></span>

<span data-ttu-id="3cc50-121">有关谓词的指导原则的详细信息，请参阅[Cmdlet 的动词名称](./approved-verbs-for-windows-powershell-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="3cc50-121">For more information about guidelines for verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span> <span data-ttu-id="3cc50-122">不能在 cmdlet 名称中使用的特殊字符的列表，请参阅[所需开发指导原则](./required-development-guidelines.md)。</span><span class="sxs-lookup"><span data-stu-id="3cc50-122">For a list of special characters that cannot be used in cmdlet names, see [Required Development Guidelines](./required-development-guidelines.md).</span></span>

## <a name="supporting-windows-powershell-functionality"></a><span data-ttu-id="3cc50-123">支持 Windows PowerShell 功能</span><span class="sxs-lookup"><span data-stu-id="3cc50-123">Supporting Windows PowerShell Functionality</span></span>

<span data-ttu-id="3cc50-124">**Cmdlet**属性还允许您指定 cmdlet 支持一些提供的 Windows PowerShell 的常见功能。</span><span class="sxs-lookup"><span data-stu-id="3cc50-124">The **Cmdlet** attribute also allows you to specify that your cmdlet supports some of the common functionality that is provided by Windows PowerShell.</span></span> <span data-ttu-id="3cc50-125">这包括对常见功能，例如用户反馈确认 （称为 ShouldProcess 功能的支持） 的支持以及对事务的支持。</span><span class="sxs-lookup"><span data-stu-id="3cc50-125">This includes support for common functionality such as user feedback confirmation (referred to as support for the ShouldProcess feature) and support for transactions.</span></span> <span data-ttu-id="3cc50-126">（对事务的支持引入了在 Windows PowerShell 2.0 中）。</span><span class="sxs-lookup"><span data-stu-id="3cc50-126">(Support for transactions was introduced in Windows PowerShell 2.0).</span></span>

<span data-ttu-id="3cc50-127">详细了解用于指定的声明语法**Cmdlet**属性，请参阅[Cmdlet 特性声明](./cmdlet-attribute-declaration.md)。</span><span class="sxs-lookup"><span data-stu-id="3cc50-127">For more information about the declaration syntax that is used to specify the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="cmdlet-class-definition"></a><span data-ttu-id="3cc50-128">Cmdlet 类定义</span><span class="sxs-lookup"><span data-stu-id="3cc50-128">Cmdlet Class Definition</span></span>

<span data-ttu-id="3cc50-129">以下代码是 GetProc cmdlet 类的定义。</span><span class="sxs-lookup"><span data-stu-id="3cc50-129">The following code is the definition for a GetProc cmdlet class.</span></span> <span data-ttu-id="3cc50-130">请注意，使用大小写，Pascal 和类的名称，包括动词和名词的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3cc50-130">Notice that Pascal casing is used and that the name of the class includes the verb and noun of the cmdlet.</span></span>

[!code-csharp[GetProcessSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L33-L34 "GetProcessSample01.cs")]

## <a name="pascal-casing"></a><span data-ttu-id="3cc50-131">Pascal 大小写</span><span class="sxs-lookup"><span data-stu-id="3cc50-131">Pascal Casing</span></span>

<span data-ttu-id="3cc50-132">当命名 cmdlet 时，使用 Pascal 大小写。</span><span class="sxs-lookup"><span data-stu-id="3cc50-132">When you name cmdlets, use Pascal casing.</span></span> <span data-ttu-id="3cc50-133">例如，`Get-Item`和`Get-ItemProperty`cmdlet 显示命名 cmdlet 时使用的大小写的正确方法。</span><span class="sxs-lookup"><span data-stu-id="3cc50-133">For example, the `Get-Item` and `Get-ItemProperty` cmdlets show the correct way to use capitalization when you are naming cmdlets.</span></span>

## <a name="see-also"></a><span data-ttu-id="3cc50-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3cc50-134">See Also</span></span>

[<span data-ttu-id="3cc50-135">System.Management.Automation.Cmdletattribute</span><span class="sxs-lookup"><span data-stu-id="3cc50-135">System.Management.Automation.Cmdletattribute</span></span>](/dotnet/api/System.Management.Automation.CmdletAttribute)

[<span data-ttu-id="3cc50-136">CmdletAttribute Declaration</span><span class="sxs-lookup"><span data-stu-id="3cc50-136">CmdletAttribute Declaration</span></span>](./cmdlet-attribute-declaration.md)

[<span data-ttu-id="3cc50-137">Cmdlet 的动词名称</span><span class="sxs-lookup"><span data-stu-id="3cc50-137">Cmdlet Verb Names</span></span>](./approved-verbs-for-windows-powershell-commands.md)

[<span data-ttu-id="3cc50-138">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3cc50-138">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="3cc50-139">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="3cc50-139">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
