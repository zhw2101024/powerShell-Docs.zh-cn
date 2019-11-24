---
title: 宽视图（GroupBy） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39388197-4ff9-4889-aa32-526011afa1f6
caps.latest.revision: 6
ms.openlocfilehash: e95ec550a7815a76a8bd7f9526dfa405a9644360
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367946"
---
# <a name="wide-view-groupby"></a><span data-ttu-id="3ef93-102">宽视图 (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="3ef93-102">Wide View (GroupBy)</span></span>

<span data-ttu-id="3ef93-103">此示例演示如何实现显示 System.serviceprocess. Servicecontroller 的组的宽视图[？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController) `Get-Service` cmdlet 返回的 Fullname 对象。</span><span class="sxs-lookup"><span data-stu-id="3ef93-103">This example shows how to implement a wide view that displays groups of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="3ef93-104">有关宽视图组件的详细信息，请参阅[创建宽视图](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="3ef93-104">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="3ef93-105">加载此格式设置文件</span><span class="sxs-lookup"><span data-stu-id="3ef93-105">To load this formatting file</span></span>

1. <span data-ttu-id="3ef93-106">将本主题的 "示例" 部分中的 XML 复制到一个文本文件中。</span><span class="sxs-lookup"><span data-stu-id="3ef93-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="3ef93-107">保存文本文件。</span><span class="sxs-lookup"><span data-stu-id="3ef93-107">Save the text file.</span></span> <span data-ttu-id="3ef93-108">请确保将 `format.ps1xml` 扩展添加到文件中，以将其标识为格式文件。</span><span class="sxs-lookup"><span data-stu-id="3ef93-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="3ef93-109">打开 Windows PowerShell 并运行以下命令，将格式化文件加载到当前会话中： `Update-formatdata -prependpath PathToFormattingFile`。</span><span class="sxs-lookup"><span data-stu-id="3ef93-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="3ef93-110">此格式化文件定义已由 Windows PowerShell 格式设置文件定义的对象的显示。</span><span class="sxs-lookup"><span data-stu-id="3ef93-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting files.</span></span> <span data-ttu-id="3ef93-111">在运行 cmdlet 时，必须使用 `prependPath` 参数，并且不能将此格式化文件作为模块加载。</span><span class="sxs-lookup"><span data-stu-id="3ef93-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="3ef93-112">示例</span><span class="sxs-lookup"><span data-stu-id="3ef93-112">Demonstrates</span></span>

<span data-ttu-id="3ef93-113">此格式化文件演示了以下 XML 元素：</span><span class="sxs-lookup"><span data-stu-id="3ef93-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="3ef93-114">视图的[名称](./name-element-for-view-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="3ef93-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="3ef93-115">定义视图要显示的对象的[ViewSelectedBy](./viewselectedby-element-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="3ef93-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="3ef93-116">定义新组的显示时间的[GroupBy](./groupby-element-for-view-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="3ef93-116">The [GroupBy](./groupby-element-for-view-format.md) element that defines when a new group is displayed.</span></span>

- <span data-ttu-id="3ef93-117">定义视图显示的属性的[WideItem](./wideitem-element-for-widecontrol-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="3ef93-117">The [WideItem](./wideitem-element-for-widecontrol-format.md) element that defines what property is displayed by the view.</span></span>

## <a name="example"></a><span data-ttu-id="3ef93-118">示例</span><span class="sxs-lookup"><span data-stu-id="3ef93-118">Example</span></span>

<span data-ttu-id="3ef93-119">下面的 XML 定义显示对象组的宽视图。</span><span class="sxs-lookup"><span data-stu-id="3ef93-119">The following XML defines a wide view that displays groups of objects.</span></span> <span data-ttu-id="3ef93-120">当[system.serviceprocess](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType)属性的值发生更改时，将启动每个新组。</span><span class="sxs-lookup"><span data-stu-id="3ef93-120">Each new group is started when the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Configuration>
  <ViewDefinitions>
    <View>
      <Name>ServiceWideView</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <Label>Service Type</Label>
        <PropertyName>ServiceType</PropertyName>
      </GroupBy>
      <WideControl>
        <WideEntries>
          <WideEntry>
            <WideItem>
              <PropertyName>ServiceName</PropertyName>
            </WideItem>
          </WideEntry>
        </WideEntries>
      </WideControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

<span data-ttu-id="3ef93-121">下面的示例演示 Windows PowerShell 如何显示[system.serviceprocess. Servicecontroller？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)加载此格式化文件之后的 Fullname 对象。</span><span class="sxs-lookup"><span data-stu-id="3ef93-121">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
   Service Type: Win32OwnProcess

Fax                             FCSAM

   Service Type: Win32ShareProcess

fdPHost                         FDResPub
FontCache

   Service Type: Win32OwnProcess

FontCache3.0.0.0                FSysAgent
FwcAgent
```

## <a name="see-also"></a><span data-ttu-id="3ef93-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3ef93-122">See Also</span></span>

[<span data-ttu-id="3ef93-123">格式化文件的示例</span><span class="sxs-lookup"><span data-stu-id="3ef93-123">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="3ef93-124">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="3ef93-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
