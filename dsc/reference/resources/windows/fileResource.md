---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: DSC File 资源
ms.openlocfilehash: b5bc2c305b8cfccbd044274811df631264a24279
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077324"
---
# <a name="dsc-file-resource"></a><span data-ttu-id="f1cda-103">DSC File 资源</span><span class="sxs-lookup"><span data-stu-id="f1cda-103">DSC File Resource</span></span>

> <span data-ttu-id="f1cda-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f1cda-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="f1cda-105">Windows PowerShell Desired State Configuration (DSC) 中的 File 资源提供了管理目标节点上的文件和文件夹的机制。</span><span class="sxs-lookup"><span data-stu-id="f1cda-105">The File resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and folders on the target node.</span></span> <span data-ttu-id="f1cda-106">目标节点必须能够访问 DestinationPath 和 SourcePath。</span><span class="sxs-lookup"><span data-stu-id="f1cda-106">The **DestinationPath** and **SourcePath** must both be accessible by the target Node.</span></span>

## <a name="syntax"></a><span data-ttu-id="f1cda-107">语法</span><span class="sxs-lookup"><span data-stu-id="f1cda-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="f1cda-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="f1cda-108">Properties</span></span>

|<span data-ttu-id="f1cda-109">属性</span><span class="sxs-lookup"><span data-stu-id="f1cda-109">Property</span></span>       |<span data-ttu-id="f1cda-110">说明</span><span class="sxs-lookup"><span data-stu-id="f1cda-110">Description</span></span>                                                                   |<span data-ttu-id="f1cda-111">必需</span><span class="sxs-lookup"><span data-stu-id="f1cda-111">Required</span></span>|<span data-ttu-id="f1cda-112">默认值</span><span class="sxs-lookup"><span data-stu-id="f1cda-112">Default</span></span>|
|---------------|------------------------------------------------------------------------------|--------|-------|
|<span data-ttu-id="f1cda-113">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="f1cda-113">DestinationPath</span></span>|<span data-ttu-id="f1cda-114">想要确保目标节点上的位置是 `Present` 或 `Absent`。</span><span class="sxs-lookup"><span data-stu-id="f1cda-114">The location, on the target node, you want to ensure is `Present` or `Absent`.</span></span>|<span data-ttu-id="f1cda-115">是</span><span class="sxs-lookup"><span data-stu-id="f1cda-115">Yes</span></span>|<span data-ttu-id="f1cda-116">否</span><span class="sxs-lookup"><span data-stu-id="f1cda-116">No</span></span>|
|<span data-ttu-id="f1cda-117">属性</span><span class="sxs-lookup"><span data-stu-id="f1cda-117">Attributes</span></span>     |<span data-ttu-id="f1cda-118">目标文件或目录的特性的所需状态。</span><span class="sxs-lookup"><span data-stu-id="f1cda-118">The desired state of the attributes for the targeted file or directory.</span></span> <span data-ttu-id="f1cda-119">有效值包括 Archive、Hidden、ReadOnly 和 System。</span><span class="sxs-lookup"><span data-stu-id="f1cda-119">Valid values are **Archive**, **Hidden**, **ReadOnly**, and **System**.</span></span>|<span data-ttu-id="f1cda-120">否</span><span class="sxs-lookup"><span data-stu-id="f1cda-120">No</span></span>|<span data-ttu-id="f1cda-121">无</span><span class="sxs-lookup"><span data-stu-id="f1cda-121">None</span></span>|
|<span data-ttu-id="f1cda-122">校验和</span><span class="sxs-lookup"><span data-stu-id="f1cda-122">Checksum</span></span>      |<span data-ttu-id="f1cda-123">当确定两个文件是否相同时使用的校验和类型。</span><span class="sxs-lookup"><span data-stu-id="f1cda-123">The checksum type to use when determining whether two files are the same.</span></span> <span data-ttu-id="f1cda-124">有效值包括：SHA-1、SHA-256、SHA-512、createdDate 和 modifiedDate。</span><span class="sxs-lookup"><span data-stu-id="f1cda-124">Valid values include: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.</span></span>|<span data-ttu-id="f1cda-125">否</span><span class="sxs-lookup"><span data-stu-id="f1cda-125">No</span></span>|<span data-ttu-id="f1cda-126">只比较文件或目录名。</span><span class="sxs-lookup"><span data-stu-id="f1cda-126">Only the file or directory name is compared.</span></span>|
|<span data-ttu-id="f1cda-127">目录</span><span class="sxs-lookup"><span data-stu-id="f1cda-127">Contents</span></span>       |<span data-ttu-id="f1cda-128">仅当与 `File` 类型一起使用时才有效。</span><span class="sxs-lookup"><span data-stu-id="f1cda-128">Only valid when used with `File` type.</span></span> <span data-ttu-id="f1cda-129">指示要确保的内容是目标文件中的 `Present` 或 `Absent`。</span><span class="sxs-lookup"><span data-stu-id="f1cda-129">Indicates the contents to Ensure are `Present` or `Absent` from the targeted file.</span></span> |<span data-ttu-id="f1cda-130">否</span><span class="sxs-lookup"><span data-stu-id="f1cda-130">No</span></span>|<span data-ttu-id="f1cda-131">无</span><span class="sxs-lookup"><span data-stu-id="f1cda-131">None</span></span>|
|<span data-ttu-id="f1cda-132">凭据</span><span class="sxs-lookup"><span data-stu-id="f1cda-132">Credential</span></span>     |<span data-ttu-id="f1cda-133">访问资源（例如源文件）所需的凭据。</span><span class="sxs-lookup"><span data-stu-id="f1cda-133">The credentials that are required to access resources, such as source files.</span></span>|<span data-ttu-id="f1cda-134">否</span><span class="sxs-lookup"><span data-stu-id="f1cda-134">No</span></span>|<span data-ttu-id="f1cda-135">目标节点的计算机帐户。</span><span class="sxs-lookup"><span data-stu-id="f1cda-135">The target node's Computer Account.</span></span> <span data-ttu-id="f1cda-136">（见备注）</span><span class="sxs-lookup"><span data-stu-id="f1cda-136">(*see note*)</span></span>|
|<span data-ttu-id="f1cda-137">Ensure</span><span class="sxs-lookup"><span data-stu-id="f1cda-137">Ensure</span></span>         |<span data-ttu-id="f1cda-138">目标文件或目录的所需状态。</span><span class="sxs-lookup"><span data-stu-id="f1cda-138">The desired state of the target file or directory.</span></span> |<span data-ttu-id="f1cda-139">否</span><span class="sxs-lookup"><span data-stu-id="f1cda-139">No</span></span>|<span data-ttu-id="f1cda-140">**存在**</span><span class="sxs-lookup"><span data-stu-id="f1cda-140">**Present**</span></span>|
|<span data-ttu-id="f1cda-141">Force</span><span class="sxs-lookup"><span data-stu-id="f1cda-141">Force</span></span>          |<span data-ttu-id="f1cda-142">覆盖将导致错误的访问操作（如覆盖文件或删除不为空的目录）。</span><span class="sxs-lookup"><span data-stu-id="f1cda-142">Overrides access operations that would result in an error (such as overwriting a file or deleting a directory that is not empty).</span></span>|<span data-ttu-id="f1cda-143">否</span><span class="sxs-lookup"><span data-stu-id="f1cda-143">No</span></span>|`$false`|
|<span data-ttu-id="f1cda-144">Recurse</span><span class="sxs-lookup"><span data-stu-id="f1cda-144">Recurse</span></span>        |<span data-ttu-id="f1cda-145">仅当与 `Directory` 类型一起使用时才有效。</span><span class="sxs-lookup"><span data-stu-id="f1cda-145">Only valid when used with `Directory` type.</span></span> <span data-ttu-id="f1cda-146">以递归方式对所有子目录执行状态操作。</span><span class="sxs-lookup"><span data-stu-id="f1cda-146">Performs the state operation recursively to all subdirectories.</span></span>|<span data-ttu-id="f1cda-147">否</span><span class="sxs-lookup"><span data-stu-id="f1cda-147">No</span></span>|`$false`|
|<span data-ttu-id="f1cda-148">DependsOn</span><span class="sxs-lookup"><span data-stu-id="f1cda-148">DependsOn</span></span>      |<span data-ttu-id="f1cda-149">设置指定资源的依赖项。</span><span class="sxs-lookup"><span data-stu-id="f1cda-149">Sets a dependency on specified resource(s).</span></span> <span data-ttu-id="f1cda-150">此资源仅在成功执行任何从属资源之后执行。</span><span class="sxs-lookup"><span data-stu-id="f1cda-150">This resource will only execute after successful execution of any dependent resources.</span></span> <span data-ttu-id="f1cda-151">可以使用语法 `"[ResourceType]ResourceName"` 指定从属资源。</span><span class="sxs-lookup"><span data-stu-id="f1cda-151">You can specify dependent resources using the syntax `"[ResourceType]ResourceName"`.</span></span> <span data-ttu-id="f1cda-152">请参阅 [about_DependsOn](../../../configurations/resource-depends-on.md)</span><span class="sxs-lookup"><span data-stu-id="f1cda-152">See [about_DependsOn](../../../configurations/resource-depends-on.md)</span></span>|<span data-ttu-id="f1cda-153">否</span><span class="sxs-lookup"><span data-stu-id="f1cda-153">No</span></span>|<span data-ttu-id="f1cda-154">无</span><span class="sxs-lookup"><span data-stu-id="f1cda-154">None</span></span>|
|<span data-ttu-id="f1cda-155">SourcePath</span><span class="sxs-lookup"><span data-stu-id="f1cda-155">SourcePath</span></span>     |<span data-ttu-id="f1cda-156">要从其中复制文件或文件夹资源的路径。</span><span class="sxs-lookup"><span data-stu-id="f1cda-156">The path from which to copy the file or folder resource.</span></span>|<span data-ttu-id="f1cda-157">否</span><span class="sxs-lookup"><span data-stu-id="f1cda-157">No</span></span>|<span data-ttu-id="f1cda-158">无</span><span class="sxs-lookup"><span data-stu-id="f1cda-158">None</span></span>|
|<span data-ttu-id="f1cda-159">类型</span><span class="sxs-lookup"><span data-stu-id="f1cda-159">Type</span></span>           |<span data-ttu-id="f1cda-160">正在配置的资源的类型。</span><span class="sxs-lookup"><span data-stu-id="f1cda-160">The type of resource being configured.</span></span> <span data-ttu-id="f1cda-161">有效值为 `Directory` 和 `File`。</span><span class="sxs-lookup"><span data-stu-id="f1cda-161">Valid values are `Directory` and `File`.</span></span>|<span data-ttu-id="f1cda-162">否</span><span class="sxs-lookup"><span data-stu-id="f1cda-162">No</span></span>|`File`|
|<span data-ttu-id="f1cda-163">MatchSource</span><span class="sxs-lookup"><span data-stu-id="f1cda-163">MatchSource</span></span>    |<span data-ttu-id="f1cda-164">确定资源是否应监视初始复制之后添加到源目录的新文件。</span><span class="sxs-lookup"><span data-stu-id="f1cda-164">Determines if the resource should monitor for new files added to the source directory after the initial copy.</span></span> <span data-ttu-id="f1cda-165">`$true` 值表示，在初始复制之后，任何新的源文件都应复制到目标位置。</span><span class="sxs-lookup"><span data-stu-id="f1cda-165">A value of `$true` indicates that, after the initial copy, any new source files should be copied to the destination.</span></span> <span data-ttu-id="f1cda-166">如果设置为 `$False`，资源将缓存源目录的内容，并忽略初始复制之后添加的任何文件。</span><span class="sxs-lookup"><span data-stu-id="f1cda-166">If set to `$False`, the resource caches the contents of the source directory and ignores any files added after the initial copy.</span></span>|<span data-ttu-id="f1cda-167">否</span><span class="sxs-lookup"><span data-stu-id="f1cda-167">No</span></span>|`$false`|

> [!WARNING]
> <span data-ttu-id="f1cda-168">如果没有为 `Credential` 或 `PSRunAsCredential` 指定值 (PS V.5)，资源将使用目标节点的计算机帐户访问 `SourcePath`。</span><span class="sxs-lookup"><span data-stu-id="f1cda-168">If you do not specify a value for `Credential` or `PSRunAsCredential` (PS V.5), the resource will use the computer account of the target node to access the `SourcePath`.</span></span>  <span data-ttu-id="f1cda-169">如果 `SourcePath` 是 UNC 共享，这可能导致“拒绝访问”错误。</span><span class="sxs-lookup"><span data-stu-id="f1cda-169">When the `SourcePath` is a UNC share, this could result in an "Access Denied" error.</span></span> <span data-ttu-id="f1cda-170">请确保相应地设置权限，或者使用 `Credential` 或 `PSRunAsCredential` 属性指定应该使用的帐户。</span><span class="sxs-lookup"><span data-stu-id="f1cda-170">Please ensure your permissions are set accordingly, or use the `Credential` or `PSRunAsCredential` properties to specify the account that should be used.</span></span>

## <a name="present-vs-absent"></a><span data-ttu-id="f1cda-171">存在与不存在</span><span class="sxs-lookup"><span data-stu-id="f1cda-171">Present vs. Absent</span></span>

<span data-ttu-id="f1cda-172">每个 DSC 资源根据你为 `Ensure` 属性指定的值执行不同的操作。</span><span class="sxs-lookup"><span data-stu-id="f1cda-172">Each DSC resource performs different operations based on the value you specify for the `Ensure` property.</span></span> <span data-ttu-id="f1cda-173">为上述属性指定的值决定执行的状态操作。</span><span class="sxs-lookup"><span data-stu-id="f1cda-173">The values you specify for the above properties determines the state operation performed.</span></span>

### <a name="existence"></a><span data-ttu-id="f1cda-174">存在</span><span class="sxs-lookup"><span data-stu-id="f1cda-174">Existence</span></span>

<span data-ttu-id="f1cda-175">仅指定 `DestinationPath` 时，资源将确保该路径存在 (`Present`) 或不存在 (`Absent`)。</span><span class="sxs-lookup"><span data-stu-id="f1cda-175">When you only specify a `DestinationPath`, the resource ensures that the path exists (`Present`) or does not exist (`Absent`).</span></span>

### <a name="copy-operations"></a><span data-ttu-id="f1cda-176">复制操作</span><span class="sxs-lookup"><span data-stu-id="f1cda-176">Copy Operations</span></span>

<span data-ttu-id="f1cda-177">当使用目录的 `Type` 值指定 `SourcePath` 和 `DestinationPath` 时，资源会将源目录复制到目标路径。</span><span class="sxs-lookup"><span data-stu-id="f1cda-177">When you specify a `SourcePath` and a `DestinationPath` with a `Type` value of **Directory**, the resource copies source directory to the destination path.</span></span> <span data-ttu-id="f1cda-178">属性 `Recurse`、`Force` 和 `MatchSource` 更改所执行的复制操作的类型，而 `Credential` 决定使用哪个帐户来访问源目录。</span><span class="sxs-lookup"><span data-stu-id="f1cda-178">The properties `Recurse`, `Force`, and `MatchSource` change the type of copy operation performed, while `Credential` determines which account to use to access the source directory.</span></span>

### <a name="limitations"></a><span data-ttu-id="f1cda-179">限制</span><span class="sxs-lookup"><span data-stu-id="f1cda-179">Limitations</span></span>

<span data-ttu-id="f1cda-180">如果在 `DestinationPath` 旁边为 `Attributes` 属性指定了 `ReadOnly` 值，`Ensure = "Present"` 将创建指定的路径，而 `Contents` 将设置文件的内容。</span><span class="sxs-lookup"><span data-stu-id="f1cda-180">If you specified a value of `ReadOnly` for the `Attributes` property alongside a `DestinationPath`, `Ensure = "Present"` would create the path specified, while `Contents` would set the contents of the file.</span></span>  <span data-ttu-id="f1cda-181">`Absent` 状态操作将完全忽略 `Attributes` 属性，并删除指定路径上的任何文件。</span><span class="sxs-lookup"><span data-stu-id="f1cda-181">An `Absent` state operation would ignore the `Attributes` property entirely, and remove any file at the specified path.</span></span>

## <a name="example"></a><span data-ttu-id="f1cda-182">示例</span><span class="sxs-lookup"><span data-stu-id="f1cda-182">Example</span></span>

<span data-ttu-id="f1cda-183">下面的示例使用文件资源将目录及其子目录从拉取服务器复制到目标节点。</span><span class="sxs-lookup"><span data-stu-id="f1cda-183">The following example copies a directory and its subdirectories from a pull server to a target node using the File Resource.</span></span> <span data-ttu-id="f1cda-184">如果操作成功，日志资源会向事件日志写入一条确认消息。</span><span class="sxs-lookup"><span data-stu-id="f1cda-184">If the operation succeeds, the Log resource writes a confirmation message to the event log.</span></span>

<span data-ttu-id="f1cda-185">源目录是从拉取服务器共享的 UNC 路径 (`\\PullServer\DemoSource`)。</span><span class="sxs-lookup"><span data-stu-id="f1cda-185">The source directory is a UNC path (`\\PullServer\DemoSource`) shared from the Pull Server.</span></span> <span data-ttu-id="f1cda-186">`Recurse` 属性还确保复制所有子目录。</span><span class="sxs-lookup"><span data-stu-id="f1cda-186">The `Recurse` property ensures that all subdirectories are copied as well.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f1cda-187">默认情况下，目标节点上的 LCM 在本地系统帐户的上下文中执行。</span><span class="sxs-lookup"><span data-stu-id="f1cda-187">The LCM on the target Node executes in the context of the local system account by default.</span></span> <span data-ttu-id="f1cda-188">要授予对 SourcePath 的访问权限，请为目标节点的计算机帐户授予适当权限。</span><span class="sxs-lookup"><span data-stu-id="f1cda-188">To grant access to the **SourcePath**, give the target Node's computer account appropriate permissions.</span></span> <span data-ttu-id="f1cda-189">Credential 和 PSDSCRunAsCredential (v5) 都更改了 LCM 用于访问 SourcePath 的上下文。</span><span class="sxs-lookup"><span data-stu-id="f1cda-189">The **Credential** and **PSDSCRunAsCredential** (v5) both change the context the LCM uses to access the **SourcePath**.</span></span> <span data-ttu-id="f1cda-190">仍需要向将用于访问 SourcePath 的帐户授予访问权限。</span><span class="sxs-lookup"><span data-stu-id="f1cda-190">You still need to grant access to the account that will be used to access the **SourcePath**.</span></span>

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

<span data-ttu-id="f1cda-191">有关在 DSC 中使用 Credentials 的详细信息，请参阅[以用户身份运行](../../../configurations/runAsUser.md)或[配置数据凭据](../../../configurations/configDataCredentials.md)。</span><span class="sxs-lookup"><span data-stu-id="f1cda-191">For more on using **Credentials** in DSC see [Run As User](../../../configurations/runAsUser.md) or [Config Data Credentials](../../../configurations/configDataCredentials.md).</span></span>
