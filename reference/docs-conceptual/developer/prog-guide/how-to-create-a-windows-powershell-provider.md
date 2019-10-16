---
title: 如何创建 Windows PowerShell 提供程序 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide]
- providers [PowerShellProgrammer's Guide], creating
- Windows PowerShell Programmer's Guide, providers
ms.assetid: 863e48e9-7206-4c6a-a59a-2ab2d30396bc
caps.latest.revision: 5
ms.openlocfilehash: ffbf8028ba2b52e77d8e22c061baa9b8b67f6da3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366646"
---
# <a name="how-to-create-a-windows-powershell-provider"></a><span data-ttu-id="d9caa-102">如何创建 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="d9caa-102">How to Create a Windows PowerShell Provider</span></span>

<span data-ttu-id="d9caa-103">本部分介绍如何生成 Windows PowerShell 提供程序。</span><span class="sxs-lookup"><span data-stu-id="d9caa-103">This section describes how to build a Windows PowerShell provider.</span></span> <span data-ttu-id="d9caa-104">可以通过两种方式来考虑 Windows PowerShell 提供程序。</span><span class="sxs-lookup"><span data-stu-id="d9caa-104">A Windows PowerShell provider can be considered in two ways.</span></span> <span data-ttu-id="d9caa-105">对于用户，提供程序表示一组存储的数据。</span><span class="sxs-lookup"><span data-stu-id="d9caa-105">To the user, the provider represents a set of stored data.</span></span> <span data-ttu-id="d9caa-106">例如，存储的数据可以是 Internet Information Services （IIS）元数据库、Microsoft Windows 注册表、Windows 文件系统、Active Directory 以及 Windows PowerShell 存储的变量和别名数据。</span><span class="sxs-lookup"><span data-stu-id="d9caa-106">For example, the stored data can be the Internet Information Services (IIS) Metabase, the Microsoft Windows Registry, the Windows file system, Active Directory, and the variable and alias data stored by Windows PowerShell.</span></span>

<span data-ttu-id="d9caa-107">对于开发人员而言，Windows PowerShell 提供程序是用户与用户需要访问的数据之间的接口。</span><span class="sxs-lookup"><span data-stu-id="d9caa-107">To the developer, the Windows PowerShell provider is the interface between the user and the data that the user needs to access.</span></span> <span data-ttu-id="d9caa-108">从此角度来看，本节中所述的每种类型的提供程序支持一组特定的基类和接口，这些类和接口允许 Windows PowerShell 运行时以常见方式向用户公开特定的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d9caa-108">From this perspective, each type of provider described in this section supports a set of specific base classes and interfaces that allow the Windows PowerShell runtime to expose certain cmdlets to the user in a common way.</span></span>

## <a name="providers-provided-by-windows-powershell"></a><span data-ttu-id="d9caa-109">Windows PowerShell 提供的提供程序</span><span class="sxs-lookup"><span data-stu-id="d9caa-109">Providers Provided by Windows PowerShell</span></span>

<span data-ttu-id="d9caa-110">Windows PowerShell 提供了几个提供程序（例如 FileSystem 提供程序、注册表提供程序和别名提供程序），用于访问已知的数据存储区。</span><span class="sxs-lookup"><span data-stu-id="d9caa-110">Windows PowerShell provides several providers (such as the FileSystem provider, Registry provider, and Alias provider) that are used to access known data stores.</span></span> <span data-ttu-id="d9caa-111">有关 Windows PowerShell 提供的提供程序的详细信息，请使用以下命令访问联机帮助：</span><span class="sxs-lookup"><span data-stu-id="d9caa-111">For more information about the providers supplied by Windows PowerShell, use the following command to access online Help:</span></span>

<span data-ttu-id="d9caa-112">**PS > get-help about_providers**</span><span class="sxs-lookup"><span data-stu-id="d9caa-112">**PS>get-help about_providers**</span></span>

## <a name="accessing-the-stored-data-using-windows-powershell-paths"></a><span data-ttu-id="d9caa-113">使用 Windows PowerShell 路径访问存储的数据</span><span class="sxs-lookup"><span data-stu-id="d9caa-113">Accessing the Stored Data Using Windows PowerShell Paths</span></span>

<span data-ttu-id="d9caa-114">Windows powershell 运行时和通过使用 Windows PowerShell 路径以编程方式访问 windows PowerShell 提供程序。</span><span class="sxs-lookup"><span data-stu-id="d9caa-114">Windows PowerShell providers are accessible to the Windows PowerShell runtime and to commands programmatically through the use of Windows PowerShell paths.</span></span> <span data-ttu-id="d9caa-115">大多数情况下，这些路径用于通过提供程序直接访问数据。</span><span class="sxs-lookup"><span data-stu-id="d9caa-115">Most of the time, these paths are used to directly access the data through the provider.</span></span> <span data-ttu-id="d9caa-116">但是，某些路径可解析为提供程序内部路径，该路径允许 cmdlet 使用非 Windows PowerShell 应用程序编程接口（Api）来访问数据。</span><span class="sxs-lookup"><span data-stu-id="d9caa-116">However, some paths can be resolved to provider-internal paths that allow a cmdlet to use non-Windows PowerShell application programming interfaces (APIs) to access the data.</span></span> <span data-ttu-id="d9caa-117">有关 Windows powershell 提供程序在 Windows PowerShell 中的运行方式的详细信息，请参阅[Windows powershell 的工作](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)原理。</span><span class="sxs-lookup"><span data-stu-id="d9caa-117">For more information about how Windows PowerShell providers operate within Windows PowerShell, see [How Windows PowerShell Works](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).</span></span>

## <a name="exposing-provider-cmdlets-using-windows-powershell-drives"></a><span data-ttu-id="d9caa-118">使用 Windows PowerShell 驱动器公开提供程序 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d9caa-118">Exposing Provider Cmdlets Using Windows PowerShell Drives</span></span>

<span data-ttu-id="d9caa-119">Windows PowerShell 提供程序使用虚拟 Windows PowerShell 驱动器公开其支持的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d9caa-119">A Windows PowerShell provider exposes its supported cmdlets using virtual Windows PowerShell drives.</span></span> <span data-ttu-id="d9caa-120">Windows PowerShell 适用于 Windows PowerShell 驱动器的以下规则：</span><span class="sxs-lookup"><span data-stu-id="d9caa-120">Windows PowerShell applies the following rules for a Windows PowerShell drive:</span></span>

- <span data-ttu-id="d9caa-121">驱动器的名称可以是任何字母数字序列。</span><span class="sxs-lookup"><span data-stu-id="d9caa-121">The name of a drive can be any alphanumeric sequence.</span></span>

- <span data-ttu-id="d9caa-122">可以在路径上的任何有效点指定驱动器，称为 "根"。</span><span class="sxs-lookup"><span data-stu-id="d9caa-122">A drive can be specified at any valid point on a path, called a "root".</span></span>

- <span data-ttu-id="d9caa-123">可以为任何存储的数据（而不仅仅是文件系统）实现驱动器。</span><span class="sxs-lookup"><span data-stu-id="d9caa-123">A drive can be implemented for any stored data, not just the file system.</span></span>

- <span data-ttu-id="d9caa-124">每个驱动器都保留其自己的当前工作位置，允许用户在驱动器之间切换时保留上下文。</span><span class="sxs-lookup"><span data-stu-id="d9caa-124">Each drive keeps its own current working location, allowing the user to retain context when shifting between drives.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d9caa-125">本部分内容</span><span class="sxs-lookup"><span data-stu-id="d9caa-125">In This Section</span></span>

<span data-ttu-id="d9caa-126">下表列出了一些主题，这些主题包括彼此之间生成的代码示例。</span><span class="sxs-lookup"><span data-stu-id="d9caa-126">The following table lists topics that include code examples that build on each other.</span></span> <span data-ttu-id="d9caa-127">从第二个主题开始，Windows PowerShell 运行时可以初始化和取消初始化基本 Windows PowerShell 提供程序，下一主题添加了用于访问数据的功能，下一主题添加了用于操作数据的功能（存储的数据中的项）等。</span><span class="sxs-lookup"><span data-stu-id="d9caa-127">Starting with the second topic, the basic Windows PowerShell provider can be initialized and uninitialized by the Windows PowerShell runtime, the next topic adds functionality for accessing the data, the next topic adds functionality for manipulating the data (the items in the stored data), and so on.</span></span>

|<span data-ttu-id="d9caa-128">主题</span><span class="sxs-lookup"><span data-stu-id="d9caa-128">Topic</span></span>|<span data-ttu-id="d9caa-129">定义</span><span class="sxs-lookup"><span data-stu-id="d9caa-129">Definition</span></span>|
|-----------|----------------|
|[<span data-ttu-id="d9caa-130">设计你的 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="d9caa-130">Designing Your Windows PowerShell Provider</span></span>](./designing-your-windows-powershell-provider.md)|<span data-ttu-id="d9caa-131">本主题讨论在实现 Windows PowerShell 提供程序之前应考虑的事项。</span><span class="sxs-lookup"><span data-stu-id="d9caa-131">This topic discusses things you should consider before implementing a Windows PowerShell provider.</span></span> <span data-ttu-id="d9caa-132">它汇总了所使用的 Windows PowerShell 提供程序的基类和接口。</span><span class="sxs-lookup"><span data-stu-id="d9caa-132">It summarizes the Windows PowerShell provider base classes and interfaces that are used.</span></span>|
|[<span data-ttu-id="d9caa-133">创建基本 Windows PowerShell 提供程序</span><span class="sxs-lookup"><span data-stu-id="d9caa-133">Creating a Basic Windows PowerShell Provider</span></span>](./creating-a-basic-windows-powershell-provider.md)|<span data-ttu-id="d9caa-134">本主题介绍如何创建 Windows PowerShell 提供程序，以允许 Windows PowerShell 运行时初始化和取消初始化提供程序。</span><span class="sxs-lookup"><span data-stu-id="d9caa-134">This topic shows how to create a Windows PowerShell provider that allows the Windows PowerShell runtime to initialize and uninitialize the provider.</span></span>|
|[<span data-ttu-id="d9caa-135">创建 Windows PowerShell 驱动器提供程序</span><span class="sxs-lookup"><span data-stu-id="d9caa-135">Creating a Windows PowerShell Drive Provider</span></span>](./creating-a-windows-powershell-drive-provider.md)|<span data-ttu-id="d9caa-136">本主题介绍如何创建允许用户通过 Windows PowerShell 驱动器访问数据存储的 Windows PowerShell 提供程序。</span><span class="sxs-lookup"><span data-stu-id="d9caa-136">This topic shows how to create a Windows PowerShell provider that allows the user to access a data store through a Windows PowerShell drive.</span></span>|
|[<span data-ttu-id="d9caa-137">创建 Windows PowerShell 项提供程序</span><span class="sxs-lookup"><span data-stu-id="d9caa-137">Creating a Windows PowerShell Item Provider</span></span>](./creating-a-windows-powershell-item-provider.md)|<span data-ttu-id="d9caa-138">本主题演示如何创建允许用户操作数据存储区中的项的 Windows PowerShell 提供程序。</span><span class="sxs-lookup"><span data-stu-id="d9caa-138">This topic shows how to create a Windows PowerShell provider that allows the user to manipulate the items in a data store.</span></span>|
|[<span data-ttu-id="d9caa-139">创建 Windows PowerShell 容器提供程序</span><span class="sxs-lookup"><span data-stu-id="d9caa-139">Creating a Windows PowerShell Container Provider</span></span>](./creating-a-windows-powershell-container-provider.md)|<span data-ttu-id="d9caa-140">本主题演示如何创建允许用户处理多层数据存储的 Windows PowerShell 提供程序。</span><span class="sxs-lookup"><span data-stu-id="d9caa-140">This topic shows how to create a Windows PowerShell provider that allows the user to work on multilayer data stores.</span></span>|
|[<span data-ttu-id="d9caa-141">创建 Windows PowerShell 导航提供程序</span><span class="sxs-lookup"><span data-stu-id="d9caa-141">Creating a Windows PowerShell Navigation Provider</span></span>](./creating-a-windows-powershell-navigation-provider.md)|<span data-ttu-id="d9caa-142">本主题介绍如何创建 Windows PowerShell 提供程序，该提供程序允许用户以分层方式浏览数据存储区中的项。</span><span class="sxs-lookup"><span data-stu-id="d9caa-142">This topic shows how to create a Windows PowerShell provider that allows the user to navigate the items of a data store in a hierarchical manner.</span></span>|
|[<span data-ttu-id="d9caa-143">创建 Windows PowerShell 内容提供程序</span><span class="sxs-lookup"><span data-stu-id="d9caa-143">Creating a Windows PowerShell Content Provider</span></span>](./creating-a-windows-powershell-content-provider.md)|<span data-ttu-id="d9caa-144">本主题演示如何创建允许用户操作数据存储区中项内容的 Windows PowerShell 提供程序。</span><span class="sxs-lookup"><span data-stu-id="d9caa-144">This topic shows how to create a Windows PowerShell provider that allows the user to manipulate the content of items in a data store.</span></span>|
|[<span data-ttu-id="d9caa-145">创建 Windows PowerShell 属性提供程序</span><span class="sxs-lookup"><span data-stu-id="d9caa-145">Creating a Windows PowerShell Property Provider</span></span>](./creating-a-windows-powershell-property-provider.md)|<span data-ttu-id="d9caa-146">本主题演示如何创建允许用户操作数据存储区中项的属性的 Windows PowerShell 提供程序。</span><span class="sxs-lookup"><span data-stu-id="d9caa-146">This topic shows how to create a Windows PowerShell provider that allows the user to manipulate the properties of items in a data store.</span></span>|

## <a name="see-also"></a><span data-ttu-id="d9caa-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d9caa-147">See Also</span></span>

[<span data-ttu-id="d9caa-148">Windows PowerShell 的工作原理</span><span class="sxs-lookup"><span data-stu-id="d9caa-148">How Windows PowerShell Works</span></span>](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[<span data-ttu-id="d9caa-149">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="d9caa-149">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="d9caa-150">Windows PowerShell 程序员指南</span><span class="sxs-lookup"><span data-stu-id="d9caa-150">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)
