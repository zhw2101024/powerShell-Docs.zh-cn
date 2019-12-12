---
title: 配置基于角色的授权 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2933a6ca-fe92-4ba2-97ee-ef0f0d5fdfcf
caps.latest.revision: 8
ms.openlocfilehash: b73284adb4bf228510bf8134aa4c6a10561b7ea2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359766"
---
# <a name="configuring-role-based-authorization"></a>配置基于角色的授权

本主题演示如何为 实现自定义授权进行管理中所述的 [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) 接口的示例实现配置[基于角色的授权策略OData IIS 扩展](./implementing-custom-authorization-for-a-management-odata-web-service.md)。

在此示例中，你将配置一个 XML 文件，该文件由示例管理 OData 应用程序用来定义授权策略。 你将创建两个角色，并将包含工作流的不同 Windows PowerShell 模块与这些角色关联。 用于定义 XML 文件的架构在[基于角色的授权配置架构](./role-based-authorization-configuration-schema.md)中列出。

## <a name="modifying-the-rbacconfigurationxml-file"></a>修改 RBacConfiguration 文件

此文件定义了应用程序的授权策略。 使用 `Group` 节点定义角色。 `Group` 节点定义分配给该组的用户可以运行的 Windows PowerShell 命令。 使用 `User` 节点将用户分配到组。

在这些示例中，会将一个模块添加到管理员 `Group` "节点，并将用户添加到每个组。

#### <a name="adding-a-module-to-a-group-node"></a>向组节点添加模块

1. 在文本编辑器中，创建一个名为**RBacConfiguration**的文件。 应将此文件保存到 web 服务的主应用程序目录中。 在文件中插入以下文本。

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <RbacConfiguration>
     <Groups>
       <!--Group consists of the following:
         Name:  Name of the group
         UserName (Optional): Windows Identity user name
         Password (Optional): Password of the Windows user name
         DomainName (Optional): Domain for the user. For local machine account either do not include them or give the machine name. Do not give empty string
         MapIncomingUser (Optional): Boolean value indicating whether to execute cmdlet in the context of network client.

         User credentials and MapIncomingUser=true are exclusive.
       -->
       <Group Name="NonAdminGroup" MapIncomingUser="true">
         <Cmdlets>
           <Cmdlet>Get-Service</Cmdlet>
           <Cmdlet>Set-Service</Cmdlet>
           <Cmdlet>Get-Process</Cmdlet>
           <Cmdlet>Get-Item</Cmdlet>
           <Cmdlet>New-Item</Cmdlet>
           <Cmdlet>Get-Command</Cmdlet>
           <Cmdlet>ConvertTo-Xml</Cmdlet>
           <Cmdlet>ConvertTo-Json</Cmdlet>
           <Cmdlet>ConvertFrom-Json</Cmdlet>
         </Cmdlets>
       </Group>
       <Group Name="AdminGroup" MapIncomingUser="true">
         <Cmdlets>
           <Cmdlet>Get-Service</Cmdlet>
           <Cmdlet>Get-Process</Cmdlet>
           <Cmdlet>Get-Item</Cmdlet>
           <Cmdlet>New-Item</Cmdlet>
           <Cmdlet>Get-Command</Cmdlet>
           <Cmdlet>ConvertTo-Xml</Cmdlet>
           <Cmdlet>ConvertTo-Json</Cmdlet>
           <Cmdlet>ConvertFrom-Json</Cmdlet>
         </Cmdlets>
         <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
       </Group>
     </Groups>
     <Users>
       <!-- User consists of the following :
         Name: Name of the user. If a user is from a cer
         AuthenticationType: Authentication type used.
         DomainName (Optional): Domain for the user
       -->
       <User Name="localNonAdmin" AuthenticationType="Basic" GroupName="NonAdminGroup" />
       <User Name="localAdmin" AuthenticationType="Basic" GroupName="AdminGroup" />
     </Users>
   </RbacConfiguration>
   ```

2. 此文件包含两个 `Group` 节点。 这表示在此示例中使用的两个角色，即 "`NonAdminGroup`" 和 "`AdminGroup`" 角色。

   在第一个 `Group` 节点的右 `Cmdlets` 标记后，添加以下 XML：

   ```xml
   <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
   ```

#### <a name="adding-a-user-to-a-group-node"></a>将用户添加到组节点

1. 在文本编辑器中打开**RBacConfiguration**文件。 如果在安装之前未更改终结点名称，则此文件位于文件夹 C：\\\inetpub\wwwroot\Modata 中。

2. 直接在 `Users` "节点中的结束标记后，添加以下 XML：

   ```xml
   <User Name="UserName" GroupName="AdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```

3. 直接在上一步添加的 XML 后面添加以下 XML：

   ```xml
   <User Name="UserName" GroupName="NonAdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```