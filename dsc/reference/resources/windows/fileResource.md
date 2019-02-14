---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: DSC File 资源
ms.openlocfilehash: b5bc2c305b8cfccbd044274811df631264a24279
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "55677454"
---
# <a name="dsc-file-resource"></a><span data-ttu-id="563eb-103">DSC File 资源</span><span class="sxs-lookup"><span data-stu-id="563eb-103">DSC File Resource</span></span>

> <span data-ttu-id="563eb-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="563eb-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="563eb-105">Windows PowerShell Desired State Configuration (DSC) 中的 File 资源提供了管理目标节点上的文件和文件夹的机制。</span><span class="sxs-lookup"><span data-stu-id="563eb-105">The File resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and folders on the target node.</span></span> <span data-ttu-id="563eb-106">**DestinationPath**并**SourcePath**必须都为可由目标节点访问。</span><span class="sxs-lookup"><span data-stu-id="563eb-106">The **DestinationPath** and **SourcePath** must both be accessible by the target Node.</span></span>

## <a name="syntax"></a><span data-ttu-id="563eb-107">语法</span><span class="sxs-lookup"><span data-stu-id="563eb-107">Syntax</span></span>

```
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ DependsOn = [string[]] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
}
```

## <a name="properties"></a><span data-ttu-id="563eb-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="563eb-108">Properties</span></span>

|<span data-ttu-id="563eb-109">属性</span><span class="sxs-lookup"><span data-stu-id="563eb-109">Property</span></span>       |<span data-ttu-id="563eb-110">说明</span><span class="sxs-lookup"><span data-stu-id="563eb-110">Description</span></span>                                                                   |<span data-ttu-id="563eb-111">必需</span><span class="sxs-lookup"><span data-stu-id="563eb-111">Required</span></span>|<span data-ttu-id="563eb-112">默认值</span><span class="sxs-lookup"><span data-stu-id="563eb-112">Default</span></span>|
|---------------|------------------------------------------------------------------------------|--------|-------|
|<span data-ttu-id="563eb-113">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="563eb-113">DestinationPath</span></span>|<span data-ttu-id="563eb-114">你想要确保在目标节点上的位置是`Present`或`Absent`。</span><span class="sxs-lookup"><span data-stu-id="563eb-114">The location, on the target node, you want to ensure is `Present` or `Absent`.</span></span>|<span data-ttu-id="563eb-115">是</span><span class="sxs-lookup"><span data-stu-id="563eb-115">Yes</span></span>|<span data-ttu-id="563eb-116">否</span><span class="sxs-lookup"><span data-stu-id="563eb-116">No</span></span>|
|<span data-ttu-id="563eb-117">属性</span><span class="sxs-lookup"><span data-stu-id="563eb-117">Attributes</span></span>     |<span data-ttu-id="563eb-118">目标的文件或目录的属性所需的状态。</span><span class="sxs-lookup"><span data-stu-id="563eb-118">The desired state of the attributes for the targeted file or directory.</span></span> <span data-ttu-id="563eb-119">有效的值为**存档**， **Hidden**， **ReadOnly**，以及**系统**。</span><span class="sxs-lookup"><span data-stu-id="563eb-119">Valid values are **Archive**, **Hidden**, **ReadOnly**, and **System**.</span></span>|<span data-ttu-id="563eb-120">否</span><span class="sxs-lookup"><span data-stu-id="563eb-120">No</span></span>|<span data-ttu-id="563eb-121">无</span><span class="sxs-lookup"><span data-stu-id="563eb-121">None</span></span>|
|<span data-ttu-id="563eb-122">校验和</span><span class="sxs-lookup"><span data-stu-id="563eb-122">Checksum</span></span>      |<span data-ttu-id="563eb-123">确定两个文件是否相同时要使用的校验和类型。</span><span class="sxs-lookup"><span data-stu-id="563eb-123">The checksum type to use when determining whether two files are the same.</span></span> <span data-ttu-id="563eb-124">有效值包括：Sha-1、 SHA-256、 SHA-512、 createdDate、 modifiedDate。</span><span class="sxs-lookup"><span data-stu-id="563eb-124">Valid values include: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.</span></span>|<span data-ttu-id="563eb-125">否</span><span class="sxs-lookup"><span data-stu-id="563eb-125">No</span></span>|<span data-ttu-id="563eb-126">仅在文件或目录名称进行比较。</span><span class="sxs-lookup"><span data-stu-id="563eb-126">Only the file or directory name is compared.</span></span>|
|<span data-ttu-id="563eb-127">目录</span><span class="sxs-lookup"><span data-stu-id="563eb-127">Contents</span></span>       |<span data-ttu-id="563eb-128">仅当与一起使用时有效`File`类型。</span><span class="sxs-lookup"><span data-stu-id="563eb-128">Only valid when used with `File` type.</span></span> <span data-ttu-id="563eb-129">指示为确保内容`Present`或`Absent`从目标文件。</span><span class="sxs-lookup"><span data-stu-id="563eb-129">Indicates the contents to Ensure are `Present` or `Absent` from the targeted file.</span></span> |<span data-ttu-id="563eb-130">否</span><span class="sxs-lookup"><span data-stu-id="563eb-130">No</span></span>|<span data-ttu-id="563eb-131">无</span><span class="sxs-lookup"><span data-stu-id="563eb-131">None</span></span>|
|<span data-ttu-id="563eb-132">凭据</span><span class="sxs-lookup"><span data-stu-id="563eb-132">Credential</span></span>     |<span data-ttu-id="563eb-133">所访问资源，如源文件所需的凭据。</span><span class="sxs-lookup"><span data-stu-id="563eb-133">The credentials that are required to access resources, such as source files.</span></span>|<span data-ttu-id="563eb-134">否</span><span class="sxs-lookup"><span data-stu-id="563eb-134">No</span></span>|<span data-ttu-id="563eb-135">目标节点的计算机帐户。</span><span class="sxs-lookup"><span data-stu-id="563eb-135">The target node's Computer Account.</span></span> <span data-ttu-id="563eb-136">（见备注）</span><span class="sxs-lookup"><span data-stu-id="563eb-136">(*see note*)</span></span>|
|<span data-ttu-id="563eb-137">Ensure</span><span class="sxs-lookup"><span data-stu-id="563eb-137">Ensure</span></span>         |<span data-ttu-id="563eb-138">目标文件或目录的所需的状态。</span><span class="sxs-lookup"><span data-stu-id="563eb-138">The desired state of the target file or directory.</span></span> |<span data-ttu-id="563eb-139">否</span><span class="sxs-lookup"><span data-stu-id="563eb-139">No</span></span>|<span data-ttu-id="563eb-140">**存在**</span><span class="sxs-lookup"><span data-stu-id="563eb-140">**Present**</span></span>|
|<span data-ttu-id="563eb-141">Force</span><span class="sxs-lookup"><span data-stu-id="563eb-141">Force</span></span>          |<span data-ttu-id="563eb-142">重写访问操作会导致错误 （如覆盖的文件或删除目录不为空）。</span><span class="sxs-lookup"><span data-stu-id="563eb-142">Overrides access operations that would result in an error (such as overwriting a file or deleting a directory that is not empty).</span></span>|<span data-ttu-id="563eb-143">否</span><span class="sxs-lookup"><span data-stu-id="563eb-143">No</span></span>|`$false`|
|<span data-ttu-id="563eb-144">Recurse</span><span class="sxs-lookup"><span data-stu-id="563eb-144">Recurse</span></span>        |<span data-ttu-id="563eb-145">仅当与一起使用时有效`Directory`类型。</span><span class="sxs-lookup"><span data-stu-id="563eb-145">Only valid when used with `Directory` type.</span></span> <span data-ttu-id="563eb-146">执行状态操作以递归方式将为所有子目录。</span><span class="sxs-lookup"><span data-stu-id="563eb-146">Performs the state operation recursively to all subdirectories.</span></span>|<span data-ttu-id="563eb-147">否</span><span class="sxs-lookup"><span data-stu-id="563eb-147">No</span></span>|`$false`|
|<span data-ttu-id="563eb-148">DependsOn</span><span class="sxs-lookup"><span data-stu-id="563eb-148">DependsOn</span></span>      |<span data-ttu-id="563eb-149">设置指定资源的依赖项。</span><span class="sxs-lookup"><span data-stu-id="563eb-149">Sets a dependency on specified resource(s).</span></span> <span data-ttu-id="563eb-150">此资源将仅在成功执行所有从属资源后执行。</span><span class="sxs-lookup"><span data-stu-id="563eb-150">This resource will only execute after successful execution of any dependent resources.</span></span> <span data-ttu-id="563eb-151">您可以指定使用语法的从属资源`"[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="563eb-151">You can specify dependent resources using the syntax `"[ResourceType]ResourceName"`.</span></span> <span data-ttu-id="563eb-152">请参阅 [about_DependsOn](../../../configurations/resource-depends-on.md)</span><span class="sxs-lookup"><span data-stu-id="563eb-152">See [about_DependsOn](../../../configurations/resource-depends-on.md)</span></span>|<span data-ttu-id="563eb-153">否</span><span class="sxs-lookup"><span data-stu-id="563eb-153">No</span></span>|<span data-ttu-id="563eb-154">无</span><span class="sxs-lookup"><span data-stu-id="563eb-154">None</span></span>|
|<span data-ttu-id="563eb-155">SourcePath</span><span class="sxs-lookup"><span data-stu-id="563eb-155">SourcePath</span></span>     |<span data-ttu-id="563eb-156">要从其中复制文件或文件夹资源路径。</span><span class="sxs-lookup"><span data-stu-id="563eb-156">The path from which to copy the file or folder resource.</span></span>|<span data-ttu-id="563eb-157">否</span><span class="sxs-lookup"><span data-stu-id="563eb-157">No</span></span>|<span data-ttu-id="563eb-158">无</span><span class="sxs-lookup"><span data-stu-id="563eb-158">None</span></span>|
|<span data-ttu-id="563eb-159">类型</span><span class="sxs-lookup"><span data-stu-id="563eb-159">Type</span></span>           |<span data-ttu-id="563eb-160">正在配置资源的类型。</span><span class="sxs-lookup"><span data-stu-id="563eb-160">The type of resource being configured.</span></span> <span data-ttu-id="563eb-161">有效的值为`Directory`和`File`。</span><span class="sxs-lookup"><span data-stu-id="563eb-161">Valid values are `Directory` and `File`.</span></span>|<span data-ttu-id="563eb-162">否</span><span class="sxs-lookup"><span data-stu-id="563eb-162">No</span></span>|`File`|
|<span data-ttu-id="563eb-163">MatchSource</span><span class="sxs-lookup"><span data-stu-id="563eb-163">MatchSource</span></span>    |<span data-ttu-id="563eb-164">确定是否资源应监视的初始复制后添加到源目录的新文件。</span><span class="sxs-lookup"><span data-stu-id="563eb-164">Determines if the resource should monitor for new files added to the source directory after the initial copy.</span></span> <span data-ttu-id="563eb-165">值为`$true`指示，初始复制后，任何新的源代码文件应复制到目标。</span><span class="sxs-lookup"><span data-stu-id="563eb-165">A value of `$true` indicates that, after the initial copy, any new source files should be copied to the destination.</span></span> <span data-ttu-id="563eb-166">如果设置为`$False`，资源缓存源目录的内容，并忽略初始复制后添加的任何文件。</span><span class="sxs-lookup"><span data-stu-id="563eb-166">If set to `$False`, the resource caches the contents of the source directory and ignores any files added after the initial copy.</span></span>|<span data-ttu-id="563eb-167">否</span><span class="sxs-lookup"><span data-stu-id="563eb-167">No</span></span>|`$false`|

> [!WARNING]
> <span data-ttu-id="563eb-168">如果未指定的值`Credential`或`PSRunAsCredential`(PS V.5)，该资源将用于目标节点的计算机帐户访问`SourcePath`。</span><span class="sxs-lookup"><span data-stu-id="563eb-168">If you do not specify a value for `Credential` or `PSRunAsCredential` (PS V.5), the resource will use the computer account of the target node to access the `SourcePath`.</span></span>  <span data-ttu-id="563eb-169">当`SourcePath`是 UNC 共享，这可能导致"拒绝访问"错误。</span><span class="sxs-lookup"><span data-stu-id="563eb-169">When the `SourcePath` is a UNC share, this could result in an "Access Denied" error.</span></span> <span data-ttu-id="563eb-170">请确保你的权限相应地，设置或使用`Credential`或`PSRunAsCredential`属性以指定应使用的帐户。</span><span class="sxs-lookup"><span data-stu-id="563eb-170">Please ensure your permissions are set accordingly, or use the `Credential` or `PSRunAsCredential` properties to specify the account that should be used.</span></span>

## <a name="present-vs-absent"></a><span data-ttu-id="563eb-171">存在 vs。不存在</span><span class="sxs-lookup"><span data-stu-id="563eb-171">Present vs. Absent</span></span>

<span data-ttu-id="563eb-172">每个 DSC 资源执行基于的值为指定的不同操作`Ensure`属性。</span><span class="sxs-lookup"><span data-stu-id="563eb-172">Each DSC resource performs different operations based on the value you specify for the `Ensure` property.</span></span> <span data-ttu-id="563eb-173">执行以上属性决定状态操作指定的值。</span><span class="sxs-lookup"><span data-stu-id="563eb-173">The values you specify for the above properties determines the state operation performed.</span></span>

### <a name="existence"></a><span data-ttu-id="563eb-174">存在</span><span class="sxs-lookup"><span data-stu-id="563eb-174">Existence</span></span>

<span data-ttu-id="563eb-175">当仅指定`DestinationPath`，资源可以确保该路径存在 (`Present`) 或不存在 (`Absent`)。</span><span class="sxs-lookup"><span data-stu-id="563eb-175">When you only specify a `DestinationPath`, the resource ensures that the path exists (`Present`) or does not exist (`Absent`).</span></span>

### <a name="copy-operations"></a><span data-ttu-id="563eb-176">复制操作</span><span class="sxs-lookup"><span data-stu-id="563eb-176">Copy Operations</span></span>

<span data-ttu-id="563eb-177">当指定`SourcePath`和一个`DestinationPath`与`Type`的值**Directory**，到目标路径的资源副本源目录。</span><span class="sxs-lookup"><span data-stu-id="563eb-177">When you specify a `SourcePath` and a `DestinationPath` with a `Type` value of **Directory**, the resource copies source directory to the destination path.</span></span> <span data-ttu-id="563eb-178">属性`Recurse`， `Force`，并`MatchSource`更改复制操作的类型执行，而`Credential`确定要用于访问源目录的帐户。</span><span class="sxs-lookup"><span data-stu-id="563eb-178">The properties `Recurse`, `Force`, and `MatchSource` change the type of copy operation performed, while `Credential` determines which account to use to access the source directory.</span></span>

### <a name="limitations"></a><span data-ttu-id="563eb-179">限制</span><span class="sxs-lookup"><span data-stu-id="563eb-179">Limitations</span></span>

<span data-ttu-id="563eb-180">如果指定的值`ReadOnly`有关`Attributes`属性一起`DestinationPath`，`Ensure = "Present"`将创建指定的路径时`Contents`会设置该文件的内容。</span><span class="sxs-lookup"><span data-stu-id="563eb-180">If you specified a value of `ReadOnly` for the `Attributes` property alongside a `DestinationPath`, `Ensure = "Present"` would create the path specified, while `Contents` would set the contents of the file.</span></span>  <span data-ttu-id="563eb-181">`Absent`状态操作会忽略`Attributes`属性完全，并删除任何文件在指定的路径。</span><span class="sxs-lookup"><span data-stu-id="563eb-181">An `Absent` state operation would ignore the `Attributes` property entirely, and remove any file at the specified path.</span></span>

## <a name="example"></a><span data-ttu-id="563eb-182">示例</span><span class="sxs-lookup"><span data-stu-id="563eb-182">Example</span></span>

<span data-ttu-id="563eb-183">下面的示例从请求服务器复制的目录和子目录到目标节点使用文件资源。</span><span class="sxs-lookup"><span data-stu-id="563eb-183">The following example copies a directory and its subdirectories from a pull server to a target node using the File Resource.</span></span> <span data-ttu-id="563eb-184">如果操作成功，日志资源向事件日志写入一条确认消息。</span><span class="sxs-lookup"><span data-stu-id="563eb-184">If the operation succeeds, the Log resource writes a confirmation message to the event log.</span></span>

<span data-ttu-id="563eb-185">源目录是 UNC 路径 (`\\PullServer\DemoSource`) 从请求服务器中共享。</span><span class="sxs-lookup"><span data-stu-id="563eb-185">The source directory is a UNC path (`\\PullServer\DemoSource`) shared from the Pull Server.</span></span> <span data-ttu-id="563eb-186">`Recurse`属性可确保所有子目录也会都复制。</span><span class="sxs-lookup"><span data-stu-id="563eb-186">The `Recurse` property ensures that all subdirectories are copied as well.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="563eb-187">默认情况下，目标节点上的 LCM 本地系统帐户的上下文中执行。</span><span class="sxs-lookup"><span data-stu-id="563eb-187">The LCM on the target Node executes in the context of the local system account by default.</span></span> <span data-ttu-id="563eb-188">若要授予访问权限**SourcePath**，目标节点的计算机帐户授予适当的权限。</span><span class="sxs-lookup"><span data-stu-id="563eb-188">To grant access to the **SourcePath**, give the target Node's computer account appropriate permissions.</span></span> <span data-ttu-id="563eb-189">**凭据**并**PSDSCRunAsCredential** (v5) 同时更改上下文 LCM 用来访问**SourcePath**。</span><span class="sxs-lookup"><span data-stu-id="563eb-189">The **Credential** and **PSDSCRunAsCredential** (v5) both change the context the LCM uses to access the **SourcePath**.</span></span> <span data-ttu-id="563eb-190">仍需要授予访问权限将使用的帐户访问**SourcePath**。</span><span class="sxs-lookup"><span data-stu-id="563eb-190">You still need to grant access to the account that will be used to access the **SourcePath**.</span></span>

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

<span data-ttu-id="563eb-191">有关更多在使用**凭据**在 DSC，请参阅[用户身份运行](../../../configurations/runAsUser.md)或[配置数据凭据](../../../configurations/configDataCredentials.md)。</span><span class="sxs-lookup"><span data-stu-id="563eb-191">For more on using **Credentials** in DSC see [Run As User](../../../configurations/runAsUser.md) or [Config Data Credentials](../../../configurations/configDataCredentials.md).</span></span>
