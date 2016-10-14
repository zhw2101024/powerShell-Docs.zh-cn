# Update-Module

从联机库中下载指定模块的最新版本，并将其安装到本地计算机。

## 说明

Update-Module cmdlet 安装通过在本地计算机上运行 Install-Module 从联机库中安装的 Windows PowerShell 模块的较新版本。

默认情况下，除非指定了所需的版本，否则会安装联机库中提供的指定模块的最新版本。 可通过指定模块的名称，更新现有的已安装模块；Update-Module 搜索 $env:PSModulePath 以查找要更新的模块。

运行 Update-Module（不使用 Name 参数）更新可在本地计算机上更新的所有模块。

### 注释

- 此 cmdlet 在 Windows PowerShell 3.0 或更高版本的 Windows PowerShell、Windows 7 或 Windows 2008 R2 及 Windows 的更高版本上运行。
- 如果未通过 Install-Modul 安装使用参数名称指定的模块，将出现错误。 只能通过运行 Install-Module 在从联机库安装的模块上运行 Update-Module。
- 如果 Update-Module 试图更新正在使用中的二进制文件，Update-Module 将返回一个问题，标识进程中的错误，并通知用户在停止进程后重试 Update-Module。
- 在 PowerShell 5.0 或更新的版本上，Update-Module 更新模块时会添加该模块的最新（或指定）版本，因此较旧和较新版本现将在同一目录中并存。 显示一个这些命令的输出示例将很有用。


## Cmdlet 语法
```powershell
Get-Command -Name Update-Module -Module PowerShellGet -Syntax
```

## Cmdlet 联机帮助参考

[Update-Module](http://go.microsoft.com/fwlink/?LinkID=398576)


## 示例命令

```powershell
PS C:\\windows\\system32> Update-Module -Name ContosoServer -RequiredVersion 1.5
PS C:\\windows\\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.0
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\1.0
PS C:\\windows\\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
PS C:\\windows\\system32> Update-Module -Name ContosoServer
PS C:\\windows\\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.8.1
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\2.8.1
Name : ContosoServer
Version : 2.0
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\1.0
PS C:\\windows\\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module
```


###  更新 TestDepWithNestedRequiredModules1 模块及其依赖项。
```powershell
Find-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo -AllVersions

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module

Update-Module -Name TestDepWithNestedRequiredModules1 -RequiredVersion 2.0
Get-InstalledModule

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        NestedRequiredModule1               LocalRepo   NestedRequiredModule1 module
2.5        NestedRequiredModule2               LocalRepo   NestedRequiredModule2 module
2.0        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
2.5        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
1.0        RequiredModule1                     LocalRepo   RequiredModule1 module
2.5        RequiredModule2                     LocalRepo   RequiredModule2 module
2.0        RequiredModule3                     LocalRepo   RequiredModule3 module
2.5        RequiredModule3                     LocalRepo   RequiredModule3 module
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
```

<!--HONumber=Aug16_HO3-->


