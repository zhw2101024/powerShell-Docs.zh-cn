---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "角色功能的常见问题"
ms.technology: powershell
ms.openlocfilehash: 8e928ec07ef98b2ec8186a27d3aefa1450a3a424
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: zh-CN
---
### <a name="common-role-capability-pitfalls"></a><span data-ttu-id="50002-103">角色功能的常见问题</span><span class="sxs-lookup"><span data-stu-id="50002-103">Common Role Capability Pitfalls</span></span>
<span data-ttu-id="50002-104">你自己完成此过程时，可能遇到一些常见问题。</span><span class="sxs-lookup"><span data-stu-id="50002-104">You may run into a few common pitfalls if you go through this process yourself.</span></span>
<span data-ttu-id="50002-105">以下是一个快速指南，阐释了修改或创建新的终结点时如何确定并修正这些问题：</span><span class="sxs-lookup"><span data-stu-id="50002-105">Here is a quick guide explaining how to identify and remediate these issues when modifying or creating a new endpoint:</span></span>

#### <a name="functions-vs-cmdlets"></a><span data-ttu-id="50002-106">函数与Cmdlet</span><span class="sxs-lookup"><span data-stu-id="50002-106">Functions vs. Cmdlets</span></span>
<span data-ttu-id="50002-107">在 PowerShell 中编写的 PowerShell 命令即 PowerShell 函数。</span><span class="sxs-lookup"><span data-stu-id="50002-107">PowerShell commands written in PowerShell are PowerShell functions.</span></span>
<span data-ttu-id="50002-108">编写为专用 .NET 类的 PowerShell 命令即 PowerShell cmdlet。</span><span class="sxs-lookup"><span data-stu-id="50002-108">PowerShell commands written as specialized .NET classes are PowerShell cmdlets.</span></span>
<span data-ttu-id="50002-109">你可以通过运行 `Get-Command` 来检查命令类型。</span><span class="sxs-lookup"><span data-stu-id="50002-109">You can check the command type by running `Get-Command`.</span></span>

#### <a name="visibleproviders"></a><span data-ttu-id="50002-110">VisibleProviders</span><span class="sxs-lookup"><span data-stu-id="50002-110">VisibleProviders</span></span>
<span data-ttu-id="50002-111">你将需要公开命令需要的任意提供程序。</span><span class="sxs-lookup"><span data-stu-id="50002-111">You will need to expose any providers your commands need.</span></span>
<span data-ttu-id="50002-112">最常见的是 FileSystem 提供程序，但你可能还需要公开其他提供程序，如 Registry 提供程序。</span><span class="sxs-lookup"><span data-stu-id="50002-112">The most common is the FileSystem provider, but you may also need to expose others, like the Registry provider.</span></span>
<span data-ttu-id="50002-113">有关提供程序的简介，请参阅这篇 [Hey, Scripting Guy](http://blogs.technet.com/b/heyscriptingguy/archive/2015/04/20/find-and-use-windows-powershell-providers.aspx)（你好，脚本专家）博客文章。</span><span class="sxs-lookup"><span data-stu-id="50002-113">For an introduction to providers, check out this [Hey, Scripting Guy blog post](http://blogs.technet.com/b/heyscriptingguy/archive/2015/04/20/find-and-use-windows-powershell-providers.aspx).</span></span>
<span data-ttu-id="50002-114">请谨慎公开提供程序 -- 通常，最好定义适用于基础提供程序的函数，而不是在 JEA 会话中直接公开提供程序。</span><span class="sxs-lookup"><span data-stu-id="50002-114">Be careful when exposing providers -- often, it is better to define your own function that works with the underlying providers than to directly expose the provider in a JEA session.</span></span>
<span data-ttu-id="50002-115">这样一来，你仍可允许用户使用文件、注册表项等，但保留了对其可使用自定义验证逻辑处理**哪些**文件和注册表项的控制权。</span><span class="sxs-lookup"><span data-stu-id="50002-115">This way, you can still allow users to work with files, registry keys, etc. but retain control over **which** files and registry keys they can work with using custom validation logic.</span></span>

