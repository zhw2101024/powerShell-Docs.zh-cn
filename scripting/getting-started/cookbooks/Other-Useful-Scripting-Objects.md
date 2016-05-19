---
title: 其他有用的脚本对象
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
---
# 其他有用的脚本对象
  以下对象提供 Windows PowerShell ISE 中的其他脚本编写功能。 它们不属于 **$psISE** 层次结构。

## 有用的脚本对象

### $psUnsupportedConsoleApplications
 在 Windows PowerShell ISE 如何与控制台应用程序交互方面存在一些限制。 需要用户干预的命令或自动化脚本可能无法像从 Windows PowerShell 控制台那样工作。 你可能想阻止这些命令或脚本在 Windows PowerShell ISE 命令窗格中运行。 **$PsUnsupportedConsoleApplications** 对象保留此类命令的列表。 如果你尝试运行此列表中的命令，你将收到它们不受支持的消息。 下面的脚本将向该列表添加一个条目。

```
# List the unsupported commands
psUnsupportedConsoleApplications
# Add a command to this list
psUnsupportedConsoleApplications.Add(“Mycommand”)
#Show the augmented list of commands
psUnsupportedConsoleApplications

```

### $psLocalHelp
 这是维护帮助主题和本地已编译的 HTML 帮助文件中和其关联链接之间的上下文相关映射的字典对象。 它用于查找有关某个特定主题的本地帮助。 你可以添加或删除此列表中的主题。 下面的代码示例显示了 **$psLocalHelp** 中包含的一些示例键值对.

```
# See the local help map
$psLocalHelp |Format-List

```

### 示例输出

|||
|-|-|
|键：Add\-Computer|值：WindowsPowerShellHelp.chm::\/html\/093f660c\-b8d5\-43cf\-aa0c\-54e5e54e76f9.htm|
|键：Add\-Content|值：WindowsPowerShellHelp.chm::\/html\/0c836a1b\-f389\-4e9a\-9325\-0f415686d194.htm|

 下面的脚本将向该列表添加一个条目。

```
$psLocalHelp.Add("get-myNoun","c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### $psOnlineHelp
 这是维护帮助主题的主题标题和其关联外部 URL 之间的上下文相关映射的字典对象。 它用于查找 Web 上有关某个特定主题的帮助。 你可以添加或删除此列表中的主题。

```
$psOnlineHelp |format-list

```

### 示例输出

|||
|-|-|
|键：Add\-Computer|值：http:\/\/go.microsoft.com\/fwlink\/p\/?LinkID\=135194|
|键：Add\-Content|值：http:\/\/go.microsoft.com\/fwlink\/p\/?LinkID\=113278|

 下面的脚本将向该列表添加一个条目。

```
$psOnlineHelp.Add("get-myNoun","http://www.mydomain.com/MyNoun.html")
```

## 另请参阅
 [Windows PowerShell ISE 脚本对象模型](../../core-powershell/ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  


<!--HONumber=May16_HO2-->


