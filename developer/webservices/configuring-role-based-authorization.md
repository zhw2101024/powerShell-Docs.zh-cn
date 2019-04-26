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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080673"
---
# <a name="configuring-role-based-authorization"></a>配置基于角色的授权

本主题演示如何配置的示例实现基于角色的授权策略[Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization)接口中所述[实现自定义管理 OData IIS 扩展的授权](./implementing-custom-authorization-for-a-management-odata-web-service.md)。

在此示例中，将配置 XML 文件的示例管理 OData 应用程序用于定义授权策略。 将创建两个角色，并将不同的 Windows PowerShell 模块包含与这些角色的工作流相关联。 列出定义 XML 文件的架构，则在[基于角色的授权配置架构](./role-based-authorization-configuration-schema.md)。

## <a name="modifying-the-rbacconfigurationxml-file"></a>修改 RBacConfiguration.xml 文件

此文件定义应用程序的授权策略。 通过定义角色`Group`节点。 一个`Group`节点定义分配给该组的用户可以运行的 Windows PowerShell 命令。 通过使用用户分配给组`User`节点。

在这些示例中，将模块添加到管理员`Group`节点，并将用户添加到每个组。

#### <a name="adding-a-module-to-a-group-node"></a>将模块添加到组节点

1. 创建名为的文件**RBacConfiguration.xml**在文本编辑器中。 此文件应保存到您的 web 服务的主应用程序目录。 在文件中插入以下文本。

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

2. 该文件包含两个`Group`节点。 这些表示在此示例中，所使用的两个角色`NonAdminGroup`和`AdminGroup`角色。

   关闭之后直接`Cmdlets`中第一个标记`Group`节点，添加以下 XML:

   ```xml
   <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
   ```

#### <a name="adding-a-user-to-a-group-node"></a>将用户添加到组节点

1. 打开**RBacConfiguration.xml**文本编辑器中的文件。 此文件位于文件夹 c:\\\inetpub\wwwroot\Modata 如果未更改之前安装的终结点名称。

2. 中的结束标记后面直接`Users`节点，添加以下 XML:

   ```xml
   <User Name="UserName" GroupName="AdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```

3. 直接在上一步中添加 XML 后，添加以下 XML:

   ```xml
   <User Name="UserName" GroupName="NonAdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```