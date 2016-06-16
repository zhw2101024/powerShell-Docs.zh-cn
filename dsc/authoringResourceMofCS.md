---
title:   在 C 中创作 DSC 资源`
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# 在 C 中创作 DSC 资源`#`

> 适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0

通常在 PowerShell 脚本中实现 Windows PowerShell Desired State Configuration (DSC) 自定义资源。 但是你也可以通过在 C# 中编写 cmdlet 来实现 DSC 自定义资源的功能。 有关在 C# 中编写 cmdlet 的介绍，请参阅[编写 Windows PowerShell Cmdlet](https://technet.microsoft.com/en-us/library/dd878294.aspx)。

除在 C# 中用 cmdlet 实现资源外，创建 MOF 架构、创建文件夹结构、导入和使用自定义 DSC 资源的过程都与[使用 MOF 编写自定义 DSC 资源](authoringResourceMOF.md)中介绍的相同。

## 编写基于 cmdlet 的资源
此示例中，我们将实现一个管理文本文件及其内容的简单资源。

### 编写 MOF 架构

下面是 MOF 资源的定义。

```
[ClassVersion("1.0.0"), FriendlyName("xDemoFile")]
class MSFT_XDemoFile : OMI_BaseResource
{
                [Key, Description("path")] String Path;
                [Write, Description("Should the file be present"), ValueMap{"Present","Absent"}, Values{"Present","Absent"}] String Ensure;
                [Write, Description("Contentof file.")] String Content;                   
};
```

### 设置 Visual Studio 项目
#### 设置 cmdlet 项目

1. 打开 Visual Studio
1. 创建 C# 项目并命名。
1. 从可用的项目模板中选择**类库**。
1. 单击“确定”。
1. 将 System.Automation.Management.dll 的程序集引用添加到项目。
1. 更改程序集名称，使其与资源名称一致。 在本示例中，程序集应该被命名为 **MSFT_XDemoFile**。

### 编写 cmdlet 代码

下列 C# 代码会实现 **Get-TargetResource**、**Set-TargetResource** 和 **Test-TargetResource** cmdlet。

```C#
Get-TargetResource
       [OutputType(typeof(System.Collections.Hashtable))]
       [Cmdlet(VerbsCommon.Get, "TargetResource")]
       public class GetTargetResource : PSCmdlet
       {
              [Parameter(Mandatory = true)]
              public string Path { get; set; }
 
///<summary>
/// Implement the logic to write the current state of the resource as a 
/// Hash table with keys being the resource properties 
/// and the Values are the corresponding current values on the target machine.
 
///</summary>
              protected override void ProcessRecord()
              {
// Download the zip file at the end of this blog to see sample implementation.
 }
 
Set-TargetResouce
         [OutputType(typeof(void))]
    [Cmdlet(VerbsCommon.Set, "TargetResource")]
    public class SetTargetResource : PSCmdlet
    {
        privatestring _ensure;
        privatestring _content;
        
[Parameter(Mandatory = true)]
        public string Path { get; set; }
        
[Parameter(Mandatory = false)]      
       [ValidateSet("Present", "Absent", IgnoreCase = true)]
       public string Ensure {
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
            public string Content {
            get { return (string.IsNullOrEmpty(this._content) ? "" : this._content); }
            set { this._content = value; }
        }
 
///<summary>
        /// Implement the logic to set the state of the machine to the desired state.
        ///</summary>
        protected override void ProcessRecord()
        {
//Implement the set method of the resource 
/* Uncomment this section if your resource needs a machine reboot.
PSVariable DscMachineStatus = new PSVariable("DSCMachineStatus", 1, ScopedItemOptions.AllScope);
                this.SessionState.PSVariable.Set(DscMachineStatus);
*/     
  }
    }
Test-TargetResource    
       [Cmdlet("Test", "TargetResource")]
    [OutputType(typeof(Boolean))]
    public class TestTargetResource : PSCmdlet
    {   
        
        private string _ensure;
        private string _content;
 
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
            get { return (string.IsNullOrEmpty(this._content) ? "“:this._content);}
            set { this._content = value; }
        }
 
///<summary>
/// Write a Boolean value which indicates whether the current machine is in    
/// desired state or not.
        ///</summary>
        protected override void ProcessRecord()
        {
                // Implement the test method of the resource.
        }
}
```

### 部署资源

应将已编译的 dll 文件保存在与基于脚本的资源相类似的文件结构中。 下面是此资源的文件夹结构。

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

### 另请参阅
#### 概念
[使用 MOF 编写自定义 DSC 资源](authoringResourceMOF.md)
#### 其他资源
[编写 Windows PowerShell Cmdlet](https://msdn.microsoft.com/en-us/library/dd878294.aspx)



<!--HONumber=May16_HO3-->


