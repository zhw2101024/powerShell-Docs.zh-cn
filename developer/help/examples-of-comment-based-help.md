---
title: 基于注释的帮助的示例 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 868194a2-17e9-4184-bc36-c04a33f26494
caps.latest.revision: 4
ms.openlocfilehash: dbccaf5b8e48a1c4d924bc0ec4ea09b25e10adf0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857963"
---
# <a name="examples-of-comment-based-help"></a><span data-ttu-id="2afa4-102">基于注释的帮助的示例</span><span class="sxs-lookup"><span data-stu-id="2afa4-102">Examples of Comment-Based Help</span></span>

<span data-ttu-id="2afa4-103">本主题包括示例，演示如何使用脚本和函数基于注释的帮助。</span><span class="sxs-lookup"><span data-stu-id="2afa4-103">This topic includes example that demonstrate how to use comment-based help for scripts and functions.</span></span>

## <a name="example-1-comment-based-help-for-a-function"></a><span data-ttu-id="2afa4-104">示例 1：有关某个函数基于注释的帮助</span><span class="sxs-lookup"><span data-stu-id="2afa4-104">Example 1: Comment-Based Help for a Function</span></span>

 <span data-ttu-id="2afa4-105">以下示例函数包含基于注释的帮助。</span><span class="sxs-lookup"><span data-stu-id="2afa4-105">The following sample function includes comment-based Help.</span></span>

```powershell
function Add-Extension
{
    param ([string]$Name,[string]$Extension = "txt")
    $name = $name + "." + $extension
    $name

    <#
        .SYNOPSIS
        Adds a file name extension to a supplied name.

        .DESCRIPTION
        Adds a file name extension to a supplied name.
        Takes any strings for the file name or extension.

        .PARAMETER Name
        Specifies the file name.

        .PARAMETER Extension
        Specifies the extension. "Txt" is the default.

        .INPUTS
        None. You cannot pipe objects to Add-Extension.

        .OUTPUTS
        System.String. Add-Extension returns a string with the extension or file name.

        .EXAMPLE
        C:\PS> extension -name "File"
        File.txt

        .EXAMPLE
        C:\PS> extension -name "File" -extension "doc"
        File.doc

        .EXAMPLE
        C:\PS> extension "File" "doc"
        File.doc

        .LINK
        Online version: http://www.fabrikam.com/extension.html

        .LINK
        Set-Item
    #>
}
```

<span data-ttu-id="2afa4-106">以下输出显示了用于显示有关添加扩展函数的帮助的 Get-help 命令的结果。</span><span class="sxs-lookup"><span data-stu-id="2afa4-106">The following output shows the results of a Get-Help command that displays the help for the Add-Extension function.</span></span>

```powershell
C:\PS> get-help add-extension -full
```

```output
        NAME
            Add-Extension

        SYNOPSIS
            Adds a file name extension to a supplied name.

        SYNTAX
            Add-Extension [[-Name] <String>] [[-Extension] <String>] [<CommonParameters>]

        DESCRIPTION
            Adds a file name extension to a supplied name. Takes any strings for the file name or extension.

        PARAMETERS
           -Name
               Specifies the file name.

               Required?                    false
               Position?                    0
               Default value
               Accept pipeline input?       false
               Accept wildcard characters?

           -Extension
               Specifies the extension. "Txt" is the default.

               Required?                    false
               Position?                    1
               Default value
               Accept pipeline input?       false
               Accept wildcard characters?

            <CommonParameters>
               This cmdlet supports the common parameters: -Verbose, -Debug,
               -ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
               -OutBuffer and -OutVariable. For more information, type
               "get-help about_commonparameters".

        INPUTS
            None. You cannot pipe objects to Add-Extension.

        OUTPUTS
            System.String. Add-Extension returns a string with the extension or file name.

            -------------------------- EXAMPLE 1 --------------------------

            C:\PS> extension -name "File"
            File.txt

            -------------------------- EXAMPLE 2 --------------------------

            C:\PS> extension -name "File" -extension "doc"
            File.doc

            -------------------------- EXAMPLE 3 --------------------------

            C:\PS> extension "File" "doc"
            File.doc

        RELATED LINKS
            Online version: http://www.fabrikam.com/extension.html
            Set-Item
```

## <a name="example-2-comment-based-help-for-a-script"></a><span data-ttu-id="2afa4-107">示例 2：基于注释的帮助的脚本</span><span class="sxs-lookup"><span data-stu-id="2afa4-107">Example 2: Comment-Based Help for a Script</span></span>

<span data-ttu-id="2afa4-108">以下示例函数包含基于注释的帮助。</span><span class="sxs-lookup"><span data-stu-id="2afa4-108">The following sample function includes comment-based Help.</span></span>

<span data-ttu-id="2afa4-109">请注意，结束之间的空行**#>** 和`Param`语句。</span><span class="sxs-lookup"><span data-stu-id="2afa4-109">Notice the blank lines between the closing **#>** and the `Param` statement.</span></span> <span data-ttu-id="2afa4-110">在脚本中不具有`Param`语句，帮助主题中的最后一个注释和第一个函数声明之间必须有至少两个空白行。</span><span class="sxs-lookup"><span data-stu-id="2afa4-110">In a script that does not have a `Param` statement, there must be at least two blank lines between the final comment in the Help topic and the first function declaration.</span></span> <span data-ttu-id="2afa4-111">而无需这些空行，获取帮助将与函数，而不是脚本关联的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="2afa4-111">Without these blank lines, Get-Help associates the Help topic with the function, instead of the script.</span></span>

```powershell
<#
  .SYNOPSIS
  Performs monthly data updates.

  .DESCRIPTION
  The Update-Month.ps1 script updates the registry with new data generated
  during the past month and generates a report.

  .PARAMETER InputPath
  Specifies the path to the CSV-based input file.

  .PARAMETER OutputPath
  Specifies the name and path for the CSV-based output file. By default,
  MonthlyUpdates.ps1 generates a name from the date and time it runs, and
  saves the output in the local directory.

  .INPUTS
  None. You cannot pipe objects to Update-Month.ps1.

  .OUTPUTS
  None. Update-Month.ps1 does not generate any output.

  .EXAMPLE
  C:\PS> .\Update-Month.ps1

  .EXAMPLE
  C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

  .EXAMPLE
  C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath C:\Reports\2009\January.csv
#>

param ([string]$InputPath, [string]$OutPutPath)

function Get-Data { }
```

<span data-ttu-id="2afa4-112">以下命令将获取脚本的帮助。</span><span class="sxs-lookup"><span data-stu-id="2afa4-112">The following command gets the script Help.</span></span> <span data-ttu-id="2afa4-113">由于该脚本不是 n Path 环境变量获取脚本的帮助的 Get-help 命令中列出的目录必须指定脚本路径。</span><span class="sxs-lookup"><span data-stu-id="2afa4-113">Because the script is not n a directory that is listed in the Path environment variable, the Get-Help command that gets the script Help must specify the script path.</span></span>

```powershell
C:\PS> get-help c:\ps-test\update-month.ps1 -full
```

```output
            NAME
                C:\ps-test\Update-Month.ps1

            SYNOPSIS
                Performs monthly data updates.

            SYNTAX
                C:\ps-test\Update-Month.ps1 [-InputPath] <String> [[-OutputPath]
                <String>] [<CommonParameters>]

            DESCRIPTION
                The Update-Month.ps1 script updates the registry with new data
                generated during the past month and generates a report.

            PARAMETERS
               -InputPath
                   Specifies the path to the CSV-based input file.

                   Required?                    true
                   Position?                    0
                   Default value
                   Accept pipeline input?       false
                   Accept wildcard characters?

               -OutputPath
                   Specifies the name and path for the CSV-based output file. By
                   default, MonthlyUpdates.ps1 generates a name from the date
                   and time it runs, and saves the output in the local directory.

                   Required?                    false
                   Position?                    1
                   Default value
                   Accept pipeline input?       false
                   Accept wildcard characters?

               <CommonParameters>
                   This cmdlet supports the common parameters: -Verbose, -Debug,
                   -ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
                   -OutBuffer and -OutVariable. For more information, type,
                   "get-help about_commonparameters".

            INPUTS
                   None. You cannot pipe objects to Update-Month.ps1.

            OUTPUTS
                   None. Update-Month.ps1 does not generate any output.

            -------------------------- EXAMPLE 1 --------------------------

            C:\PS> .\Update-Month.ps1

            -------------------------- EXAMPLE 2 --------------------------

            C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

            -------------------------- EXAMPLE 3 --------------------------

            C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath
            C:\Reports\2009\January.csv

            RELATED LINKS
```

## <a name="example-3-parameter-descriptions-in-a-param-statement"></a><span data-ttu-id="2afa4-114">示例 3：Param 语句中的参数说明</span><span class="sxs-lookup"><span data-stu-id="2afa4-114">Example 3: Parameter Descriptions in a Param Statement</span></span>

<span data-ttu-id="2afa4-115">此示例演示如何插入中的 parameterdescriptions`Param`函数或脚本的语句。</span><span class="sxs-lookup"><span data-stu-id="2afa4-115">This example show how to insert parameterdescriptions in the `Param` statement of a function or script.</span></span> <span data-ttu-id="2afa4-116">简要参数说明时，此格式是最有用。</span><span class="sxs-lookup"><span data-stu-id="2afa4-116">This format is most useful when the parameter descriptions are brief.</span></span>

```powershell
function Add-Extension
{
    param
    (
        [string]
        # Specifies the file name.
        $name,

        [string]
        # Specifies the file name extension. "Txt" is the default.
        $extension = "txt"
    )
    $name = $name + "." + $extension
    $name

    <#
        .SYNOPSIS
        Adds a file name extension to a supplied name.
...
    #>
```

<span data-ttu-id="2afa4-117">结果是相同的结果如 1。</span><span class="sxs-lookup"><span data-stu-id="2afa4-117">The results are the same as the results for Example 1.</span></span> <span data-ttu-id="2afa4-118">获取帮助解释参数说明，就好像它们伴随着`.Parameter`关键字。</span><span class="sxs-lookup"><span data-stu-id="2afa4-118">Get-Help interprets the parameter descriptions as though they were accompanied by the `.Parameter` keyword.</span></span>

## <a name="example-4--redirecting-to-an-xml-file"></a><span data-ttu-id="2afa4-119">示例 4:将重定向到一个 XML 文件</span><span class="sxs-lookup"><span data-stu-id="2afa4-119">Example 4:  Redirecting to an XML File</span></span>

<span data-ttu-id="2afa4-120">您可以编写基于 XML 的函数和脚本的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="2afa4-120">You can write XML-based Help topics for functions and scripts.</span></span> <span data-ttu-id="2afa4-121">尽管基于注释的帮助更轻松地实现，但，如果想要更精确地控制帮助内容，或如果您要翻译为多种语言的帮助主题，则需要基于 XML 的帮助。下面的示例演示更新 Month.ps1 脚本的前几行。</span><span class="sxs-lookup"><span data-stu-id="2afa4-121">Although comment-based Help is easier to implement, XML-based Help is required if you want more precise control over Help content or if you are translating Help topics into multiple languages.The following example shows the first few lines of the Update-Month.ps1 script.</span></span> <span data-ttu-id="2afa4-122">该脚本使用`.ExternalHelp`关键字来指定有关该脚本基于 XML 的帮助主题的路径。</span><span class="sxs-lookup"><span data-stu-id="2afa4-122">The script uses the `.ExternalHelp` keyword to specify the path to an XML-based Help topic for the script.</span></span>

```powershell
#  .ExternalHelp C:\MyScripts\Update-Month-Help.xml

    param ([string]$InputPath, [string]$OutPutPath)

    function Get-Data { }
```

<span data-ttu-id="2afa4-123">下面的示例演示如何使用`.ExternalHelp`在函数中的关键字。</span><span class="sxs-lookup"><span data-stu-id="2afa4-123">The following example shows the use of the `.ExternalHelp` keyword in a function.</span></span>

```powershell
function Add-Extension
{
    param ([string] $name, [string]$extension = "txt")
    $name = $name + "." + $extension
    $name

    # .ExternalHelp C:\ps-test\Add-Extension.xml
}
```

## <a name="example-5--redirecting-to-a-different-help-topic"></a><span data-ttu-id="2afa4-124">示例 5：将重定向到不同的帮助主题</span><span class="sxs-lookup"><span data-stu-id="2afa4-124">Example 5:  Redirecting to a Different Help Topic</span></span>

<span data-ttu-id="2afa4-125">下面的代码是一段摘录的内置开头`Help`在 Windows PowerShell 中，一次显示一个屏幕的帮助文本的函数。</span><span class="sxs-lookup"><span data-stu-id="2afa4-125">The following code is an excerpt from the beginning of the built-in `Help` function in Windows PowerShell, which displays one screen of Help text at a time.</span></span> <span data-ttu-id="2afa4-126">Get-help cmdlet 的帮助主题介绍了帮助函数，因为该帮助函数使用`.ForwardHelpTargetName`和`.ForwardHelpCategory`关键字来将用户重定向到 Get-help cmdlet 帮助主题。</span><span class="sxs-lookup"><span data-stu-id="2afa4-126">Because the Help topic for the Get-Help cmdlet describes the Help function, the Help function uses the `.ForwardHelpTargetName` and `.ForwardHelpCategory` keywords to redirect the user to the Get-Help cmdlet Help topic.</span></span>

```powershell
function help
{

    <#
      .FORWARDHELPTARGETNAME Get-Help
      .FORWARDHELPCATEGORY Cmdlet
    #>
    [CmdletBinding(DefaultParameterSetName='AllUsersView')]
    param(
            [Parameter(Position=0, ValueFromPipelineByPropertyName=$true)]
            [System.String]
            ${Name},
    ...
```

<span data-ttu-id="2afa4-127">以下命令使用此功能。</span><span class="sxs-lookup"><span data-stu-id="2afa4-127">The following command uses this feature.</span></span> <span data-ttu-id="2afa4-128">当用户键入帮助函数的 Get-help 命令时，获取帮助显示 Get-help cmdlet 的帮助主题。</span><span class="sxs-lookup"><span data-stu-id="2afa4-128">When a user types a Get-Help command for the Help function, Get-Help displays the Help topic for the Get-Help cmdlet.</span></span>

```powershell
C:\PS> get-help help
```

```output
            NAME
                Get-Help

            SYNOPSIS
                Displays information about Windows PowerShell cmdlets and concepts.
            ...
```