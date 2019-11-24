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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359816"
---
# <a name="adding-resources-to-a-management-odata-web-service"></a>向管理 OData Web 服务添加资源

此示例演示如何使用管理 OData 架构设计器将资源添加到现有的管理 OData web 服务。 [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a)示例创建一个公开进程和服务器资源的 web 服务。 在此示例中，你将向 web 服务添加一个虚拟机（VM）资源。

## <a name="prerequisites"></a>先决条件

本主题假定你已按照[创建 Windows PowerShell Web 服务](./creating-a-management-odata-web-service.md)中所述下载并安装了[PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a)示例，并且已下载并安装了[管理 OData 架构设计器](https://marketplace.visualstudio.com/items?itemName=jlisc0.ManagementODataSchemaDesigner)。 本主题还假设你在设置管理 Odata 终结点的计算机上安装了 Hyper-v Windows PowerShell 模块。

## <a name="adding-vm-as-a-resource-to-the-web-service"></a>将 VM 作为资源添加到 Web 服务

第一步是将架构从现有的管理 OData 终结点导入到架构设计器中。 下面的过程介绍了如何执行此操作。

#### <a name="importing-an-existing-schema-into-the-schema-designer"></a>将现有架构导入到架构设计器中

1. 打开管理 OData 架构设计器。

2. 从 "**文件**" 菜单中选择 "**文件**";**新建**;**文件**。 此时将显示 "**新建文件**" 对话框。

3. 单击 "**管理 OData 模型**"，然后单击 "**打开**"。

4. 在主窗口中右键单击，然后单击 "**架构文件**";**导入**。 此时将显示 "**打开**" 对话框。

5. 导航到为[PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a)示例设置了 Management OData web 服务的文件夹。 如果你使用随该示例提供的 Windows PowerShell 脚本来设置终结点而不修改脚本，则该文件夹为**C:\inetpub\wwwroot\Modata**。 选择 "架构"，并单击 "**打开**"。

   此时，请在文本编辑器中打开架构. mof 和 .xml 文件，并注意它们包含进程和服务资源的映射。 架构的 mof 文件使用[分布式管理任务组](https://www.dmtf.org/)（DTMF）托管对象（mof）标准。 架构 .xml 文件使用[资源映射架构](./resource-mapping-schema.md)中描述的 xml 架构。

   以下过程描述如何将中的 Hyper-v cmdlet 导入到架构模型中。

#### <a name="importing-cmdlets-into-the-schema"></a>将 cmdlet 导入架构

1. 右键单击 "架构设计器" 窗口的空白区域，然后单击 "**导入 cmdlet**"。 此时将显示 " **Cmdlet 导入向导**" 对话框。

2. 请确保选择 "**本地计算机**"，然后单击 "**下一步**"。

3. 确保选中 "已安装的 Windows PowerShell 模块"，然后从下拉列表中选择 "Hyper-v"。 单击 "**下一步**"。 单击 **下一步**。

4. 在 " **Cmdlet 名词**" 列表中，选择 " **VM**"。 单击“下一步”

5. 在此示例中，我们将仅绑定带有 cmdlet 的 Get 和 Delete 命令。 清除 "**创建**" 和 "**更新**" 复选框，并确保选中 "**获取**" 和 "**删除**" 复选框。 请确保为**GET**选择 `Get-VM` cmdlet，并选择 `Remove-VM` Cmdlet 进行**删除**。

6. 由于 VM cmdlet 的元数据未指定输出类型，因此你将需要运行 cmdlet 来指定输出类型。 选择 "**提供输出类型**"，然后单击 "**运行 cmdlet**"。 此时会出现 "**运行 Cmdlet** " 对话框。 单击 "**运行**"。 将用 `VirtualMachine` 类型填充 " **CLR 类型**" 框。 单击 **"确定"** ，然后单击 "**下一步**"。

7. 默认情况下，将选择 VirtualMachine 对象的所有属性。 在从 web 服务请求此资源时，你可以清除不希望作为数据的一部分返回的任何属性。 单击 **下一步**。

8. 必须至少选择一个要用作键的属性。 在列表中选择 "**名称**"，然后单击 "**下一步**"。

9. 下一窗口允许将管理 OData 资源的属性映射到基础 cmdlet 的属性。 默认情况下，向导映射具有相同名称的属性。 例如，资源的 `ComputerName` 属性映射到 cmdlet 的 `ComputerName` 属性。  这使你可以在对 web 服务的请求中指定 `ComputerName` 属性，并将指定的值传递给 `Get-VM` cmdlet。 默认情况下，还会映射 `Id` 和 `Name`。

   10. 单击 "**下一步**"，然后单击 "**完成**"。

       VM 资源现在会显示在 "架构设计器" 窗口中。 您可以检查与资源关联的属性和操作。 接下来，将更新的架构文件导出到 web 服务的虚拟目录中。

#### <a name="exporting-schema-files-from-the-schema-designer"></a>从架构设计器导出架构文件

1. 右键单击 "架构设计器" 窗口的空白区域，然后单击 "**架构文件**";**导出**。 此时将显示 "**另存为**" 对话框。

2. 导航到从中导入 MOF 文件的目录。 将该文件命名为与原始 MOF 文件相同（默认情况下为 Schema），然后单击 "**保存**"。 确认是否要覆盖现有文件。

   尽管它未在 "**另存为**" 对话框中显式声明，但这会同时替换架构和架构 .xml 文件。

## <a name="next-steps"></a>后续步骤

从管理 OData web 服务访问新的 VM 资源之前，你必须更新 RbacConfiguration 文件以允许访问 Hyper-v Windows PowerShell 模块，如[配置基于角色的授权](./configuring-role-based-authorization.md)中所述，你还需要重新启动 web 服务。