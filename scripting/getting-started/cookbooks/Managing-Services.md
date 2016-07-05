---
title: "管理服务"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 7a410e4d-514b-4813-ba0c-0d8cef88df31
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: a9d6ece1df3b66090b2abf9d85019fee4db946b5

---

# 管理服务
有八个专为各种服务任务设计的核心 Service cmdlet。 我们将只查看列出和更改服务的运行状态，但是你可以通过使用 **Get\-Help \&#42;\-Service** 获取 Service cmdlet 列表，还可以使用 **Get\-Help<Cmdlet\-Name>**（例如 **Get\-Help New\-Service**）找到每个 Service cmdlet 的相关信息。

## 获取服务
可以通过使用 **Get\-Service** cmdlet 获取本地或远程计算机上的服务。 与使用 **Get\-Process** 相同，使用不带参数的 **Get\-Service** 命令将返回所有服务。 你可以按名称进行筛选，甚至可以使用星号作为通配符：

```
PS> Get-Service -Name se*
Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

因为服务的真实名称并不总是可见，所以你可能会发现你需要按显示名称查找服务。 可以按特定名称（使用通配符或使用显示名称的列表）执行此操作：

```
PS> Get-Service -DisplayName se*
Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Running  SamSs              Security Accounts Manager
Running  seclogon           Secondary Logon
Stopped  ServiceLayer       ServiceLayer
Running  wscsvc             Security Center
PS> Get-Service -DisplayName ServiceLayer,Server
Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Stopped  ServiceLayer       ServiceLayer
```

可以使用 Get\-Service cmdlet 的 ComputerName 参数获取远程计算机上的服务。 ComputerName 参数接受多个值和通配符，因此你可以使用单个命令获取多台计算机上的服务。 例如，下面的命令获取 Server01 远程计算机上的服务。

```
Get-Service -ComputerName Server01
```

## 获取必需和从属服务
Get\-Service cmdlet 具有两个在服务管理中非常有用的参数。 DependentServices 参数获取依赖于该服务的服务。 RequiredServices 参数获取此服务所依赖的服务。

这些参数只显示 Get\-Service 返回的 System.ServiceProcess.ServiceController 对象的 DependentServices 和 ServicesDependedOn (alias\=RequiredServices) 属性的值，但是它们可简化命令，使获取此信息更加简单。

下面的命令获取 LanmanWorkstation 服务需要的服务。

```
PS> Get-Service -Name LanmanWorkstation -RequiredServices
Status   Name               DisplayName
------   ----               -----------
Running  MRxSmb20           SMB 2.0 MiniRedirector
Running  bowser             Bowser
Running  MRxSmb10           SMB 1.x MiniRedirector
Running  NSI                Network Store Interface Service
```

下面的命令获取需要 LanmanWorkstation 服务的服务。

```
PS> Get-Service -Name LanmanWorkstation -DependentServices
Status   Name               DisplayName
------   ----               -----------
Running  SessionEnv         Terminal Services Configuration
Running  Netlogon           Netlogon
Stopped  Browser            Computer Browser
Running  BITS               Background Intelligent Transfer Ser...
```

你甚至可以获取所有具有依赖关系的服务。 下面的命令所做的就是这些，然后使用 Format\-Table cmdlet 来显示计算机上服务的 Status、Name、RequiredServices 和 DependentServices 属性。

```
Get-Service -Name * | where {$_.RequiredServices -or $_.DependentServices} | Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## 停止、启动、暂停和重启服务
所有 Service cmdlet 都具有相同的一般形式。 可以按公用名或显示名称指定服务，并使用列表和通配符作为值。 若要停止打印后台处理程序，请使用：

```
Stop-Service -Name spooler
```

若要在停止后启动打印后台处理程序，请使用：

```
Start-Service -Name spooler
```

若要暂停打印后台处理程序，请使用：

```
Suspend-Service -Name spooler
```

虽然 **Restart\-Service** cmdlet 的操作方式与其他 Service cmdlet 的操作方式相同，但是我们将针对它列举一些更复杂的示例。 使用最简单的方式指定服务的名称：

```
PS> Restart-Service -Name spooler
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

你将注意到你收到了有关打印后台处理程序启动的重复警告消息。 执行需要耗费一些时间的服务操作时，Windows PowerShell 将通知你它仍在尝试执行该任务。

如果想要重启多个服务，则可获取服务列表，并对其进行筛选，然后执行重启操作：

```
PS> Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service
WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
Restart-Service : Cannot stop service 'Logical Disk Manager (dmserver)' because
 it has dependent services. It can only be stopped if the Force flag is set.
At line:1 char:57
+ Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service <<<<
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
```

虽然这些 Service cmdlet 没有 ComputerName 参数，但是你可通过使用 Invoke\-Command cmdlet 在远程计算机上运行它们。 例如，下面的命令在 Server01 远程计算机上重启后台打印程序服务。

```
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## 设置服务属性
Set\-Service cmdlet 更改本地或远程计算机上服务的属性。 因为服务状态是一种属性，所以你可以使用此 cmdlet 来启动、停止和暂停服务。 Set\-Service cmdlet 还有一个 StartupType 参数，可让你更改服务启动类型。

若要在 Windows Vista 及 Windows 的更高版本上使用 Set\-Service，请使用“以管理员身份运行”选项打开 Windows PowerShell。

有关详细信息，请参阅 [Set-Service [m2]](https://technet.microsoft.com/en-us/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)

## 另请参阅
[Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)
[Set-Service [m2]](https://technet.microsoft.com/en-us/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)
[Restart-Service [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)
[Suspend-Service [m2]](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)




<!--HONumber=Jun16_HO4-->


