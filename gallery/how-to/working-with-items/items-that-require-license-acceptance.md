---
ms.date: 06/12/2017
contributor: Farehar
ms.topic: conceptual
keywords: 库, powershell, psgallery
title: 需要接受许可证
ms.openlocfilehash: 76f16e848e1cd660e062bf8569fb914b32f14934
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2018
---
# <a name="require-license-acceptance"></a>需要接受许可证

对于需要接受许可证的模块，会在项目详细信息页上显示“需要接受许可证”文本。 可以通过单击“View License.txt”链接查看模块的许可证。

![需要接受许可证](../../Images/RequireLicenseAcceptance.png)

通过 PowerShellGet 安装、保存或更新模块或部署到 Azure 自动化时，用户将收到接受许可证的提示。

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a>在部署到 Azure 自动化时需要接受许可证

如果正在部署到 Azure 自动化的模块需要接受许可证，则门户 UI 将会显示内容为“此模块需要接受许可证。 单击“确定”接受许可证条款。”的声明

![部署到 Azure 自动化需要接受许可证](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a>详细信息

[需要在 PowerShellGet 中接受许可证](../../concepts/module-license-acceptance.md)
[Azure 自动化网站](/azure/automation)