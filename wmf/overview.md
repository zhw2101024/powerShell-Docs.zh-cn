---
ms.date: 06/12/2018
keywords: wmf,powershell,安装程序
title: Windows Management Framework (WMF)
ms.openlocfilehash: 17011f88c364cb56a0c87f092873ccd99db450bc
ms.sourcegitcommit: 68093cc12a7a22c53d11ce7d33c18622921a0dd1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2018
ms.locfileid: "36943601"
---
# <a name="windows-management-framework"></a>Windows Management Framework

Windows Management Framework (WMF) 为 Windows 提供一致的管理界面。 WMF 提供一种无缝方式来管理各种版本的 Windows 客户端和 Windows Server。 WMF 安装程序包包含管理功能的更新，并且可用于较早版本的 Windows。

WMF 安装添加和/或更新了以下功能：

- Windows PowerShell
- Windows PowerShell Desired State Configuration (DSC)
- Windows PowerShell 集成脚本环境 (ISE)
- Windows 远程管理 (WinRM)
- Windows 管理规范 (WMI)
- Windows PowerShell Web 服务（Management OData IIS 扩展）
- 软件清单日志记录 (SIL)
- 服务器管理器 CIM 提供程序

## <a name="wmf-release-notes"></a>WMF 发行说明

若要了解给定 WMF 的 PowerShell 和其他组件中的各种增强功能，请参阅以下链接以查看发行说明：

- [WMF 5.1](5.1/release-notes.md)
- [WMF 5.0](5.0/releasenotes.md)
- [WMF 4.0](https://download.microsoft.com/download/3/D/6/3D61D262-8549-4769-A660-230B67E15B25/Windows%20Management%20Framework%204%200%20Release%20Notes.docx)
- [WMF 3.0](https://download.microsoft.com/download/E/7/6/E76850B8-DA6E-4FF5-8CCE-A24FC513FD16/WMF%203%20Release%20Notes.docx)

## <a name="wmf-availability-across-windows-operating-systems"></a>各个 Windows 操作系统间的 WMF 可用性

|操作系统版本  |[WMF 5.1][] |[WMF 5.0][] |[WMF 4.0][] |[WMF 3.0][]  |[WMF 2.0][] |
|--------------------------|------------|------------|------------|-------------|------------|
|Windows Server 2016       |内置提供|            |            |             |            |
|Windows 10                |内置提供|内置提供|            |             |            |
|Windows Server 2012 R2    |是         |是         |内置提供|             |            |
|Windows 8.1               |是         |是         |内置提供|             |            |
|Windows Server 2012       |是         |是         |是         |内置提供 |            |
|Windows 8                 |            |            |            |内置提供 |            |
|Windows Server 2008 R2 SP1|是         |是         |是         |是          |内置提供|
|Windows 7 SP1             |是         |是         |是         |是          |内置提供|
|Windows Server 2008 SP2   |            |            |            |是          |是         |
|Windows Vista             |            |            |            |             |是         |
|Windows Server 2003       |            |            |            |             |是         |
|Windows XP                |            |            |            |是          |            |

内置提供：指定版本的 WMF 的功能内置于所示的 Windows 客户端或 Windows Server 版本中。

[WMF 5.1]: https://aka.ms/wmf51download
[WMF 5.0]: https://aka.ms/wmf5download
[WMF 4.0]: https://aka.ms/wmf4download
[WMF 3.0]: https://aka.ms/wmf3download
[WMF 2.0]: https://aka.ms/wmf2download
