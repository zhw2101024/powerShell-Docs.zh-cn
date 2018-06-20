---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: DSC WindowsProcess 资源
ms.openlocfilehash: 72668136a3a51c17c52f762c6f94bec3ed4597b0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187021"
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="e06c1-103">DSC WindowsProcess 资源</span><span class="sxs-lookup"><span data-stu-id="e06c1-103">DSC WindowsProcess Resource</span></span>

> <span data-ttu-id="e06c1-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e06c1-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="e06c1-105">Windows PowerShell Desired State Configuration (DSC) 中的 **WindowsProcess** 资源提供了用于在目标节点上配置进程的机制。</span><span class="sxs-lookup"><span data-stu-id="e06c1-105">The **WindowsProcess** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="e06c1-106">语法</span><span class="sxs-lookup"><span data-stu-id="e06c1-106">Syntax</span></span>

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ DependsOn = [string[]] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="e06c1-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="e06c1-107">Properties</span></span>
|  <span data-ttu-id="e06c1-108">属性</span><span class="sxs-lookup"><span data-stu-id="e06c1-108">Property</span></span>  |  <span data-ttu-id="e06c1-109">说明</span><span class="sxs-lookup"><span data-stu-id="e06c1-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="e06c1-110">参数</span><span class="sxs-lookup"><span data-stu-id="e06c1-110">Arguments</span></span>| <span data-ttu-id="e06c1-111">指示要原样传递到进程的参数字符串</span><span class="sxs-lookup"><span data-stu-id="e06c1-111">Indicates a string of arguments to pass to the process as-is.</span></span> <span data-ttu-id="e06c1-112">如果需要传递多个参数，请将它们全部放在此字符串中。</span><span class="sxs-lookup"><span data-stu-id="e06c1-112">If you need to pass several arguments, put them all in this string.</span></span>|
| <span data-ttu-id="e06c1-113">路径</span><span class="sxs-lookup"><span data-stu-id="e06c1-113">Path</span></span>| <span data-ttu-id="e06c1-114">进程可执行文件的路径。</span><span class="sxs-lookup"><span data-stu-id="e06c1-114">The path to the process executable.</span></span> <span data-ttu-id="e06c1-115">如果这是可执行文件的文件名（不是完全限定的路径），则 DSC 资源会搜索环境**路径**变量 (`$env:Path`) 以查找可执行文件。</span><span class="sxs-lookup"><span data-stu-id="e06c1-115">If this the file name of the executable (not the fully qualified path), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the executable file.</span></span> <span data-ttu-id="e06c1-116">如果此属性的值是完全限定的路径，则 DSC 不使用**路径**环境变量查找文件，并且会在不存在路径时引发错误。</span><span class="sxs-lookup"><span data-stu-id="e06c1-116">If the value of this property is a fully qualified path, DSC will not use the **Path** environment variable to find the file, and will throw an error if the path does not exist.</span></span> <span data-ttu-id="e06c1-117">不允许使用相对路径。</span><span class="sxs-lookup"><span data-stu-id="e06c1-117">Relative paths are not allowed.</span></span>|
| <span data-ttu-id="e06c1-118">凭据</span><span class="sxs-lookup"><span data-stu-id="e06c1-118">Credential</span></span>| <span data-ttu-id="e06c1-119">指示启动进程的凭据。</span><span class="sxs-lookup"><span data-stu-id="e06c1-119">Indicates the credentials for starting the process.</span></span>|
| <span data-ttu-id="e06c1-120">Ensure</span><span class="sxs-lookup"><span data-stu-id="e06c1-120">Ensure</span></span>| <span data-ttu-id="e06c1-121">指示进程是否存在。</span><span class="sxs-lookup"><span data-stu-id="e06c1-121">Indicates if the process exists.</span></span> <span data-ttu-id="e06c1-122">将此属性设置为“Present”以确保进程存在。</span><span class="sxs-lookup"><span data-stu-id="e06c1-122">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="e06c1-123">否则，将其设置为“Absent”。</span><span class="sxs-lookup"><span data-stu-id="e06c1-123">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="e06c1-124">默认值为“Present”。</span><span class="sxs-lookup"><span data-stu-id="e06c1-124">The default is "Present".</span></span>|
| <span data-ttu-id="e06c1-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="e06c1-125">DependsOn</span></span> | <span data-ttu-id="e06c1-126">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="e06c1-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="e06c1-127">例如，如果你想要首先运行 ID 为 __ResourceName__、类型为 __ResourceType__ 的资源配置脚本块，则使用此属性的语法为 \`DependsOn = "[ResourceType]ResourceName"\`\`。</span><span class="sxs-lookup"><span data-stu-id="e06c1-127">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\` .</span></span>|
| <span data-ttu-id="e06c1-128">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="e06c1-128">StandardErrorPath</span></span>| <span data-ttu-id="e06c1-129">指示写入标准错误的目录路径。</span><span class="sxs-lookup"><span data-stu-id="e06c1-129">Indicates the directory path to write the standard error.</span></span> <span data-ttu-id="e06c1-130">将覆盖任何现有文件。</span><span class="sxs-lookup"><span data-stu-id="e06c1-130">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="e06c1-131">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="e06c1-131">StandardInputPath</span></span>| <span data-ttu-id="e06c1-132">指示标准输入位置。</span><span class="sxs-lookup"><span data-stu-id="e06c1-132">Indicates the standard input location.</span></span>|
| <span data-ttu-id="e06c1-133">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="e06c1-133">StandardOutputPath</span></span>| <span data-ttu-id="e06c1-134">指示写入标准输出的位置。</span><span class="sxs-lookup"><span data-stu-id="e06c1-134">Indicates the location to write the standard output.</span></span> <span data-ttu-id="e06c1-135">将覆盖任何现有文件。</span><span class="sxs-lookup"><span data-stu-id="e06c1-135">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="e06c1-136">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="e06c1-136">WorkingDirectory</span></span>| <span data-ttu-id="e06c1-137">指示将用作进程当前工作目录的位置。</span><span class="sxs-lookup"><span data-stu-id="e06c1-137">Indicates the location that will be used as the current working directory for the process.</span></span>|