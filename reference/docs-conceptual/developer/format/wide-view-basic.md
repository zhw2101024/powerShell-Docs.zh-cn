---
title: 宽视图（基本） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9abb63b8-6d02-4e24-9c0e-2d15a04e9051
caps.latest.revision: 8
ms.openlocfilehash: 7a36f548a3eccdf2c9cad04a8bfe28bf4e8d6dfd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367936"
---
# <a name="wide-view-basic"></a><span data-ttu-id="56076-102">宽视图 (Basic)</span><span class="sxs-lookup"><span data-stu-id="56076-102">Wide View (Basic)</span></span>

<span data-ttu-id="56076-103">此示例演示如何实现显示[system.serviceprocess. Servicecontroller 的基本视图？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)由 `Get-Service` cmdlet 返回的 Fullname 对象。</span><span class="sxs-lookup"><span data-stu-id="56076-103">This example shows how to implement a basic wide view that displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="56076-104">有关宽视图组件的详细信息，请参阅[创建宽视图](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="56076-104">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="56076-105">加载此格式设置文件</span><span class="sxs-lookup"><span data-stu-id="56076-105">To load this formatting file</span></span>

1. <span data-ttu-id="56076-106">将本主题的 "示例" 部分中的 XML 复制到一个文本文件中。</span><span class="sxs-lookup"><span data-stu-id="56076-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="56076-107">保存文本文件。</span><span class="sxs-lookup"><span data-stu-id="56076-107">Save the text file.</span></span> <span data-ttu-id="56076-108">请确保将 @no__t 0 扩展添加到文件，以将其标识为格式文件。</span><span class="sxs-lookup"><span data-stu-id="56076-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="56076-109">打开 Windows PowerShell 并运行以下命令，将格式化文件加载到当前会话中： `Update-formatdata -prependpath PathToFormattingFile`。</span><span class="sxs-lookup"><span data-stu-id="56076-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="56076-110">此格式化文件定义已由 Windows PowerShell 格式设置文件定义的对象的显示。</span><span class="sxs-lookup"><span data-stu-id="56076-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="56076-111">当你运行 cmdlet 时，必须使用 @no__t 参数，并且无法将此格式化文件作为模块加载。</span><span class="sxs-lookup"><span data-stu-id="56076-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="56076-112">示例</span><span class="sxs-lookup"><span data-stu-id="56076-112">Demonstrates</span></span>

<span data-ttu-id="56076-113">此格式化文件演示了以下 XML 元素：</span><span class="sxs-lookup"><span data-stu-id="56076-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="56076-114">视图的[名称](./name-element-for-view-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="56076-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="56076-115">定义视图要显示的对象的[ViewSelectedBy](./viewselectedby-element-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="56076-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="56076-116">定义视图显示的属性的[WideItem](./wideitem-element-for-widecontrol-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="56076-116">The [WideItem](./wideitem-element-for-widecontrol-format.md) element that defines what property is displayed by the view.</span></span>

## <a name="example"></a><span data-ttu-id="56076-117">示例</span><span class="sxs-lookup"><span data-stu-id="56076-117">Example</span></span>

<span data-ttu-id="56076-118">下面的 XML 定义显示[system.serviceprocess. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName)属性值的宽视图。</span><span class="sxs-lookup"><span data-stu-id="56076-118">The following XML defines a wide view that displays the value of the [System.Serviceprocess.Servicecontroller.Servicename](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName) property.</span></span>

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

<span data-ttu-id="56076-119">下面的示例演示 Windows PowerShell 如何显示[system.serviceprocess. Servicecontroller？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)加载此格式化文件之后的 Fullname 对象。</span><span class="sxs-lookup"><span data-stu-id="56076-119">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
Fax                      FCSAM
fdPHost                  FDResPub
FontCache                FontCache3.0.0.0
FSysAgent                FwcAgent
```

## <a name="see-also"></a><span data-ttu-id="56076-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="56076-120">See Also</span></span>

[<span data-ttu-id="56076-121">格式化文件的示例</span><span class="sxs-lookup"><span data-stu-id="56076-121">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="56076-122">编写 PowerShell 格式化文件</span><span class="sxs-lookup"><span data-stu-id="56076-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
