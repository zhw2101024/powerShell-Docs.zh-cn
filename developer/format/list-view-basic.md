---
title: 列表视图 (Basic) |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 918f381c-43e6-4594-a468-a40bfa8a16d6
caps.latest.revision: 7
ms.openlocfilehash: 1c683693c331ccfaf7355a0dd51801ed6fd39b3b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853303"
---
# <a name="list-view-basic"></a><span data-ttu-id="8a1f0-102">列表视图 (Basic)</span><span class="sxs-lookup"><span data-stu-id="8a1f0-102">List View (Basic)</span></span>

<span data-ttu-id="8a1f0-103">此示例演示如何实现一个基本的列表视图，显示[System.Serviceprocess.Servicecontroller？Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController)返回的对象[Get-service](/powershell/module/microsoft.powershell.management/get-service) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8a1f0-103">This example shows how to implement a basic list view that displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="8a1f0-104">列表视图的组件的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="8a1f0-104">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>
<span data-ttu-id="8a1f0-105">此示例演示如何实现一个基本的列表视图，显示[System.Serviceprocess.Servicecontroller？Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController)返回的对象[Get-service](/powershell/module/microsoft.powershell.management/get-service) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8a1f0-105">This example shows how to implement a basic list view that displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="8a1f0-106">列表视图的组件的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="8a1f0-106">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="8a1f0-107">若要加载此格式设置文件</span><span class="sxs-lookup"><span data-stu-id="8a1f0-107">To load this formatting file</span></span>

1. <span data-ttu-id="8a1f0-108">将 XML 从本主题的示例部分复制到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="8a1f0-108">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="8a1f0-109">保存文本文件。</span><span class="sxs-lookup"><span data-stu-id="8a1f0-109">Save the text file.</span></span> <span data-ttu-id="8a1f0-110">请务必添加`format.ps1xml`扩展其标识为格式设置文件的文件。</span><span class="sxs-lookup"><span data-stu-id="8a1f0-110">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="8a1f0-111">打开 Windows PowerShell 并运行以下命令以加载到当前会话中的格式设置文件： `Update-formatdata -prependpath PathToFormattingFile`。</span><span class="sxs-lookup"><span data-stu-id="8a1f0-111">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="8a1f0-112">此格式设置文件定义显示由 Windows PowerShell 格式设置文件已定义的对象。</span><span class="sxs-lookup"><span data-stu-id="8a1f0-112">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="8a1f0-113">必须使用`prependPath`参数时运行 cmdlet，并且无法加载此格式设置文件作为一个模块。</span><span class="sxs-lookup"><span data-stu-id="8a1f0-113">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="8a1f0-114">说明</span><span class="sxs-lookup"><span data-stu-id="8a1f0-114">Demonstrates</span></span>

<span data-ttu-id="8a1f0-115">此格式设置文件演示了以下 XML 元素：</span><span class="sxs-lookup"><span data-stu-id="8a1f0-115">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="8a1f0-116">[名称](./name-element-for-view-format.md)视图元素。</span><span class="sxs-lookup"><span data-stu-id="8a1f0-116">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="8a1f0-117">[ViewSelectedBy](./viewselectedby-element-format.md)元素，用于定义该视图将显示哪些对象。</span><span class="sxs-lookup"><span data-stu-id="8a1f0-117">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="8a1f0-118">[ListControl](./listcontrol-element-format.md)定义由视图显示哪些属性的元素。</span><span class="sxs-lookup"><span data-stu-id="8a1f0-118">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="8a1f0-119">[ListItem](./listitem-element-for-listitems-for-listcontrol-format.md)元素，用于定义列表视图中的某一行中显示的内容。</span><span class="sxs-lookup"><span data-stu-id="8a1f0-119">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="8a1f0-120">[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)定义显示的属性的元素。</span><span class="sxs-lookup"><span data-stu-id="8a1f0-120">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="8a1f0-121">示例</span><span class="sxs-lookup"><span data-stu-id="8a1f0-121">Example</span></span>

<span data-ttu-id="8a1f0-122">下面的 XML 定义显示的四个属性的列表视图[System.Serviceprocess.Servicecontroller？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)对象。</span><span class="sxs-lookup"><span data-stu-id="8a1f0-122">The following XML defines a list view that displays four properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="8a1f0-123">在每个行，跟属性的值显示的属性的名称。</span><span class="sxs-lookup"><span data-stu-id="8a1f0-123">In each row, the name of the property is displayed followed by the value of the property.</span></span>

```xml
<Configuration>
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
              <PropertyName>Name</PropertyName>
            </ListItem>
            <ListItem>
              <PropertyName>DisplayName</PropertyName>
            </ListItem>
            <ListItem>
              <PropertyName>Status</PropertyName>
            </ListItem>
            <ListItem>
              <PropertyName>ServiceType</PropertyName>
            </ListItem>
          </ListItems>
        </ListEntry>
      </ListEntries>
    </ListControl>
  </View>
</Configuration>
```

<span data-ttu-id="8a1f0-124">下面的示例演示 Windows PowerShell 会显示如何[System.Serviceprocess.Servicecontroller？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)对象后加载此格式化文件。</span><span class="sxs-lookup"><span data-stu-id="8a1f0-124">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
Name        : Fax
DisplayName : Fax
Status      : Stopped
ServiceType : Win32OwnProcess

Name        : FCSAM
DisplayName : Microsoft Antimalware Service
Status      : Running
ServiceType : Win32OwnProcess

Name        : fdPHost
DisplayName : Function Discovery Provider Host
Status      : Stopped
ServiceType : Win32ShareProcess

Name        : FDResPub
DisplayName : Function Discovery Resource Publication
Status      : Running
ServiceType : Win32ShareProcess

Name        : FontCache
DisplayName : Windows Font Cache Service
Status      : Running
ServiceType : Win32ShareProcess

Name        : FontCache3.0.0.0
DisplayName : Windows Presentation Foundation Font Cache 3.0.0.0
Status      : Stopped
ServiceType : Win32OwnProcess

Name        : FSysAgent
DisplayName : Microsoft Forefront System Agent
Status      : Running
ServiceType : Win32OwnProcess

Name        : FwcAgent
DisplayName : Firewall Client Agent
Status      : Running
ServiceType : Win32OwnProcess
```

## <a name="see-also"></a><span data-ttu-id="8a1f0-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8a1f0-125">See Also</span></span>

[<span data-ttu-id="8a1f0-126">格式设置文件的示例</span><span class="sxs-lookup"><span data-stu-id="8a1f0-126">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="8a1f0-127">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="8a1f0-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
