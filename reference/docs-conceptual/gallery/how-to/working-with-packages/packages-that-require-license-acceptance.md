---
ms.date: 06/12/2017
contributor: Farehar
keywords: 库, powershell, psgallery
title: 需要接受许可证
ms.openlocfilehash: eaed248895d14bd455d2d8d3c2222d8848eeccae
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328208"
---
# <a name="require-license-acceptance"></a><span data-ttu-id="76892-103">需要接受许可证</span><span class="sxs-lookup"><span data-stu-id="76892-103">Require license acceptance</span></span>

<span data-ttu-id="76892-104">对于需要接受许可证的模块，会在项目详细信息页上显示“需要接受许可证”文本。</span><span class="sxs-lookup"><span data-stu-id="76892-104">Require License Acceptance text shows up on item details page for modules that require license acceptance.</span></span> <span data-ttu-id="76892-105">可以通过单击“View License.txt”链接查看模块的许可证。</span><span class="sxs-lookup"><span data-stu-id="76892-105">License for module can be viewed by clicking on 'View License.txt' link.</span></span>

![需要接受许可证](../../Images/RequireLicenseAcceptance.png)

<span data-ttu-id="76892-107">通过 PowerShellGet 安装、保存或更新模块或部署到 Azure 自动化时，用户将收到接受许可证的提示。</span><span class="sxs-lookup"><span data-stu-id="76892-107">Users will be prompted to accept the license when installing, saving or updating the module through PowerShellGet or when deploying to Azure Automation.</span></span>

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a><span data-ttu-id="76892-108">在部署到 Azure 自动化时需要接受许可证</span><span class="sxs-lookup"><span data-stu-id="76892-108">Require License Acceptance on Deploy to Azure Automation</span></span>

<span data-ttu-id="76892-109">如果正在部署到 Azure 自动化的模块需要接受许可证，则门户 UI 将会显示内容为“此模块需要接受许可证。</span><span class="sxs-lookup"><span data-stu-id="76892-109">If the module being deployed to Azure Automation requires license acceptance, portal UI will show a disclaimer saying 'This module requires license acceptance.</span></span> <span data-ttu-id="76892-110">单击“确定”接受许可证条款。”的声明</span><span class="sxs-lookup"><span data-stu-id="76892-110">By clicking OK, you are accepting license terms.'</span></span>

![部署到 Azure 自动化需要接受许可证](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a><span data-ttu-id="76892-112">详细信息</span><span class="sxs-lookup"><span data-stu-id="76892-112">More details</span></span>

<span data-ttu-id="76892-113">[需要在 PowerShellGet 中接受许可证](../../concepts/module-license-acceptance.md)
[Azure 自动化网站](/azure/automation)</span><span class="sxs-lookup"><span data-stu-id="76892-113">[Require License Acceptance in PowerShellGet](../../concepts/module-license-acceptance.md)
[Azure Automation website](/azure/automation)</span></span>
