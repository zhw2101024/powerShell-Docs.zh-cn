---
title: 将资源添加到管理 OData Web 服务 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e620bf6d-76be-47b0-a7a8-f43418f30c60
caps.latest.revision: 6
ms.openlocfilehash: b81a32b867795ae51c3f5308c2f82c31ed2747fa
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858363"
---
# <a name="adding-resources-to-a-management-odata-web-service"></a>向管理 OData Web 服务添加资源

此示例演示如何使用管理 OData 架构设计器将资源添加到现有管理 OData web 服务。 [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a)示例创建公开的过程和服务器资源的 web 服务。 在此示例中，会将虚拟机 (VM) 资源添加到 web 服务。

## <a name="prerequisites"></a>必备条件

本主题假定你已下载并安装[PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a)示例中所述[创建的 Windows PowerShell Web 服务](./creating-a-management-odata-web-service.md)，并且已下载并安装[管理 OData 架构设计器](https://marketplace.visualstudio.com/items?itemName=jlisc0.ManagementODataSchemaDesigner)。 本主题还假定已在其中设置管理 Odata 终结点的计算机上安装 HYPER-V Windows PowerShell 模块。

## <a name="adding-vm-as-a-resource-to-the-web-service"></a>将 VM 作为资源添加到 Web 服务

第一步是在架构中导入架构设计器从现有管理 OData 终结点。 以下过程介绍如何执行该操作。

#### <a name="importing-an-existing-schema-into-the-schema-designer"></a>架构设计器导入现有的架构

1. 打开管理 OData 架构设计器。

2. 从**文件**菜单中，选择**文件**;**新**;**文件**。 **新的文件**此时将显示对话框。

3. 单击**管理 OData 模型**，然后单击**打开**。

4. 在主窗口中，右键单击，然后单击**架构文件**;**导入**。 **打开**此时将显示对话框。

5. 导航到在其中设置的管理 OData web 服务的文件夹[PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a)示例。 如果该示例随附的 Windows PowerShell 脚本用于设置终结点，而无需修改脚本，该文件夹是**C:\inetpub\wwwroot\Modata**。 选择 Schema.mof，然后单击**打开**。

   此时，在文本编辑器中，打开 Schema.mof 和 Schema.xml 文件，请注意，它们包含的进程和服务资源的映射。 Schema.mof 文件使用[Distributed Management Task Force](https://www.dmtf.org/) (DTMF) 托管对象 (MOF) 标准。 Schema.xml 文件使用 XML 架构中所述[资源的映射架构](./resource-mapping-schema.md)。

   以下过程介绍如何导入的架构模型中的 HYPER-V cmdlet。

#### <a name="importing-cmdlets-into-the-schema"></a>Cmdlet 导入架构

1. 右键单击架构设计器窗口的空白区域，然后单击**导入 Cmdlet**。 **Cmdlet 导入向导**此时将显示对话框。

2. 请确保**本地计算机**已选中，然后单击**下一步**。

3. 请确保选择了已安装 Windows PowerShell 模块，并从下拉列表中选择的 HYPER-V。 单击**下一步**。 单击 **下一步**。

4. 在中**Cmdlet 名词**列表中，选择**VM**。 单击“下一步”

5. 对于此示例中，我们将绑定只有的 Get 和 Delete 命令使用 cmdlet。 清除**创建**和**更新**复选框，并确保**获取**并**删除**检查对应的复选框。 请确保`Get-VM`cmdlet 选择了**获取**，和`Remove-VM`cmdlet 用于**删除**。

6. 由于 VM cmdlet 的元数据未指定输出类型，需要运行 cmdlet 来指定输出类型。 选择**提供输出类型**然后单击**运行 cmdlet**。 **运行 Cmdlet**此时将显示对话框。 单击**运行**。 **CLR 类型**框中填入`VirtualMachine`类型。 单击**确定**，然后单击**下一步**。

7. 默认情况下已选中所有 VirtualMachine 对象的属性。 您可以清除不希望从 web 服务请求此资源时所返回数据的一部分的任何属性。 单击 **下一步**。

8. 必须选择至少一个要用作键的属性。 选择**名称**在列表中，单击**下一步**。

9. 下一个窗口，可将管理 OData 资源的属性映射到基础 cmdlet 的属性。 该向导默认情况下映射具有相同名称的属性。 例如，`ComputerName`资源的属性将映射到`ComputerName`属性的 cmdlet。  这允许您指定`ComputerName`到 web 服务的请求中的属性并且具有指定的值传递给`Get-VM`cmdlet。 `Id` 和`Name`还默认映射。

   10. 单击**下一步**，然后单击**完成**。

       现在，将架构设计器窗口中显示 VM 资源。 您可以检查的属性和与资源相关联的操作。 接下来，你将更新的架构文件导出到 web 服务的虚拟目录。

#### <a name="exporting-schema-files-from-the-schema-designer"></a>从架构设计器导出架构文件

1. 右键单击架构设计器窗口的空白区域，然后单击**架构文件**;**导出**。 **另存为**此时将显示对话框。

2. 您可以导入 MOF 文件中导航到同一个目录。 命名该文件与原始的 MOF 文件 (默认情况下的 Schema.mof) 相同，然后单击**保存**。 确认你想要覆盖现有文件。

   虽然未显式指定在**另存为**对话框中，这会替换 Schema.mof 和 Schema.xml 文件。

## <a name="next-steps"></a>后续步骤

从管理 OData web 服务访问新的 VM 资源之前，必须更新 RbacConfiguration.xml 文件以允许访问 HYPER-V Windows PowerShell 模块，如中所述[基于配置的角色的授权](./configuring-role-based-authorization.md)，并且还需要重新启动 web 服务。