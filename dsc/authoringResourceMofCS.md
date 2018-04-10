---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,配置,安装程序
title: 在 C# 中创作 DSC 资源
ms.openlocfilehash: 112b2ae3eb7ecbccc4ae04cd71e06ea43f5e9249
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2018
---
# <a name="authoring-a-dsc-resource-in-c"></a><span data-ttu-id="26343-103">在 C# 中创作 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="26343-103">Authoring a DSC resource in C#</span></span>

> <span data-ttu-id="26343-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="26343-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="26343-105">通常在 PowerShell 脚本中实现 Windows PowerShell Desired State Configuration (DSC) 自定义资源。</span><span class="sxs-lookup"><span data-stu-id="26343-105">Typically, a Windows PowerShell Desired State Configuration (DSC) custom resource is implemented in a PowerShell script.</span></span> <span data-ttu-id="26343-106">但是你也可以通过在 C# 中编写 cmdlet 来实现 DSC 自定义资源的功能。</span><span class="sxs-lookup"><span data-stu-id="26343-106">However, you can also implement the functionality of a DSC custom resource by writing cmdlets in C#.</span></span> <span data-ttu-id="26343-107">有关在 C# 中编写 cmdlet 的介绍，请参阅[编写 Windows PowerShell Cmdlet](https://technet.microsoft.com/library/dd878294.aspx)。</span><span class="sxs-lookup"><span data-stu-id="26343-107">For an introduction on writing cmdlets in C#, see [Writing a Windows PowerShell Cmdlet](https://technet.microsoft.com/library/dd878294.aspx).</span></span>

<span data-ttu-id="26343-108">除在 C# 中用 cmdlet 实现资源外，创建 MOF 架构、创建文件夹结构、导入和使用自定义 DSC 资源的过程都与[使用 MOF 编写自定义 DSC 资源](authoringResourceMOF.md)中介绍的相同。</span><span class="sxs-lookup"><span data-stu-id="26343-108">Aside from implementing the resource in C# as cmdlets, the process of creating the MOF schema, creating the folder structure, importing and using your custom DSC resource are the same as described in [Writing a custom DSC resource with MOF](authoringResourceMOF.md).</span></span>

## <a name="writing-a-cmdlet-based-resource"></a><span data-ttu-id="26343-109">编写基于 cmdlet 的资源</span><span class="sxs-lookup"><span data-stu-id="26343-109">Writing a cmdlet-based resource</span></span>
<span data-ttu-id="26343-110">此示例中，我们将实现一个管理文本文件及其内容的简单资源。</span><span class="sxs-lookup"><span data-stu-id="26343-110">For this example, we will implement a simple resource that manages a text file and its contents.</span></span>

### <a name="writing-the-mof-schema"></a><span data-ttu-id="26343-111">编写 MOF 架构</span><span class="sxs-lookup"><span data-stu-id="26343-111">Writing the MOF schema</span></span>

<span data-ttu-id="26343-112">下面是 MOF 资源的定义。</span><span class="sxs-lookup"><span data-stu-id="26343-112">The following is the MOF resource definition.</span></span>

```
[ClassVersion("1.0.0"), FriendlyName("xDemoFile")]
class MSFT_XDemoFile : OMI_BaseResource
{
                [Key, Description("path")] String Path;
                [Write, Description("Should the file be present"), ValueMap{"Present","Absent"}, Values{"Present","Absent"}] String Ensure;
                [Write, Description("Contentof file.")] String Content;
};
```

### <a name="setting-up-the-visual-studio-project"></a><span data-ttu-id="26343-113">设置 Visual Studio 项目</span><span class="sxs-lookup"><span data-stu-id="26343-113">Setting up the Visual Studio project</span></span>
#### <a name="setting-up-a-cmdlet-project"></a><span data-ttu-id="26343-114">设置 cmdlet 项目</span><span class="sxs-lookup"><span data-stu-id="26343-114">Setting up a cmdlet project</span></span>

1. <span data-ttu-id="26343-115">打开 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="26343-115">Open Visual Studio.</span></span>
1. <span data-ttu-id="26343-116">创建 C# 项目并命名。</span><span class="sxs-lookup"><span data-stu-id="26343-116">Create a C# project and provide the name.</span></span>
1. <span data-ttu-id="26343-117">从可用的项目模板中选择**类库**。</span><span class="sxs-lookup"><span data-stu-id="26343-117">Select **Class Library** from the available project templates.</span></span>
1. <span data-ttu-id="26343-118">单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="26343-118">Click **Ok**.</span></span>
1. <span data-ttu-id="26343-119">将 System.Automation.Management.dll 的程序集引用添加到项目。</span><span class="sxs-lookup"><span data-stu-id="26343-119">Add an assembly reference to System.Automation.Management.dll to your project.</span></span>
1. <span data-ttu-id="26343-120">更改程序集名称，使其与资源名称一致。</span><span class="sxs-lookup"><span data-stu-id="26343-120">Change the assembly name to match the resource name.</span></span> <span data-ttu-id="26343-121">在本示例中，程序集应该被命名为 **MSFT_XDemoFile**。</span><span class="sxs-lookup"><span data-stu-id="26343-121">In this case, the assembly should be named **MSFT_XDemoFile**.</span></span>

### <a name="writing-the-cmdlet-code"></a><span data-ttu-id="26343-122">编写 cmdlet 代码</span><span class="sxs-lookup"><span data-stu-id="26343-122">Writing the cmdlet code</span></span>

<span data-ttu-id="26343-123">下列 C# 代码会实现 **Get-TargetResource**、**Set-TargetResource** 和 **Test-TargetResource** cmdlet。</span><span class="sxs-lookup"><span data-stu-id="26343-123">The following C# code implements the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** cmdlets.</span></span>

```C#


namespace cSharpDSCResourceExample
{
    using System;
    using System.Collections.Generic;
    using System.IO;
    using System.Management.Automation;  // Windows PowerShell assembly.

    #region Get-TargetResource

    [OutputType(typeof(System.Collections.Hashtable))]
    [Cmdlet(VerbsCommon.Get, "TargetResource")]
    public class GetTargetResource : PSCmdlet
    {
        [Parameter(Mandatory = true)]
        public string Path { get; set; }

        /// <summary>
        /// Implement the logic to return the current state of the resource as a hashtable with keys being the resource properties
        /// and the values are the corresponding current value on the machine.
        /// </summary>
        protected override void ProcessRecord()
        {
            var currentResourceState = new Dictionary<string, string>();
            if (File.Exists(Path))
            {
                currentResourceState.Add("Ensure", "Present");

                // read current content
                string CurrentContent = "";
                using (var reader = new StreamReader(Path))
                {
                    CurrentContent = reader.ReadToEnd();
                }
                currentResourceState.Add("Content", CurrentContent);
            }
            else
            {
                currentResourceState.Add("Ensure", "Absent");
                currentResourceState.Add("Content", "");
            }
            // write the hashtable in the PS console.
            WriteObject(currentResourceState);
        }
    }

    # endregion

    #region Set-TargetResource
    [OutputType(typeof(void))]
    [Cmdlet(VerbsCommon.Set, "TargetResource")]
    public class SetTargetResource : PSCmdlet
    {
        [Parameter(Mandatory = true)]
        public string Path { get; set; }

        [Parameter(Mandatory = false)]

        [ValidateSet("Present", "Absent", IgnoreCase = true)]
        public string Ensure {
            get
            {
                // set the default to present.
               return (this._ensure ?? "Present") ;
            }
            set
            {
                this._ensure = value;
            }
        }

        [Parameter(Mandatory = false)]
        public string Content {
            get { return (string.IsNullOrEmpty(this._content) ? "" : this._content); }
            set { this._content = value; }
        }

        private string _ensure;
        private string _content;

        /// <summary>
        /// Implement the logic to set the state of the machine to the desired state.
        /// </summary>
        protected override void ProcessRecord()
        {
            WriteVerbose(string.Format("Running set with parameters {0}{1}{2}", Path, Ensure, Content));
            if (File.Exists(Path))
            {
                if (Ensure.Equals("absent", StringComparison.InvariantCultureIgnoreCase))
                {
                    File.Delete(Path);
                }
                else
                {
                    // file already exist and ensure "present" is specified. start writing the content to a file
                    if (!string.IsNullOrEmpty(Content))
                    {
                        string existingContent = null;
                        using (var reader = new StreamReader(Path))
                        {
                            existingContent = reader.ReadToEnd();
                        }
                        // check if the content of the file mathes the content passed
                        if (!existingContent.Equals(Content, StringComparison.InvariantCultureIgnoreCase))
                        {
                            WriteVerbose("Existing content did not match with desired content updating the content of the file");
                            using (var writer = new StreamWriter(Path))
                            {
                                writer.Write(Content);
                                writer.Flush();
                            }
                        }
                    }
                }

            }
            else
            {
                if (Ensure.Equals("present", StringComparison.InvariantCultureIgnoreCase))
                {
                    // if nothing is passed for content just write "" otherwise write the content passed.
                    using (var writer = new StreamWriter(Path))
                    {
                        WriteVerbose(string.Format("Creating a file under path {0} with content {1}", Path, Content));
                        writer.Write(Content);
                    }
                }

            }

            /* if you need to reboot the VM. please add the following two line of code.
            PSVariable DscMachineStatus = new PSVariable("DSCMachineStatus", 1, ScopedItemOptions.AllScope);
            this.SessionState.PSVariable.Set(DscMachineStatus);
             */

        }

    }

    # endregion

    #region Test-TargetResource

    [Cmdlet("Test", "TargetResource")]
    [OutputType(typeof(Boolean))]
    public class TestTargetResource : PSCmdlet
    {
        [Parameter(Mandatory = true)]
        public string Path { get; set; }

        [Parameter(Mandatory = false)]

        [ValidateSet("Present", "Absent", IgnoreCase = true)]
        public string Ensure
        {
            get
            {
                // set the default to present.
                return (this._ensure ?? "Present");
            }
            set
            {
                this._ensure = value;
            }
        }

        [Parameter(Mandatory = false)]
        public string Content
        {
            get { return (string.IsNullOrEmpty(this._content) ? "" : this._content); }
            set { this._content = value; }
        }

        private string _ensure;
        private string _content;

        /// <summary>
        /// Return a boolean value which indicates wheather the current machine is in desired state or not.
        /// </summary>
        protected override void ProcessRecord()
        {
            if (File.Exists(Path))
            {
                if( Ensure.Equals("absent", StringComparison.InvariantCultureIgnoreCase))
                {
                    WriteObject(false);
                }
                else
                {
                    // check if the content matches

                    string existingContent = null;
                    using (var stream = new StreamReader(Path))
                    {
                        existingContent = stream.ReadToEnd();
                    }

                    WriteObject(Content.Equals(existingContent, StringComparison.InvariantCultureIgnoreCase));
                }
            }
            else
            {
                WriteObject(Ensure.Equals("Absent", StringComparison.InvariantCultureIgnoreCase));
            }
        }
    }

    # endregion

}
```

### <a name="deploying-the-resource"></a><span data-ttu-id="26343-124">部署资源</span><span class="sxs-lookup"><span data-stu-id="26343-124">Deploying the resource</span></span>

<span data-ttu-id="26343-125">应将已编译的 dll 文件保存在与基于脚本的资源相类似的文件结构中。</span><span class="sxs-lookup"><span data-stu-id="26343-125">The compiled dll file should be saved in a file structure similar to a script-based resource.</span></span> <span data-ttu-id="26343-126">下面是此资源的文件夹结构。</span><span class="sxs-lookup"><span data-stu-id="26343-126">The following is the folder structure for this resource.</span></span>

```
$env: psmodulepath (folder)
    |- MyDscResources (folder)
        |- MyDscResources.psd1 (file, required)
        |- DSCResources (folder)
            |- MSFT_XDemoFile (folder)
                |- MSFT_XDemoFile.psd1 (file, optional)
                |- MSFT_XDemoFile.dll (file, required)
                |- MSFT_XDemoFile.schema.mof (file, required)
```

### <a name="see-also"></a><span data-ttu-id="26343-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="26343-127">See Also</span></span>
#### <a name="concepts"></a><span data-ttu-id="26343-128">概念</span><span class="sxs-lookup"><span data-stu-id="26343-128">Concepts</span></span>
[<span data-ttu-id="26343-129">使用 MOF 编写自定义 DSC 资源</span><span class="sxs-lookup"><span data-stu-id="26343-129">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
#### <a name="other-resources"></a><span data-ttu-id="26343-130">其他资源</span><span class="sxs-lookup"><span data-stu-id="26343-130">Other Resources</span></span>
[<span data-ttu-id="26343-131">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="26343-131">Writing a Windows PowerShell Cmdlet</span></span>](https://msdn.microsoft.com/library/dd878294.aspx)