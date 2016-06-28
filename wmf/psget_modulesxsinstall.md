# PowerShell 5.0 或更高版本上的并行版本支持

现在，在 Windows PowerShell 5.0 或更高版本运行的 Install-Module cmdlet、Update-Module cmdlet 和 Publish-Module cmdlet 中有了对并行 (SxS) 模块版本的支持。
此外，我们还将 -RequiredVersion 参数添加到了 Publish-Module cmdlet 中以指定要发布的版本。 Path 参数现在支持具有版本文件夹的模块基准路径。

**Install-Module 示例：**
```powershell
PS C:\\windows\\system32&gt; Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.0 -Repository PSGallery
PS C:\\windows\\system32&gt; Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase
Name : PSScriptAnalyzer
Version : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

PS C:\\windows\\system32&gt; Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.1 -Repository PSGallery
PS C:\\windows\\system32&gt; Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase
Name       : PSScriptAnalyzer 
Version    : 1.1.1
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.1
Name       : PSScriptAnalyzer
Version    : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

PS C:\\windows\\system32&gt; Get-InstalledModule -Name PSScriptAnalyzer -AllVersions
Version    Name                                Type       Repository           Description            
-------    ----                                ----       ----------           -----------            
1.1.0      PSScriptAnalyzer                    Module     PSGallery            PSScriptAnalyzer provides script analysis... 
1.1.1      PSScriptAnalyzer                    Module     PSGallery            PSScriptAnalyzer provides script analysis...
```


<!--HONumber=Jun16_HO4-->


