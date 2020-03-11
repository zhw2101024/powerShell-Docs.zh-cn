---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: 使用打印机
ms.openlocfilehash: 1d6b9a57ec61f06af694757dc8017d50b4dd40fe
ms.sourcegitcommit: 1fa89ab20d14a61f139f1394c45aaedd5a7c5438
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/09/2020
ms.locfileid: "78935212"
---
# <a name="working-with-printers-in-windows"></a>在 Windows 中使用打印机

你可以通过 PowerShell 使用 WMI 和 WSH 中的 WScript.Network  COM 对象来管理打印机。 我们将结合这两种工具来演示特定任务。

## <a name="listing-printer-connections"></a>列出打印机连接

列出计算机上安装的打印机的最简单方法是使用 WMI **Win32_Printer** 类：

```powershell
Get-CimInstance -Class Win32_Printer
```

此外还可以通过使用通常在 WSH 脚本中使用的 **WScript.Network** COM 对象列出打印机：

```powershell
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

由于此命令返回的端口名和打印机设备名的简单字符串集合没有任何可以区分的标签，因此并不容易解释。

## <a name="adding-a-network-printer"></a>添加网络打印机

若要添加新的网络打印机，请使用 **WScript.Network**：

```powershell
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

## <a name="setting-a-default-printer"></a>设置默认打印机

若要使用 WMI 设置默认打印机，请在 **Win32_Printer** 集合中查找打印机，然后调用 **SetDefaultPrinter** 方法：

```powershell
$printer = Get-CimInstance -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'"
Invoke-CimMethod -InputObject $printer -MethodName SetDefaultPrinter
```

**WScript.Network** 使用起来要简单一些，因为它具有 **SetDefaultPrinter** 方法，该方法仅将打印机名称作为参数：

```powershell
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

## <a name="removing-a-printer-connection"></a>删除打印机连接

若要删除打印机连接，请使用 **WScript.Network RemovePrinterConnection** 方法：

```powershell
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```
