---
ms.date: 04/19/2019
keywords: wmf,powershell,安装程序
title: Windows Management Framework (WMF)
ms.openlocfilehash: d581370fd602e03c86aa549eb8b273ff4d01b4e5
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2019
ms.locfileid: "71147907"
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

- [WMF 5.1](whats-new/release-notes.md#wmf-51-changes)
- [WMF 5.0](whats-new/release-notes.md#wmf-50-changes)
- [WMF 4.0](https://download.microsoft.com/download/3/D/6/3D61D262-8549-4769-A660-230B67E15B25/Windows%20Management%20Framework%204%200%20Release%20Notes.docx)
- [WMF 3.0](https://download.microsoft.com/download/E/7/6/E76850B8-DA6E-4FF5-8CCE-A24FC513FD16/WMF%203%20Release%20Notes.docx)

## <a name="wmf-availability-across-windows-operating-systems"></a>各个 Windows 操作系统间的 WMF 可用性

|        操作系统版本         | [WMF 5.1][]  | WMF 5.0<br>*不支持* | [WMF 4.0][]  | [WMF 3.0][]  | [WMF 2.0][]  |
| --------------------------------------- | ------------ | --------------------------- | ------------ | ------------ | ------------ |
| Windows Server 2019                     | 内置提供 |                             |              |              |              |
| Windows Server 2016                     | 内置提供 |                             |              |              |              |
| Windows 10                              | 内置提供 | 内置提供                |              |              |              |
| Windows Server 2012 R2                  | 是          | 是                         | 内置提供 |              |              |
| Windows 8.1                             | 是          | 是                         | 内置提供 |              |              |
| Windows Server 2012                     | 是          | 是                         | 是          | 内置提供 |              |
| Windows 8<br>*不支持*           |              |                             |              | 内置提供 |              |
| Windows Server 2008 R2 SP1              | 是          | 是                         | 是          | 是          | 内置提供 |
| Windows 7 SP1                           | 是          | 是                         | 是          | 是          | 内置提供 |
| Windows Server 2008 SP2                 |              |                             |              | 是          | 是          |
| Windows Vista<br>*不支持*       |              |                             |              |              | 是          |
| Windows Server 2003<br>*不支持* |              |                             |              |              | 是          |
| Windows XP<br>*不支持*          |              |                             |              | 是          | 是          |

- **内置提供**：指定版本的 WMF 的功能内置于所示的 Windows 客户端或 Windows Server 版本中。
- **不支持**：Microsoft 不再支持这些产品。 必须升级到受支持的新版本。 有关详细信息，请参阅 [Microsoft 生命周期策略][]页。

> [!NOTE]
> WMF 5.0 的安装程序不再可用或受支持。 它已被 WMF 5.1 取代。

[Microsoft 生命周期策略]: https://support.microsoft.com/lifecycle
[WMF 5.1]: https://aka.ms/wmf51download
[WMF 4.0]: https://aka.ms/wmf4download
[WMF 3.0]: https://aka.ms/wmf3download
[WMF 2.0]: https://aka.ms/wmf2download
