---
title: 支持联机帮助 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3204599c-7159-47aa-82ec-4a476f461027
caps.latest.revision: 7
ms.openlocfilehash: b76f45299d11dc10c8b16ed80f87c7f1fcc5ed65
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082135"
---
# <a name="supporting-online-help"></a><span data-ttu-id="79897-102">支持联机帮助</span><span class="sxs-lookup"><span data-stu-id="79897-102">Supporting Online Help</span></span>

<span data-ttu-id="79897-103">从 Windows PowerShell 3.0 开始，有两种方法来支持`Get-Help`Windows PowerShell 命令的联机功能。</span><span class="sxs-lookup"><span data-stu-id="79897-103">Beginning in Windows PowerShell 3.0, there are two ways to support the `Get-Help` Online feature for Windows PowerShell commands.</span></span> <span data-ttu-id="79897-104">本主题说明如何实现此功能对于不同的命令类型。</span><span class="sxs-lookup"><span data-stu-id="79897-104">This topic explains how to implement this feature for different command types.</span></span>

## <a name="about-online-help"></a><span data-ttu-id="79897-105">有关联机帮助</span><span class="sxs-lookup"><span data-stu-id="79897-105">About Online Help</span></span>

<span data-ttu-id="79897-106">联机帮助始终是 Windows PowerShell 的关键部分。</span><span class="sxs-lookup"><span data-stu-id="79897-106">Online help has always been a vital part of Windows PowerShell.</span></span> <span data-ttu-id="79897-107">尽管`Get-Help`cmdlet 显示帮助主题的命令提示符处，许多用户首选的联机读取，包括颜色编码、 超链接和社区内容和 wiki 基于文档中的共享想法的体验。</span><span class="sxs-lookup"><span data-stu-id="79897-107">Although the `Get-Help` cmdlet displays help topics at the command prompt, many users prefer the experience of reading online, including color-coding, hyperlinks, and sharing ideas in Community Content and wiki-based documents.</span></span> <span data-ttu-id="79897-108">最重要的是之前可更新帮助的问世，, 联机帮助提供的帮助文件的最新版本。</span><span class="sxs-lookup"><span data-stu-id="79897-108">Most importantly, before the advent of Updatable Help, online help provided the most up-to-date version of the help files.</span></span>

<span data-ttu-id="79897-109">随着在 Windows PowerShell 3.0 中的可更新帮助，联机帮助仍扮演着重要角色。</span><span class="sxs-lookup"><span data-stu-id="79897-109">With the advent of Updatable Help in Windows PowerShell 3.0, online help still plays a vital role.</span></span> <span data-ttu-id="79897-110">灵活的用户体验，除了联机帮助提供了向用户对于没有或不能使用可更新的帮助来下载帮助主题的帮助。</span><span class="sxs-lookup"><span data-stu-id="79897-110">In addition to the flexible user experience, online help provides help to users who do not or cannot use Updatable Help to download help topics.</span></span>

## <a name="how-get-help--online-works"></a><span data-ttu-id="79897-111">如何获取帮助的联机工作原理</span><span class="sxs-lookup"><span data-stu-id="79897-111">How Get-Help -Online Works</span></span>

<span data-ttu-id="79897-112">若要帮助用户查找联机帮助主题的命令，`Get-Help`命令有一个用户的默认 Internet 浏览器中打开一个命令的帮助主题的联机版本的 Online 参数。</span><span class="sxs-lookup"><span data-stu-id="79897-112">To help users find the online help topics for commands, the `Get-Help` command has an Online parameter that opens the online version of help topic for a command in the user's default Internet browser.</span></span>

<span data-ttu-id="79897-113">例如，以下命令将打开联机帮助主题中的`Invoke-Command`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="79897-113">For example, the following command opens the online help topic for the `Invoke-Command` cmdlet.</span></span>

```powershell
Get-Help Invoke-Command -Online
```

<span data-ttu-id="79897-114">若要实现`Get-Help`-联机， `Get-Help` cmdlet 看起来的统一资源标识符 (URI) 的以下位置中的联机版本帮助主题。</span><span class="sxs-lookup"><span data-stu-id="79897-114">To implement `Get-Help` -Online, the `Get-Help` cmdlet looks for a Uniform Resource Identifier (URI) for the online version help topic in the following locations.</span></span>

- <span data-ttu-id="79897-115">该命令的帮助主题的相关链接部分中的第一个链接。</span><span class="sxs-lookup"><span data-stu-id="79897-115">The first link in the Related Links section of the help topic for the command.</span></span> <span data-ttu-id="79897-116">必须在用户计算机上安装的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="79897-116">The help topic must be installed on the user's computer.</span></span> <span data-ttu-id="79897-117">在 Windows PowerShell 2.0 中引入了此功能。</span><span class="sxs-lookup"><span data-stu-id="79897-117">This feature was introduced in Windows PowerShell 2.0.</span></span>

- <span data-ttu-id="79897-118">任何命令的 HelpUri 属性。</span><span class="sxs-lookup"><span data-stu-id="79897-118">The HelpUri property of any command.</span></span> <span data-ttu-id="79897-119">即使在用户的计算机上未安装该命令的帮助主题时，才可访问 HelpUri 属性。</span><span class="sxs-lookup"><span data-stu-id="79897-119">The HelpUri property is accessible even when the help topic for the command is not installed on the user's computer.</span></span> <span data-ttu-id="79897-120">在 Windows PowerShell 3.0 中引入了此功能。</span><span class="sxs-lookup"><span data-stu-id="79897-120">This feature was introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="79897-121">`Get-Help` 查找之前获取的 HelpUri 属性值中的相关链接部分中的第一个条目的 URI。</span><span class="sxs-lookup"><span data-stu-id="79897-121">`Get-Help` looks for a URI in the first entry in the Related Links section before getting the HelpUri property value.</span></span> <span data-ttu-id="79897-122">如果属性值不正确或已更改，您可以通过在第一个相关链接中输入一个不同的值重写它。</span><span class="sxs-lookup"><span data-stu-id="79897-122">If the property value is incorrect or has changed, you can override it by entering a different value in the first Related Link.</span></span> <span data-ttu-id="79897-123">但是，第一个相关链接仅适用于用户的计算机上安装的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="79897-123">However, the first Related Link works only when the help topics are installed on the user's computer.</span></span>

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a><span data-ttu-id="79897-124">将 URI 添加到命令的帮助主题的第一个相关链接</span><span class="sxs-lookup"><span data-stu-id="79897-124">Adding a URI to the first related link of a command help topic</span></span>

<span data-ttu-id="79897-125">您可以支持`Get-Help`-联机的任何命令通过将是有效的 URI 添加到命令的基于 XML 的帮助主题的相关链接部分中的第一个条目。</span><span class="sxs-lookup"><span data-stu-id="79897-125">You can support `Get-Help` -Online for any command by adding a valid URI to the first entry in the Related Links section of the XML-based help topic for the command.</span></span> <span data-ttu-id="79897-126">此选项仅在基于 XML 的帮助主题中有效，并且仅适用于用户的计算机上安装的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="79897-126">This option is valid only in XML-based help topics and works only when the help topic is installed on the user's computer.</span></span> <span data-ttu-id="79897-127">当安装的帮助主题，并且填充 URI 时，此值将优先于**HelpUri**命令的属性。</span><span class="sxs-lookup"><span data-stu-id="79897-127">When the help topic is installed and the URI is populated, this value takes precedence over the **HelpUri** property of the command.</span></span> <span data-ttu-id="79897-128">有关基于 XML 的命令的帮助主题的信息，请参阅[Writing XML-Based 命令的帮助主题](../help/writing-xml-based-help-topics-for-commands.md)。</span><span class="sxs-lookup"><span data-stu-id="79897-128">For information about XML-based help topics for commands, see [Writing XML-Based Help Topics for Commands](../help/writing-xml-based-help-topics-for-commands.md).</span></span>

<span data-ttu-id="79897-129">若要支持此功能，URI 必须出现在`maml:uri`下第一个元素`maml:relatedLinks/maml:navigationLink`中的元素`maml:relatedLinks`元素。</span><span class="sxs-lookup"><span data-stu-id="79897-129">To support this feature, the URI must appear in the `maml:uri` element under the first `maml:relatedLinks/maml:navigationLink` element in the `maml:relatedLinks` element.</span></span>

<span data-ttu-id="79897-130">以下 XML 显示了 URI 的正确位置。</span><span class="sxs-lookup"><span data-stu-id="79897-130">The following XML shows the correct placement of the URI.</span></span> <span data-ttu-id="79897-131">"联机版本:"中的文本`maml:linkText`元素是最佳做法，但它不是必需。</span><span class="sxs-lookup"><span data-stu-id="79897-131">The "Online version:" text in the `maml:linkText` element is a best practice, but it is not required.</span></span>

```xml

<maml:relatedLinks>
    <maml:navigationLink>
        <maml:linkText>Online version:</maml:linkText>
        <maml:uri>http://go.microsoft.com/fwlink/?LinkID=113279</maml:uri>
    </maml:navigationLink>
    <maml:navigationLink>
        <maml:linkText>about_History</maml:linkText>
        <maml:uri/>
    </maml:navigationLink>
</maml:relatedLinks>
```

## <a name="adding-the-helpuri-property-to-a-command"></a><span data-ttu-id="79897-132">将 HelpUri 属性添加到命令</span><span class="sxs-lookup"><span data-stu-id="79897-132">Adding the HelpUri property to a command</span></span>

<span data-ttu-id="79897-133">本部分演示如何将 HelpUri 属性添加到不同类型的命令。</span><span class="sxs-lookup"><span data-stu-id="79897-133">This section shows how to add the HelpUri property to commands of different types.</span></span>

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a><span data-ttu-id="79897-134">将 HelpUri 属性添加到 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="79897-134">Adding a HelpUri Property to a Cmdlet</span></span>

<span data-ttu-id="79897-135">编写的 cmdlet 的C#，添加**HelpUri**在 Cmdlet 类的属性。</span><span class="sxs-lookup"><span data-stu-id="79897-135">For cmdlets written in C#, add a **HelpUri** attribute to the Cmdlet class.</span></span> <span data-ttu-id="79897-136">属性的值必须是"http"或"https"开头的 URI。</span><span class="sxs-lookup"><span data-stu-id="79897-136">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="79897-137">下面的代码演示的 HelpUri 属性`Get-History`cmdlet 类。</span><span class="sxs-lookup"><span data-stu-id="79897-137">The following code shows the HelpUri attribute of the `Get-History` cmdlet class.</span></span>

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "http://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a><span data-ttu-id="79897-138">将 HelpUri 属性添加到高级功能</span><span class="sxs-lookup"><span data-stu-id="79897-138">Adding a HelpUri Property to an Advanced Function</span></span>

<span data-ttu-id="79897-139">对于高级函数，添加**HelpUri**属性设置为**CmdletBinding**属性。</span><span class="sxs-lookup"><span data-stu-id="79897-139">For advanced functions, add a **HelpUri** property to the **CmdletBinding** attribute.</span></span> <span data-ttu-id="79897-140">属性的值必须是"http"或"https"开头的 URI。</span><span class="sxs-lookup"><span data-stu-id="79897-140">The value of the property must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="79897-141">下面的代码显示了新建日历函数的 HelpUri 属性</span><span class="sxs-lookup"><span data-stu-id="79897-141">The following code shows the HelpUri attribute of the New-Calendar function</span></span>

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="http://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a><span data-ttu-id="79897-142">将 HelpUri 属性添加到 CIM 命令</span><span class="sxs-lookup"><span data-stu-id="79897-142">Adding a HelpUri Attribute to a CIM Command</span></span>

<span data-ttu-id="79897-143">有关 CIM 命令，添加**HelpUri**归于**CmdletMetadata** CDXML 文件中的元素。</span><span class="sxs-lookup"><span data-stu-id="79897-143">For CIM commands, add a **HelpUri** attribute to the **CmdletMetadata** element in the CDXML file.</span></span> <span data-ttu-id="79897-144">属性的值必须是"http"或"https"开头的 URI。</span><span class="sxs-lookup"><span data-stu-id="79897-144">The value of the attribute must be a URI that begins with "http" or "https".</span></span>

<span data-ttu-id="79897-145">下面的代码演示开始调试 CIM 命令的 HelpUri 属性</span><span class="sxs-lookup"><span data-stu-id="79897-145">The following code shows the HelpUri attribute of the Start-Debug CIM command</span></span>

```
<CmdletMetadata Verb="Debug" HelpUri="http://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a><span data-ttu-id="79897-146">将 HelpUri 属性添加到工作流</span><span class="sxs-lookup"><span data-stu-id="79897-146">Adding a HelpUri Attribute to a Workflow</span></span>

<span data-ttu-id="79897-147">Windows PowerShell 语言编写而成的工作流，将添加 **。ExternalHelp**到工作流代码注释指令。</span><span class="sxs-lookup"><span data-stu-id="79897-147">For workflows that are written in the Windows PowerShell language, add an **.ExternalHelp** comment directive to the workflow code.</span></span> <span data-ttu-id="79897-148">指令的值必须以"http"或"https"开头的 URI。</span><span class="sxs-lookup"><span data-stu-id="79897-148">The value of the directive must be a URI that begins with "http" or "https".</span></span>

> [!NOTE]
> <span data-ttu-id="79897-149">有关基于 XAML 的 Windows PowerShell 中的工作流不支持的 HelpUri 属性。</span><span class="sxs-lookup"><span data-stu-id="79897-149">The HelpUri property is not supported for XAML-based workflows in Windows PowerShell.</span></span>

<span data-ttu-id="79897-150">下面的代码演示。工作流文件中的 ExternalHelp 指令。</span><span class="sxs-lookup"><span data-stu-id="79897-150">The following code shows the .ExternalHelp directive in a workflow file.</span></span>

```powershell
# .ExternalHelp "http://go.microsoft.com/fwlink/?LinkID=138338"
```