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
ms.openlocfilehash: 65d04c526ef7aa112da82adb924c0789731f3850
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853463"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a>创建具有 Windows PowerShell 活动的工作流

通过从 Visual Studio 工具箱中选择活动并将其拖动到工作流设计器窗口，可以创建 Windows PowerShell 工作流。 有关将 Windows PowerShell 活动添加到 Visual Studio 工具箱的信息，请参阅[到 Visual Studio 工具箱中添加 Windows PowerShell 活动](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)。

以下过程描述如何创建检查一组用户指定计算机的域状态，将它们加入到域中，如果它们已未联接，然后再次检查状态的工作流。

### <a name="setting-up-the-project"></a>设置项目

1. 按照中的过程[到 Visual Studio 工具箱中添加 Windows PowerShell 活动](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)若要创建工作流项目并添加从活动[Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities)并[Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities)到工具箱的程序集。

2. 将 System.Management.Automation、 Microsoft.PowerShell.Activities、 System.Management、 Microsoft.PowerShell.Management.Activities 和 Microsoft.PowerShell.Commands.Management 关于项目添加为引用程序集。

### <a name="adding-activities-to-the-workflow"></a>将活动添加到工作流

1. 添加**序列**到工作流活动。

2. 创建名为的参数`ComputerName`使用的参数类型为`String[]`。 此参数表示要检查并加入的计算机的名称。

3. 创建名为的参数`DomainCred`类型的[System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)。 此参数表示有权将计算机加入到域的域帐户的域凭据。

4. 创建名为的参数`MachineCred`类型的[System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)。 此参数表示要检查并加入的计算机上管理员的凭据。

5. 添加**ParallelForEach**内的活动**序列**活动。 输入`comp`并`ComputerName`中的文本框，以便循环，循环访问的元素`ComputerName`数组。

6. 添加**序列**活动的正文**ParallelForEach**活动。 设置**DisplayName**到序列的属性`JoinDomain`。

7. 添加**GetWmiObject**活动**JoinDomain**序列。

8. 编辑的属性**GetWmiObject**活动，如下所示。

   |属性|值|
   |--------------|-----------|
   |**类**|"Win32_ComputerSystem"|
   |**PSComputerName**|{comp}|
   |**PSCredential**|MachineCred|

9. 添加**AddComputer**活动**JoinDomain**序列后**GetWmiObject**活动。

10. 编辑的属性**AddComputer**活动，如下所示。

    |属性|值|
    |--------------|-----------|
    |**ComputerName**|{comp}|
    |**DomainCredential**|DomainCred|

11. 添加**RestartComputer**活动**JoinDomain**序列后**AddComputer**活动。

12. 编辑的属性**RestartComputer**活动，如下所示。

    |属性|值|
    |--------------|-----------|
    |**ComputerName**|{comp}|
    |**凭据**|MachineCred|
    |**For**|Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell|
    |**Force**|True|
    |Wait|True|
    |PSComputerName|{""}|

13. 添加**GetWmiObject**活动**JoinDomain**序列后**RestartComputer**活动。 编辑其属性与以前相同**GetWmiObject**活动。

    完成这些过程后，工作流设计窗口应如下所示。

    ![在工作流设计器中的 JoinDomain XAML](../media/joindomainworkflow.png)
    ![工作流设计器中的 JoinDomain XAML](../media/joindomainworkflow.png "JoinDomainWorkflow")