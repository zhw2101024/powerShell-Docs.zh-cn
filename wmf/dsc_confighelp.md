# DSC 配置的帮助支持

现在，当你使用 `-?` 调用配置函数时，可以使用 DSC 配置内部基于注释的帮助，获取关于该配置使用情况的帮助：  

首先，我们定义名为 HelpSample1 和 HelpSample2 的两个配置函数，每个函数基于注释的帮助也包含在内：

```powershell
<#
.SYNOPSIS
The synopsis for the configuration goes here. This can be one line, or many.

.DESCRIPTION
The description for the configuration is usually a longer, more detailed explanation of what the script or function does. Use as many lines as you need.

.PARAMETER computername
Here, the dotted keyword is followed by a single parameter name. Don't precede that with a hyphen. The following lines describe the purpose of the parameter:

.PARAMETER filePath
Provide a PARAMETER section for each parameter that your script or function accepts.

.EXAMPLE
There's no need to number your examples.

.EXAMPLE
Windows PowerShell will number them for you when it displays your help text to a user.
#>

configuration HelpSample1
{
    param([string]$computername,[string]$filePath)
    File f
    {
        Contents="Hello World"
        DestinationPath = "c:\Destination.txt"
    }
}

<#
.SYNOPSIS
The synopsis for the configuration HelpSample2 goes here. This can be one line, or many.

.DESCRIPTION
The description for the configuration bar is usually a longer, more detailed explanation of what the script or function does. Take as many lines as you need.

.PARAMETER computername
Here, the dotted keyword is followed by a single parameter name. Don't precede that with a hyphen. The following lines describe the purpose of the parameter:

.PARAMETER filePath
Provide a PARAMETER section for each parameter that your script or function accepts.

.EXAMPLE
There's no need to number your examples.

.EXAMPLE
Windows PowerShell will number them for you when it displays your help text to a user.

#>

configuration HelpSample2
{
    param([string]$computername,[string]$filePath)

    File f
    {
        Contents="Hello World"
        DestinationPath = "c:\Destination.txt"
    }
}
```

若要获取 HelpSample1 的帮助，只需运行：

```powershell
HelpSample1 -?
```

```
NAME
HelpSample1

SYNOPSIS
The synopsis for the configuration goes here. This can be one line, or many.

SYNTAX
HelpSample1 [[-InstanceName] <String>] [[-DependsOn] <String[]>] [[-OutputPath] <String>] [[-ConfigurationData] <Hashtable>] [[-computername] <String>] [[-filePath] <String>] [<CommonParameters>]

DESCRIPTION
The description for the configuration is usually a longer, more detailed explanation of what the script or function does. Take as many lines as you need.

RELATED LINKS

REMARKS

To see the examples, type: "get-help HelpSample1 -examples".
For more information, type: "get-help HelpSample1 -detailed".
For technical information, type: "get-help HelpSample1 -full".
```

你还可以使用 Get-Help 获取详细帮助：

```powershell
get-help HelpSample2 -detailed
```

```
NAME
HelpSample2

SYNOPSIS
The synopsis for the configuration HelpSample2 goes here. This can be one line, or many.

SYNTAX
HelpSample2 [[-InstanceName] <String>] [[-DependsOn] <String[]>] [[-OutputPath] <String>] [[-ConfigurationData] <Hashtable>] [[-computername] <String>] [[-filePath] <String>] [<CommonParameters>]

DESCRIPTION
The description for the configuration bar is usually a longer, more detailed explanation of what the script or function does. Take as many lines as you need.

PARAMETERS
-InstanceName <String>
-DependsOn <String[]>
-OutputPath <String>
-ConfigurationData <Hashtable>
-computername <String>

Here, the dotted keyword is followed by a single parameter name. Don't precede that with a hyphen. The following lines describe the purpose of the parameter:

-filePath <String>

Provide a PARAMETER section for each parameter that your script or function accepts.

<CommonParameters>

This cmdlet supports the common parameters: Verbose, Debug,
ErrorAction, ErrorVariable, WarningAction, WarningVariable,
OutBuffer, PipelineVariable, and OutVariable. For more information, see
about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

-------------------------- EXAMPLE 1 --------------------------

PS C:\>There's no need to number your examples.

-------------------------- EXAMPLE 2 --------------------------

PS C:\>Windows PowerShell will number them for you when it displays your help text to a user.

REMARKS
To see the examples, type: "get-help HelpSample2 -examples".
For more information, type: "get-help HelpSample2 -detailed".
For technical information, type: "get-help HelpSample2 -full".
```<!--HONumber=Mar16_HO2-->
