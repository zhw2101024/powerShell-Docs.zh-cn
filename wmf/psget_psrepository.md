# 注册 PowerShell 存储库
你可以配置 PowerShellGet 以针对内部存储库进行操作。 可通过使用以下附加内容完成此配置：
- Register-PSRepository：为当前用户注册存储库。
- Unregister-PSRepository：为当前用户删除已注册的存储库。
- Set-PSRepository：为已注册的存储库设置值。
- Get-PSRepository：为当前用户获取所有已注册的存储库。

注册存储库后，可以使用 Find-Module 和 Install-Module 对它进行操作。

```powershell
\#Register a default repository
Register-PSRepository –Name DemoRepo –SourceLocation “https://www.myget.org/F/powershellgetdemo/api/v2” –PublishLocation “<https://www.myget.org/F/powershellgetdemo/api/v2>/package” –InstallationPolicy –Trusted

\#Get all of the registered repositories
Get-PSRepository
Name SourceLocation
---- --------------
PSGallery https://msconfiggallery.cloudapp...
DemoRepo https://www.myget.org/F/powershe...

\#Search only the new repository for modules
Find-Module -Repository DemoRepo
Repository Version Name
---------- ------- ----
DemoRepo 1.0.1 xActiveDirectory
DemoRepo 1.1.1 SomeModule

\#By default, PowerShellGet operates against all registered repositories when none is specified. In this example, the “SomeModule” module is installed from the DemoRepo.
Install-Module SomeModule

\#Removing a repository
Unregister-PSRepository DemoRepo
```<!--HONumber=Mar16_HO2-->
