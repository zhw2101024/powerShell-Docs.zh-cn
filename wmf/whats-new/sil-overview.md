---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
title: 软件清单日志记录 (SIL)
ms.openlocfilehash: b12cfc4ae1e505bbc4d47596bed9352ce53a98f2
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855432"
---
# <a name="software-inventory-logging-sil"></a>软件清单日志记录 (SIL)

> [!IMPORTANT]
> 当在已经运行 SIL 的 Windows Server 2012 R2 Server 上安装 WMF 5.x 时，WMF 安装后，有必要运行 Start-SilLogging cmdlet，因为安装进程会错误地停止“软件清单日志记录”功能。

“软件清单日志记录”有助于降低获取服务器上本地安装的有关 Microsoft 软件的准确信息时存在的运营成本，尤其适用于这些软件分布在 IT 环境中的多台服务器上的情形（假设已安装该软件并在 IT 环境中运行）。 假设已设置一条日志，则可以将此数据转发到聚合服务器，并通过使用统一的自动化进程将日志数据收集到一个位置。

虽然你还可以通过直接查询每台计算机来记录软件清单数据，但“软件清单日志记录”仍然可以通过由每台服务器启动的转发（通过网络）体系结构，来克服许多软件清单与资产管理方案经常存在的服务器发现难题。 “软件清单日志记录”使用 SSL 保护通过 HTTPS 转发到聚合服务器的数据。 将数据存储到一个位置可以更方便地随时分析、处理和共享数据。

该功能在执行过程中不会将其中的任何数据发送到 Microsoft。 软件清单日志记录数据和功能仅供服务器软件的已授权所有者和管理员使用。

有关软件清单日志记录 cmdlet 的详细信息和文档，请参阅[在 Windows Server 2012 R2 中管理软件清单日志记录](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383584(v=ws.11))。
