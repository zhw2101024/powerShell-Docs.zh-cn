---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: DSC WindowsProcess 资源
ms.openlocfilehash: cee93ab283ded407d6e032161125aa6d6ac98827
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/26/2018
ms.locfileid: "39267951"
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="6511d-103">DSC WindowsProcess 资源</span><span class="sxs-lookup"><span data-stu-id="6511d-103">DSC WindowsProcess Resource</span></span>

<span data-ttu-id="6511d-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="6511d-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="6511d-105">Windows PowerShell Desired State Configuration (DSC) 中的 **WindowsProcess** 资源提供了用于在目标节点上配置进程的机制。</span><span class="sxs-lookup"><span data-stu-id="6511d-105">The **WindowsProcess** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="6511d-106">语法</span><span class="sxs-lookup"><span data-stu-id="6511d-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="6511d-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="6511d-107">Properties</span></span>

| <span data-ttu-id="6511d-108">属性</span><span class="sxs-lookup"><span data-stu-id="6511d-108">Property</span></span> | <span data-ttu-id="6511d-109">说明</span><span class="sxs-lookup"><span data-stu-id="6511d-109">Description</span></span> |
| --- | --- |
| <span data-ttu-id="6511d-110">参数</span><span class="sxs-lookup"><span data-stu-id="6511d-110">Arguments</span></span>| <span data-ttu-id="6511d-111">指示要原样传递到进程的参数字符串</span><span class="sxs-lookup"><span data-stu-id="6511d-111">Indicates a string of arguments to pass to the process as-is.</span></span> <span data-ttu-id="6511d-112">如果需要传递多个参数，请将它们全部放在此字符串中。</span><span class="sxs-lookup"><span data-stu-id="6511d-112">If you need to pass several arguments, put them all in this string.</span></span>|
| <span data-ttu-id="6511d-113">路径</span><span class="sxs-lookup"><span data-stu-id="6511d-113">Path</span></span>| <span data-ttu-id="6511d-114">进程可执行文件的路径。</span><span class="sxs-lookup"><span data-stu-id="6511d-114">The path to the process executable.</span></span> <span data-ttu-id="6511d-115">如果这是可执行文件的文件名（不是完全限定的路径），则 DSC 资源会搜索环境**路径**变量 (`$env:Path`) 以查找可执行文件。</span><span class="sxs-lookup"><span data-stu-id="6511d-115">If this the file name of the executable (not the fully qualified path), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the executable file.</span></span> <span data-ttu-id="6511d-116">如果此属性的值是完全限定的路径，则 DSC 不使用**路径**环境变量查找文件，并且会在不存在路径时引发错误。</span><span class="sxs-lookup"><span data-stu-id="6511d-116">If the value of this property is a fully qualified path, DSC will not use the **Path** environment variable to find the file, and will throw an error if the path does not exist.</span></span> <span data-ttu-id="6511d-117">不允许使用相对路径。</span><span class="sxs-lookup"><span data-stu-id="6511d-117">Relative paths are not allowed.</span></span>|
| <span data-ttu-id="6511d-118">凭据</span><span class="sxs-lookup"><span data-stu-id="6511d-118">Credential</span></span>| <span data-ttu-id="6511d-119">指示启动进程的凭据。</span><span class="sxs-lookup"><span data-stu-id="6511d-119">Indicates the credentials for starting the process.</span></span>|
| <span data-ttu-id="6511d-120">Ensure</span><span class="sxs-lookup"><span data-stu-id="6511d-120">Ensure</span></span>| <span data-ttu-id="6511d-121">指示进程是否存在。</span><span class="sxs-lookup"><span data-stu-id="6511d-121">Indicates if the process exists.</span></span> <span data-ttu-id="6511d-122">将此属性设置为“Present”以确保进程存在。</span><span class="sxs-lookup"><span data-stu-id="6511d-122">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="6511d-123">否则，将其设置为“Absent”。</span><span class="sxs-lookup"><span data-stu-id="6511d-123">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="6511d-124">默认值为“Present”。</span><span class="sxs-lookup"><span data-stu-id="6511d-124">The default is "Present".</span></span>|
| <span data-ttu-id="6511d-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="6511d-125">DependsOn</span></span> | <span data-ttu-id="6511d-126">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="6511d-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="6511d-127">例如，如果想要首先运行 ID 为“ResourceName”、类型为“ResourceType”的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="6511d-127">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"` .</span></span>|
| <span data-ttu-id="6511d-128">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="6511d-128">StandardErrorPath</span></span>| <span data-ttu-id="6511d-129">指示写入标准错误的目录路径。</span><span class="sxs-lookup"><span data-stu-id="6511d-129">Indicates the directory path to write the standard error.</span></span> <span data-ttu-id="6511d-130">将覆盖任何现有文件。</span><span class="sxs-lookup"><span data-stu-id="6511d-130">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="6511d-131">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="6511d-131">StandardInputPath</span></span>| <span data-ttu-id="6511d-132">指示标准输入位置。</span><span class="sxs-lookup"><span data-stu-id="6511d-132">Indicates the standard input location.</span></span>|
| <span data-ttu-id="6511d-133">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="6511d-133">StandardOutputPath</span></span>| <span data-ttu-id="6511d-134">指示写入标准输出的位置。</span><span class="sxs-lookup"><span data-stu-id="6511d-134">Indicates the location to write the standard output.</span></span> <span data-ttu-id="6511d-135">将覆盖任何现有文件。</span><span class="sxs-lookup"><span data-stu-id="6511d-135">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="6511d-136">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="6511d-136">WorkingDirectory</span></span>| <span data-ttu-id="6511d-137">指示将用作进程当前工作目录的位置。</span><span class="sxs-lookup"><span data-stu-id="6511d-137">Indicates the location that will be used as the current working directory for the process.</span></span>|