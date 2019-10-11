---
ms.date: 09/20/2019
keywords: dsc,powershell,配置,安装程序
title: DSC File 资源
ms.openlocfilehash: 4c6945d4cdcbc64ac6d52db563823efe8fd0247e
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954674"
---
# <a name="dsc-file-resource"></a><span data-ttu-id="aec5d-103">DSC File 资源</span><span class="sxs-lookup"><span data-stu-id="aec5d-103">DSC File Resource</span></span>

> <span data-ttu-id="aec5d-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="aec5d-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="aec5d-105">Windows PowerShell Desired State Configuration (DSC) 中的 **File** 资源提供用于管理目标节点上的文件和文件夹的机制。</span><span class="sxs-lookup"><span data-stu-id="aec5d-105">The **File** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and folders on the target node.</span></span> <span data-ttu-id="aec5d-106">目标节点必须能够访问 **DestinationPath** 和 **SourcePath**。</span><span class="sxs-lookup"><span data-stu-id="aec5d-106">**DestinationPath** and **SourcePath** must both be accessible by the target Node.</span></span>

## <a name="syntax"></a><span data-ttu-id="aec5d-107">语法</span><span class="sxs-lookup"><span data-stu-id="aec5d-107">Syntax</span></span>

```Syntax
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="aec5d-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="aec5d-108">Properties</span></span>

|<span data-ttu-id="aec5d-109">属性</span><span class="sxs-lookup"><span data-stu-id="aec5d-109">Property</span></span> |<span data-ttu-id="aec5d-110">说明</span><span class="sxs-lookup"><span data-stu-id="aec5d-110">Description</span></span> |
|---|---|
|<span data-ttu-id="aec5d-111">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="aec5d-111">DestinationPath</span></span> |<span data-ttu-id="aec5d-112">想要通过 **Ensure** 确保目标节点上的位置 **Present** 或 **Absent**。</span><span class="sxs-lookup"><span data-stu-id="aec5d-112">The location, on the target node, you want to ensure is **Present** or **Absent** with **Ensure**.</span></span> |
|<span data-ttu-id="aec5d-113">属性</span><span class="sxs-lookup"><span data-stu-id="aec5d-113">Attributes</span></span> |<span data-ttu-id="aec5d-114">目标文件或目录的特性的所需状态。</span><span class="sxs-lookup"><span data-stu-id="aec5d-114">The desired state of the attributes for the targeted file or directory.</span></span> <span data-ttu-id="aec5d-115">有效值包括 Archive  、Hidden  、ReadOnly  和 System  。</span><span class="sxs-lookup"><span data-stu-id="aec5d-115">Valid values are _Archive_, _Hidden_, _ReadOnly_, and _System_.</span></span> |
|<span data-ttu-id="aec5d-116">校验和</span><span class="sxs-lookup"><span data-stu-id="aec5d-116">Checksum</span></span> |<span data-ttu-id="aec5d-117">当确定两个文件是否相同时使用的校验和类型。</span><span class="sxs-lookup"><span data-stu-id="aec5d-117">The checksum type to use when determining whether two files are the same.</span></span> <span data-ttu-id="aec5d-118">有效值包括：**SHA-1**、**SHA-256**、**SHA-512**、**createdDate**、**modifiedDate**。</span><span class="sxs-lookup"><span data-stu-id="aec5d-118">Valid values include: **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**.</span></span> |
|<span data-ttu-id="aec5d-119">目录</span><span class="sxs-lookup"><span data-stu-id="aec5d-119">Contents</span></span> |<span data-ttu-id="aec5d-120">仅当与 **Type** **File** 一起使用时才有效。</span><span class="sxs-lookup"><span data-stu-id="aec5d-120">Only valid when used with **Type** **File**.</span></span> <span data-ttu-id="aec5d-121">指示要 **Ensure** 的内容在目标文件中的 **Present** 或 **Absent** 状态。</span><span class="sxs-lookup"><span data-stu-id="aec5d-121">Indicates the contents to **Ensure** are **Present** or **Absent** from the targeted file.</span></span> |
|<span data-ttu-id="aec5d-122">凭据</span><span class="sxs-lookup"><span data-stu-id="aec5d-122">Credential</span></span> |<span data-ttu-id="aec5d-123">访问资源（例如源文件）所需的凭据。</span><span class="sxs-lookup"><span data-stu-id="aec5d-123">The credentials that are required to access resources, such as source files.</span></span> |
|<span data-ttu-id="aec5d-124">Force</span><span class="sxs-lookup"><span data-stu-id="aec5d-124">Force</span></span> |<span data-ttu-id="aec5d-125">覆盖将导致错误的访问操作（如覆盖文件或删除不为空的目录）。</span><span class="sxs-lookup"><span data-stu-id="aec5d-125">Overrides access operations that would result in an error (such as overwriting a file or deleting a directory that is not empty).</span></span> <span data-ttu-id="aec5d-126">默认值为 `$false`。</span><span class="sxs-lookup"><span data-stu-id="aec5d-126">Default value is `$false`.</span></span> |
|<span data-ttu-id="aec5d-127">Recurse</span><span class="sxs-lookup"><span data-stu-id="aec5d-127">Recurse</span></span> |<span data-ttu-id="aec5d-128">仅当与 **Type** **Directory** 类型一起使用时才有效。</span><span class="sxs-lookup"><span data-stu-id="aec5d-128">Only valid when used with **Type** **Directory**.</span></span> <span data-ttu-id="aec5d-129">以递归方式对所有子目录执行状态操作。</span><span class="sxs-lookup"><span data-stu-id="aec5d-129">Performs the state operation recursively to all subdirectories.</span></span> <span data-ttu-id="aec5d-130">默认值为 `$false`。</span><span class="sxs-lookup"><span data-stu-id="aec5d-130">Default value is `$false`.</span></span> |
|<span data-ttu-id="aec5d-131">SourcePath</span><span class="sxs-lookup"><span data-stu-id="aec5d-131">SourcePath</span></span> |<span data-ttu-id="aec5d-132">要从其中复制文件或文件夹资源的路径。</span><span class="sxs-lookup"><span data-stu-id="aec5d-132">The path from which to copy the file or folder resource.</span></span> |
|<span data-ttu-id="aec5d-133">类型</span><span class="sxs-lookup"><span data-stu-id="aec5d-133">Type</span></span> |<span data-ttu-id="aec5d-134">正在配置的资源的类型。</span><span class="sxs-lookup"><span data-stu-id="aec5d-134">The type of resource being configured.</span></span> <span data-ttu-id="aec5d-135">有效值为 **Directory** 和 **File**。</span><span class="sxs-lookup"><span data-stu-id="aec5d-135">Valid values are **Directory** and **File**.</span></span> <span data-ttu-id="aec5d-136">默认值为 **File**。</span><span class="sxs-lookup"><span data-stu-id="aec5d-136">Default value is **File**.</span></span> |
|<span data-ttu-id="aec5d-137">MatchSource</span><span class="sxs-lookup"><span data-stu-id="aec5d-137">MatchSource</span></span> |<span data-ttu-id="aec5d-138">确定资源是否应监视初始复制之后添加到源目录的新文件。</span><span class="sxs-lookup"><span data-stu-id="aec5d-138">Determines if the resource should monitor for new files added to the source directory after the initial copy.</span></span> <span data-ttu-id="aec5d-139">`$true` 值表示，在初始复制之后，任何新的源文件都应复制到目标位置。</span><span class="sxs-lookup"><span data-stu-id="aec5d-139">A value of `$true` indicates that, after the initial copy, any new source files should be copied to the destination.</span></span> <span data-ttu-id="aec5d-140">如果设置为 `$false`，资源将缓存源目录的内容，并忽略初始复制之后添加的任何文件。</span><span class="sxs-lookup"><span data-stu-id="aec5d-140">If set to `$false`, the resource caches the contents of the source directory and ignores any files added after the initial copy.</span></span> <span data-ttu-id="aec5d-141">默认值为 `$false`。</span><span class="sxs-lookup"><span data-stu-id="aec5d-141">Default value is `$false`.</span></span> |

> [!WARNING]
> <span data-ttu-id="aec5d-142">如果没有为 **Credential** 或 **PSRunAsCredential** 指定值，则资源将使用目标节点的计算机帐户访问 **SourcePath**。</span><span class="sxs-lookup"><span data-stu-id="aec5d-142">If you do not specify a value for **Credential** or **PSRunAsCredential**, the resource will use the computer account of the target node to access the **SourcePath**.</span></span> <span data-ttu-id="aec5d-143">如果 **SourcePath** 是 UNC 共享，这可能导致“拒绝访问”错误。</span><span class="sxs-lookup"><span data-stu-id="aec5d-143">When the **SourcePath** is a UNC share, this could result in an "Access Denied" error.</span></span> <span data-ttu-id="aec5d-144">请确保相应地设置权限，或者使用 **Credential** 或 **PSRunAsCredential** 属性指定应该使用的帐户。</span><span class="sxs-lookup"><span data-stu-id="aec5d-144">Please ensure your permissions are set accordingly, or use the **Credential** or **PSRunAsCredential** properties to specify the account that should be used.</span></span>

## <a name="common-properties"></a><span data-ttu-id="aec5d-145">公共属性</span><span class="sxs-lookup"><span data-stu-id="aec5d-145">Common properties</span></span>

|<span data-ttu-id="aec5d-146">属性</span><span class="sxs-lookup"><span data-stu-id="aec5d-146">Property</span></span> |<span data-ttu-id="aec5d-147">说明</span><span class="sxs-lookup"><span data-stu-id="aec5d-147">Description</span></span> |
|---|---|
|<span data-ttu-id="aec5d-148">DependsOn</span><span class="sxs-lookup"><span data-stu-id="aec5d-148">DependsOn</span></span> |<span data-ttu-id="aec5d-149">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="aec5d-149">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="aec5d-150">例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="aec5d-150">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="aec5d-151">Ensure</span><span class="sxs-lookup"><span data-stu-id="aec5d-151">Ensure</span></span> |<span data-ttu-id="aec5d-152">确定文件和 **Destination** 中的 **Contents** 是否应该存在。</span><span class="sxs-lookup"><span data-stu-id="aec5d-152">Determines whether the file and **Contents** at the **Destination** should exist or not.</span></span> <span data-ttu-id="aec5d-153">将此属性设置为 **Present** 可确保文件存在。</span><span class="sxs-lookup"><span data-stu-id="aec5d-153">Set this property to **Present** to ensure the file exists.</span></span> <span data-ttu-id="aec5d-154">将其设置为 **Absent** 可确保内容不存在。</span><span class="sxs-lookup"><span data-stu-id="aec5d-154">Set it to **Absent** to ensure they do not exist.</span></span> <span data-ttu-id="aec5d-155">默认值为 **Present**。</span><span class="sxs-lookup"><span data-stu-id="aec5d-155">The default value is **Present**.</span></span> |
|<span data-ttu-id="aec5d-156">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="aec5d-156">PsDscRunAsCredential</span></span> |<span data-ttu-id="aec5d-157">设置用于运行整个资源的身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="aec5d-157">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="aec5d-158">在 WMF 5.0 中添加了 **PsDscRunAsCredential** 公共属性，用于允许在其他凭据上下文中运行任何 DSC 资源。</span><span class="sxs-lookup"><span data-stu-id="aec5d-158">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="aec5d-159">有关详细信息，请参阅[将凭据与 DSC 资源配合使用](../../../configurations/runasuser.md)。</span><span class="sxs-lookup"><span data-stu-id="aec5d-159">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

### <a name="additional-information"></a><span data-ttu-id="aec5d-160">附加信息</span><span class="sxs-lookup"><span data-stu-id="aec5d-160">Additional information</span></span>

- <span data-ttu-id="aec5d-161">仅指定 **DestinationPath** 时，资源可确保该路径存在 (**Present**) 或不存在 (**Absent**)。</span><span class="sxs-lookup"><span data-stu-id="aec5d-161">When you only specify a **DestinationPath**, the resource ensures that the path exists if **Present** or does not exist if **Absent**.</span></span>
- <span data-ttu-id="aec5d-162">当使用 **Directory** 的 **Type** 值指定 **SourcePath** 和 **DestinationPath** 时，资源会将源目录复制到目标路径。</span><span class="sxs-lookup"><span data-stu-id="aec5d-162">When you specify a **SourcePath** and a **DestinationPath** with a **Type** value of **Directory**, the resource copies source directory to the destination path.</span></span> <span data-ttu-id="aec5d-163">属性 **Recurse**、**Force** 和 **MatchSource** 更改所执行的复制操作的类型，而 **Credential** 决定使用哪个帐户来访问源目录。</span><span class="sxs-lookup"><span data-stu-id="aec5d-163">The properties **Recurse**, **Force**, and **MatchSource** change the type of copy operation performed, while **Credential** determines which account to use to access the source directory.</span></span>
- <span data-ttu-id="aec5d-164">如果为 **Attributes** 属性指定的值为 **ReadOnly** 并指定 **DestinationPath**，则 **Ensure** **Present** 将创建指定的路径，而 **Contents** 将设置文件的内容。</span><span class="sxs-lookup"><span data-stu-id="aec5d-164">If you specified a value of **ReadOnly** for the **Attributes** property alongside a **DestinationPath**, **Ensure** **Present** would create the path specified, while **Contents** would set the contents of the file.</span></span> <span data-ttu-id="aec5d-165">**Ensure** **Absent** 设置将完全忽略 **Attributes** 属性，并删除指定路径下的任何文件。</span><span class="sxs-lookup"><span data-stu-id="aec5d-165">An **Ensure** **Absent** setting would ignore the **Attributes** property entirely, and remove any file at the specified path.</span></span>

## <a name="example"></a><span data-ttu-id="aec5d-166">示例</span><span class="sxs-lookup"><span data-stu-id="aec5d-166">Example</span></span>

<span data-ttu-id="aec5d-167">下面的示例使用文件资源将目录及其子目录从拉取服务器复制到目标节点。</span><span class="sxs-lookup"><span data-stu-id="aec5d-167">The following example copies a directory and its subdirectories from a pull server to a target node using the File Resource.</span></span> <span data-ttu-id="aec5d-168">如果操作成功，日志资源会向事件日志写入一条确认消息。</span><span class="sxs-lookup"><span data-stu-id="aec5d-168">If the operation succeeds, the Log resource writes a confirmation message to the event log.</span></span>

<span data-ttu-id="aec5d-169">源目录是从拉取服务器共享的 UNC 路径 (`\\PullServer\DemoSource`)。</span><span class="sxs-lookup"><span data-stu-id="aec5d-169">The source directory is a UNC path (`\\PullServer\DemoSource`) shared from the Pull Server.</span></span> <span data-ttu-id="aec5d-170">**Recurse** 属性还可确保复制所有子目录。</span><span class="sxs-lookup"><span data-stu-id="aec5d-170">The **Recurse** property ensures that all subdirectories are copied as well.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aec5d-171">默认情况下，目标节点上的 LCM 在本地系统帐户的上下文中执行。</span><span class="sxs-lookup"><span data-stu-id="aec5d-171">The LCM on the target Node executes in the context of the local system account by default.</span></span> <span data-ttu-id="aec5d-172">要授予对 SourcePath  的访问权限，请为目标节点的计算机帐户授予适当权限。</span><span class="sxs-lookup"><span data-stu-id="aec5d-172">To grant access to the **SourcePath**, give the target Node's computer account appropriate permissions.</span></span> <span data-ttu-id="aec5d-173">**Credential** 和 **PSDSCRunAsCredential** 都更改了 LCM 用于访问 **SourcePath** 的上下文。</span><span class="sxs-lookup"><span data-stu-id="aec5d-173">The **Credential** and **PSDSCRunAsCredential** both change the context the LCM uses to access the **SourcePath**.</span></span> <span data-ttu-id="aec5d-174">仍需要向将用于访问 SourcePath  的帐户授予访问权限。</span><span class="sxs-lookup"><span data-stu-id="aec5d-174">You still need to grant access to the account that will be used to access the **SourcePath**.</span></span>

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present" # Ensure the directory is Present on the target node.
            Type = "Directory" # The default is File.
            Recurse = $true # Recursively copy all subdirectories.
            SourcePath = "\\PullServer\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # Depends on successful execution of the File resource.
        }
    }
}
```

<span data-ttu-id="aec5d-175">有关在 DSC 中使用 Credentials  的详细信息，请参阅[以用户身份运行](../../../configurations/runAsUser.md)或[配置数据凭据](../../../configurations/configDataCredentials.md)。</span><span class="sxs-lookup"><span data-stu-id="aec5d-175">For more on using **Credentials** in DSC see [Run As User](../../../configurations/runAsUser.md) or [Config Data Credentials](../../../configurations/configDataCredentials.md).</span></span>