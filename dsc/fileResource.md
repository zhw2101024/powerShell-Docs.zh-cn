---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: "dsc,powershell,配置,安装程序"
title: "DSC File 资源"
ms.openlocfilehash: 54d01bf0769eeed0354606eb3543973b0f850a6f
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-file-resource"></a><span data-ttu-id="313db-103">DSC File 资源</span><span class="sxs-lookup"><span data-stu-id="313db-103">DSC File Resource</span></span>

> <span data-ttu-id="313db-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="313db-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="313db-105">Windows PowerShell Desired State Configuration (DSC) 中的 File 资源提供了管理目标节点上的文件和文件夹的机制。</span><span class="sxs-lookup"><span data-stu-id="313db-105">The File resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and folders on the target node.</span></span>

><span data-ttu-id="313db-106">**注意：**如果 **MatchSource** 属性设为 **$false**（这是默认值），那么第一次应用配置时将缓存要复制的内容。</span><span class="sxs-lookup"><span data-stu-id="313db-106">**Note:** If the **MatchSource** property is set to **$false** (which is the default value), the contents to be copied are cached the first time the configuration is applied.</span></span> 
><span data-ttu-id="313db-107">配置的后续应用将不再检查由 **SourcePath** 指定的路径中的已更新文件和/或文件夹。</span><span class="sxs-lookup"><span data-stu-id="313db-107">Subsequent applications of the configuration will not check for updated files and/or folders in the path specified by **SourcePath**.</span></span> <span data-ttu-id="313db-108">如果想要每次应用配置时检查 **SourcePath** 中文件和/或文件夹的更新，请将 **MatchSource** 设为 **$true**。</span><span class="sxs-lookup"><span data-stu-id="313db-108">If you want to check for updates to the files and/or folders in **SourcePath** every time the configuration is applied, set **MatchSource** to **$true**.</span></span> 

## <a name="syntax"></a><span data-ttu-id="313db-109">语法</span><span class="sxs-lookup"><span data-stu-id="313db-109">Syntax</span></span>
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

## <a name="properties"></a><span data-ttu-id="313db-110">“属性”</span><span class="sxs-lookup"><span data-stu-id="313db-110">Properties</span></span>

|  <span data-ttu-id="313db-111">属性</span><span class="sxs-lookup"><span data-stu-id="313db-111">Property</span></span>  |  <span data-ttu-id="313db-112">说明</span><span class="sxs-lookup"><span data-stu-id="313db-112">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="313db-113">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="313db-113">DestinationPath</span></span>| <span data-ttu-id="313db-114">指示你想确保其中文件或目录状态的位置。</span><span class="sxs-lookup"><span data-stu-id="313db-114">Indicates the location where you want to ensure the state for a file or directory.</span></span>| 
| <span data-ttu-id="313db-115">属性</span><span class="sxs-lookup"><span data-stu-id="313db-115">Attributes</span></span>| <span data-ttu-id="313db-116">指定目标文件或目录的特性的所需状态。</span><span class="sxs-lookup"><span data-stu-id="313db-116">Specifies the desired state of the attributes for the targeted file or directory.</span></span>| 
| <span data-ttu-id="313db-117">校验和</span><span class="sxs-lookup"><span data-stu-id="313db-117">Checksum</span></span>| <span data-ttu-id="313db-118">指示当确定两个文件是否相同时使用的校验和类型。</span><span class="sxs-lookup"><span data-stu-id="313db-118">Indicates the checksum type to use when determining whether two files are the same.</span></span> <span data-ttu-id="313db-119">如果未指定__校验和__，则只是文件或目录名用于比较。</span><span class="sxs-lookup"><span data-stu-id="313db-119">If __Checksum__ is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="313db-120">有效值包括：SHA-1、SHA-256、SHA-512、createdDate、modifiedDate。</span><span class="sxs-lookup"><span data-stu-id="313db-120">Valid values include: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.</span></span>| 
| <span data-ttu-id="313db-121">目录</span><span class="sxs-lookup"><span data-stu-id="313db-121">Contents</span></span>| <span data-ttu-id="313db-122">指定文件的内容，例如特定字符串。</span><span class="sxs-lookup"><span data-stu-id="313db-122">Specifies the contents of a file, such as a particular string.</span></span>| 
| <span data-ttu-id="313db-123">凭据</span><span class="sxs-lookup"><span data-stu-id="313db-123">Credential</span></span>| <span data-ttu-id="313db-124">指示需要进行访问时访问资源（例如源文件）所需的凭据。</span><span class="sxs-lookup"><span data-stu-id="313db-124">Indicates the credentials that are required to access resources, such as source files, if such access is required.</span></span>| 
| <span data-ttu-id="313db-125">Ensure</span><span class="sxs-lookup"><span data-stu-id="313db-125">Ensure</span></span>| <span data-ttu-id="313db-126">指示文件或目录是否存在。</span><span class="sxs-lookup"><span data-stu-id="313db-126">Indicates if the file or directory exists.</span></span> <span data-ttu-id="313db-127">将此属性设置为“Absent”可确保该文件或目录不存在。</span><span class="sxs-lookup"><span data-stu-id="313db-127">Set this property to "Absent" to ensure that the file or directory does not exist.</span></span> <span data-ttu-id="313db-128">将其设置为“Present”可确保该文件或目录确实存在。</span><span class="sxs-lookup"><span data-stu-id="313db-128">Set it to "Present" to ensure that the file or directory does exist.</span></span> <span data-ttu-id="313db-129">默认值为“Present”。</span><span class="sxs-lookup"><span data-stu-id="313db-129">The default is "Present".</span></span>| 
| <span data-ttu-id="313db-130">Force</span><span class="sxs-lookup"><span data-stu-id="313db-130">Force</span></span>| <span data-ttu-id="313db-131">某些文件操作（如覆盖文件或删除不为空的目录）将导致错误。</span><span class="sxs-lookup"><span data-stu-id="313db-131">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="313db-132">使用 Force 属性覆盖此类错误。</span><span class="sxs-lookup"><span data-stu-id="313db-132">Using the Force property overrides such errors.</span></span> <span data-ttu-id="313db-133">默认值为 __$false__。</span><span class="sxs-lookup"><span data-stu-id="313db-133">The default value is __$false__.</span></span>| 
| <span data-ttu-id="313db-134">Recurse</span><span class="sxs-lookup"><span data-stu-id="313db-134">Recurse</span></span>| <span data-ttu-id="313db-135">指示是否包含子目录。</span><span class="sxs-lookup"><span data-stu-id="313db-135">Indicates if subdirectories are included.</span></span> <span data-ttu-id="313db-136">将此属性设置为 __$true__ 以指示你想要包含子目录。</span><span class="sxs-lookup"><span data-stu-id="313db-136">Set this property to __$true__ to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="313db-137">默认值为 __$false__。</span><span class="sxs-lookup"><span data-stu-id="313db-137">The default is __$false__.</span></span> <span data-ttu-id="313db-138">**注意：**只有将 Type 属性设置为 Directory 时，此属性才有效。</span><span class="sxs-lookup"><span data-stu-id="313db-138">**Note**: This property is only valid when the Type property is set to Directory.</span></span>| 
| <span data-ttu-id="313db-139">DependsOn</span><span class="sxs-lookup"><span data-stu-id="313db-139">DependsOn</span></span> | <span data-ttu-id="313db-140">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="313db-140">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="313db-141">例如，如果你想要首先运行 ID 为 __ResourceName__、类型为 __ResourceType__ 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="313db-141">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 
| <span data-ttu-id="313db-142">SourcePath</span><span class="sxs-lookup"><span data-stu-id="313db-142">SourcePath</span></span>| <span data-ttu-id="313db-143">指示要从其中复制文件或文件夹资源的路径。</span><span class="sxs-lookup"><span data-stu-id="313db-143">Indicates the path from which to copy the file or folder resource.</span></span>| 
| <span data-ttu-id="313db-144">类型</span><span class="sxs-lookup"><span data-stu-id="313db-144">Type</span></span>| <span data-ttu-id="313db-145">指示正在配置的资源是目录还是文件。</span><span class="sxs-lookup"><span data-stu-id="313db-145">Indicates if the resource being configured is a directory or a file.</span></span> <span data-ttu-id="313db-146">将此属性设置为“Directory”可指示该资源是一个目录。</span><span class="sxs-lookup"><span data-stu-id="313db-146">Set this property to "Directory" to indicate that the resource is a directory.</span></span> <span data-ttu-id="313db-147">将其设置为“File”可指示该资源是一个文件。</span><span class="sxs-lookup"><span data-stu-id="313db-147">Set it to "File" to indicate that the resource is a file.</span></span> <span data-ttu-id="313db-148">默认值为“File”。</span><span class="sxs-lookup"><span data-stu-id="313db-148">The default value is “File”.</span></span>| 
| <span data-ttu-id="313db-149">MatchSource</span><span class="sxs-lookup"><span data-stu-id="313db-149">MatchSource</span></span>| <span data-ttu-id="313db-150">如果设置的默认值为 __$false__，则将在首次运用此配置时将源中的任何文件（如文件 A、B 和 C）添加到目标中。</span><span class="sxs-lookup"><span data-stu-id="313db-150">If set to the default value of __$false__, then any files on the source (say, files A, B, and C) will be added to the destination the first time the configuration is applied.</span></span> <span data-ttu-id="313db-151">如果已添加新文件 (D) 到源中，则即使稍后重新应用配置也不会将其添加到目标中。</span><span class="sxs-lookup"><span data-stu-id="313db-151">If a new file (D) is added to the source, it will not be added to the destination, even when the configuration is re-applied later.</span></span> <span data-ttu-id="313db-152">如果值为 __$true__，则每当应用此配置时，在源上随后找到的新文件（如本示例中的文件 D）将会被添加到目标中。</span><span class="sxs-lookup"><span data-stu-id="313db-152">If the value is __$true__, then each time the configuration is applied, new files subsequently found on the source (such as file D in this example) are added to the destination.</span></span> <span data-ttu-id="313db-153">默认值为 **$false**。</span><span class="sxs-lookup"><span data-stu-id="313db-153">The default value is **$false**.</span></span>| 

## <a name="example"></a><span data-ttu-id="313db-154">示例</span><span class="sxs-lookup"><span data-stu-id="313db-154">Example</span></span>

<span data-ttu-id="313db-155">以下示例表明了如何使用 File 资源以确保源计算机（如“请求”服务器）上具有路径 `C:\Users\Public\Documents\DSCDemo\DemoSource` 的目录（以及所有子目录）也存在于目标节点上。</span><span class="sxs-lookup"><span data-stu-id="313db-155">The following example shows how to use the File resource to ensure that a directory with the path `C:\Users\Public\Documents\DSCDemo\DemoSource` on a source computer (such as the “pull” server) is also present (along with all subdirectories) on the target node.</span></span> <span data-ttu-id="313db-156">此外，完成时也会将确认消息写入日志，并包含用于确保记录操作前运行文件检查操作的声明。</span><span class="sxs-lookup"><span data-stu-id="313db-156">It also writes a confirmatory message to the log when complete and includes a statement to ensure that the file-checking operation runs prior to the logging operation.</span></span>

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present"  # You can also set Ensure to "Absent"
            Type = "Directory" # Default is "File".
            Recurse = $true # Ensure presence of subdirectories, too
            SourcePath = "C:\Users\Public\Documents\DSCDemo\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"    
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # This means run "DirectoryCopy" first.
        }
    }
}
```

