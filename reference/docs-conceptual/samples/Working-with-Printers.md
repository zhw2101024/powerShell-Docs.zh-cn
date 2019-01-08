---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 使用打印机
ms.assetid: 4f29ead3-f83b-4706-ac3e-f2154ff38dc5
ms.openlocfilehash: 5638629fdf79371c8eff9ee9194b642034250fff
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401017"
---
# <a name="working-with-printers"></a><span data-ttu-id="6b227-103">使用打印机</span><span class="sxs-lookup"><span data-stu-id="6b227-103">Working with Printers</span></span>

<span data-ttu-id="6b227-104">你可以通过 Windows PowerShell 使用 WMI 和 WSH 中的 WScript.Network COM 对象来管理打印机。</span><span class="sxs-lookup"><span data-stu-id="6b227-104">You can use Windows PowerShell to manage printers by using WMI and the WScript.Network COM object from WSH.</span></span> <span data-ttu-id="6b227-105">我们将结合这两种工具来演示特定任务。</span><span class="sxs-lookup"><span data-stu-id="6b227-105">We will use a mix of both tools to demonstrate specific tasks.</span></span>

### <a name="listing-printer-connections"></a><span data-ttu-id="6b227-106">列出打印机连接</span><span class="sxs-lookup"><span data-stu-id="6b227-106">Listing Printer Connections</span></span>

<span data-ttu-id="6b227-107">列出计算机上安装的打印机的最简单方法是使用 WMI **Win32_Printer** 类：</span><span class="sxs-lookup"><span data-stu-id="6b227-107">The simplest way to list the printers installed on a computer is to use the WMI **Win32_Printer** class:</span></span>

```powershell
Get-WmiObject -Class Win32_Printer -ComputerName
```

<span data-ttu-id="6b227-108">此外还可以通过使用通常在 WSH 脚本中使用的 **WScript.Network** COM 对象列出打印机：</span><span class="sxs-lookup"><span data-stu-id="6b227-108">You can also list the printers by using the **WScript.Network** COM object that is typically used in WSH scripts:</span></span>

```powershell
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

<span data-ttu-id="6b227-109">由于此命令返回的端口名和打印机设备名的简单字符串集合没有任何可以区分的标签，因此并不容易解释。</span><span class="sxs-lookup"><span data-stu-id="6b227-109">Because this command returns a simple string collection of port names and printer device names without any distinguishing labels, it is not easy to interpret.</span></span>

### <a name="adding-a-network-printer"></a><span data-ttu-id="6b227-110">添加网络打印机</span><span class="sxs-lookup"><span data-stu-id="6b227-110">Adding a Network Printer</span></span>

<span data-ttu-id="6b227-111">若要添加新的网络打印机，请使用 **WScript.Network**：</span><span class="sxs-lookup"><span data-stu-id="6b227-111">To add a new network printer, use **WScript.Network**:</span></span>

```powershell
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

### <a name="setting-a-default-printer"></a><span data-ttu-id="6b227-112">设置默认打印机</span><span class="sxs-lookup"><span data-stu-id="6b227-112">Setting a Default Printer</span></span>

<span data-ttu-id="6b227-113">若要使用 WMI 设置默认打印机，请在 **Win32_Printer** 集合中查找打印机，然后调用 **SetDefaultPrinter** 方法：</span><span class="sxs-lookup"><span data-stu-id="6b227-113">To use WMI to set the default printer, find the printer in the **Win32_Printer** collection and then invoke the **SetDefaultPrinter** method:</span></span>

```powershell
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

<span data-ttu-id="6b227-114">**WScript.Network** 使用起来要简单一些，因为它具有 **SetDefaultPrinter** 方法，该方法仅将打印机名称作为参数：</span><span class="sxs-lookup"><span data-stu-id="6b227-114">**WScript.Network** is a little simpler to use, because it has a **SetDefaultPrinter** method that takes only the printer name as an argument:</span></span>

```powershell
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

### <a name="removing-a-printer-connection"></a><span data-ttu-id="6b227-115">删除打印机连接</span><span class="sxs-lookup"><span data-stu-id="6b227-115">Removing a Printer Connection</span></span>

<span data-ttu-id="6b227-116">若要删除打印机连接，请使用 **WScript.Network RemovePrinterConnection** 方法：</span><span class="sxs-lookup"><span data-stu-id="6b227-116">To remove a printer connection, use the **WScript.Network RemovePrinterConnection** method:</span></span>

```powershell
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```