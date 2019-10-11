---
ms.date: 09/20/2019
keywords: dsc,powershell,配置,安装程序
title: DSC WindowsProcess 资源
ms.openlocfilehash: e168cdebb04f7ec83b73a537a5f188299f40d8b7
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952834"
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="7bc29-103">DSC WindowsProcess 资源</span><span class="sxs-lookup"><span data-stu-id="7bc29-103">DSC WindowsProcess Resource</span></span>

> <span data-ttu-id="7bc29-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="7bc29-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="7bc29-105">Windows PowerShell Desired State Configuration (DSC) 中的 **WindowsProcess** 资源提供了用于在目标节点上配置进程的机制。</span><span class="sxs-lookup"><span data-stu-id="7bc29-105">The **WindowsProcess** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="7bc29-106">语法</span><span class="sxs-lookup"><span data-stu-id="7bc29-106">Syntax</span></span>

```Syntax
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="7bc29-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="7bc29-107">Properties</span></span>

|<span data-ttu-id="7bc29-108">属性</span><span class="sxs-lookup"><span data-stu-id="7bc29-108">Property</span></span> |<span data-ttu-id="7bc29-109">说明</span><span class="sxs-lookup"><span data-stu-id="7bc29-109">Description</span></span> |
|---|---|
|<span data-ttu-id="7bc29-110">参数</span><span class="sxs-lookup"><span data-stu-id="7bc29-110">Arguments</span></span> |<span data-ttu-id="7bc29-111">指示要原样传递到进程的参数字符串</span><span class="sxs-lookup"><span data-stu-id="7bc29-111">Indicates a string of arguments to pass to the process as-is.</span></span> <span data-ttu-id="7bc29-112">如果需要传递多个参数，请将它们全部放在此字符串中。</span><span class="sxs-lookup"><span data-stu-id="7bc29-112">If you need to pass several arguments, put them all in this string.</span></span> |
|<span data-ttu-id="7bc29-113">路径</span><span class="sxs-lookup"><span data-stu-id="7bc29-113">Path</span></span> |<span data-ttu-id="7bc29-114">进程可执行文件的路径。</span><span class="sxs-lookup"><span data-stu-id="7bc29-114">The path to the process executable.</span></span> <span data-ttu-id="7bc29-115">如果这是可执行文件的文件名（不是完全限定的路径），则 DSC 资源会搜索环境 `$env:Path` 变量以查找可执行文件。</span><span class="sxs-lookup"><span data-stu-id="7bc29-115">If this the file name of the executable (not the fully qualified path), the DSC resource will search the environment `$env:Path` variable to find the executable file.</span></span> <span data-ttu-id="7bc29-116">如果此属性的值是完全限定的路径，则 DSC 不使用 `$env:Path` 变量查找文件，并且会在不存在路径时引发错误。</span><span class="sxs-lookup"><span data-stu-id="7bc29-116">If the value of this property is a fully qualified path, DSC will not use the `$env:Path` variable to find the file, and will throw an error if the path does not exist.</span></span> <span data-ttu-id="7bc29-117">不允许使用相对路径。</span><span class="sxs-lookup"><span data-stu-id="7bc29-117">Relative paths are not allowed.</span></span> |
|<span data-ttu-id="7bc29-118">凭据</span><span class="sxs-lookup"><span data-stu-id="7bc29-118">Credential</span></span> |<span data-ttu-id="7bc29-119">指示启动进程的凭据。</span><span class="sxs-lookup"><span data-stu-id="7bc29-119">Indicates the credentials for starting the process.</span></span> |
|<span data-ttu-id="7bc29-120">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="7bc29-120">StandardErrorPath</span></span> |<span data-ttu-id="7bc29-121">指示写入标准错误的目录路径。</span><span class="sxs-lookup"><span data-stu-id="7bc29-121">Indicates the directory path to write the standard error.</span></span> <span data-ttu-id="7bc29-122">将覆盖任何现有文件。</span><span class="sxs-lookup"><span data-stu-id="7bc29-122">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="7bc29-123">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="7bc29-123">StandardInputPath</span></span> |<span data-ttu-id="7bc29-124">指示标准输入位置。</span><span class="sxs-lookup"><span data-stu-id="7bc29-124">Indicates the standard input location.</span></span> |
|<span data-ttu-id="7bc29-125">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="7bc29-125">StandardOutputPath</span></span> |<span data-ttu-id="7bc29-126">指示写入标准输出的位置。</span><span class="sxs-lookup"><span data-stu-id="7bc29-126">Indicates the location to write the standard output.</span></span> <span data-ttu-id="7bc29-127">将覆盖任何现有文件。</span><span class="sxs-lookup"><span data-stu-id="7bc29-127">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="7bc29-128">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="7bc29-128">WorkingDirectory</span></span> |<span data-ttu-id="7bc29-129">指示将用作进程当前工作目录的位置。</span><span class="sxs-lookup"><span data-stu-id="7bc29-129">Indicates the location that will be used as the current working directory for the process.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="7bc29-130">公共属性</span><span class="sxs-lookup"><span data-stu-id="7bc29-130">Common properties</span></span>

|<span data-ttu-id="7bc29-131">属性</span><span class="sxs-lookup"><span data-stu-id="7bc29-131">Property</span></span> |<span data-ttu-id="7bc29-132">说明</span><span class="sxs-lookup"><span data-stu-id="7bc29-132">Description</span></span> |
|---|---|
|<span data-ttu-id="7bc29-133">DependsOn</span><span class="sxs-lookup"><span data-stu-id="7bc29-133">DependsOn</span></span> |<span data-ttu-id="7bc29-134">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="7bc29-134">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="7bc29-135">例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="7bc29-135">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="7bc29-136">Ensure</span><span class="sxs-lookup"><span data-stu-id="7bc29-136">Ensure</span></span> |<span data-ttu-id="7bc29-137">指示进程是否存在。</span><span class="sxs-lookup"><span data-stu-id="7bc29-137">Indicates if the process exists.</span></span> <span data-ttu-id="7bc29-138">将此属性设置为 **Present** 可确保进程存在。</span><span class="sxs-lookup"><span data-stu-id="7bc29-138">Set this property to **Present** to ensure that the process exists.</span></span> <span data-ttu-id="7bc29-139">否则，将其设置为 **Absent**。</span><span class="sxs-lookup"><span data-stu-id="7bc29-139">Otherwise, set it to **Absent**.</span></span> <span data-ttu-id="7bc29-140">默认值为 **Present**。</span><span class="sxs-lookup"><span data-stu-id="7bc29-140">The default value is **Present**.</span></span> |
|<span data-ttu-id="7bc29-141">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="7bc29-141">PsDscRunAsCredential</span></span> |<span data-ttu-id="7bc29-142">设置用于运行整个资源的身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="7bc29-142">Sets the credential for running the entire resource as.</span></span> |