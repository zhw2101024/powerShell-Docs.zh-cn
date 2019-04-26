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
# <a name="configuring-role-based-authorization"></a><span data-ttu-id="1e6f7-102">配置基于角色的授权</span><span class="sxs-lookup"><span data-stu-id="1e6f7-102">Configuring Role-based Authorization</span></span>

<span data-ttu-id="1e6f7-103">本主题演示如何配置的示例实现基于角色的授权策略[Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization)接口中所述[实现自定义管理 OData IIS 扩展的授权](./implementing-custom-authorization-for-a-management-odata-web-service.md)。</span><span class="sxs-lookup"><span data-stu-id="1e6f7-103">This topic demonstrates how to configure the role-based authorization policy for the sample implementation of the [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) interface described in [Implementing Custom Authorization for Management OData IIS Extension](./implementing-custom-authorization-for-a-management-odata-web-service.md).</span></span>

<span data-ttu-id="1e6f7-104">在此示例中，将配置 XML 文件的示例管理 OData 应用程序用于定义授权策略。</span><span class="sxs-lookup"><span data-stu-id="1e6f7-104">In this example, you will configure an XML file that is used by the sample Management OData application to define the authorization policy.</span></span> <span data-ttu-id="1e6f7-105">将创建两个角色，并将不同的 Windows PowerShell 模块包含与这些角色的工作流相关联。</span><span class="sxs-lookup"><span data-stu-id="1e6f7-105">You will create two roles and associate different Windows PowerShell modules that contain workflows with those roles.</span></span> <span data-ttu-id="1e6f7-106">列出定义 XML 文件的架构，则在[基于角色的授权配置架构](./role-based-authorization-configuration-schema.md)。</span><span class="sxs-lookup"><span data-stu-id="1e6f7-106">The schema that defines the XML file is listed at [Role-Based Authorization Configuration Schema](./role-based-authorization-configuration-schema.md).</span></span>

## <a name="modifying-the-rbacconfigurationxml-file"></a><span data-ttu-id="1e6f7-107">修改 RBacConfiguration.xml 文件</span><span class="sxs-lookup"><span data-stu-id="1e6f7-107">Modifying the RBacConfiguration.xml File</span></span>

<span data-ttu-id="1e6f7-108">此文件定义应用程序的授权策略。</span><span class="sxs-lookup"><span data-stu-id="1e6f7-108">This file defines the authorization policy for the application.</span></span> <span data-ttu-id="1e6f7-109">通过定义角色`Group`节点。</span><span class="sxs-lookup"><span data-stu-id="1e6f7-109">Roles are defined by using `Group` nodes.</span></span> <span data-ttu-id="1e6f7-110">一个`Group`节点定义分配给该组的用户可以运行的 Windows PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="1e6f7-110">A `Group` node defines the Windows PowerShell commands that users assigned to that group can run.</span></span> <span data-ttu-id="1e6f7-111">通过使用用户分配给组`User`节点。</span><span class="sxs-lookup"><span data-stu-id="1e6f7-111">Users are assigned to groups by using `User` nodes.</span></span>

<span data-ttu-id="1e6f7-112">在这些示例中，将模块添加到管理员`Group`节点，并将用户添加到每个组。</span><span class="sxs-lookup"><span data-stu-id="1e6f7-112">In these examples, you will add a module to the Administrator `Group` node, and add a user to each group.</span></span>

#### <a name="adding-a-module-to-a-group-node"></a><span data-ttu-id="1e6f7-113">将模块添加到组节点</span><span class="sxs-lookup"><span data-stu-id="1e6f7-113">Adding a Module to a Group Node</span></span>

1. <span data-ttu-id="1e6f7-114">创建名为的文件**RBacConfiguration.xml**在文本编辑器中。</span><span class="sxs-lookup"><span data-stu-id="1e6f7-114">Create a file named **RBacConfiguration.xml** in a text editor.</span></span> <span data-ttu-id="1e6f7-115">此文件应保存到您的 web 服务的主应用程序目录。</span><span class="sxs-lookup"><span data-stu-id="1e6f7-115">This file should be saved to the main application directory for your web service.</span></span> <span data-ttu-id="1e6f7-116">在文件中插入以下文本。</span><span class="sxs-lookup"><span data-stu-id="1e6f7-116">Insert the following text in the file.</span></span>

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

2. <span data-ttu-id="1e6f7-117">该文件包含两个`Group`节点。</span><span class="sxs-lookup"><span data-stu-id="1e6f7-117">The file contains two `Group` nodes.</span></span> <span data-ttu-id="1e6f7-118">这些表示在此示例中，所使用的两个角色`NonAdminGroup`和`AdminGroup`角色。</span><span class="sxs-lookup"><span data-stu-id="1e6f7-118">These represent the two roles used in this example, the `NonAdminGroup` and the `AdminGroup` roles.</span></span>

   <span data-ttu-id="1e6f7-119">关闭之后直接`Cmdlets`中第一个标记`Group`节点，添加以下 XML:</span><span class="sxs-lookup"><span data-stu-id="1e6f7-119">Directly after the closing `Cmdlets` tag in the first `Group` node, add the following XML:</span></span>

   ```xml
   <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
   ```

#### <a name="adding-a-user-to-a-group-node"></a><span data-ttu-id="1e6f7-120">将用户添加到组节点</span><span class="sxs-lookup"><span data-stu-id="1e6f7-120">Adding a User to a Group Node</span></span>

1. <span data-ttu-id="1e6f7-121">打开**RBacConfiguration.xml**文本编辑器中的文件。</span><span class="sxs-lookup"><span data-stu-id="1e6f7-121">Open the **RBacConfiguration.xml** file in a text editor.</span></span> <span data-ttu-id="1e6f7-122">此文件位于文件夹 c:\\\inetpub\wwwroot\Modata 如果未更改之前安装的终结点名称。</span><span class="sxs-lookup"><span data-stu-id="1e6f7-122">This file is located in the folder C:\\\inetpub\wwwroot\Modata  if you did not change the endpoint name before installation.</span></span>

2. <span data-ttu-id="1e6f7-123">中的结束标记后面直接`Users`节点，添加以下 XML:</span><span class="sxs-lookup"><span data-stu-id="1e6f7-123">Directly after the closing tag in the `Users` node, add the following XML:</span></span>

   ```xml
   <User Name="UserName" GroupName="AdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```

3. <span data-ttu-id="1e6f7-124">直接在上一步中添加 XML 后，添加以下 XML:</span><span class="sxs-lookup"><span data-stu-id="1e6f7-124">Directly after the XML added in the previous step, add the following XML:</span></span>

   ```xml
   <User Name="UserName" GroupName="NonAdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```