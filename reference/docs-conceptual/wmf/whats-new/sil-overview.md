---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
title: 软件清单日志记录 (SIL)
ms.openlocfilehash: b12cfc4ae1e505bbc4d47596bed9352ce53a98f2
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2019
ms.locfileid: "71147777"
---
# <a name="software-inventory-logging-sil"></a><span data-ttu-id="1d057-103">软件清单日志记录 (SIL)</span><span class="sxs-lookup"><span data-stu-id="1d057-103">Software Inventory Logging (SIL)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1d057-104">当在已经运行 SIL 的 Windows Server 2012 R2 Server 上安装 WMF 5.x 时，WMF 安装后，有必要运行 Start-SilLogging cmdlet，因为安装进程会错误地停止“软件清单日志记录”功能。</span><span class="sxs-lookup"><span data-stu-id="1d057-104">When installing WMF 5.x on a Windows Server 2012 R2 Server that is already running SIL, it is necessary to run the Start-SilLogging cmdlet once after the WMF install, as the installation process will errantly stop the Software Inventory Logging feature.</span></span>

<span data-ttu-id="1d057-105">“软件清单日志记录”有助于降低获取服务器上本地安装的有关 Microsoft 软件的准确信息时存在的运营成本，尤其适用于这些软件分布在 IT 环境中的多台服务器上的情形（假设已安装该软件并在 IT 环境中运行）。</span><span class="sxs-lookup"><span data-stu-id="1d057-105">Software Inventory Logging helps reduce the operational costs of getting accurate information about the Microsoft software installed locally on a server, but especially across many servers in an IT environment (assuming the software is installed and running across the IT environment).</span></span> <span data-ttu-id="1d057-106">假设已设置一条日志，则可以将此数据转发到聚合服务器，并通过使用统一的自动化进程将日志数据收集到一个位置。</span><span class="sxs-lookup"><span data-stu-id="1d057-106">Provided one is set up, you can forward this data to an aggregation server, and collect the log data in one place by using a uniform, automatic process.</span></span>

<span data-ttu-id="1d057-107">虽然你还可以通过直接查询每台计算机来记录软件清单数据，但“软件清单日志记录”仍然可以通过由每台服务器启动的转发（通过网络）体系结构，来克服许多软件清单与资产管理方案经常存在的服务器发现难题。</span><span class="sxs-lookup"><span data-stu-id="1d057-107">While you can also log software inventory data by querying each computer directly, Software Inventory Logging, by employing a forwarding (over the network) architecture initiated by each server, can overcome server discovery challenges that are typical for many software inventory and asset management scenarios.</span></span> <span data-ttu-id="1d057-108">“软件清单日志记录”使用 SSL 保护通过 HTTPS 转发到聚合服务器的数据。</span><span class="sxs-lookup"><span data-stu-id="1d057-108">Software Inventory Logging uses SSL to secure data that is forwarded over HTTPS to an aggregation server.</span></span> <span data-ttu-id="1d057-109">将数据存储到一个位置可以更方便地随时分析、处理和共享数据。</span><span class="sxs-lookup"><span data-stu-id="1d057-109">Storing the data in one place makes the data easier to analyze, manipulate, and share when necessary.</span></span>

<span data-ttu-id="1d057-110">该功能在执行过程中不会将其中的任何数据发送到 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="1d057-110">None of this data is sent to Microsoft as part of the feature functionality.</span></span> <span data-ttu-id="1d057-111">软件清单日志记录数据和功能仅供服务器软件的已授权所有者和管理员使用。</span><span class="sxs-lookup"><span data-stu-id="1d057-111">Software Inventory Logging data and functionality is meant for the sole use of the server software’s licensed owner and administrators.</span></span>

<span data-ttu-id="1d057-112">有关软件清单日志记录 cmdlet 的详细信息和文档，请参阅[在 Windows Server 2012 R2 中管理软件清单日志记录](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383584(v=ws.11))。</span><span class="sxs-lookup"><span data-stu-id="1d057-112">For more information and documentation about Software Inventory Logging cmdlets, see [Manage Software Inventory Logging in Windows Server 2012 R2](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383584(v=ws.11)).</span></span>
