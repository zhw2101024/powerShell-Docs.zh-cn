---
ms.date: 06/12/2017
contributor: JKeithB
keywords: 库,powershell,cmdlet,psgallery
title: 部署到 Azure 自动化
ms.openlocfilehash: 707691e24a77647064e60da0d9a31ad5eece1c59
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/27/2019
ms.locfileid: "71327908"
---
# <a name="deploy-to-azure-automation"></a><span data-ttu-id="2f6c5-103">部署到 Azure 自动化</span><span class="sxs-lookup"><span data-stu-id="2f6c5-103">Deploy to Azure Automation</span></span>

<span data-ttu-id="2f6c5-104">包详细信息页上的“部署到 Azure 自动化”按钮会将包从 PowerShell 库部署到 Azure 自动化。</span><span class="sxs-lookup"><span data-stu-id="2f6c5-104">The Deploy to Azure Automation button on the package details page will deploy the package from the PowerShell Gallery to Azure Automation.</span></span>

![“部署到 Azure 自动化”按钮](../../Images/DeployToAzureAutomationButton.png)

<span data-ttu-id="2f6c5-106">单击后，将重定向到 Azure 管理门户，可使用 Azure 帐户凭据进行登录。</span><span class="sxs-lookup"><span data-stu-id="2f6c5-106">When clicked, it will redirect you to the Azure Management Portal, where you sign in using your Azure account credentials.</span></span>
<span data-ttu-id="2f6c5-107">如果该包包含依赖关系，则所有依赖关系也将部署到 Azure 自动化。</span><span class="sxs-lookup"><span data-stu-id="2f6c5-107">If the package includes dependencies, all the dependencies will be deployed to Azure Automation as well.</span></span>

> [!WARNING]
> <span data-ttu-id="2f6c5-108">如果自动化帐户中已存在相同的包和版本，将其从 PowerShell 库再次部署会覆盖自动化帐户中的包。</span><span class="sxs-lookup"><span data-stu-id="2f6c5-108">If the same package and version already exist in your Automation account, deploying it again from the PowerShell Gallery will overwrite the package in your Automation account.</span></span>

<span data-ttu-id="2f6c5-109">如果部署模块，则该模块会出现在 Azure 自动化的“模块”部分中。</span><span class="sxs-lookup"><span data-stu-id="2f6c5-109">If you deploy a module, it will appear in the Modules section of Azure Automation.</span></span>  <span data-ttu-id="2f6c5-110">如果部署脚本，则该脚本会出现在 Azure 自动化的“Runbook”部分中。</span><span class="sxs-lookup"><span data-stu-id="2f6c5-110">If you deploy a script, it will appear in the Runbooks section of Azure Automation.</span></span>

<span data-ttu-id="2f6c5-111">通过将 AzureAutomationNotSupported 标记添加到包元数据可禁用“部署到 Azure 自动化”按钮。</span><span class="sxs-lookup"><span data-stu-id="2f6c5-111">The Deploy to Azure Automation button can be disabled by adding the AzureAutomationNotSupported tag to the package metadata.</span></span>

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a><span data-ttu-id="2f6c5-112">在部署到 Azure 自动化时需要接受许可证</span><span class="sxs-lookup"><span data-stu-id="2f6c5-112">Require License Acceptance on Deploy to Azure Automation</span></span>

<span data-ttu-id="2f6c5-113">如果正在部署到 Azure 自动化的模块需要接受许可证，则门户 UI 将会显示内容为“此模块需要接受许可证。</span><span class="sxs-lookup"><span data-stu-id="2f6c5-113">If the module being deployed to Azure Automation requires license acceptance, portal UI will show a disclaimer saying 'This module requires license acceptance.</span></span> <span data-ttu-id="2f6c5-114">单击“确定”接受许可证条款。”的声明</span><span class="sxs-lookup"><span data-stu-id="2f6c5-114">By clicking OK, you are accepting license terms.'</span></span>

![部署到 Azure 自动化需要接受许可证](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a><span data-ttu-id="2f6c5-116">详细信息</span><span class="sxs-lookup"><span data-stu-id="2f6c5-116">More details</span></span>

- [<span data-ttu-id="2f6c5-117">在 PowerShellGet 中需要接受许可证</span><span class="sxs-lookup"><span data-stu-id="2f6c5-117">Require License Acceptance in PowerShellGet</span></span>](../../concepts/module-license-acceptance.md)
- [<span data-ttu-id="2f6c5-118">在 Power 库中需要接受许可证</span><span class="sxs-lookup"><span data-stu-id="2f6c5-118">Require License Acceptance in PowerShell Gallery</span></span>](packages-that-require-license-acceptance.md)
- [<span data-ttu-id="2f6c5-119">Azure 自动化网站</span><span class="sxs-lookup"><span data-stu-id="2f6c5-119">Azure Automation website</span></span>](https://azure.microsoft.com/services/automation/)
