---
ms.date: 09/20/2019
keywords: dsc,powershell,配置,安装程序
title: 适用于 Linux nxFile 资源的 DSC
ms.openlocfilehash: be5f098d2fe1c8b354c07e6a8f882b8fdf00e1db
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954824"
---
# <a name="dsc-for-linux-nxfile-resource"></a><span data-ttu-id="16a9f-103">适用于 Linux nxFile 资源的 DSC</span><span class="sxs-lookup"><span data-stu-id="16a9f-103">DSC for Linux nxFile Resource</span></span>

<span data-ttu-id="16a9f-104">PowerShell Desired State Configuration (DSC) 中的 nxFile  资源提供了管理 Linux 节点上的文件和目录的机制。</span><span class="sxs-lookup"><span data-stu-id="16a9f-104">The **nxFile** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and directories on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="16a9f-105">语法</span><span class="sxs-lookup"><span data-stu-id="16a9f-105">Syntax</span></span>

```Syntax
nxFile <string> #ResourceName
{
    DestinationPath = <string>
    [ SourcePath = <string> ]
    [ Type = <string> { directory | file | link } ]
    [ Contents = <string> ]
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Recurse = <bool> ]
    [ Force = <bool> ]
    [ Links = <string> { follow | manage | ignore } ]
    [ Group = <string> ]
    [ Mode = <string> ]
    [ Owner = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="16a9f-106">“属性”</span><span class="sxs-lookup"><span data-stu-id="16a9f-106">Properties</span></span>

|<span data-ttu-id="16a9f-107">属性</span><span class="sxs-lookup"><span data-stu-id="16a9f-107">Property</span></span> |<span data-ttu-id="16a9f-108">说明</span><span class="sxs-lookup"><span data-stu-id="16a9f-108">Description</span></span> |
|---|---|
|<span data-ttu-id="16a9f-109">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="16a9f-109">DestinationPath</span></span> |<span data-ttu-id="16a9f-110">指定你想确保其中文件或目录状态的位置。</span><span class="sxs-lookup"><span data-stu-id="16a9f-110">Specifies the location where you want to ensure the state for a file or directory.</span></span> |
|<span data-ttu-id="16a9f-111">SourcePath</span><span class="sxs-lookup"><span data-stu-id="16a9f-111">SourcePath</span></span> |<span data-ttu-id="16a9f-112">指定要从其中复制文件或文件夹资源的路径。</span><span class="sxs-lookup"><span data-stu-id="16a9f-112">Specifies the path from which to copy the file or folder resource.</span></span> <span data-ttu-id="16a9f-113">此路径可以是本地路径，或者 `http/https/ftp` URL。</span><span class="sxs-lookup"><span data-stu-id="16a9f-113">This path may be a local path, or an `http/https/ftp` URL.</span></span> <span data-ttu-id="16a9f-114">只有在 **Type** 属性的值为 **file** 时，才支持远程 `http/https/ftp` URL。</span><span class="sxs-lookup"><span data-stu-id="16a9f-114">Remote `http/https/ftp` URLs are only supported when the value of the **Type** property is **file**.</span></span> |
|<span data-ttu-id="16a9f-115">类型</span><span class="sxs-lookup"><span data-stu-id="16a9f-115">Type</span></span> |<span data-ttu-id="16a9f-116">指定正在配置的资源是目录还是文件。</span><span class="sxs-lookup"><span data-stu-id="16a9f-116">Specifies whether the resource being configured is a directory or a file.</span></span> <span data-ttu-id="16a9f-117">将此属性设置为 **directory** 可指示该资源是一个目录。</span><span class="sxs-lookup"><span data-stu-id="16a9f-117">Set this property to **directory** to indicate that the resource is a directory.</span></span> <span data-ttu-id="16a9f-118">将其设置为 **file** 可指示该资源是一个文件。</span><span class="sxs-lookup"><span data-stu-id="16a9f-118">Set it to **file** to indicate that the resource is a file.</span></span> <span data-ttu-id="16a9f-119">默认值为 **file**。</span><span class="sxs-lookup"><span data-stu-id="16a9f-119">The default value is **file**.</span></span> |
|<span data-ttu-id="16a9f-120">目录</span><span class="sxs-lookup"><span data-stu-id="16a9f-120">Contents</span></span> |<span data-ttu-id="16a9f-121">指定文件的内容，例如特定字符串。</span><span class="sxs-lookup"><span data-stu-id="16a9f-121">Specifies the contents of a file, such as a particular string.</span></span> |
|<span data-ttu-id="16a9f-122">校验和</span><span class="sxs-lookup"><span data-stu-id="16a9f-122">Checksum</span></span> |<span data-ttu-id="16a9f-123">定义当确定两个文件是否相同时使用的类型。</span><span class="sxs-lookup"><span data-stu-id="16a9f-123">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="16a9f-124">如果未指定**校验和**，则只是文件或目录名用于比较。</span><span class="sxs-lookup"><span data-stu-id="16a9f-124">If **Checksum** is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="16a9f-125">值为：**ctime**、**mtime** 或 **md5**。</span><span class="sxs-lookup"><span data-stu-id="16a9f-125">Values are: **ctime**, **mtime**, or **md5**.</span></span> |
|<span data-ttu-id="16a9f-126">Recurse</span><span class="sxs-lookup"><span data-stu-id="16a9f-126">Recurse</span></span> |<span data-ttu-id="16a9f-127">指示是否包含子目录。</span><span class="sxs-lookup"><span data-stu-id="16a9f-127">Indicates if subdirectories are included.</span></span> <span data-ttu-id="16a9f-128">将此属性设置为 `$true` 以指示你想要包含子目录。</span><span class="sxs-lookup"><span data-stu-id="16a9f-128">Set this property to `$true` to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="16a9f-129">默认值为 `$false`。</span><span class="sxs-lookup"><span data-stu-id="16a9f-129">The default is `$false`.</span></span> <span data-ttu-id="16a9f-130">只有将 **Type** 属性设置为 **directory** 时，此属性才有效。</span><span class="sxs-lookup"><span data-stu-id="16a9f-130">This property is only valid when the **Type** property is set to **directory**.</span></span> |
|<span data-ttu-id="16a9f-131">Force</span><span class="sxs-lookup"><span data-stu-id="16a9f-131">Force</span></span> |<span data-ttu-id="16a9f-132">某些文件操作（如覆盖文件或删除不为空的目录）将导致错误。</span><span class="sxs-lookup"><span data-stu-id="16a9f-132">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="16a9f-133">使用 **Force** 属性覆盖此类错误。</span><span class="sxs-lookup"><span data-stu-id="16a9f-133">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="16a9f-134">默认值为 `$false`。</span><span class="sxs-lookup"><span data-stu-id="16a9f-134">The default value is `$false`.</span></span> |
|<span data-ttu-id="16a9f-135">链接</span><span class="sxs-lookup"><span data-stu-id="16a9f-135">Links</span></span> |<span data-ttu-id="16a9f-136">指定符号链接的所需行为。</span><span class="sxs-lookup"><span data-stu-id="16a9f-136">Specifies the desired behavior for symbolic links.</span></span> <span data-ttu-id="16a9f-137">将此属性设置为 **follow** 可跟随符号链接，并对链接目标进行操作。</span><span class="sxs-lookup"><span data-stu-id="16a9f-137">Set this property to **follow** to follow symbolic links and act on the links target.</span></span> <span data-ttu-id="16a9f-138">例如，复制文件而不是链接。</span><span class="sxs-lookup"><span data-stu-id="16a9f-138">For example, copy the file instead of the link.</span></span> <span data-ttu-id="16a9f-139">将此属性设置为 **manage** 可对此链接进行操作。</span><span class="sxs-lookup"><span data-stu-id="16a9f-139">Set this property to **manage** to act on the link.</span></span> <span data-ttu-id="16a9f-140">例如，复制链接本身。</span><span class="sxs-lookup"><span data-stu-id="16a9f-140">For example, copy the link itself.</span></span> <span data-ttu-id="16a9f-141">将此属性设置为 **ignore** 可忽略符号链接。</span><span class="sxs-lookup"><span data-stu-id="16a9f-141">Set this property to **ignore** to ignore symbolic links.</span></span> |
|<span data-ttu-id="16a9f-142">组</span><span class="sxs-lookup"><span data-stu-id="16a9f-142">Group</span></span> |<span data-ttu-id="16a9f-143">拥有对文件或目录的权限的 **Group** 的名称。</span><span class="sxs-lookup"><span data-stu-id="16a9f-143">The name of the **Group** to have permissions to the file or directory.</span></span> |
|<span data-ttu-id="16a9f-144">模式</span><span class="sxs-lookup"><span data-stu-id="16a9f-144">Mode</span></span> |<span data-ttu-id="16a9f-145">以八进制或符号表示法指定资源的所需权限。</span><span class="sxs-lookup"><span data-stu-id="16a9f-145">Specifies the desired permissions for the resource, in octal or symbolic notation.</span></span> <span data-ttu-id="16a9f-146">例如，**777** 或 **rwxrwxrwx**。</span><span class="sxs-lookup"><span data-stu-id="16a9f-146">For example, **777** or **rwxrwxrwx**.</span></span> <span data-ttu-id="16a9f-147">如果使用符号表示法，不需提供指示文件或目录的第一个字符。</span><span class="sxs-lookup"><span data-stu-id="16a9f-147">If using symbolic notation, do not provide the first character which indicates directory or file.</span></span> |
|<span data-ttu-id="16a9f-148">所有者</span><span class="sxs-lookup"><span data-stu-id="16a9f-148">Owner</span></span> |<span data-ttu-id="16a9f-149">拥有文件或目录的组的名称。</span><span class="sxs-lookup"><span data-stu-id="16a9f-149">The name of the group to own the file or directory.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="16a9f-150">公共属性</span><span class="sxs-lookup"><span data-stu-id="16a9f-150">Common properties</span></span>

|<span data-ttu-id="16a9f-151">属性</span><span class="sxs-lookup"><span data-stu-id="16a9f-151">Property</span></span> |<span data-ttu-id="16a9f-152">说明</span><span class="sxs-lookup"><span data-stu-id="16a9f-152">Description</span></span> |
|---|---|
|<span data-ttu-id="16a9f-153">DependsOn</span><span class="sxs-lookup"><span data-stu-id="16a9f-153">DependsOn</span></span> |<span data-ttu-id="16a9f-154">指示必须先运行其他资源的配置，再配置此资源。</span><span class="sxs-lookup"><span data-stu-id="16a9f-154">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="16a9f-155">例如，如果想要首先运行 ID 为 ResourceName、类型为 ResourceType 的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。</span><span class="sxs-lookup"><span data-stu-id="16a9f-155">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="16a9f-156">Ensure</span><span class="sxs-lookup"><span data-stu-id="16a9f-156">Ensure</span></span> |<span data-ttu-id="16a9f-157">确定是否要检查该文件是否存在。</span><span class="sxs-lookup"><span data-stu-id="16a9f-157">Determines whether to check if the file exists.</span></span> <span data-ttu-id="16a9f-158">将此属性设置为 **Present** 可确保文件存在。</span><span class="sxs-lookup"><span data-stu-id="16a9f-158">Set this property to **Present** to ensure the file exists.</span></span> <span data-ttu-id="16a9f-159">将其设置为 **Absent** 可确保文件不存在。</span><span class="sxs-lookup"><span data-stu-id="16a9f-159">Set it to **Absent** to ensure the file does not exist.</span></span> <span data-ttu-id="16a9f-160">默认值为 **Present**。</span><span class="sxs-lookup"><span data-stu-id="16a9f-160">The default value is **Present**.</span></span> |

## <a name="additional-information"></a><span data-ttu-id="16a9f-161">其他信息</span><span class="sxs-lookup"><span data-stu-id="16a9f-161">Additional Information</span></span>

<span data-ttu-id="16a9f-162">Linux 和 Windows 在文本文件中默认使用不同的换行符，这可能会导致在 Linux 计算机上使用 **nxFile** 配置某些文件时产生意外结果。</span><span class="sxs-lookup"><span data-stu-id="16a9f-162">Linux and Windows use different line break characters in text files by default, and this can cause unexpected results when configuring some files on a Linux computer with **nxFile**.</span></span> <span data-ttu-id="16a9f-163">有多种管理 Linux 文件内容，同时避免由意外换行符引起问题的方法：</span><span class="sxs-lookup"><span data-stu-id="16a9f-163">There are multiple ways to manage the content of a Linux file while avoiding issues caused by unexpected line break characters:</span></span>

1. <span data-ttu-id="16a9f-164">从远程源（http、https 或 ftp）中复制文件</span><span class="sxs-lookup"><span data-stu-id="16a9f-164">Copy the file from a remote source (http, https, or ftp)</span></span>

   <span data-ttu-id="16a9f-165">使用所需内容在 Linux 上创建一个文件，并将其暂存于能够访问将配置的节点的网页或 ftp 服务器上。</span><span class="sxs-lookup"><span data-stu-id="16a9f-165">Create a file on Linux with the desired contents, and stage it on a web or ftp server accessible the node(s) you will configure.</span></span> <span data-ttu-id="16a9f-166">然后使用该文件的 Web 或 ftp URL 在 **nxFile** 资源中定义 **SourcePath** 属性。</span><span class="sxs-lookup"><span data-stu-id="16a9f-166">Define the **SourcePath** property in the **nxFile** resource with the web or ftp URL to the file.</span></span>

   ```powershell
   Import-DSCResource -Module nx

   Node $Node
   {
      nxFile resolvConf
      {
         SourcePath = "http://10.185.85.11/conf/resolv.conf"
         DestinationPath = "/etc/resolv.conf"
         Mode = "644"
         Type = "file"
      }
   }
   ```

1. <span data-ttu-id="16a9f-167">设置 **$OFS** 属性以使用 Linux 换行符后，通过 [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) 来读取 PowerShell 脚本的内容。</span><span class="sxs-lookup"><span data-stu-id="16a9f-167">Read the file contents in the PowerShell script with [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) after setting the **$OFS** property to use the Linux line-break character.</span></span>

   ```powershell
   Import-DSCResource -Module nx

   Node $Node
   {
      $OFS = "`n"
      $Contents = Get-Content C:\temp\resolv.conf

      nxFile resolvConf
      {
         DestinationPath = "/etc/resolv.conf"
         Mode = "644"
         Type = "file"
         Contents = "$Contents"
      }
   }
   ```

1. <span data-ttu-id="16a9f-168">使用 PowerShell 函数以将 Windows 换行符替换为 Linux 换行符。</span><span class="sxs-lookup"><span data-stu-id="16a9f-168">Use a PowerShell function to replace Windows line breaks with Linux line-break characters.</span></span>

   ```powershell
   Function LinuxString($inputStr){
      $outputStr = $inputStr.Replace("`r`n","`n")
      $outputStr += "`n"
      Return $outputStr
   }

   Import-DSCResource -Module nx

   Node $Node
   {
      $Contents = @'
   search contoso.com
   domain contoso.com
   nameserver 10.185.85.11
   '@
       $Contents = LinuxString $Contents

      nxFile resolvConf
      {
         DestinationPath = "/etc/resolv.conf"
         Mode = "644"
         Type = "file"
         Contents = $Contents
      }
   }
   ```

## <a name="example"></a><span data-ttu-id="16a9f-169">示例</span><span class="sxs-lookup"><span data-stu-id="16a9f-169">Example</span></span>

<span data-ttu-id="16a9f-170">以下示例可确保目录 `/opt/mydir` 存在，并且具有指定内容的文件存在于此目录中。</span><span class="sxs-lookup"><span data-stu-id="16a9f-170">The following example ensures that the directory `/opt/mydir` exists, and that a file with specified contents exists this directory.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node {
    nxFile DirectoryExample
    {
        Ensure = "Present"
        DestinationPath = "/opt/mydir"
        Type = "Directory"
    }

    nxFile FileExample
    {
        Ensure = "Present"
        Destinationpath = "/opt/mydir/myfile"
        Contents=@"
#!/bin/bash`necho "hello world"`n
"@
        Mode = "755"
        DependsOn = "[nxFile]DirectoryExample"
    }
}
```