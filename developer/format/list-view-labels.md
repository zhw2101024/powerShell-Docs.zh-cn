---
title: 列表视图 （标签） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53442bb1-74a3-49f9-9150-3bc3081a7565
caps.latest.revision: 6
ms.openlocfilehash: 27de41c88e224f7610c10a764e51524016ecc8cb
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794818"
---
# <a name="list-view-labels"></a><span data-ttu-id="46f95-102">列表视图 (Label)</span><span class="sxs-lookup"><span data-stu-id="46f95-102">List View (Labels)</span></span>

<span data-ttu-id="46f95-103">此示例演示如何实现显示列表的每个行的自定义标签的列表视图。</span><span class="sxs-lookup"><span data-stu-id="46f95-103">This example shows how to implement a list view that displays a custom label for each row of the list.</span></span> <span data-ttu-id="46f95-104">此列表视图显示的属性[System.Serviceprocess.Servicecontroller？Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController)返回的对象[Get-service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="46f95-104">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="46f95-105">列表视图的组件的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="46f95-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="46f95-106">若要加载此格式设置文件</span><span class="sxs-lookup"><span data-stu-id="46f95-106">To load this formatting file</span></span>

1. <span data-ttu-id="46f95-107">将 XML 从本主题的示例部分复制到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="46f95-107">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="46f95-108">保存文本文件。</span><span class="sxs-lookup"><span data-stu-id="46f95-108">Save the text file.</span></span> <span data-ttu-id="46f95-109">请务必添加`format.ps1xml`扩展其标识为格式设置文件的文件。</span><span class="sxs-lookup"><span data-stu-id="46f95-109">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="46f95-110">打开 Windows PowerShell 并运行以下命令以加载到当前会话中的格式设置文件： `Update-formatdata -prependpath PathToFormattingFile`。</span><span class="sxs-lookup"><span data-stu-id="46f95-110">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="46f95-111">此格式设置文件定义显示由 Windows PowerShell 格式设置文件已定义的对象。</span><span class="sxs-lookup"><span data-stu-id="46f95-111">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="46f95-112">必须使用`prependPath`参数时运行 cmdlet，并且无法加载此格式设置文件作为一个模块。</span><span class="sxs-lookup"><span data-stu-id="46f95-112">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="46f95-113">说明</span><span class="sxs-lookup"><span data-stu-id="46f95-113">Demonstrates</span></span>

<span data-ttu-id="46f95-114">此格式设置文件演示了以下 XML 元素：</span><span class="sxs-lookup"><span data-stu-id="46f95-114">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="46f95-115">[名称](./name-element-for-view-format.md)视图元素。</span><span class="sxs-lookup"><span data-stu-id="46f95-115">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="46f95-116">[ViewSelectedBy](./viewselectedby-element-format.md)元素，用于定义该视图将显示哪些对象。</span><span class="sxs-lookup"><span data-stu-id="46f95-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="46f95-117">[ListControl](./listcontrol-element-format.md)定义由视图显示哪些属性的元素。</span><span class="sxs-lookup"><span data-stu-id="46f95-117">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="46f95-118">[ListItem](./listitem-element-for-listitems-for-listcontrol-format.md)元素，用于定义列表视图中的某一行中显示的内容。</span><span class="sxs-lookup"><span data-stu-id="46f95-118">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="46f95-119">[标签](./label-element-for-listitem-for-listcontrol-format.md)元素，用于定义列表视图中的某一行中显示的内容。</span><span class="sxs-lookup"><span data-stu-id="46f95-119">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="46f95-120">[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)定义显示的属性的元素。</span><span class="sxs-lookup"><span data-stu-id="46f95-120">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="46f95-121">示例</span><span class="sxs-lookup"><span data-stu-id="46f95-121">Example</span></span>

<span data-ttu-id="46f95-122">下面的 XML 定义每个行中显示的自定义标签的列表视图。</span><span class="sxs-lookup"><span data-stu-id="46f95-122">The following XML defines a list view that displays a custom label in each row.</span></span> <span data-ttu-id="46f95-123">在这种情况下，标签包括每个字母大写的属性名称和"属性"一词。</span><span class="sxs-lookup"><span data-stu-id="46f95-123">In this case, the label includes the property name with each letter capitalized and the word "property".</span></span> <span data-ttu-id="46f95-124">在每个行，跟属性的值显示的属性的名称。</span><span class="sxs-lookup"><span data-stu-id="46f95-124">In each row, the name of the property is displayed followed by the value of the property.</span></span>

```xml
<Configuration>
  <ViewDefinitions>
    <View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <Label>NAME property</Label>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <Label>DISPLAYNAME property</Label>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <Label>STATUS property</Label>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <Label>SERVICETYPE property</Label>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>

  </ViewDefinitions>
</Configuration>
```

<span data-ttu-id="46f95-125">下面的示例演示 Windows PowerShell 会显示如何[System.Serviceprocess.Servicecontroller？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)对象后加载此格式化文件。</span><span class="sxs-lookup"><span data-stu-id="46f95-125">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
NAME property        : Fax
DISPLAYNAME property : Fax
STATUS property      : Stopped
SERVICETYPE property : Win32OwnProcess

NAME property        : FCSAM
DISPLAYNAME property : Microsoft Antimalware Service
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess

NAME property        : fdPHost
DISPLAYNAME property : Function Discovery Provider Host
STATUS property      : Stopped
SERVICETYPE property : Win32ShareProcess

NAME property        : FDResPub
DISPLAYNAME property : Function Discovery Resource Publication
STATUS property      : Running
SERVICETYPE property : Win32ShareProcess

NAME property        : FontCache
DISPLAYNAME property : Windows Font Cache Service
STATUS property      : Running
SERVICETYPE property : Win32ShareProcess

NAME property        : FontCache3.0.0.0
DISPLAYNAME property : Windows Presentation Foundation Font Cache 3.0.0.0
STATUS property      : Stopped
SERVICETYPE property : Win32OwnProcess

NAME property        : FSysAgent
DISPLAYNAME property : Microsoft Forefront System Agent
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess

NAME property        : FwcAgent
DISPLAYNAME property : Firewall Client Agent
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess
```

## <a name="see-also"></a><span data-ttu-id="46f95-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="46f95-126">See Also</span></span>

[<span data-ttu-id="46f95-127">格式设置文件的示例</span><span class="sxs-lookup"><span data-stu-id="46f95-127">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="46f95-128">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="46f95-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
