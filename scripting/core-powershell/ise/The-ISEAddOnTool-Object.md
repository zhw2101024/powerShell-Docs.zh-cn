---
title:  ISEAddOnTool 对象
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  ce84d8bc-07ba-41f6-bdde-d6f3fddcd1e3
---

# ISEAddOnTool 对象
  **ISEAddonTool** 对象表示已安装的可提供 Windows PowerShell ISE 附加功能的附加设备工具。 例如，“命令”工具，你可以通过单击“查看”，然后单击“显示命令附加设备”进行显示。 然后，你可以通过操作各种可用 **ISEAddOnTool** 对象来访问此工具。

 每个附加设备工具可以与垂直窗格或水平窗格相关联。 垂直窗格停靠在 Windows PowerShell ISE 的右边缘。 水平窗格停靠在底部边缘。

 Windows PowerShell ISE 中的每个 PowerShell 选项卡上可以安装自己的附加设备工具集。 请参阅 [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-ISEAddOnToolCollection-Object.md) 和 [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-ISEAddOnToolCollection-Object.md) 以访问可用于当前选定的选项卡或 [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md) 集合对象中任何 **PowerShellTab** 对象上的相同属性的工具集合。

## 方法
 没有特定于 Windows PowerShell ISE 的方法可用于此类的对象。

## “属性”

###  <a name="Control"></a> 控件
  在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

 **Control** 属性提供对命令附加设备工具的大量详细信息的读取访问权限。

```
# View the properties of the Commands add-on tool.
# (assumes that it is visible in the vertical pane)
$psISE.CurrentVisibleVerticalTool.Control
HostObject                  : Microsoft.PowerShell.Host.ISE.ObjectModelRoot
Content                     :
HasContent                  :
ContentTemplate             :
ContentTemplateSelector     :
ContentStringFormat         :
BorderBrush                 :
BorderThickness             :
Background                  :
Foreground                  :
FontFamily                  :
FontSize                    :
FontStretch                 :
FontStyle                   :
FontWeight                  :
HorizontalContentAlignment  :
VerticalContentAlignment    :
TabIndex                    :
IsTabStop                   :
Padding                     :
Template                    : System.Windows.Controls.ControlTemplate
Style                       :
OverridesDefaultStyle       :
UseLayoutRounding           :
Triggers                    : {}
TemplatedParent             :
Resources                   : {System.Windows.Controls.TabItem}
DataContext                 :
BindingGroup                :
Language                    :
Name                        :
Tag                         :
InputScope                  :
ActualWidth                 : 370.75
ActualHeight                : 676.559097412109
LayoutTransform             :
Width                       :
MinWidth                    :
MaxWidth                    :
Height                      :
MinHeight                   :
MaxHeight                   :
FlowDirection               : LeftToRight
Margin                      :
HorizontalAlignment         :
VerticalAlignment           :
FocusVisualStyle            :
Cursor                      :
ForceCursor                 :
IsInitialized               : True
IsLoaded                    :
ToolTip                     :
ContextMenu                 :
Parent                      :
HasAnimatedProperties       :
InputBindings               :
CommandBindings             :
AllowDrop                   :
DesiredSize                 : 227.66,676.559097412109
IsMeasureValid              : True
IsArrangeValid              : True
RenderSize                  : 370.75,676.559097412109
RenderTransform             :
RenderTransformOrigin       :
IsMouseDirectlyOver         : False
IsMouseOver                 : False
IsStylusOver                : False
IsKeyboardFocusWithin       : False
IsMouseCaptured             :
IsMouseCaptureWithin        : False
IsStylusDirectlyOver        : False
IsStylusCaptured            :
IsStylusCaptureWithin       : False
IsKeyboardFocused           : False
IsInputMethodEnabled        :
Opacity                     :
OpacityMask                 :
BitmapEffect                :
Effect                      :
BitmapEffectInput           :
CacheMode                   :
Uid                         :
Visibility                  : Visible
ClipToBounds                : False
Clip                        :
SnapsToDevicePixels         : False
IsFocused                   :
IsEnabled                   :
IsHitTestVisible            :
IsVisible                   : True
Focusable                   :
PersistId                   : 1
IsManipulationEnabled       :
AreAnyTouchesOver           : False
AreAnyTouchesDirectlyOver   :
AreAnyTouchesCapturedWithin : False
AreAnyTouchesCaptured       :
TouchesCaptured             : {}
TouchesCapturedWithin       : {}
TouchesOver                 : {}
TouchesDirectlyOver         : {}
DependencyObjectType        : System.Windows.DependencyObjectType
IsSealed                    : False
Dispatcher                  : System.Windows.Threading.Dispatcher

```

###  <a name="IsVisible"></a> IsVisible
  在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

 布尔值属性，指示附加设备工具当前是否在其已分配的窗格中可见。 如果可见，则可以将 **IsVisible** 属性设置为 **$false** 以隐藏工具，或将 **IsVisible** 属性设置为 **$true** 以使附加设备工具在其 PowerShell 选项卡上可见。 请注意，隐藏附加设备工具后，将无法再通过 **CurrentVisibleHorizontalTool** 或 **CurrentVisibleVerticalTool** 对象对其进行访问，因此无法使用该对象上的此属性使其可见。

```
# Hide the current tool in the vertical tool pane
$psISE.CurrentVisibleVerticalTool.IsVisible = $false
# Show the first tool on the currently selected PowerShell tab
$psISE.CurrentPowerShellTab.VerticalAddOnTools[0].IsVisible=$true

```

###  <a name="name"></a> 名称
  在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。

 只读属性，可获取附加设备工具的名称。

```
# Gets the name of the visible vertical pane add-on tool.
$psISE.CurrentVisibleVerticalTool.name
Commands

```

## 另请参阅
 [ISEAddOnToolCollection 对象](The-ISEAddOnToolCollection-Object.md)
 [Windows PowerShell ISE 脚本对象模型](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
 [Windows PowerShell ISE 对象模型参考](Windows-PowerShell-ISE-Object-Model-Reference.md)
 [ISE 对象模型层次结构](The-ISE-Object-Model-Hierarchy.md)



<!--HONumber=May16_HO2-->


