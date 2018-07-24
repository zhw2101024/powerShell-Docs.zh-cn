---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: DSC ProcessSet 资源
ms.openlocfilehash: d18d2c96239abd83cea735e0fbce198d0456cea6
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093984"
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="984a2-103">DSC WindowsProcess 资源</span><span class="sxs-lookup"><span data-stu-id="984a2-103">DSC WindowsProcess Resource</span></span>

> <span data-ttu-id="984a2-104">适用于：Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="984a2-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="984a2-105">Windows PowerShell Desired State Configuration (DSC) 中的 **ProcessSet** 资源提供了用于在目标节点上配置进程的机制。</span><span class="sxs-lookup"><span data-stu-id="984a2-105">The **ProcessSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span> <span data-ttu-id="984a2-106">此资源是[复合资源](authoringResourceComposite.md)，它会针对 `GroupName` 参数中指定的每个组调用 [WindowsProcess 资源](windowsProcessResource.md)。</span><span class="sxs-lookup"><span data-stu-id="984a2-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [WindowsProcess resource](windowsProcessResource.md) for each group specified in the `GroupName` parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="984a2-107">语法</span><span class="sxs-lookup"><span data-stu-id="984a2-107">Syntax</span></span>

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="984a2-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="984a2-108">Properties</span></span>

|  <span data-ttu-id="984a2-109">属性</span><span class="sxs-lookup"><span data-stu-id="984a2-109">Property</span></span>  |  <span data-ttu-id="984a2-110">说明</span><span class="sxs-lookup"><span data-stu-id="984a2-110">Description</span></span>   |
|---|---|
| <span data-ttu-id="984a2-111">参数</span><span class="sxs-lookup"><span data-stu-id="984a2-111">Arguments</span></span>| <span data-ttu-id="984a2-112">包含要原样传递到进程的参数的字符串。</span><span class="sxs-lookup"><span data-stu-id="984a2-112">A string that contains arguments to pass to the process as-is.</span></span> <span data-ttu-id="984a2-113">如果需要传递多个参数，请将它们全部放在此字符串中。</span><span class="sxs-lookup"><span data-stu-id="984a2-113">If you need to pass several arguments, put them all in this string.</span></span>|
| <span data-ttu-id="984a2-114">路径</span><span class="sxs-lookup"><span data-stu-id="984a2-114">Path</span></span>| <span data-ttu-id="984a2-115">进程可执行文件的路径。</span><span class="sxs-lookup"><span data-stu-id="984a2-115">The paths to the process executables.</span></span> <span data-ttu-id="984a2-116">如果这些是可执行文件的名称（不是完全限定的路径），则 DSC 资源会搜索环境**路径**变量 (`$env:Path`) 以查找文件。</span><span class="sxs-lookup"><span data-stu-id="984a2-116">If these are the names of the executable files (not fully qualified paths), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the files.</span></span> <span data-ttu-id="984a2-117">如果此属性的值是完全限定的路径，则 DSC 不使用**路径**环境变量查找文件，并且会在不存在任何路径时引发错误。</span><span class="sxs-lookup"><span data-stu-id="984a2-117">If the values of this property are fully qualified paths, DSC will not use the **Path** environment variable to find the files, and will throw an error if any of the paths do not exist.</span></span> <span data-ttu-id="984a2-118">不允许使用相对路径。</span><span class="sxs-lookup"><span data-stu-id="984a2-118">Relative paths are not allowed.</span></span>|
| <span data-ttu-id="984a2-119">凭据</span><span class="sxs-lookup"><span data-stu-id="984a2-119">Credential</span></span>| <span data-ttu-id="984a2-120">指示启动进程的凭据。</span><span class="sxs-lookup"><span data-stu-id="984a2-120">Indicates the credentials for starting the process.</span></span>|
| <span data-ttu-id="984a2-121">Ensure</span><span class="sxs-lookup"><span data-stu-id="984a2-121">Ensure</span></span>| <span data-ttu-id="984a2-122">指定进程是否存在。</span><span class="sxs-lookup"><span data-stu-id="984a2-122">Specifies whether the processes exists.</span></span> <span data-ttu-id="984a2-123">将此属性设置为“Present”以确保进程存在。</span><span class="sxs-lookup"><span data-stu-id="984a2-123">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="984a2-124">否则，将其设置为“Absent”。</span><span class="sxs-lookup"><span data-stu-id="984a2-124">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="984a2-125">默认值为“Present”。</span><span class="sxs-lookup"><span data-stu-id="984a2-125">The default is "Present".</span></span>|
| <span data-ttu-id="984a2-126">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="984a2-126">StandardErrorPath</span></span>| <span data-ttu-id="984a2-127">进程写入标准错误的路径。</span><span class="sxs-lookup"><span data-stu-id="984a2-127">The path to which the processes write standard error.</span></span> <span data-ttu-id="984a2-128">将覆盖任何现有文件。</span><span class="sxs-lookup"><span data-stu-id="984a2-128">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="984a2-129">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="984a2-129">StandardInputPath</span></span>| <span data-ttu-id="984a2-130">进程从中接收标准输入的流。</span><span class="sxs-lookup"><span data-stu-id="984a2-130">The stream from which the process receives standard input.</span></span>|
| <span data-ttu-id="984a2-131">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="984a2-131">StandardOutputPath</span></span>| <span data-ttu-id="984a2-132">进程写入标准输出的文件的路径。</span><span class="sxs-lookup"><span data-stu-id="984a2-132">The path of the file to which the processes write standard output.</span></span> <span data-ttu-id="984a2-133">将覆盖任何现有文件。</span><span class="sxs-lookup"><span data-stu-id="984a2-133">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="984a2-134">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="984a2-134">WorkingDirectory</span></span>| <span data-ttu-id="984a2-135">用作进程当前工作目录的位置。</span><span class="sxs-lookup"><span data-stu-id="984a2-135">The location used as the current working directory for the processes.</span></span>|
| <span data-ttu-id="984a2-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="984a2-136">DependsOn</span></span> | <span data-ttu-id="984a2-137">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="984a2-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="984a2-138">例如，如果你想要首先运行 ID 为 **ResourceName**、类型为 **ResourceType** 的资源配置脚本块，则使用此属性的语法为 \`DependsOn = "[ResourceType]ResourceName"\`\`。</span><span class="sxs-lookup"><span data-stu-id="984a2-138">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **_ResourceType**, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\` .</span></span>|