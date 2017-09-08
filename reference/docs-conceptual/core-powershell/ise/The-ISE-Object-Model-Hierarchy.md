---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "ISE 对象模型层次结构"
ms.assetid: bc3300e4-9c17-4f00-a621-c8867126e3b3
ms.openlocfilehash: b6e251eac7db56896490362392e0a1c4c10a8d4a
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2017
---
# <a name="the-ise-object-model-hierarchy"></a>ISE 对象模型层次结构
  本主题介绍了属于 Windows PowerShell 集成脚本环境 (ISE) 一部分的对象的层次结构。 在 Windows PowerShell 3.0 和 Windows PowerShell 4.0 中包含 Windows PowerShell ISE。 单击一个对象，使你转到定义对象的类的参考文档。

##  <a name="psise-object"></a>**$psISE 对象**
 **$PsISE** 对象是 Windows PowerShell ISE 对象层次结构的[根对象](The-ObjectModelRoot-Object.md)。 它位于顶层，使以下对象可用于脚本编写：

-   **[$psISE.CurrentFile]()**

-   **[$psISE.CurrentPowerShellTab]()**

-   **[$psISE.CurrentVisibleHorizontalTool]()**

-   **[$psISE.CurrentVisibleVerticalTool]()**

-   **[$psISE.Options]()**

-   **[$psISE.PowerShellTabs]()**

##  <a name="psisecurrentfilethe-isefile-objectmd"></a>**[$psISE.CurrentFile](The-ISEFile-Object.md)**
 **$PsISE.CurrentFile** 对象是 [ISEFile](The-ISEFile-Object.md) 类的实例，使以下对象可用于脚本编写：

-   **[$psISE.CurrentFile.DisplayName](The-ISEFile-Object.md)**

-   **[$psISE.CurrentFile.Editor](The-ISEEditor-Object.md)**  此对象是 [ISEEditor](The-ISEEditor-Object.md) 类的实例，使以下对象可用于脚本编写：

    -   **[$psISE.CurrentFile.Editor.CanGoToMatch](The-ISEEditor-Object.md)**

    -   **[CaretColumn](The-ISEEditor-Object.md)**

    -   **[CaretLine](The-ISEEditor-Object.md)**

    -   **[$psISE.CurrentFile.Editor.CaretLineText](The-ISEEditor-Object.md)**

    -   **[LineCount](The-ISEEditor-Object.md)**

    -   **[SelectedText](The-ISEEditor-Object.md)**

    -   **[Text](The-ISEEditor-Object.md)**

-   [EncodingThe-ISEFile-Object.md]()

-   [FullPathThe-ISEFile-Object.md]()

-   [IsSavedThe-ISEFile-Object.md]()

-   [IsUntitledThe-ISEFile-Object.md]()

##  <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>**[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)**
 **$psISE.CurrentPowerShellTab** 对象是 [PowerShellTab](The-PowerShellTab-Object.md) 类的实例，使以下对象可用于脚本编写：

-   **[$psISE.CurrentPowerShellTab.AddOnsMenu](The-ISEMenuItem-Object.md)**  此对象是 [ISEMenuItem](The-ISEMenuItem-Object.md) 类的实例，使以下对象可用于脚本编写：

    -   [$psISE.CurrentPowerShellTab.AddOnsMenu.ActionThe-ISEMenuItem-Object.md]()

    -   [$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayNameThe-ISEMenuItem-Object.md]()

    -   [$psISE.CurrentPowerShellTab.AddOnsMenu.ShortcutThe-ISEMenuItem-Object.md]()

    -   **[$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus](The-ISEMenuItemCollection-Object.md)**

-   [$psISE.CurrentPowerShellTab.CanInvokeThe-PowerShellTab-Object.md]()

-   **[$psISE.CurrentPowerShellTab.ConsolePane](The-ISEEditor-Object.md)**  此对象是 [ISEEditor](The-ISEEditor-Object.md) 类的实例，使以下对象可用于脚本编写：

    -   [$psISE.CurrentPowerShellTab.ConsolePane.CanGoToMatchThe-ISEEditor-Object.md]()

    -   [CaretColumnThe-ISEEditor-Object.md]()

    -   [CaretLineThe-ISEEditor-Object.md]()

    -   [$psISE.CurrentPowerShellTab.ConsolePane.CaretLineTextThe-ISEEditor-Object.md]()

    -   [LineCountThe-ISEEditor-Object.md]()

    -   [SelectedTextThe-ISEEditor-Object.md]()

    -   [TextThe-ISEEditor-Object.md]()

-   [$psISE.CurrentPowerShellTab.DisplayNameThe-PowerShellTab-Object.md]()

-   [$psISE.CurrentPowerShellTab.ExpandedScriptThe-PowerShellTab-Object.md]()

-   **[$psISE.CurrentPowerShellTab.Files](The-ISEFileCollection-Object.md)**

-   **[$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**

-   [$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpenedThe-PowerShellTab-Object.md]()

-   [$psISE.CurrentPowerShellTab.PromptThe-PowerShellTab-Object.md]()

-   [$psISE.CurrentPowerShellTab.ShowCommandsThe-PowerShellTab-Object.md]()

-   **[$psISE.CurrentPowerShellTab.Snippets](The-ISESnippetCollection-Object.md)**

-   [$psISE.CurrentPowerShellTab.StatusTextThe-PowerShellTab-Object.md]()

-   **[$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**

-   [$psISE.CurrentPowerShellTab.VerticalAddOnToolsPaneOpenedThe-PowerShellTab-Object.md]()

-   **[$psISE.CurrentPowerShellTab.VisibleHorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md)**

-   **[$psISE.CurrentPowerShellTab.VisibleVerticalAddOnTools](The-ISEAddOnToolCollection-Object.md)**

##  <a name="psisecurrentvisiblehorizontaltool"></a>$psISE.CurrentVisibleHorizontalTool
 **$PsISE.CurrentVisibleHorizontalTool** 对象是 [ISEAddOnTool](The-ISEAddOnTool-Object.md) 类的实例。 它表示已安装的外接程序工具，当前停靠在 Windows PowerShell ISE 窗口的顶部。 此对象使以下对象可用于脚本编写：

-   [$psISE.CurrentVisibleHorizontalTool.ControlThe-ISEAddOnTool-Object.md]()

-   [$psISE.CurrentVisibleHorizontalTool.IsVisibleThe-ISEAddOnTool-Object.md]()

-   [$psISE.CurrentVisibleHorizontalTool.NameThe-ISEAddOnTool-Object.md]()

##  <a name="psisecurrentvisibleverticaltool"></a>$psISE.CurrentVisibleVerticalTool
 **$PsISE.CurrentVisibleHorizontalTool** 对象是 [ISEAddOnTool](The-ISEAddOnTool-Object.md) 类的实例。 它表示已安装的外接程序工具，当前停靠在 Windows PowerShell ISE 窗口的右侧。 此对象使以下对象可用于脚本编写：

-   [$psISE.CurrentVisibleHorizontalTool.ControlThe-ISEAddOnTool-Object.md]()

-   [$psISE.CurrentVisibleHorizontalTool.IsVisibleThe-ISEAddOnTool-Object.md]()

-   [$psISE.CurrentVisibleHorizontalTool.NameThe-ISEAddOnTool-Object.md]()

##  <a name="psiseoptions"></a>$psISE.Options
 **$psISE.Options** 对象使以下对象可用于脚本编写：

-   [$psISE.Options.AutoSaveMinuteIntervalThe-ISEOptions-Object.md]()

-   [$psISE.Options.ConsolePaneBackgroundColorThe-ISEOptions-Object.md]()

-   [$psISE.Options.ConsolePaneTextForegroundColorThe-ISEOptions-Object.md]()

-   [$psISE.Options.ConsolePaneTextBackgroundColorThe-ISEOptions-Object.md]()

-   [$psISE.Options.ConsoleTokenColorsThe-ISEOptions-Object.md]()

-   [$psISE.Options.DebugBackgroundColorThe-ISEOptions-Object.md]()

-   [$psISE.Options.DebugForegroundColorThe-ISEOptions-Object.md]()

-   **[$psISE.Options.DefaultOptions](The-ISEOptions-Object.md)**

-   [$psISE.Options.ErrorBackgroundColorThe-ISEOptions-Object.md]()

-   [$psISE.Options.ErrorForegroundColorThe-ISEOptions-Object.md]()

-   [$psISE.Options.FontNameThe-ISEOptions-Object.md]()

-   [$psISE.Options.FontsizeThe-ISEOptions-Object.md]()

-   [$psISE.Options.IntellisenseTimeoutInSecondsThe-ISEOptions-Object.md]()

-   [$psISE.Options.MRUCountThe-ISEOptions-Object.md]()

-   [$psISE.Options.ScriptPaneBackgroundColorThe-ISEOptions-Object.md]()

-   [$psISE.Options.ScriptPaneForegroundColorThe-ISEOptions-Object.md]()

-   [$psISE.Options.SelectedScriptPaneStateThe-ISEOptions-Object.md]()

-   [$psISE.Options.ShowDefaultSnippetsThe-ISEOptions-Object.md]()

-   [$psISE.Options.ShowIntellisenseInConsolePaneThe-ISEOptions-Object.md]()

-   [$psISE.Options.ShowIntellisenseInScriptPaneThe-ISEOptions-Object.md]()

-   [$psISE.Options.ShowLineNumbersThe-ISEOptions-Object.md]()

-   [$psISE.Options.ShowOutliningThe-ISEOptions-Object.md]()

-   [$psISE.Options.ShowToolBarThe-ISEOptions-Object.md]()

-   [$psISE.Options.ShowWarningBeforeSavingOnRunThe-ISEOptions-Object.md]()

-   [$psISE.Options.ShowWarningForDuplicateFilesThe-ISEOptions-Object.md]()

-   [$psISE.Options.TokenColorsThe-ISEOptions-Object.md]()

-   [$psISE.Options.UseEnterToSelectConsolePaneIntellisenseThe-ISEOptions-Object.md]()

-   **[$psISE.Options.UseEnterToSelectScriptPaneIntellisenseThe-ISEOptions-Object.md]()**

-   [$psISE.Options.UseLocalHelpThe-ISEOptions-Object.md]()

-   [$psISE.Options.VerboseBackgroundColorThe-ISEOptions-Object.md]()

-   [$psISE.Options.VerboseForegroundColorThe-ISEOptions-Object.md]()

-   [$psISE.Options.WarningBackgroundColorThe-ISEOptions-Object.md]()

-   [$psISE.Options.WarningForegroundColorThe-ISEOptions-Object.md]()

-   [$psISE.Options.XmlTokenColorsThe-ISEOptions-Object.md]()

-   [$psISE.Options.ZoomThe-ISEOptions-Object.md]()

##  <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>**[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)**
 **$PsISE.PowerShellTabs** 对象是 [PowerShellTabCollection](The-PowerShellTabCollection-Object.md) 类的实例。 它是所有当前打开的 PowerShell 选项卡的集合，表示本地计算机上或在已连接的远程计算机上可用的 Windows PowerShell 运行环境。 集合中的每个成员均为 [PowerShellTab](The-PowerShellTab-Object.md) 类的实例。

## <a name="see-also"></a>另请参阅
- [Windows PowerShell ISE 脚本对象模型](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Windows PowerShell ISE 对象模型参考](Windows-PowerShell-ISE-Object-Model-Reference.md)

