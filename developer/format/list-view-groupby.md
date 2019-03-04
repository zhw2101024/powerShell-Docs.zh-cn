---
title: 列表视图 (GroupBy) |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2e66c86-83a7-4148-8575-c28d6d429d4f
caps.latest.revision: 6
ms.openlocfilehash: ad7ea457fe0f67bfa41f6bf81f36d4b2e4a76cb3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860143"
---
# <a name="list-view-groupby"></a><span data-ttu-id="25e53-102">列表视图 (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="25e53-102">List View (GroupBy)</span></span>

<span data-ttu-id="25e53-103">此示例演示如何实现将列表的行分隔成组的列表视图。</span><span class="sxs-lookup"><span data-stu-id="25e53-103">This example shows how to implement a list view that separates the rows of the list into groups.</span></span> <span data-ttu-id="25e53-104">此列表视图显示的属性[System.Serviceprocess.Servicecontroller？Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController)返回的对象[Get-service](/powershell/module/microsoft.powershell.management/get-service) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="25e53-104">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="25e53-105">列表视图的组件的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="25e53-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>
<span data-ttu-id="25e53-106">此示例演示如何实现将列表的行分隔成组的列表视图。</span><span class="sxs-lookup"><span data-stu-id="25e53-106">This example shows how to implement a list view that separates the rows of the list into groups.</span></span> <span data-ttu-id="25e53-107">此列表视图显示的属性[System.Serviceprocess.Servicecontroller？Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController)返回的对象[Get-service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="25e53-107">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="25e53-108">列表视图的组件的详细信息，请参阅[创建列表视图](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="25e53-108">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="25e53-109">若要加载此格式设置文件</span><span class="sxs-lookup"><span data-stu-id="25e53-109">To load this formatting file</span></span>

1. <span data-ttu-id="25e53-110">将 XML 从本主题的示例部分复制到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="25e53-110">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="25e53-111">保存文本文件。</span><span class="sxs-lookup"><span data-stu-id="25e53-111">Save the text file.</span></span> <span data-ttu-id="25e53-112">请务必添加`format.ps1xml`扩展其标识为格式设置文件的文件。</span><span class="sxs-lookup"><span data-stu-id="25e53-112">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="25e53-113">打开 Windows PowerShell 并运行以下命令以加载到当前会话中的格式设置文件： `Update-formatdata -prependpath PathToFormattingFile`。</span><span class="sxs-lookup"><span data-stu-id="25e53-113">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="25e53-114">此格式设置文件定义显示由 Windows PowerShell 格式设置文件已定义的对象。</span><span class="sxs-lookup"><span data-stu-id="25e53-114">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="25e53-115">必须使用`prependPath`参数时运行 cmdlet，并且无法加载此格式设置文件作为一个模块。</span><span class="sxs-lookup"><span data-stu-id="25e53-115">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="25e53-116">说明</span><span class="sxs-lookup"><span data-stu-id="25e53-116">Demonstrates</span></span>

<span data-ttu-id="25e53-117">此格式设置文件演示了以下 XML 元素：</span><span class="sxs-lookup"><span data-stu-id="25e53-117">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="25e53-118">[名称](./name-element-for-view-format.md)视图元素。</span><span class="sxs-lookup"><span data-stu-id="25e53-118">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="25e53-119">[ViewSelectedBy](./viewselectedby-element-format.md)元素，用于定义该视图将显示哪些对象。</span><span class="sxs-lookup"><span data-stu-id="25e53-119">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="25e53-120">[GroupBy](./viewselectedby-element-format.md)元素，用于定义一组新对象的显示方式。</span><span class="sxs-lookup"><span data-stu-id="25e53-120">The [GroupBy](./viewselectedby-element-format.md) element that defines how a new group of objects is displayed.</span></span>

- <span data-ttu-id="25e53-121">[ListControl](./listcontrol-element-format.md)定义由视图显示哪些属性的元素。</span><span class="sxs-lookup"><span data-stu-id="25e53-121">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="25e53-122">[ListItem](./listitem-element-for-listitems-for-listcontrol-format.md)元素，用于定义列表视图中的某一行中显示的内容。</span><span class="sxs-lookup"><span data-stu-id="25e53-122">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="25e53-123">[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)定义显示的属性的元素。</span><span class="sxs-lookup"><span data-stu-id="25e53-123">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="25e53-124">示例</span><span class="sxs-lookup"><span data-stu-id="25e53-124">Example</span></span>

<span data-ttu-id="25e53-125">下面的 XML 定义启动一个新的列表视图分组时的值[System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status)属性更改。</span><span class="sxs-lookup"><span data-stu-id="25e53-125">The following XML defines a list view that starts a new group whenever the value of the [System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status) property changes.</span></span> <span data-ttu-id="25e53-126">当启动每个组时，自定义标签将显示一个包含属性的新值。</span><span class="sxs-lookup"><span data-stu-id="25e53-126">When each group is started, a custom label is displayed that includes the new value of the property.</span></span>

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <Name>System.ServiceProcess.ServiceController</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <PropertyName>Status</PropertyName>
        <Label>New Service Status</Label>
      </GroupBy>
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

<span data-ttu-id="25e53-127">下面的示例演示 Windows PowerShell 会显示如何[System.Serviceprocess.Servicecontroller？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)对象后加载此格式化文件。</span><span class="sxs-lookup"><span data-stu-id="25e53-127">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span> <span data-ttu-id="25e53-128">通过 Windows PowerShell 会自动添加空白行添加之前和之后组标签。</span><span class="sxs-lookup"><span data-stu-id="25e53-128">The blank lines added before and after the group label are automatically added by Windows PowerShell.</span></span>

```powershell
Get-Service f*
```

```output
   New Service Status: Stopped

Name        : Fax
DisplayName : Fax
ServiceType : Win32OwnProcess

   New Service Status: Running

Name        : FCSAM
DisplayName : Microsoft Antimalware Service
ServiceType : Win32OwnProcess

   New Service Status: Stopped

Name        : fdPHost
DisplayName : Function Discovery Provider Host
ServiceType : Win32ShareProcess

   New Service Status: Running

Name        : FDResPub
DisplayName : Function Discovery Resource Publication
ServiceType : Win32ShareProcess

Name        : FontCache
DisplayName : Windows Font Cache Service
ServiceType : Win32ShareProcess

   New Service Status: Stopped

Name        : FontCache3.0.0.0
DisplayName : Windows Presentation Foundation Font Cache 3.0.0.0
ServiceType : Win32OwnProcess

   New Service Status: Running

Name        : FSysAgent
DisplayName : Microsoft Forefront System Agent
ServiceType : Win32OwnProcess

Name        : FwcAgent
DisplayName : Firewall Client Agent
ServiceType : Win32OwnProcess
```

## <a name="see-also"></a><span data-ttu-id="25e53-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="25e53-129">See Also</span></span>

[<span data-ttu-id="25e53-130">格式设置文件的示例</span><span class="sxs-lookup"><span data-stu-id="25e53-130">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="25e53-131">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="25e53-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
