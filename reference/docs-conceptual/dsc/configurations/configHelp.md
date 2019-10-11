---
ms.date: 12/12/2018
keywords: dsc,powershell,配置,安装程序
title: 编写 DSC 配置的帮助
ms.openlocfilehash: 498ec0f594ed3229e097903c4ea2ae34d3da03a2
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954134"
---
# <a name="writing-help-for-dsc-configurations"></a><span data-ttu-id="7f977-103">编写 DSC 配置的帮助</span><span class="sxs-lookup"><span data-stu-id="7f977-103">Writing help for DSC configurations</span></span>

><span data-ttu-id="7f977-104">适用于：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="7f977-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="7f977-105">可在 DSC 配置中使用基于注释的帮助。</span><span class="sxs-lookup"><span data-stu-id="7f977-105">You can use comment-based help in DSC configurations.</span></span> <span data-ttu-id="7f977-106">若要访问帮助内容，用户可以使用 `-?` 调用配置  或使用 [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7f977-106">Users can access the help by calling the **Configuration** with `-?`, or by using the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet.</span></span> <span data-ttu-id="7f977-107">将基于注释的帮助直接置于 `Configuration` 关键字上方。</span><span class="sxs-lookup"><span data-stu-id="7f977-107">Place your Comment-based help directly above the `Configuration` keyword.</span></span>
<span data-ttu-id="7f977-108">可以将参数帮助置于注释块的同一行中，或直接放置在参数声明上方，或同时放置在两个位置，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="7f977-108">You can place parameter help in-line with your comment block, directly above the parameter declaration, or both as in the example below.</span></span>

<span data-ttu-id="7f977-109">若要详细了解基于 PowerShell 注释的帮助内容，请参阅 [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)。</span><span class="sxs-lookup"><span data-stu-id="7f977-109">For more information about PowerShell comment-based help, see [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span></span>

> [!NOTE]
> <span data-ttu-id="7f977-110">PowerShell 开发环境（如 VSCode 和 ISE）也具有可用于自动插入注释块模板的代码片段。</span><span class="sxs-lookup"><span data-stu-id="7f977-110">PowerShell development environments, like VSCode and the ISE, also have snippets to allow you to automatically insert comment block templates.</span></span>

<span data-ttu-id="7f977-111">下面的示例演示了一个脚本，它包含一个配置以及有关该配置的基于注释的帮助。</span><span class="sxs-lookup"><span data-stu-id="7f977-111">The following example shows a script that contains a configuration and comment-based help for it.</span></span> <span data-ttu-id="7f977-112">此示例显示带有参数的配置。</span><span class="sxs-lookup"><span data-stu-id="7f977-112">This example shows a Configuration with parameters.</span></span> <span data-ttu-id="7f977-113">若要了解有关在配置中使用参数的详细信息，请参阅[将参数添加到配置中](add-parameters-to-a-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="7f977-113">To learn more about using parameters in your Configurations, see [Add Parameters to your Configurations](add-parameters-to-a-configuration.md).</span></span>

```powershell
<#
.SYNOPSIS
A brief description of the function or script. This keyword can be used only once for each configuration.


.DESCRIPTION
A detailed description of the function or script. This keyword can be used only once for each configuration.


.PARAMETER ComputerName
The description of a parameter. Add a .PARAMETER keyword for each parameter in the function or script syntax.

Type the parameter name on the same line as the .PARAMETER keyword. Type the parameter description on the lines following the .PARAMETER keyword.
Windows PowerShell interprets all text between the .PARAMETER line and the next keyword or the end of the comment block as part of the parameter description.
The description can include paragraph breaks.

The Parameter keywords can appear in any order in the comment block, but the function or script syntax determines the order in which the parameters
(and their descriptions) appear in help topic. To change the order, change the syntax.

.EXAMPLE
HelpSample -ComputerName localhost

A sample command that uses the function or script, optionally followed by sample output and a description. Repeat this keyword for each example.
PowerShell automatically prefaces the first line with a PowerShell prompt. Additional lines are treated as output and description. The example can contain spaces, newlines and PowerShell code.

If you have multiple examples, there is no need to number them. PowerShell will number the examples in help text.
.EXAMPLE
HelpSample -FilePath "C:\output.txt"

This example will be labeled "EXAMPLE 2" when help is displayed to the user.
#>
configuration HelpSample1
{
    param
    (
        [string]$ComputerName = 'localhost',
        # Provide a PARAMETER section for each parameter that your script or function accepts.
        [string]$FilePath = 'C:\Destination.txt'
    )

    Node $ComputerName
    {
        File HelloWorld
        {
            Contents="Hello World"
            DestinationPath = $FilePath
        }
    }
}
```

## <a name="viewing-configuration-help"></a><span data-ttu-id="7f977-114">查看配置帮助</span><span class="sxs-lookup"><span data-stu-id="7f977-114">Viewing configuration help</span></span>

<span data-ttu-id="7f977-115">若要查看有关配置的帮助，请使用带有函数名称的 `Get-Help` cmdlet，或键入后跟 `-?` 的函数名称。</span><span class="sxs-lookup"><span data-stu-id="7f977-115">To view the help for a configuration, use the `Get-Help` cmdlet with the name of the function, or type the name of the function followed by `-?`.</span></span> <span data-ttu-id="7f977-116">下面展示了在传递给 `Get-Help` 的上一个配置的输出。</span><span class="sxs-lookup"><span data-stu-id="7f977-116">The following is the output of the previous Configuration passed to `Get-Help`.</span></span>

```powershell
Get-Help HelpSample1 -Detailed
```

```output
NAME
    HelpSample1

SYNOPSIS
    A brief description of the function or script. This keyword can be used only once for each configuration.


SYNTAX
    HelpSample1 [[-InstanceName] <String>] [[-DependsOn] <String[]>] [[-PsDscRunAsCredential] <PSCredential>] [[-OutputPath] <String>] [[-ConfigurationData] <Hashtable>] [[-ComputerName] <String>] [[-FilePath] <String>] [<CommonParameters>]


DESCRIPTION
    A detailed description of the function or script. This keyword can be used only once for each configuration.


PARAMETERS
    -InstanceName <String>

    -DependsOn <String[]>

    -PsDscRunAsCredential <PSCredential>

    -OutputPath <String>

    -ConfigurationData <Hashtable>

    -ComputerName <String>
        The description of a parameter. Add a .PARAMETER keyword for each parameter in the function or script syntax.

        Type the parameter name on the same line as the .PARAMETER keyword. Type the parameter description on the lines following the .PARAMETER keyword.
        Windows PowerShell interprets all text between the .PARAMETER line and the next keyword or the end of the comment block as part of the parameter description.
        The description can include paragraph breaks.

        The Parameter keywords can appear in any order in the comment block, but the function or script syntax determines the order in which the parameters
        (and their descriptions) appear in help topic. To change the order, change the syntax.

    -FilePath <String>
        Provide a PARAMETER section for each parameter that your script or function accepts.

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, PipelineVariable, and OutVariable. For more information, see
        about_CommonParameters (https:/go.microsoft.com/fwlink/?LinkID=113216).

    -------------------------- EXAMPLE 1 --------------------------

    PS C:\>HelpSample -ComputerName localhost

    A sample command that uses the function or script, optionally followed by sample output and a description. Repeat this keyword for each example.
    PowerShell automatically prefaces the first line with a PowerShell prompt. Additional lines are treated as output and description. The example can contain spaces, newlines and PowerShell code.

    If you have multiple examples, there is no need to number them. PowerShell will number the examples in help text.




    -------------------------- EXAMPLE 2 --------------------------

    PS C:\>HelpSample -FilePath "C:\output.txt"

    This example will be labeled "EXAMPLE 2" when help is displayed to the user.




REMARKS
    To see the examples, type: "get-help HelpSample1 -examples".
    For more information, type: "get-help HelpSample1 -detailed".
    For technical information, type: "get-help HelpSample1 -full".
```

> [!NOTE]
> <span data-ttu-id="7f977-117">PowerShell 会自动为你生成语法字段和参数属性。</span><span class="sxs-lookup"><span data-stu-id="7f977-117">Syntax fields and parameter attributes are automatically generated for you by PowerShell.</span></span>

## <a name="see-also"></a><span data-ttu-id="7f977-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7f977-118">See Also</span></span>

- [<span data-ttu-id="7f977-119">DSC 配置</span><span class="sxs-lookup"><span data-stu-id="7f977-119">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="7f977-120">编写、编译和应用配置</span><span class="sxs-lookup"><span data-stu-id="7f977-120">Write, Compile, and Apply a Configuration</span></span>](write-compile-apply-configuration.md)
- [<span data-ttu-id="7f977-121">向配置添加参数</span><span class="sxs-lookup"><span data-stu-id="7f977-121">Add Parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
