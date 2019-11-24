---
title: 支持在 Cmdlet 参数中使用通配符
ms.custom: ''
ms.date: 08/26/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.openlocfilehash: 19644c5bc186a5554d6b134a67fc7c4d7aa7b64c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365306"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a><span data-ttu-id="bc0dd-102">支持在 Cmdlet 参数中使用通配符</span><span class="sxs-lookup"><span data-stu-id="bc0dd-102">Supporting Wildcard Characters in Cmdlet Parameters</span></span>

<span data-ttu-id="bc0dd-103">通常，你必须将 cmdlet 设计为针对一组资源而不是针对单个资源运行。</span><span class="sxs-lookup"><span data-stu-id="bc0dd-103">Often, you will have to design a cmdlet to run against a group of resources rather than against a single resource.</span></span> <span data-ttu-id="bc0dd-104">例如，cmdlet 可能需要查找数据存储区中具有相同名称或扩展名的所有文件。</span><span class="sxs-lookup"><span data-stu-id="bc0dd-104">For example, a cmdlet might need to locate all the files in a data store that have the same name or extension.</span></span> <span data-ttu-id="bc0dd-105">设计将对一组资源运行的 cmdlet 时，必须提供对通配符字符的支持。</span><span class="sxs-lookup"><span data-stu-id="bc0dd-105">You must provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

> [!NOTE]
> <span data-ttu-id="bc0dd-106">使用通配符*有时称为 "组合"。*</span><span class="sxs-lookup"><span data-stu-id="bc0dd-106">Using wildcard characters is sometimes referred to as *globbing*.</span></span>

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a><span data-ttu-id="bc0dd-107">使用通配符的 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="bc0dd-107">Windows PowerShell Cmdlets That Use Wildcards</span></span>

 <span data-ttu-id="bc0dd-108">许多 Windows PowerShell cmdlet 都支持为其参数值提供通配符。</span><span class="sxs-lookup"><span data-stu-id="bc0dd-108">Many Windows PowerShell cmdlets support wildcard characters for their parameter values.</span></span> <span data-ttu-id="bc0dd-109">例如，几乎每个具有 `Name` 或 `Path` 参数的 cmdlet 都支持这些参数的通配符。</span><span class="sxs-lookup"><span data-stu-id="bc0dd-109">For example, almost every cmdlet that has a `Name` or `Path` parameter supports wildcard characters for these parameters.</span></span> <span data-ttu-id="bc0dd-110">（尽管大多数包含 `Path` 参数的 cmdlet 也具有不支持通配符的 `LiteralPath` 参数。）以下命令显示了如何使用通配符来返回当前会话中其名称包含 Get 谓词的所有 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bc0dd-110">(Although most cmdlets that have a `Path` parameter also have a `LiteralPath` parameter that does not support wildcard characters.) The following command shows how a wildcard character is used to return all the cmdlets in the current session whose name contains the Get verb.</span></span>

 `Get-Command get-*`

## <a name="supported-wildcard-characters"></a><span data-ttu-id="bc0dd-111">支持的通配符</span><span class="sxs-lookup"><span data-stu-id="bc0dd-111">Supported Wildcard Characters</span></span>

<span data-ttu-id="bc0dd-112">Windows PowerShell 支持以下通配符。</span><span class="sxs-lookup"><span data-stu-id="bc0dd-112">Windows PowerShell supports the following wildcard characters.</span></span>

| <span data-ttu-id="bc0dd-113">通配符</span><span class="sxs-lookup"><span data-stu-id="bc0dd-113">Wildcard</span></span> |                             <span data-ttu-id="bc0dd-114">描述</span><span class="sxs-lookup"><span data-stu-id="bc0dd-114">Description</span></span>                             |  <span data-ttu-id="bc0dd-115">示例</span><span class="sxs-lookup"><span data-stu-id="bc0dd-115">Example</span></span>   |     <span data-ttu-id="bc0dd-116">匹配</span><span class="sxs-lookup"><span data-stu-id="bc0dd-116">Matches</span></span>      | <span data-ttu-id="bc0dd-117">不匹配</span><span class="sxs-lookup"><span data-stu-id="bc0dd-117">Does not match</span></span> |
| -------- | ------------------------------------------------------------------- | ---------- | ---------------- | -------------- |
| *        | <span data-ttu-id="bc0dd-118">匹配零个或多个字符（从指定位置开始）</span><span class="sxs-lookup"><span data-stu-id="bc0dd-118">Matches zero or more characters, starting at the specified position</span></span> | `a*`       | <span data-ttu-id="bc0dd-119">A、ag、Apple</span><span class="sxs-lookup"><span data-stu-id="bc0dd-119">A, ag, Apple</span></span>     |                |
| <span data-ttu-id="bc0dd-120">?</span><span class="sxs-lookup"><span data-stu-id="bc0dd-120">?</span></span>        | <span data-ttu-id="bc0dd-121">匹配指定位置的任何字符</span><span class="sxs-lookup"><span data-stu-id="bc0dd-121">Matches any character at the specified position</span></span>                     | `?n`       | <span data-ttu-id="bc0dd-122">，在中，在</span><span class="sxs-lookup"><span data-stu-id="bc0dd-122">An, in, on</span></span>       | <span data-ttu-id="bc0dd-123">为名</span><span class="sxs-lookup"><span data-stu-id="bc0dd-123">ran</span></span>            |
| <span data-ttu-id="bc0dd-124">[ ]</span><span class="sxs-lookup"><span data-stu-id="bc0dd-124">[ ]</span></span>      | <span data-ttu-id="bc0dd-125">匹配一系列字符</span><span class="sxs-lookup"><span data-stu-id="bc0dd-125">Matches a range of characters</span></span>                                       | `[a-l]ook` | <span data-ttu-id="bc0dd-126">书籍，库，查找</span><span class="sxs-lookup"><span data-stu-id="bc0dd-126">book, cook, look</span></span> | <span data-ttu-id="bc0dd-127">nook，拍摄</span><span class="sxs-lookup"><span data-stu-id="bc0dd-127">nook, took</span></span>     |
| <span data-ttu-id="bc0dd-128">[ ]</span><span class="sxs-lookup"><span data-stu-id="bc0dd-128">[ ]</span></span>      | <span data-ttu-id="bc0dd-129">匹配指定字符</span><span class="sxs-lookup"><span data-stu-id="bc0dd-129">Matches the specified characters</span></span>                                    | `[bn]ook`  | <span data-ttu-id="bc0dd-130">书籍，nook</span><span class="sxs-lookup"><span data-stu-id="bc0dd-130">book, nook</span></span>       | <span data-ttu-id="bc0dd-131">库，查找</span><span class="sxs-lookup"><span data-stu-id="bc0dd-131">cook, look</span></span>     |

<span data-ttu-id="bc0dd-132">设计支持通配符的 cmdlet 时，允许组合通配符字符。</span><span class="sxs-lookup"><span data-stu-id="bc0dd-132">When you design cmdlets that support wildcard characters, allow for combinations of wildcard characters.</span></span> <span data-ttu-id="bc0dd-133">例如，以下命令使用 `Get-ChildItem` cmdlet 来检索 c:\Techdocs 文件夹中所有以字母 "a" 到 "l" 开头的 .txt 文件。</span><span class="sxs-lookup"><span data-stu-id="bc0dd-133">For example, the following command uses the `Get-ChildItem` cmdlet to retrieve all the .txt files that are in the c:\Techdocs folder and that begin with the letters "a" through "l."</span></span>

`Get-ChildItem c:\techdocs\[a-l]\*.txt`

<span data-ttu-id="bc0dd-134">前面的命令使用范围通配符 `[a-l]` 来指定文件名应以字符 "a" 到 "l" 开头，并使用 `*` 通配符作为文件名第一个字母与 **.txt**扩展名之间的任何字符的占位符。</span><span class="sxs-lookup"><span data-stu-id="bc0dd-134">The previous command uses the range wildcard `[a-l]` to specify that the file name should begin with the characters "a" through "l" and uses the `*` wildcard character as a placeholder for any characters between the first letter of the filename and the **.txt** extension.</span></span>

<span data-ttu-id="bc0dd-135">下面的示例使用范围通配符模式，该模式不包括字母 "d"，但包含 "a" 到 "f" 的所有其他字母。</span><span class="sxs-lookup"><span data-stu-id="bc0dd-135">The following example uses a range wildcard pattern that excludes the letter "d" but includes all the other letters from "a" through "f."</span></span>

`Get-ChildItem c:\techdocs\[a-cef]\*.txt`

## <a name="handling-literal-characters-in-wildcard-patterns"></a><span data-ttu-id="bc0dd-136">在通配符模式中处理文本字符</span><span class="sxs-lookup"><span data-stu-id="bc0dd-136">Handling Literal Characters in Wildcard Patterns</span></span>

<span data-ttu-id="bc0dd-137">如果指定的通配符模式包含不应解释为通配符的原义字符，请使用反撇号字符（`` ` ``）作为转义符。</span><span class="sxs-lookup"><span data-stu-id="bc0dd-137">If the wildcard pattern you specify contains literal characters that should not be interpretted as wildcard characters, use the backtick character (`` ` ``) as an escape character.</span></span> <span data-ttu-id="bc0dd-138">当你为 PowerShell API 指定整数字符时，请使用单个反撇号。</span><span class="sxs-lookup"><span data-stu-id="bc0dd-138">When you specify literal characters int the PowerShell API, use a single backtick.</span></span> <span data-ttu-id="bc0dd-139">在 PowerShell 命令提示符处指定原义字符时，请使用两个反撇号。</span><span class="sxs-lookup"><span data-stu-id="bc0dd-139">When you specify literal characters at the PowerShell command prompt, use two backticks.</span></span>

<span data-ttu-id="bc0dd-140">例如，下面的模式包含两个必须按原义取的方括号。</span><span class="sxs-lookup"><span data-stu-id="bc0dd-140">For example, the following pattern contains two brackets that must be taken literally.</span></span>

<span data-ttu-id="bc0dd-141">使用 PowerShell API 时，请使用：</span><span class="sxs-lookup"><span data-stu-id="bc0dd-141">When used in the PowerShell API use:</span></span>

- <span data-ttu-id="bc0dd-142">"John Smith \`[\* ']"</span><span class="sxs-lookup"><span data-stu-id="bc0dd-142">"John Smith \`[\*\`]"</span></span>

<span data-ttu-id="bc0dd-143">在 PowerShell 命令提示符下使用时：</span><span class="sxs-lookup"><span data-stu-id="bc0dd-143">When used from the PowerShell command prompt:</span></span>

- <span data-ttu-id="bc0dd-144">"John Smith \`\`[\*\`"] "</span><span class="sxs-lookup"><span data-stu-id="bc0dd-144">"John Smith \`\`[\*\`\`]"</span></span>

<span data-ttu-id="bc0dd-145">此模式匹配 "John Smith [行销]" 或 "John Smith [开发]"。</span><span class="sxs-lookup"><span data-stu-id="bc0dd-145">This pattern matches "John Smith [Marketing]" or "John Smith [Development]".</span></span> <span data-ttu-id="bc0dd-146">例如：</span><span class="sxs-lookup"><span data-stu-id="bc0dd-146">For example:</span></span>

```
PS> "John Smith [Marketing]" -like "John Smith ``[*``]"
True

PS> "John Smith [Development]" -like "John Smith ``[*``]"
True
```

## <a name="cmdlet-output-and-wildcard-characters"></a><span data-ttu-id="bc0dd-147">Cmdlet 输出和通配符</span><span class="sxs-lookup"><span data-stu-id="bc0dd-147">Cmdlet Output and Wildcard Characters</span></span>

<span data-ttu-id="bc0dd-148">当 cmdlet 参数支持通配符时，操作通常会生成一个数组输出。</span><span class="sxs-lookup"><span data-stu-id="bc0dd-148">When cmdlet parameters support wildcard characters, the operation usually generates an array output.</span></span>
<span data-ttu-id="bc0dd-149">有时，因为用户可能只使用一个项，所以不能提供支持数组输出的意义。</span><span class="sxs-lookup"><span data-stu-id="bc0dd-149">Occasionally, it makes no sense to support an array output because the user might use only a single item.</span></span> <span data-ttu-id="bc0dd-150">例如，`Set-Location` cmdlet 不支持数组输出，因为用户仅设置了一个位置。</span><span class="sxs-lookup"><span data-stu-id="bc0dd-150">For example, the `Set-Location` cmdlet does not support array output because the user sets only a single location.</span></span> <span data-ttu-id="bc0dd-151">在这种情况下，该 cmdlet 仍支持通配符，但会强制将分辨率转换为单一位置。</span><span class="sxs-lookup"><span data-stu-id="bc0dd-151">In this instance, the cmdlet still supports wildcard characters, but it forces resolution to a single location.</span></span>

## <a name="see-also"></a><span data-ttu-id="bc0dd-152">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bc0dd-152">See Also</span></span>

[<span data-ttu-id="bc0dd-153">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="bc0dd-153">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="bc0dd-154">WildcardPattern 类</span><span class="sxs-lookup"><span data-stu-id="bc0dd-154">WildcardPattern Class</span></span>](/dotnet/api/system.management.automation.wildcardpattern)
