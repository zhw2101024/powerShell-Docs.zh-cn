---
title: 宽的视图 (Basic) |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9abb63b8-6d02-4e24-9c0e-2d15a04e9051
caps.latest.revision: 8
ms.openlocfilehash: 7a36f548a3eccdf2c9cad04a8bfe28bf4e8d6dfd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860103"
---
# <a name="wide-view-basic"></a><span data-ttu-id="84bcd-102">宽视图 (Basic)</span><span class="sxs-lookup"><span data-stu-id="84bcd-102">Wide View (Basic)</span></span>

<span data-ttu-id="84bcd-103">此示例演示如何实现一个基本的宽视图，显示[System.Serviceprocess.Servicecontroller？Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController)返回的对象`Get-Service`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="84bcd-103">This example shows how to implement a basic wide view that displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="84bcd-104">有关较宽的视图的组件的详细信息，请参阅[创建较宽的视图](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="84bcd-104">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="84bcd-105">若要加载此格式设置文件</span><span class="sxs-lookup"><span data-stu-id="84bcd-105">To load this formatting file</span></span>

1. <span data-ttu-id="84bcd-106">将 XML 从本主题的示例部分复制到文本文件中。</span><span class="sxs-lookup"><span data-stu-id="84bcd-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="84bcd-107">保存文本文件。</span><span class="sxs-lookup"><span data-stu-id="84bcd-107">Save the text file.</span></span> <span data-ttu-id="84bcd-108">请务必添加`format.ps1xml`扩展其标识为格式设置文件的文件。</span><span class="sxs-lookup"><span data-stu-id="84bcd-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="84bcd-109">打开 Windows PowerShell 并运行以下命令以加载到当前会话中的格式设置文件： `Update-formatdata -prependpath PathToFormattingFile`。</span><span class="sxs-lookup"><span data-stu-id="84bcd-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="84bcd-110">此格式设置文件定义显示由 Windows PowerShell 格式设置文件已定义的对象。</span><span class="sxs-lookup"><span data-stu-id="84bcd-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="84bcd-111">必须使用`prependPath`参数时运行 cmdlet，并且无法加载此格式设置文件作为一个模块。</span><span class="sxs-lookup"><span data-stu-id="84bcd-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="84bcd-112">说明</span><span class="sxs-lookup"><span data-stu-id="84bcd-112">Demonstrates</span></span>

<span data-ttu-id="84bcd-113">此格式设置文件演示了以下 XML 元素：</span><span class="sxs-lookup"><span data-stu-id="84bcd-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="84bcd-114">[名称](./name-element-for-view-format.md)视图元素。</span><span class="sxs-lookup"><span data-stu-id="84bcd-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="84bcd-115">[ViewSelectedBy](./viewselectedby-element-format.md)元素，用于定义该视图将显示哪些对象。</span><span class="sxs-lookup"><span data-stu-id="84bcd-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="84bcd-116">[WideItem](./wideitem-element-for-widecontrol-format.md)定义由视图显示哪些属性的元素。</span><span class="sxs-lookup"><span data-stu-id="84bcd-116">The [WideItem](./wideitem-element-for-widecontrol-format.md) element that defines what property is displayed by the view.</span></span>

## <a name="example"></a><span data-ttu-id="84bcd-117">示例</span><span class="sxs-lookup"><span data-stu-id="84bcd-117">Example</span></span>

<span data-ttu-id="84bcd-118">下面的 XML 定义中显示的值较宽的视图[System.Serviceprocess.Servicecontroller.Servicename](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName)属性。</span><span class="sxs-lookup"><span data-stu-id="84bcd-118">The following XML defines a wide view that displays the value of the [System.Serviceprocess.Servicecontroller.Servicename](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName) property.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Configuration>
  <ViewDefinitions>
    <View>
      <Name>ServiceWideView</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
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

<span data-ttu-id="84bcd-119">下面的示例演示 Windows PowerShell 会显示如何[System.Serviceprocess.Servicecontroller？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)对象后加载此格式化文件。</span><span class="sxs-lookup"><span data-stu-id="84bcd-119">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
Fax                      FCSAM
fdPHost                  FDResPub
FontCache                FontCache3.0.0.0
FSysAgent                FwcAgent
```

## <a name="see-also"></a><span data-ttu-id="84bcd-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="84bcd-120">See Also</span></span>

[<span data-ttu-id="84bcd-121">格式设置文件的示例</span><span class="sxs-lookup"><span data-stu-id="84bcd-121">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="84bcd-122">编写 PowerShell 格式设置文件</span><span class="sxs-lookup"><span data-stu-id="84bcd-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
