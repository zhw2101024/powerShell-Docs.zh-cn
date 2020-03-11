---
ms.date: 06/12/2017
contributor: Farehar
keywords: 库, powershell, psgallery
title: 需要接受许可证
ms.openlocfilehash: 4b293ea693062cf9717fa4ca913c3eb9abaf7014
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2020
ms.locfileid: "78278632"
---
# <a name="require-license-acceptance"></a><span data-ttu-id="93df7-103">需要接受许可证</span><span class="sxs-lookup"><span data-stu-id="93df7-103">Require license acceptance</span></span>

<span data-ttu-id="93df7-104">对于需要接受许可证的模块，会在项目详细信息页上显示“需要接受许可证”文本。</span><span class="sxs-lookup"><span data-stu-id="93df7-104">Require License Acceptance text shows up on item details page for modules that require license acceptance.</span></span> <span data-ttu-id="93df7-105">可以通过单击“View License.txt”链接查看模块的许可证。</span><span class="sxs-lookup"><span data-stu-id="93df7-105">License for module can be viewed by clicking on 'View License.txt' link.</span></span>

![需要接受许可证](media/packages-that-require-license-acceptance/RequireLicenseAcceptance.png)

<span data-ttu-id="93df7-107">通过 PowerShellGet 安装、保存或更新模块或部署到 Azure 自动化时，用户将收到接受许可证的提示。</span><span class="sxs-lookup"><span data-stu-id="93df7-107">Users will be prompted to accept the license when installing, saving or updating the module through PowerShellGet or when deploying to Azure Automation.</span></span>

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a><span data-ttu-id="93df7-108">在部署到 Azure 自动化时需要接受许可证</span><span class="sxs-lookup"><span data-stu-id="93df7-108">Require License Acceptance on Deploy to Azure Automation</span></span>

<span data-ttu-id="93df7-109">如果正在部署到 Azure 自动化的模块需要接受许可证，则门户 UI 将会显示内容为“此模块需要接受许可证。</span><span class="sxs-lookup"><span data-stu-id="93df7-109">If the module being deployed to Azure Automation requires license acceptance, portal UI will show a disclaimer saying 'This module requires license acceptance.</span></span> <span data-ttu-id="93df7-110">单击“确定”接受许可证条款。”的声明</span><span class="sxs-lookup"><span data-stu-id="93df7-110">By clicking OK, you are accepting license terms.'</span></span>

![部署到 Azure 自动化需要接受许可证](media/packages-that-require-license-acceptance/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a><span data-ttu-id="93df7-112">更多详细信息</span><span class="sxs-lookup"><span data-stu-id="93df7-112">More details</span></span>

<span data-ttu-id="93df7-113">[需要在 PowerShellGet 中接受许可证](../../concepts/module-license-acceptance.md)
[Azure 自动化网站](/azure/automation)</span><span class="sxs-lookup"><span data-stu-id="93df7-113">[Require License Acceptance in PowerShellGet](../../concepts/module-license-acceptance.md)
[Azure Automation website](/azure/automation)</span></span>
