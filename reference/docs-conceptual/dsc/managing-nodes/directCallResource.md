---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: 直接调用 DSC 资源方法
ms.openlocfilehash: cf237f638593706e5959e2bcc0d851b0e55baf0e
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954384"
---
# <a name="calling-dsc-resource-methods-directly"></a><span data-ttu-id="b9616-103">直接调用 DSC 资源方法</span><span class="sxs-lookup"><span data-stu-id="b9616-103">Calling DSC resource methods directly</span></span>

><span data-ttu-id="b9616-104">适用于：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b9616-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="b9616-105">你可以使用 [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) cmdlet 直接调用 DSC 资源的函数或方法（基于 MOF 资源的 **Get-TargetResource**、**Set-TargetResource** 和 **Test-TargetResource** 函数，或基于类的资源的 **Get**、**Set** 和 **Test** 方法）。</span><span class="sxs-lookup"><span data-stu-id="b9616-105">You can use the [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) cmdlet to directly call the functions or methods of a DSC resource (The **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions of a MOF-based resource, or the **Get**, **Set**, and **Test** methods of a class-based resource).</span></span>
<span data-ttu-id="b9616-106">这可为想要使用 DSC 资源的第三方所用，也可以作为开发资源时非常有用的工具。</span><span class="sxs-lookup"><span data-stu-id="b9616-106">This can be used by third-parties that want to use DSC resources, or as a helpful tool while developing resources.</span></span>

<span data-ttu-id="b9616-107">此 cmdlet 通常与元配置属性 `refreshMode = 'Disabled'` 组合使用，但无论 **refreshMode** 设置为何值，都可以使用它。</span><span class="sxs-lookup"><span data-stu-id="b9616-107">This cmdlet is typically used in combination with a metaconfiguration property `refreshMode = 'Disabled'`, but it can be used no matter what **refreshMode** is set to.</span></span>

<span data-ttu-id="b9616-108">在调用 **Invoke DscResource** cmdlet 时，可以通过使用 **Method** 参数来指定要调用的方法和函数。</span><span class="sxs-lookup"><span data-stu-id="b9616-108">When calling the **Invoke-DscResource** cmdlet, you specify which method or function to call by using the **Method** parameter.</span></span> <span data-ttu-id="b9616-109">你可以将哈希表作为 **Property** 参数的值进行传递，从而指定资源的属性。</span><span class="sxs-lookup"><span data-stu-id="b9616-109">You specify the properties of the resource by passing a hashtable as the value of the **Property** parameter.</span></span>

<span data-ttu-id="b9616-110">直接调用资源方法的示例如下：</span><span class="sxs-lookup"><span data-stu-id="b9616-110">The following are examples of directly calling resource methods:</span></span>

## <a name="ensure-a-file-is-present"></a><span data-ttu-id="b9616-111">确保文件存在</span><span class="sxs-lookup"><span data-stu-id="b9616-111">Ensure a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
                            DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
                            Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="test-that-a-file-is-present"></a><span data-ttu-id="b9616-112">测试文件存在</span><span class="sxs-lookup"><span data-stu-id="b9616-112">Test that a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="get-the-contents-of-file"></a><span data-ttu-id="b9616-113">获取文件内容</span><span class="sxs-lookup"><span data-stu-id="b9616-113">Get the contents of file</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

><span data-ttu-id="b9616-114">**注意：** 不支持直接调用复合资源方法。</span><span class="sxs-lookup"><span data-stu-id="b9616-114">**Note:** Directly calling composite resource methods is not supported.</span></span> <span data-ttu-id="b9616-115">请改为调用构成复合资源的基础资源的方法。</span><span class="sxs-lookup"><span data-stu-id="b9616-115">Instead, call the methods of the underlying resources that make up the composite resource.</span></span>

## <a name="see-also"></a><span data-ttu-id="b9616-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b9616-116">See Also</span></span>
- [<span data-ttu-id="b9616-117">使用 MOF 编写自定义 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="b9616-117">Writing a custom DSC resource with MOF</span></span>](../resources/authoringResourceMOF.md)
- [<span data-ttu-id="b9616-118">使用 PowerShell 类编写自定义 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="b9616-118">Writing a custom DSC resource with PowerShell classes</span></span>](../resources/authoringResourceClass.md)
- [<span data-ttu-id="b9616-119">调试 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="b9616-119">Debugging DSC resources</span></span>](../troubleshooting/debugResource.md)