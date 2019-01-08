---
ms.date: 08/24/2018
keywords: dsc,powershell,配置,安装程序
title: DSC Script 资源
ms.openlocfilehash: ef84239820a44aab2a028f7f0fe17653a851b72e
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047191"
---
# <a name="dsc-script-resource"></a>DSC Script 资源

> 适用于：Windows PowerShell 4.0 中，Windows PowerShell 5.x

Windows PowerShell Desired State Configuration (DSC) 中的 **Script** 资源提供了在目标节点上运行 Windows PowerShell 脚本的机制。 脚本资源使用 `GetScript``SetScript` 和 `TestScript` 属性，这些属性包含定义以执行相应的 DSC 状态操作的脚本块。

## <a name="syntax"></a>语法

```
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> 将 `GetScript`、`TestScript` 和 `SetScript` 块存储为字符串。

## <a name="properties"></a>“属性”

|属性|说明|
|--------|-----------|
|GetScript|一个返回节点当前状态的脚本块。|
|SetScript|DSC 在节点未处于所需状态时用于强制执行符合性的脚本块。|
|TestScript|一个用于确定节点是否处于所需状态的脚本块。|
|凭据| 指示要用于运行此脚本的凭据（如果需要凭据）。|
|DependsOn| 指示必须先运行其他资源的配置，再配置此资源。 例如，如果你想要首先运行 ID 为 **ResourceName**、类型为 **ResourceType** 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。

### <a name="getscript"></a>GetScript

DSC 不使用来自 `GetScript` 的输出。 [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet 执行 `GetScript` 以检索节点的当前状态。 `GetScript` 不需要返回值。 如果指定返回值，则它必须是包含值为 `String` 的 Result 键的 `hashtable`。

### <a name="testscript"></a>TestScript

DSC 执行 `TestScript` 以确定是否应运行 `SetScript`。 如果 `TestScript` 返回 `$false`，则 DSC 执行 `SetScript` 以使节点恢复到所需状态。 它必须返回一个 `boolean` 值。 `$true` 的结果表示节点是符合的，不应执行 `SetScript`。

[Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) cmdlet 执行 `TestScript` 以检索节点是否符合脚本资源。 但是，在这种情况下，无论 `TestScript` 块返回什么，`SetScript` 都不会运行。

> [!NOTE]
> `TestScript` 的所有输出都是其返回值的一部分。 PowerShell 将未压缩的输出视为非零，这意味着无论节点的状态如何，`TestScript` 都将返回 `$true`。
> 这会导致不可预测的结果和误报，并导致在故障排除时出现问题。

### <a name="setscript"></a>SetScript

`SetScript` 修改节点以强制执行所需的状态。 如果 `TestScript` 脚本块返回 `$false`，则其由 DSC 调用。 `SetScript` 应该没有返回值。

## <a name="examples"></a>示例

### <a name="example-1-write-sample-text-using-a-script-resource"></a>示例 1：编写使用脚本资源的示例文本

此示例测试每个节点上是否存在 `C:\TempFolder\TestFile.txt`。 如果它不存在，则使用 `SetScript` 创建它。 `GetScript` 返回文件的内容，并且不使用其返回值。

```powershell
Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script ScriptExample
        {
            SetScript = {
                $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
                $sw.WriteLine("Some sample string")
                $sw.Close()
            }
            TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
            GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }
        }
    }
}
```

### <a name="example-2-compare-version-information-using-a-script-resource"></a>示例 2：使用脚本资源的版本信息进行比较

此示例从创作计算机上的文本文件中检索符合的版本信息，并将其存储在 `$version` 变量中。 在生成节点的 MOF 文件时，DSC 将每个脚本块中的 `$using:version` 变量替换为 `$version` 变量的值。 在执行期间，符合的版本存储在每个节点上的文本文件中，并在后续执行时进行比较和更新。

```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script UpdateConfigurationVersion
        {
            GetScript = {
                $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
                return @{ 'Result' = "$currentVersion" }
            }
            TestScript = {
                # Create and invoke a scriptblock using the $GetScript automatic variable, which contains a string representation of the GetScript.
                $state = [scriptblock]::Create($GetScript).Invoke()

                if( $state['Result'] -eq $using:version )
                {
                    Write-Verbose -Message ('{0} -eq {1}' -f $state['Result'],$using:version)
                    return $true
                }
                Write-Verbose -Message ('Version up-to-date: {0}' -f $using:version)
                return $false
            }
            SetScript = {
                $using:version | Set-Content -Path (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
            }
        }
    }
}
```