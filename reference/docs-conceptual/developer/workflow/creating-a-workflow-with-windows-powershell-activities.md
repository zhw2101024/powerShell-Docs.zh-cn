---
title: 使用 Windows PowerShell 活动创建工作流 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb55971a-4ea4-4c51-aeff-4e0bb05a51b2
caps.latest.revision: 6
ms.openlocfilehash: 98cac43698b3f537ee318cd2570b2174631665a7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359626"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a>创建具有 Windows PowerShell 活动的工作流

可以通过从 Visual Studio "工具箱" 中选择 "活动" 并将其拖到 "工作流设计器" 窗口中来创建 Windows PowerShell 工作流。 有关将 Windows PowerShell 活动添加到 Visual Studio 工具箱中的信息，请参阅[将 Windows Powershell 活动添加到 Visual Studio 工具箱](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)。

下面的过程介绍如何创建一个工作流，用于检查一组用户指定计算机的域状态，将这些计算机加入域（如果尚未加入域），然后再次检查状态。

### <a name="setting-up-the-project"></a>设置项目

1. 按照[将 Windows PowerShell 活动添加到 Visual Studio 工具箱](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)中的过程，创建一个工作流项目，并将这些活动从 " [microsoft](/dotnet/api/Microsoft.PowerShell.Activities) " 和 " [microsoft. 管理](/dotnet/api/Microsoft.PowerShell.Management.Activities)" 程序集添加到 "工具箱"。

2. 将 System.object 作为引用程序集添加到项目中，以作为引用程序集的作为项目的 "管理"、"microsoft"、"管理" 和 "microsoft"。

### <a name="adding-activities-to-the-workflow"></a>向工作流添加活动

1. 向工作流添加**序列**活动。

2. 创建一个名为 `ComputerName` 的参数，参数类型为 `String[]`。 此参数表示要检查和加入的计算机的名称。

3. 创建一个名为的参数，该参数[的类型为 `DomainCred`。](/dotnet/api/System.Management.Automation.PSCredential) 此参数表示有权将计算机加入域的域帐户的域凭据。

4. 创建一个名为的参数，该参数[的类型为 `MachineCred`。](/dotnet/api/System.Management.Automation.PSCredential) 此参数表示要检查和加入计算机上的管理员的凭据。

5. 添加 "**序列**" 活动中的**ParallelForEach**活动。 在文本框中输入 `comp` 和 `ComputerName`，以便循环遍历 `ComputerName` 数组的元素。

6. 将 "**序列**" 活动添加到 " **ParallelForEach** " 活动的正文中。 将序列的**DisplayName**属性设置为 `JoinDomain`。

7. 将**GetWmiObject**活动添加到**JoinDomain**序列。

8. 按如下所示编辑 " **GetWmiObject** " 活动的属性。

   |属性|值|
   |--------------|-----------|
   |**班级**|"Win32_ComputerSystem"|
   |**PSComputerName**|压缩|
   |**PSCredential**|MachineCred|

9. 在**GetWmiObject**活动后，将**AddComputer**活动添加到**JoinDomain**序列。

10. 按如下所示编辑 " **AddComputer** " 活动的属性。

    |属性|值|
    |--------------|-----------|
    |**ComputerName**|压缩|
    |**DomainCredential**|DomainCred|

11. 在**AddComputer**活动后，将**RestartComputer**活动添加到**JoinDomain**序列。

12. 按如下所示编辑 " **RestartComputer** " 活动的属性。

    |属性|值|
    |--------------|-----------|
    |**ComputerName**|压缩|
    |**Credential**|MachineCred|
    |**进行**|WaitForServiceTypes （PowerShell）|
    |**团队**|True|
    |Wait|True|
    |PSComputerName|{""}|

13. 在**RestartComputer**活动后，将**GetWmiObject**活动添加到**JoinDomain**序列。 编辑其属性，使其与之前的**GetWmiObject**活动相同。

    完成这些过程后，工作流设计窗口应如下所示。

    ![工作流设计器中的 JoinDomain XAML](../media/joindomainworkflow.png)
    ![JOINDOMAIN xaml In workflow designer](../media/joindomainworkflow.png "JoinDomainWorkflow")