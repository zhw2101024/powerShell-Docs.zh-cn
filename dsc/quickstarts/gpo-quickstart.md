---
ms.date: 07/09/2019
keywords: dsc,gpo,powershell,配置,安装程序
title: 快速入门 - 将组策略转换为 DSC
ms.openlocfilehash: 8c89dbbce5b2b146194b799d7e36ecce3105bfeb
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67787373"
---
> <span data-ttu-id="046c6-103">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="046c6-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="quickstart-convert-group-policy-into-dsc"></a><span data-ttu-id="046c6-104">快速入门：将组策略转换为 DSC</span><span class="sxs-lookup"><span data-stu-id="046c6-104">Quickstart: Convert Group Policy into DSC</span></span>

<span data-ttu-id="046c6-105">可从组策略或 Azure 安全中心基线生成 DSC 配置。</span><span class="sxs-lookup"><span data-stu-id="046c6-105">You can generate a DSC configuration from a Group Policy or Azure Security Center baseline.</span></span> <span data-ttu-id="046c6-106">[BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) 模块包含以下用于完成此任务的命令。</span><span class="sxs-lookup"><span data-stu-id="046c6-106">The [BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) module includes the following commands for accomplishing this task.</span></span>

- <span data-ttu-id="046c6-107">`ConvertFrom-GPO` - 转换组策略，存储为文件。</span><span class="sxs-lookup"><span data-stu-id="046c6-107">`ConvertFrom-GPO` - Converts Group Policies, stored as files.</span></span> <span data-ttu-id="046c6-108">还可指定一个目录，它包含多个要合并为一个配置的策略。</span><span class="sxs-lookup"><span data-stu-id="046c6-108">You can also specify a directory containing multiple policies that will be combined into one Configuration.</span></span>
  - <span data-ttu-id="046c6-109">要在环境中导出组策略，请使用 [Backup-GPO](/powershell/module/grouppolicy/backup-gpo?view=win10-ps) cmdlet，或按照[将 GPO 导出到文件](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file)中的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="046c6-109">To export Group Policies in your environment, use the [Backup-GPO](/powershell/module/grouppolicy/backup-gpo?view=win10-ps) cmdlet, or follow the instructions in [Export a GPO to a File](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file).</span></span>
- <span data-ttu-id="046c6-110">`ConvertFrom-SCM` - 转换安全合规性管理器基线，存储为 `.xml` 文件。</span><span class="sxs-lookup"><span data-stu-id="046c6-110">`ConvertFrom-SCM` - Converts Security Compliance Manager baselines, stored as `.xml` files.</span></span>
- <span data-ttu-id="046c6-111">`ConvertFrom-ASC` - 转换 Azure 安全中心基线，存储为 `.json` 文件。</span><span class="sxs-lookup"><span data-stu-id="046c6-111">`ConvertFrom-ASC` - Converts Azure Security Center baselines, stored as `.json` files.</span></span>
- <span data-ttu-id="046c6-112">`Merge-GPOs` - 转换应用于目标计算机的组策略。</span><span class="sxs-lookup"><span data-stu-id="046c6-112">`Merge-GPOs` - Converts Group Policies applied to a target computer.</span></span>

<span data-ttu-id="046c6-113">上面列出的 cmdlet 将基线转换为 DSC `.mof` 文件。</span><span class="sxs-lookup"><span data-stu-id="046c6-113">The cmdlets listed above convert a baseline into a DSC `.mof` file.</span></span> <span data-ttu-id="046c6-114">还可选择输出能编辑和重新编译的配置脚本 (`.ps1`)。</span><span class="sxs-lookup"><span data-stu-id="046c6-114">You can also choose to output a Configuration script (`.ps1`), that you can edit and recompile.</span></span> <span data-ttu-id="046c6-115">cmdlet 会检测缺少资源或资源块重复的编译错误。</span><span class="sxs-lookup"><span data-stu-id="046c6-115">The cmdlets detect compilation errors for missing resources, or duplicate resource blocks.</span></span> <span data-ttu-id="046c6-116">注释掉可能导致编译错误的资源块。</span><span class="sxs-lookup"><span data-stu-id="046c6-116">Resource blocks that would cause compilation errors are commented out.</span></span>

<span data-ttu-id="046c6-117">以下示例将 [Microsoft 安全基线](https://www.microsoft.com/en-us/download/details.aspx?id=55319)转换为 DSC 配置脚本 (`.ps1`) 和 `.mof` 文件。</span><span class="sxs-lookup"><span data-stu-id="046c6-117">The following example converts a [Microsoft Security Baseline](https://www.microsoft.com/en-us/download/details.aspx?id=55319) into a DSC configuration script (`.ps1`) and `.mof` file.</span></span>

```powershell
Install-Module BaselineManagement
Import-Module BaselineManagement
ConvertFrom-GPO -Path '.\Windows 10 Version 1903 and Windows Server Version 1903 Security Baseline\GPOs\' -OutputConfigurationScript
```

<span data-ttu-id="046c6-118">运行命令后，可发现在当前路径下创建了默认“输出”目录中的两个文件。</span><span class="sxs-lookup"><span data-stu-id="046c6-118">After running the commands, you see two files in the default "Output" directory created under your current path.</span></span>

```powershell
Get-ChildItem -Path .\Output
```

```Output
    Directory:  C:\Temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----         7/9/2019   9:35 AM   227.37KB DSCFromGPO.ps1
-a----         7/9/2019   9:35 AM   410.03KB localhost.mof
```

<span data-ttu-id="046c6-119">每个托管的节点还需要以下两个模块：</span><span class="sxs-lookup"><span data-stu-id="046c6-119">Each managed node will also need the following two modules:</span></span>

- [<span data-ttu-id="046c6-120">SecurityPolicyDSC</span><span class="sxs-lookup"><span data-stu-id="046c6-120">SecurityPolicyDSC</span></span>](https://www.powershellgallery.com/packages/SecurityPolicyDsc)
- [<span data-ttu-id="046c6-121">AuditPolicyDSC</span><span class="sxs-lookup"><span data-stu-id="046c6-121">AuditPolicyDSC</span></span>](https://www.powershellgallery.com/packages/AuditPolicyDsc)

> [!NOTE]
> <span data-ttu-id="046c6-122">BaselineManagement 是社区开发的一种解决方案，可使 DSC 更易被发现，用于支持来自项目维护人员的社区解决方案，而不是来自 Microsoft 的解决方案  。</span><span class="sxs-lookup"><span data-stu-id="046c6-122">**BaselineManagement** is a solution developed by the community to make DSC more discoverable for Support for community solutions come from the project maintainers and not from Microsoft.</span></span> <span data-ttu-id="046c6-123">可在 [GitHub](https://github.com/microsoft/BaselineManagement) 上提出有关 BaselineManagement 的新问题  。</span><span class="sxs-lookup"><span data-stu-id="046c6-123">You can open a new issue for **BaselineManagement** on [GitHub](https://github.com/microsoft/BaselineManagement).</span></span>

## <a name="next-steps"></a><span data-ttu-id="046c6-124">后续步骤</span><span class="sxs-lookup"><span data-stu-id="046c6-124">Next steps</span></span>

- <span data-ttu-id="046c6-125">要将配置脚本上传到 Azure 自动化状态配置，请参阅[入门](/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation)。</span><span class="sxs-lookup"><span data-stu-id="046c6-125">To upload your configuration script into Azure Automation State Configuration, see [Getting Started](/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation).</span></span>
- <span data-ttu-id="046c6-126">将 SecurityPolicyDSC 和 AuditPolicyDSC 模块添加到[自动化帐户](/azure/automation/shared-resources/modules)   。</span><span class="sxs-lookup"><span data-stu-id="046c6-126">Add the **SecurityPolicyDSC** and **AuditPolicyDSC** modules to your [Automation Account](/azure/automation/shared-resources/modules).</span></span>
- <span data-ttu-id="046c6-127">在 [PowerShell 库](https://www.powershellgallery.com/)中查找 DSC 配置和资源。</span><span class="sxs-lookup"><span data-stu-id="046c6-127">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
