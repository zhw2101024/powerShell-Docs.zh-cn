---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "ISEAddOnTool 对象"
ms.assetid: ce84d8bc-07ba-41f6-bdde-d6f3fddcd1e3
ms.openlocfilehash: b813fcac547c8069e84741081a3ceb00044bab87
ms.sourcegitcommit: 3720ce4efb6735694cfb53a1b793d949af5d1bc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/29/2017
---
# <a name="the-iseaddontool-object"></a><span data-ttu-id="dcdef-103">ISEAddOnTool 对象</span><span class="sxs-lookup"><span data-stu-id="dcdef-103">The ISEAddOnTool Object</span></span>
  <span data-ttu-id="dcdef-104">**ISEAddonTool** 对象表示已安装的可提供 Windows PowerShell ISE 附加功能的附加设备工具。</span><span class="sxs-lookup"><span data-stu-id="dcdef-104">An **ISEAddonTool** object represents an installed add-on tool that provides additional functionality toWindows PowerShell ISE.</span></span> <span data-ttu-id="dcdef-105">例如，“**命令**”工具，你可以通过单击“**查看**”，然后单击“**显示命令附加设备**”进行显示。</span><span class="sxs-lookup"><span data-stu-id="dcdef-105">An example is the **Commands** tool that you can display by clicking **View**, then **Show Command Add-on**.</span></span> <span data-ttu-id="dcdef-106">然后，你可以通过操作各种可用 **ISEAddOnTool** 对象来访问此工具。</span><span class="sxs-lookup"><span data-stu-id="dcdef-106">This tool is then accessible to you by manipulating the various available **ISEAddOnTool** objects.</span></span>

 <span data-ttu-id="dcdef-107">每个附加设备工具可以与垂直窗格或水平窗格相关联。</span><span class="sxs-lookup"><span data-stu-id="dcdef-107">Each add-on tool can be associated with either the vertical pane or the horizontal pane.</span></span> <span data-ttu-id="dcdef-108">垂直窗格停靠在 Windows PowerShell ISE 的右边缘。</span><span class="sxs-lookup"><span data-stu-id="dcdef-108">The vertical pane is docked to the right edge of Windows PowerShell ISE.</span></span> <span data-ttu-id="dcdef-109">水平窗格停靠在底部边缘。</span><span class="sxs-lookup"><span data-stu-id="dcdef-109">The horizontal pane is docked to the bottom edge.</span></span>

 <span data-ttu-id="dcdef-110">Windows PowerShell ISE 中的每个 PowerShell 选项卡上可以安装自己的附加设备工具集。</span><span class="sxs-lookup"><span data-stu-id="dcdef-110">Each PowerShell tab in Windows PowerShell ISE can have its own set of add-on tools installed.</span></span> <span data-ttu-id="dcdef-111">请参阅 [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-PowerShellTab-Object.md) 和 [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-PowerShellTab-Object.md) 以访问可用于当前选定的选项卡或 [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md) 集合对象中任何 **PowerShellTab** 对象上的相同属性的工具集合。</span><span class="sxs-lookup"><span data-stu-id="dcdef-111">See [$psISE.CurrentPowerShellTab.HorizontalAddOnTools](The-PowerShellTab-Object.md) and [$psISE.CurrentPowerShellTab.VerticalAddOnTools](The-PowerShellTab-Object.md) to access the collection of tools available to the currently selected tab or the same properties on any of the **PowerShellTab** objects in the [$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md) collection object.</span></span>

## <a name="methods"></a><span data-ttu-id="dcdef-112">方法</span><span class="sxs-lookup"><span data-stu-id="dcdef-112">Methods</span></span>
 <span data-ttu-id="dcdef-113">没有特定于 Windows PowerShell ISE 的方法可用于此类的对象。</span><span class="sxs-lookup"><span data-stu-id="dcdef-113">There are no Windows PowerShell ISE-specific methods available for objects of this class.</span></span>

## <a name="properties"></a><span data-ttu-id="dcdef-114">“属性”</span><span class="sxs-lookup"><span data-stu-id="dcdef-114">Properties</span></span>

### <a name="control"></a><span data-ttu-id="dcdef-115">控件</span><span class="sxs-lookup"><span data-stu-id="dcdef-115">Control</span></span>
  <span data-ttu-id="dcdef-116">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="dcdef-116">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="dcdef-117">**Control** 属性提供对命令附加设备工具的大量详细信息的读取访问权限。</span><span class="sxs-lookup"><span data-stu-id="dcdef-117">The **Control** property provides read access to many of the details of the Commands add-on tool.</span></span>

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

### <a name="isvisible"></a><span data-ttu-id="dcdef-118">IsVisible</span><span class="sxs-lookup"><span data-stu-id="dcdef-118">IsVisible</span></span>
  <span data-ttu-id="dcdef-119">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="dcdef-119">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="dcdef-120">布尔值属性，指示附加设备工具当前是否在其已分配的窗格中可见。</span><span class="sxs-lookup"><span data-stu-id="dcdef-120">The Boolean property that indicates whether the add-on tool is currently visible in its assigned pane.</span></span> <span data-ttu-id="dcdef-121">如果可见，则可以将 **IsVisible** 属性设置为 **$false** 以隐藏工具，或将 **IsVisible** 属性设置为 **$true** 以使附加设备工具在其 PowerShell 选项卡上可见。请注意，隐藏附加设备工具后，将无法再通过 **CurrentVisibleHorizontalTool** 或 **CurrentVisibleVerticalTool** 对象对其进行访问，因此无法使用该对象上的此属性使其可见。</span><span class="sxs-lookup"><span data-stu-id="dcdef-121">If it is visible, you can set the **IsVisible** property to **$false** to hide the tool, or set the **IsVisible** property to **$true** to make an add-on tool visible on its PowerShell tab. Note that after an add-on tool is hidden, it is no longer accessible through the **CurrentVisibleHorizontalTool** or **CurrentVisibleVerticalTool** objects, and therefore cannot be made visible by using this property on that object.</span></span>

```
# Hide the current tool in the vertical tool pane
$psISE.CurrentVisibleVerticalTool.IsVisible = $false
# Show the first tool on the currently selected PowerShell tab
$psISE.CurrentPowerShellTab.VerticalAddOnTools[0].IsVisible=$true

```

### <a name="name"></a><span data-ttu-id="dcdef-122">名称</span><span class="sxs-lookup"><span data-stu-id="dcdef-122">Name</span></span>
  <span data-ttu-id="dcdef-123">在 Windows PowerShell ISE 3.0 和更高版本中受支持，但不存在于早期版本中。</span><span class="sxs-lookup"><span data-stu-id="dcdef-123">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="dcdef-124">只读属性，可获取附加设备工具的名称。</span><span class="sxs-lookup"><span data-stu-id="dcdef-124">The read-only property that gets the name of the add-on tool.</span></span>

```
# Gets the name of the visible vertical pane add-on tool.
$psISE.CurrentVisibleVerticalTool.name
Commands

```

## <a name="see-also"></a><span data-ttu-id="dcdef-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dcdef-125">See Also</span></span>
- [<span data-ttu-id="dcdef-126">ISEAddOnToolCollection 对象</span><span class="sxs-lookup"><span data-stu-id="dcdef-126">The ISEAddOnToolCollection Object</span></span>](The-ISEAddOnToolCollection-Object.md)
- [<span data-ttu-id="dcdef-127">Windows PowerShell ISE 脚本对象模型</span><span class="sxs-lookup"><span data-stu-id="dcdef-127">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="dcdef-128">Windows PowerShell ISE 对象模型参考</span><span class="sxs-lookup"><span data-stu-id="dcdef-128">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [<span data-ttu-id="dcdef-129">ISE 对象模型层次结构</span><span class="sxs-lookup"><span data-stu-id="dcdef-129">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

