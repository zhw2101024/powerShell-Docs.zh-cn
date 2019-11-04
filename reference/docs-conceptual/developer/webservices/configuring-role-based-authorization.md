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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359766"
---
# <a name="configuring-role-based-authorization"></a><span data-ttu-id="63104-102">配置基于角色的授权</span><span class="sxs-lookup"><span data-stu-id="63104-102">Configuring Role-based Authorization</span></span>

<span data-ttu-id="63104-103">本主题演示如何为 实现自定义授权进行管理中所述的 [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) 接口的示例实现配置[基于角色的授权策略OData IIS 扩展](./implementing-custom-authorization-for-a-management-odata-web-service.md)。</span><span class="sxs-lookup"><span data-stu-id="63104-103">This topic demonstrates how to configure the role-based authorization policy for the sample implementation of the [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) interface described in [Implementing Custom Authorization for Management OData IIS Extension](./implementing-custom-authorization-for-a-management-odata-web-service.md).</span></span>

<span data-ttu-id="63104-104">在此示例中，你将配置一个 XML 文件，该文件由示例管理 OData 应用程序用来定义授权策略。</span><span class="sxs-lookup"><span data-stu-id="63104-104">In this example, you will configure an XML file that is used by the sample Management OData application to define the authorization policy.</span></span> <span data-ttu-id="63104-105">你将创建两个角色，并将包含工作流的不同 Windows PowerShell 模块与这些角色关联。</span><span class="sxs-lookup"><span data-stu-id="63104-105">You will create two roles and associate different Windows PowerShell modules that contain workflows with those roles.</span></span> <span data-ttu-id="63104-106">用于定义 XML 文件的架构在[基于角色的授权配置架构](./role-based-authorization-configuration-schema.md)中列出。</span><span class="sxs-lookup"><span data-stu-id="63104-106">The schema that defines the XML file is listed at [Role-Based Authorization Configuration Schema](./role-based-authorization-configuration-schema.md).</span></span>

## <a name="modifying-the-rbacconfigurationxml-file"></a><span data-ttu-id="63104-107">修改 RBacConfiguration 文件</span><span class="sxs-lookup"><span data-stu-id="63104-107">Modifying the RBacConfiguration.xml File</span></span>

<span data-ttu-id="63104-108">此文件定义了应用程序的授权策略。</span><span class="sxs-lookup"><span data-stu-id="63104-108">This file defines the authorization policy for the application.</span></span> <span data-ttu-id="63104-109">使用 `Group` 节点定义角色。</span><span class="sxs-lookup"><span data-stu-id="63104-109">Roles are defined by using `Group` nodes.</span></span> <span data-ttu-id="63104-110">@No__t_0 节点定义分配给该组的用户可以运行的 Windows PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="63104-110">A `Group` node defines the Windows PowerShell commands that users assigned to that group can run.</span></span> <span data-ttu-id="63104-111">使用 `User` 节点将用户分配到组。</span><span class="sxs-lookup"><span data-stu-id="63104-111">Users are assigned to groups by using `User` nodes.</span></span>

<span data-ttu-id="63104-112">在这些示例中，会将一个模块添加到管理员 `Group` "节点，并将用户添加到每个组。</span><span class="sxs-lookup"><span data-stu-id="63104-112">In these examples, you will add a module to the Administrator `Group` node, and add a user to each group.</span></span>

#### <a name="adding-a-module-to-a-group-node"></a><span data-ttu-id="63104-113">向组节点添加模块</span><span class="sxs-lookup"><span data-stu-id="63104-113">Adding a Module to a Group Node</span></span>

1. <span data-ttu-id="63104-114">在文本编辑器中，创建一个名为**RBacConfiguration**的文件。</span><span class="sxs-lookup"><span data-stu-id="63104-114">Create a file named **RBacConfiguration.xml** in a text editor.</span></span> <span data-ttu-id="63104-115">应将此文件保存到 web 服务的主应用程序目录中。</span><span class="sxs-lookup"><span data-stu-id="63104-115">This file should be saved to the main application directory for your web service.</span></span> <span data-ttu-id="63104-116">在文件中插入以下文本。</span><span class="sxs-lookup"><span data-stu-id="63104-116">Insert the following text in the file.</span></span>

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

2. <span data-ttu-id="63104-117">此文件包含两个 `Group` 节点。</span><span class="sxs-lookup"><span data-stu-id="63104-117">The file contains two `Group` nodes.</span></span> <span data-ttu-id="63104-118">这表示在此示例中使用的两个角色，即 "`NonAdminGroup`" 和 "`AdminGroup`" 角色。</span><span class="sxs-lookup"><span data-stu-id="63104-118">These represent the two roles used in this example, the `NonAdminGroup` and the `AdminGroup` roles.</span></span>

   <span data-ttu-id="63104-119">在第一个 `Group` 节点的右 `Cmdlets` 标记后，添加以下 XML：</span><span class="sxs-lookup"><span data-stu-id="63104-119">Directly after the closing `Cmdlets` tag in the first `Group` node, add the following XML:</span></span>

   ```xml
   <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
   ```

#### <a name="adding-a-user-to-a-group-node"></a><span data-ttu-id="63104-120">将用户添加到组节点</span><span class="sxs-lookup"><span data-stu-id="63104-120">Adding a User to a Group Node</span></span>

1. <span data-ttu-id="63104-121">在文本编辑器中打开**RBacConfiguration**文件。</span><span class="sxs-lookup"><span data-stu-id="63104-121">Open the **RBacConfiguration.xml** file in a text editor.</span></span> <span data-ttu-id="63104-122">如果在安装之前未更改终结点名称，则此文件位于文件夹 C： \\ \inetpub\wwwroot\Modata 中。</span><span class="sxs-lookup"><span data-stu-id="63104-122">This file is located in the folder C:\\\inetpub\wwwroot\Modata  if you did not change the endpoint name before installation.</span></span>

2. <span data-ttu-id="63104-123">直接在 `Users` "节点中的结束标记后，添加以下 XML：</span><span class="sxs-lookup"><span data-stu-id="63104-123">Directly after the closing tag in the `Users` node, add the following XML:</span></span>

   ```xml
   <User Name="UserName" GroupName="AdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```

3. <span data-ttu-id="63104-124">直接在上一步添加的 XML 后面添加以下 XML：</span><span class="sxs-lookup"><span data-stu-id="63104-124">Directly after the XML added in the previous step, add the following XML:</span></span>

   ```xml
   <User Name="UserName" GroupName="NonAdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```