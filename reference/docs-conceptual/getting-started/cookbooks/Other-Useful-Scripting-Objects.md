---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "其他有用的脚本对象"
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: 8334d0b346e59dea3643a93bf52b780b361d1945
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2017
---
# <a name="other-useful-scripting-objects"></a><span data-ttu-id="bcf95-103">其他有用的脚本对象</span><span class="sxs-lookup"><span data-stu-id="bcf95-103">Other Useful Scripting Objects</span></span>
  <span data-ttu-id="bcf95-104">以下对象提供 Windows PowerShell ISE 中的其他脚本编写功能。</span><span class="sxs-lookup"><span data-stu-id="bcf95-104">The following objects provide additional scripting functionality in Windows PowerShell ISE.</span></span> <span data-ttu-id="bcf95-105">它们不属于 **$psISE** 层次结构。</span><span class="sxs-lookup"><span data-stu-id="bcf95-105">They are not part of the **$psISE** hierarchy.</span></span>

## <a name="useful-scripting-objects"></a><span data-ttu-id="bcf95-106">有用的脚本对象</span><span class="sxs-lookup"><span data-stu-id="bcf95-106">Useful Scripting objects</span></span>

### <a name="psunsupportedconsoleapplications"></a><span data-ttu-id="bcf95-107">$psUnsupportedConsoleApplications</span><span class="sxs-lookup"><span data-stu-id="bcf95-107">$psUnsupportedConsoleApplications</span></span>
 <span data-ttu-id="bcf95-108">在 Windows PowerShell ISE 如何与控制台应用程序交互方面存在一些限制。</span><span class="sxs-lookup"><span data-stu-id="bcf95-108">There are some limitations on how Windows PowerShell ISE interacts with console applications.</span></span> <span data-ttu-id="bcf95-109">需要用户干预的命令或自动化脚本可能无法像从 Windows PowerShell 控制台那样工作。</span><span class="sxs-lookup"><span data-stu-id="bcf95-109">A command or an automation script that requires user intervention might not work the way it works from the Windows PowerShell console.</span></span> <span data-ttu-id="bcf95-110">你可能想阻止这些命令或脚本在 Windows PowerShell ISE 命令窗格中运行。</span><span class="sxs-lookup"><span data-stu-id="bcf95-110">You might want to block these commands or scripts from running in the Windows PowerShell ISE Command pane.</span></span> <span data-ttu-id="bcf95-111">**$PsUnsupportedConsoleApplications** 对象保留此类命令的列表。</span><span class="sxs-lookup"><span data-stu-id="bcf95-111">The **$psUnsupportedConsoleApplications** object keeps a list of such commands.</span></span> <span data-ttu-id="bcf95-112">如果你尝试运行此列表中的命令，你将收到它们不受支持的消息。</span><span class="sxs-lookup"><span data-stu-id="bcf95-112">If you try to run the commands in this list, you get a message that they are not supported.</span></span> <span data-ttu-id="bcf95-113">下面的脚本将向该列表添加一个条目。</span><span class="sxs-lookup"><span data-stu-id="bcf95-113">The following script adds an entry to the list.</span></span>

```
# List the unsupported commands
psUnsupportedConsoleApplications
# Add a command to this list
psUnsupportedConsoleApplications.Add(“Mycommand”)
#Show the augmented list of commands
psUnsupportedConsoleApplications

```

### <a name="pslocalhelp"></a><span data-ttu-id="bcf95-114">$psLocalHelp</span><span class="sxs-lookup"><span data-stu-id="bcf95-114">$psLocalHelp</span></span>
 <span data-ttu-id="bcf95-115">这是维护帮助主题和本地已编译的 HTML 帮助文件中和其关联链接之间的上下文相关映射的字典对象。</span><span class="sxs-lookup"><span data-stu-id="bcf95-115">This is a dictionary object that maintains a context-sensitive mapping between Help topics and their associated links in the local compiled HTML Help file.</span></span> <span data-ttu-id="bcf95-116">它用于查找有关某个特定主题的本地帮助。</span><span class="sxs-lookup"><span data-stu-id="bcf95-116">It is used to locate the local Help for a particular topic.</span></span> <span data-ttu-id="bcf95-117">你可以添加或删除此列表中的主题。</span><span class="sxs-lookup"><span data-stu-id="bcf95-117">You can add or delete topics from this list.</span></span> <span data-ttu-id="bcf95-118">下面的代码示例显示了 **$psLocalHelp** 中包含的一些示例键值对。</span><span class="sxs-lookup"><span data-stu-id="bcf95-118">The following code example shows some example key-value pairs that are contained in **$psLocalHelp**.</span></span>

```
# See the local help map
$psLocalHelp | Format-List

```

### <a name="sample-output"></a><span data-ttu-id="bcf95-119">示例输出</span><span class="sxs-lookup"><span data-stu-id="bcf95-119">Sample Output</span></span>

|||
|-|-|
|<span data-ttu-id="bcf95-120">键：Add-Computer</span><span class="sxs-lookup"><span data-stu-id="bcf95-120">Key : Add-Computer</span></span>|<span data-ttu-id="bcf95-121">值：WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm</span><span class="sxs-lookup"><span data-stu-id="bcf95-121">Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm</span></span>|
|<span data-ttu-id="bcf95-122">键：Add-Content</span><span class="sxs-lookup"><span data-stu-id="bcf95-122">Key : Add-Content</span></span>|<span data-ttu-id="bcf95-123">值：WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm</span><span class="sxs-lookup"><span data-stu-id="bcf95-123">Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm</span></span>|

 <span data-ttu-id="bcf95-124">下面的脚本将向该列表添加一个条目。</span><span class="sxs-lookup"><span data-stu-id="bcf95-124">The following script adds an entry to the list.</span></span>

```
$psLocalHelp.Add("get-myNoun","c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a><span data-ttu-id="bcf95-125">$psOnlineHelp</span><span class="sxs-lookup"><span data-stu-id="bcf95-125">$psOnlineHelp</span></span>
 <span data-ttu-id="bcf95-126">这是维护帮助主题的主题标题和其关联外部 URL 之间的上下文相关映射的字典对象。</span><span class="sxs-lookup"><span data-stu-id="bcf95-126">This is a dictionary object that maintains a context-sensitive mapping between topic titles of Help topics and their associated external URLs.</span></span> <span data-ttu-id="bcf95-127">它用于查找 Web 上有关某个特定主题的帮助。</span><span class="sxs-lookup"><span data-stu-id="bcf95-127">It is used to locate the Help for a particular topic on the web.</span></span> <span data-ttu-id="bcf95-128">你可以添加或删除此列表中的主题。</span><span class="sxs-lookup"><span data-stu-id="bcf95-128">You can add or delete topics from this list.</span></span>

```
$psOnlineHelp | Format-List

```

### <a name="sample-output"></a><span data-ttu-id="bcf95-129">示例输出</span><span class="sxs-lookup"><span data-stu-id="bcf95-129">Sample Output</span></span>

|||
|-|-|
|<span data-ttu-id="bcf95-130">键：Add-Computer</span><span class="sxs-lookup"><span data-stu-id="bcf95-130">Key : Add-Computer</span></span>|<span data-ttu-id="bcf95-131">值：http://go.microsoft.com/fwlink/p/?LinkID=135194</span><span class="sxs-lookup"><span data-stu-id="bcf95-131">Value : http://go.microsoft.com/fwlink/p/?LinkID=135194</span></span>|
|<span data-ttu-id="bcf95-132">键：Add-Content</span><span class="sxs-lookup"><span data-stu-id="bcf95-132">Key : Add-Content</span></span>|<span data-ttu-id="bcf95-133">值：http://go.microsoft.com/fwlink/p/?LinkID=113278</span><span class="sxs-lookup"><span data-stu-id="bcf95-133">Value : http://go.microsoft.com/fwlink/p/?LinkID=113278</span></span>|

 <span data-ttu-id="bcf95-134">下面的脚本将向该列表添加一个条目。</span><span class="sxs-lookup"><span data-stu-id="bcf95-134">The following script adds an entry to the list.</span></span>

```
$psOnlineHelp.Add("get-myNoun","http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a><span data-ttu-id="bcf95-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bcf95-135">See Also</span></span>
- [<span data-ttu-id="bcf95-136">Windows PowerShell ISE 脚本对象模型</span><span class="sxs-lookup"><span data-stu-id="bcf95-136">The Windows PowerShell ISE Scripting Object Model</span></span>](../../core-powershell/ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  
