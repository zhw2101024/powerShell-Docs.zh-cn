---
ms.date: 07/09/2019
keywords: dsc,gpo,powershell,配置,安装程序
title: 快速入门 - 将组策略转换为 DSC
ms.openlocfilehash: 8c89dbbce5b2b146194b799d7e36ecce3105bfeb
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953464"
---
> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

# <a name="quickstart-convert-group-policy-into-dsc"></a>快速入门：将组策略转换为 DSC

可从组策略或 Azure 安全中心基线生成 DSC 配置。 [BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) 模块包含以下用于完成此任务的命令。

- `ConvertFrom-GPO` - 转换组策略，存储为文件。 还可指定一个目录，它包含多个要合并为一个配置的策略。
  - 要在环境中导出组策略，请使用 [Backup-GPO](/powershell/module/grouppolicy/backup-gpo?view=win10-ps) cmdlet，或按照[将 GPO 导出到文件](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file)中的说明进行操作。
- `ConvertFrom-SCM` - 转换安全合规性管理器基线，存储为 `.xml` 文件。
- `ConvertFrom-ASC` - 转换 Azure 安全中心基线，存储为 `.json` 文件。
- `Merge-GPOs` - 转换应用于目标计算机的组策略。

上面列出的 cmdlet 将基线转换为 DSC `.mof` 文件。 还可选择输出能编辑和重新编译的配置脚本 (`.ps1`)。 cmdlet 会检测缺少资源或资源块重复的编译错误。 注释掉可能导致编译错误的资源块。

以下示例将 [Microsoft 安全基线](https://www.microsoft.com/en-us/download/details.aspx?id=55319)转换为 DSC 配置脚本 (`.ps1`) 和 `.mof` 文件。

```powershell
Install-Module BaselineManagement
Import-Module BaselineManagement
ConvertFrom-GPO -Path '.\Windows 10 Version 1903 and Windows Server Version 1903 Security Baseline\GPOs\' -OutputConfigurationScript
```

运行命令后，可发现在当前路径下创建了默认“输出”目录中的两个文件。

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

每个托管的节点还需要以下两个模块：

- [SecurityPolicyDSC](https://www.powershellgallery.com/packages/SecurityPolicyDsc)
- [AuditPolicyDSC](https://www.powershellgallery.com/packages/AuditPolicyDsc)

> [!NOTE]
> BaselineManagement 是社区开发的一种解决方案，可使 DSC 更易被发现，用于支持来自项目维护人员的社区解决方案，而不是来自 Microsoft 的解决方案  。 可在 [GitHub](https://github.com/microsoft/BaselineManagement) 上提出有关 BaselineManagement 的新问题  。

## <a name="next-steps"></a>后续步骤

- 要将配置脚本上传到 Azure 自动化状态配置，请参阅[入门](/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation)。
- 将 SecurityPolicyDSC 和 AuditPolicyDSC 模块添加到[自动化帐户](/azure/automation/shared-resources/modules)   。
- 在 [PowerShell 库](https://www.powershellgallery.com/)中查找 DSC 配置和资源。
