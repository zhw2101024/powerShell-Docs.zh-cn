---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "多计算机部署和维护"
ms.technology: powershell
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 784806197a64eb30af1ecea4af55575434ce7b87

---

# 多计算机部署和维护
此时，你已多次将 JEA 部署到本地系统。
因为你的生产环境可能由多台计算机组成，因此请务必演练部署过程中必须在每台计算机上重复的关键步骤。

## 大致步骤：
1.  将你的模块（及角色功能）复制到每个节点。
2.  将你的会话配置文件复制到每个节点。
3.  使用你的会话配置运行 `Register-PSSessionConfiguration`。
4.  在安全的位置保留会话配置和工具包的一份副本。
进行修改时，最好拥有“单一事实来源”。

## 示例脚本
以下是部署的一个示例脚本。
若要在你的环境中使用它，需使用实际文件共享和模块的名称/路径。
```PowerShell
# First, copy the session configuration and modules (containing role capability files) onto a file share you have access to.
Copy-Item -Path 'C:\Demo\Demo.pssc' -Destination '\\FileShare\JEA\Demo.pssc'
Copy-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\SomeModule\' -Recurse -Destination '\\FileShare\JEA\SomeModule'

# Next, author a setup script (C:\JEA\Deploy.ps1) to run on each individual node
    # Contents of C:\JEA\Deploy.ps1
    New-Item -ItemType Directory -Path C:\JEADeploy
    Copy-Item -Path '\\FileShare\JEA\Demo.pssc' -Destination 'C:\JEADeploy\'
    Copy-Item -Path '\\FileShare\JEA\SomeModule' -Recurse -Destination 'C:\Program Files\WindowsPowerShell\Modules' # Remember, Role Capability Files are found in modules
    if (Get-PSSessionConfiguration -Name JEADemo -ErrorAction SilentlyContinue)
    {
        Unregister-PSSessionConfiguration -Name JEADemo -ErrorAction Stop
    }

    Register-PSSessionConfiguration -Name JEADemo -Path 'C:\JEADeploy\Demo.pssc'
    Remove-Item -Path 'C:\JEADeploy' # Don't forget to clean up!

# Now, invoke the script on all of the target machines.
# Note: this requires PowerShell Remoting be enabled on each machine. Enabling PowerShell remoting is a requirement to use JEA as well.
# You may need to provide the "-Credential" parameter if your current user account does not have admin permissions on these machines.
Invoke-Command –ComputerName 'Node1', 'Node2', 'Node3', 'NodeN' -FilePath 'C:\JEA\Deploy.ps1'

# Finally, delete the session configuration and role capability files from the file share.
Remove-Item -Path '\\FileShare\JEA\Demo.pssc'
Remove-Item -Path '\\FileShare\JEA\SomeModule' -Recurse
```
## 修改功能
当处理多台计算机时，请务必以一致的方式推行修改。
JEA 拥有 DSC 资源时，这将帮助确保你的环境保持同步。
在此之前，我们强烈建议你保留会话配置的主副本，并在每次修改后进行重新部署。

## 删除功能
若要从系统中删除 JEA 配置，请在每台计算机上使用以下命令：
```PowerShell
Unregister-PSSessionConfiguration -Name JEADemo
```




<!--HONumber=Jun16_HO4-->


