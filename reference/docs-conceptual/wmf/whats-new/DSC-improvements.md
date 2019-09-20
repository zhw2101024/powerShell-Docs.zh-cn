---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,安装程序
title: WMF 5.1 中的 DSC 改进
ms.openlocfilehash: 47c1de362108096f26c0420d6135a9d9028a0302
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2019
ms.locfileid: "71147667"
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a><span data-ttu-id="25e82-103">WMF 5.1 中的 Desired State Configuration (DSC) 改进</span><span class="sxs-lookup"><span data-stu-id="25e82-103">Improvements in Desired State Configuration (DSC) in WMF 5.1</span></span>

## <a name="dsc-class-resource-improvements"></a><span data-ttu-id="25e82-104">DSC 类资源改进</span><span class="sxs-lookup"><span data-stu-id="25e82-104">DSC class resource improvements</span></span>

<span data-ttu-id="25e82-105">在 WMF 5.1 中，我们已解决下列已知问题：</span><span class="sxs-lookup"><span data-stu-id="25e82-105">In WMF 5.1, we have fixed the following known issues:</span></span>

- <span data-ttu-id="25e82-106">如果基于类的 DSC 资源的 Get() 函数返回复杂/哈希表类型，则 Get-DscConfiguration 可能会返回空值 (null) 或错误。</span><span class="sxs-lookup"><span data-stu-id="25e82-106">Get-DscConfiguration may return empty values (null) or errors if a complex/hash table type is returned by Get() function of a class-based DSC resource.</span></span>
- <span data-ttu-id="25e82-107">如果在 DSC 配置中使用 RunAs 凭据，Get-DscConfiguration 将返回错误。</span><span class="sxs-lookup"><span data-stu-id="25e82-107">Get-DscConfiguration returns error if RunAs credential is used in DSC configuration.</span></span>
- <span data-ttu-id="25e82-108">不能在复合配置中使用基于类的资源。</span><span class="sxs-lookup"><span data-stu-id="25e82-108">Class-based resource cannot be used in a composite configuration.</span></span>
- <span data-ttu-id="25e82-109">如果基于类的资源具有和自己类型一样的属性，Start-DscConfiguration 将挂起。</span><span class="sxs-lookup"><span data-stu-id="25e82-109">Start-DscConfiguration hangs if class-based resource has a property of its own type.</span></span>
- <span data-ttu-id="25e82-110">基于类的资源不能用作独占资源。</span><span class="sxs-lookup"><span data-stu-id="25e82-110">Class-based resource cannot be used as an exclusive resource.</span></span>

## <a name="dsc-resource-debugging-improvements"></a><span data-ttu-id="25e82-111">DSC 资源调试改进</span><span class="sxs-lookup"><span data-stu-id="25e82-111">DSC resource debugging improvements</span></span>

<span data-ttu-id="25e82-112">在 WMF 5.0 中，PowerShell 调试器不直接在基于类的资源方法（Get/Set/Test）处停止。</span><span class="sxs-lookup"><span data-stu-id="25e82-112">In WMF 5.0, the PowerShell debugger did not stop at the class-based resource method (Get/Set/Test) directly.</span></span> <span data-ttu-id="25e82-113">在 WMF 5.1 中，调试器在基于类的资源方法处停止，与遇到基于 MOF 的资源方法时一样。</span><span class="sxs-lookup"><span data-stu-id="25e82-113">In WMF 5.1, the debugger stops at the class-based resource method in the same way as for MOF-based resources methods.</span></span>

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a><span data-ttu-id="25e82-114">DSC 请求客户端支持 TLS 1.1 和 TLS 1.2</span><span class="sxs-lookup"><span data-stu-id="25e82-114">DSC pull client supports TLS 1.1 and TLS 1.2</span></span>

<span data-ttu-id="25e82-115">以前，DSC 请求客户端仅支持基于 https 连接的 SSL3.0 和 TLS1.0。</span><span class="sxs-lookup"><span data-stu-id="25e82-115">Previously, the DSC pull client only supported SSL3.0 and TLS1.0 over HTTPS connections.</span></span> <span data-ttu-id="25e82-116">当强制使用更安全的协议时，请求客户端停止工作了。</span><span class="sxs-lookup"><span data-stu-id="25e82-116">When forced to use more secure protocols, the pull client would stop functioning.</span></span> <span data-ttu-id="25e82-117">在 WMF 5.1 中，DSC 请求客户端不再支持 SSL 3.0，而增加了对更安全的 TLS 1.1 和 TLS 1.2 协议的支持。</span><span class="sxs-lookup"><span data-stu-id="25e82-117">In WMF 5.1, the DSC pull client no longer supports SSL 3.0 and adds support for the more secure TLS 1.1 and TLS 1.2 protocols.</span></span>

## <a name="improved-pull-server-registration"></a><span data-ttu-id="25e82-118">改进的请求服务器注册</span><span class="sxs-lookup"><span data-stu-id="25e82-118">Improved pull server registration</span></span>

<span data-ttu-id="25e82-119">在 WMF 的早期版本中，在使用 ESENT 数据库时同时注册 DSC 请求服务器或向其报告请求，将导致 LCM 无法注册和/或报告。</span><span class="sxs-lookup"><span data-stu-id="25e82-119">In the earlier versions of WMF, simultaneous registrations/reporting requests to a DSC pull server while using the ESENT database would lead to LCM failing to register and/or report.</span></span> <span data-ttu-id="25e82-120">在这种情况下，请求服务器上的事件日志显示错误“实例名称已使用”。</span><span class="sxs-lookup"><span data-stu-id="25e82-120">In such cases, the event logs on the pull server has the error "Instance Name already in use."</span></span> <span data-ttu-id="25e82-121">这是由于在多线程情况下使用不正确的模式访问 ESENT 数据库。</span><span class="sxs-lookup"><span data-stu-id="25e82-121">This was caused by an incorrect pattern being used to access the ESENT database in a multi-threaded scenario.</span></span> <span data-ttu-id="25e82-122">在 WMF 5.1 中已修复此问题。</span><span class="sxs-lookup"><span data-stu-id="25e82-122">In WMF 5.1, this issue has been fixed.</span></span> <span data-ttu-id="25e82-123">在 WMF 5.1 中，并发注册或报告（涉及 ESENT 数据库）可以正常运行。</span><span class="sxs-lookup"><span data-stu-id="25e82-123">Concurrent registrations or reporting (involving ESENT database) works fine in WMF 5.1.</span></span> <span data-ttu-id="25e82-124">此问题仅适用于 ESENT 数据库，并不适用于 OLEDB 数据库。</span><span class="sxs-lookup"><span data-stu-id="25e82-124">This issue is applicable only to the ESENT database and does not apply to the OLEDB database.</span></span>

## <a name="enable-circular-log-on-esent-database-instance"></a><span data-ttu-id="25e82-125">在 ESENT 数据库实例上启用循环日志</span><span class="sxs-lookup"><span data-stu-id="25e82-125">Enable Circular log on ESENT database instance</span></span>

<span data-ttu-id="25e82-126">在旧版 DSC PullServer 中，ESENT 数据库日志文件填满了 pullserver 的磁盘空间，因为数据库实例在创建时未启用循环日志。</span><span class="sxs-lookup"><span data-stu-id="25e82-126">In eariler version of DSC-PullServer, the ESENT database log files were filling up the disk space of the pullserver becouse the database instance was being created without circular logging.</span></span> <span data-ttu-id="25e82-127">在此版本中，可以视需要使用 pullserver 的 web.config 来控制实例的循环记录行为。</span><span class="sxs-lookup"><span data-stu-id="25e82-127">In this release, you have the option to control the circular logging behavior of the instance using the web.config of the pullserver.</span></span> <span data-ttu-id="25e82-128">默认情况下，CircularLogging 设为 TRUE。</span><span class="sxs-lookup"><span data-stu-id="25e82-128">By default CircularLogging is set to TRUE.</span></span>

```xml
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```

## <a name="wow64-support-for-configuration-keyword"></a><span data-ttu-id="25e82-129">对 Configuration 关键字的 WOW64 支持</span><span class="sxs-lookup"><span data-stu-id="25e82-129">WOW64 support for Configuration Keyword</span></span>

<span data-ttu-id="25e82-130">64 位计算机上的 WOW64 中现支持 `Configuration` 关键字。</span><span class="sxs-lookup"><span data-stu-id="25e82-130">The `Configuration` keyword is now supported in WOW64 on a 64-bit computer.</span></span> <span data-ttu-id="25e82-131">这意味着，可以在运行于 64 位计算机上的 32 位进程（例如 Windows PowerShell ISE (x86)）中定义和编译 DSC 配置。</span><span class="sxs-lookup"><span data-stu-id="25e82-131">This means that a DSC configuration can be defined and compiled within a 32-bit process such as Windows PowerShell ISE (x86) running on a 64-bit computer.</span></span>

## <a name="pull-partial-configuration-naming-convention"></a><span data-ttu-id="25e82-132">拉取部分配置命名约定</span><span class="sxs-lookup"><span data-stu-id="25e82-132">Pull partial configuration naming convention</span></span>

<span data-ttu-id="25e82-133">在以前的版本中，部分配置的命名约定为请求服务器/服务中 mof 文件名应与本地配置管理器设置中指定的部分配置名称匹配，反过来后者必须与 MOF 文件中嵌入的配置名称匹配。</span><span class="sxs-lookup"><span data-stu-id="25e82-133">In the previous release, the naming convention for a partial configuration was that the MOF file name in the pull server/service should match the partial configuration name specified in the local configuration manager settings that in turn must match the configuration name embedded in the MOF file.</span></span>

<span data-ttu-id="25e82-134">请参阅以下快照：</span><span class="sxs-lookup"><span data-stu-id="25e82-134">See the snapshots below:</span></span>

- <span data-ttu-id="25e82-135">本地配置设置，定义了节点可以接收的部分配置。</span><span class="sxs-lookup"><span data-stu-id="25e82-135">Local configuration settings which defines a partial configuration that a node is allowed to receive.</span></span>

  ![示例 metaconfiguration](../images/DSC-improvements/MetaConfigPartialOne.png)

- <span data-ttu-id="25e82-137">部分配置定义示例</span><span class="sxs-lookup"><span data-stu-id="25e82-137">Sample partial configuration definition</span></span>

  ```powershell
  Configuration PartialOne
  {
      Node('localhost')
      {
          File test
          {
              DestinationPath = "$env:TEMP\partialconfigexample.txt"
              Contents = 'Partial Config Example'
          }
      }
  }
  PartialOne
  ```

- <span data-ttu-id="25e82-138">生成的 MOF 文件中嵌入的“ConfigurationName”。</span><span class="sxs-lookup"><span data-stu-id="25e82-138">'ConfigurationName' embedded in the generated MOF file.</span></span>

  ![生成的 mof 文件示例](../images/DSC-improvements/PartialGeneratedMof.png)

- <span data-ttu-id="25e82-140">拉取配置存储库中的文件名</span><span class="sxs-lookup"><span data-stu-id="25e82-140">FileName in the pull configuration repository</span></span>

  ![配置存储库中的文件名](../images/DSC-improvements/PartialInConfigRepository.png)

  <span data-ttu-id="25e82-142">Azure 自动化服务名称生成的 MOF 文件名为 `<ConfigurationName>.<NodeName>.mof`。</span><span class="sxs-lookup"><span data-stu-id="25e82-142">Azure Automation service name generated MOF files as `<ConfigurationName>.<NodeName>.mof`.</span></span> <span data-ttu-id="25e82-143">因此，下面的配置编译到 PartialOne.localhost.mof 中。</span><span class="sxs-lookup"><span data-stu-id="25e82-143">So the configuration below compiles to PartialOne.localhost.mof.</span></span>

  <span data-ttu-id="25e82-144">这样将无法从 Azure 自动化服务中提取一个部分配置。</span><span class="sxs-lookup"><span data-stu-id="25e82-144">This made it impossible to pull one of your partial configuration from Azure Automation service.</span></span>

  ```powershell
  Configuration PartialOne
  {
      Node('localhost')
      {
          File test
          {
              DestinationPath = "$env:TEMP\partialconfigexample.txt"
              Contents = 'Partial Config Example'
          }
      }
  }
  PartialOne
  ```

  <span data-ttu-id="25e82-145">在 WMF 5.1 中，请求服务器/服务中的部分配置可以命名为 `<ConfigurationName>.<NodeName>.mof`。</span><span class="sxs-lookup"><span data-stu-id="25e82-145">In WMF 5.1, a partial configuration in the pull server/service can be named as `<ConfigurationName>.<NodeName>.mof`.</span></span> <span data-ttu-id="25e82-146">此外，如果一台计算机从请求服务器/服务中提取一个配置，那么请求服务器配置存储库上的配置文件可以有任何文件名。</span><span class="sxs-lookup"><span data-stu-id="25e82-146">Moreover, if a machine is pulling a single configuration from a pull server/service then the configuration file on the pull server configuration repository can have any file name.</span></span> <span data-ttu-id="25e82-147">借助这种命名灵活性，可以使用 Azure 自动化服务管理部分节点（节点的一些配置来自 Azure 自动化 DSC），也可以在本地管理部分配置。</span><span class="sxs-lookup"><span data-stu-id="25e82-147">This naming flexibility allows you to manage your nodes partially by Azure Automation service, where some configuration for your node is coming from Azure Automation DSC and with a partial configuration that you manage locally.</span></span>

  <span data-ttu-id="25e82-148">下面的元配置将节点设置为可以在本地管理，也可以由 Azure 自动化服务管理。</span><span class="sxs-lookup"><span data-stu-id="25e82-148">The metaconfiguration below sets up a node to be managed both locally as well as by Azure Automation service.</span></span>

  ```powershell
  [DscLocalConfigurationManager()]
  Configuration RegistrationMetaConfig
  {
      Settings
      {
          RefreshFrequencyMins = 30
          RefreshMode = "PULL"
      }

      ConfigurationRepositoryWeb web
      {
          ServerURL =  $endPoint
          RegistrationKey = $registrationKey
          ConfigurationNames = $configurationName
      }

      # Partial configuration managed by Azure Automation service.
      PartialConfiguration PartialConfigurationManagedByAzureAutomation
      {
          ConfigurationSource = "[ConfigurationRepositoryWeb]Web"
      }

      # This partial configuration is managed locally.
      PartialConfiguration OnPremisesConfig
      {
          RefreshMode = "PUSH"
          ExclusiveResources = @("Script")
      }

  }

  RegistrationMetaConfig
  Set-DscLocalConfigurationManager -Path .\RegistrationMetaConfig -Verbose
  ```

## <a name="using-psdscrunascredential-with-dsc-composite-resources"></a><span data-ttu-id="25e82-149">在 DSC 复合资源中使用 PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="25e82-149">Using PsDscRunAsCredential with DSC composite resources</span></span>

<span data-ttu-id="25e82-150">我们新增了对 DSC [复合](https://msdn.microsoft.com/powershell/dsc/authoringresourcecomposite)资源使用 [PsDscRunAsCredential](/powershell/dsc/configurations/runAsUser) 的支持。</span><span class="sxs-lookup"><span data-stu-id="25e82-150">We have added support for using [PsDscRunAsCredential](/powershell/dsc/configurations/runAsUser) with DSC [Composite](https://msdn.microsoft.com/powershell/dsc/authoringresourcecomposite) resources.</span></span>

<span data-ttu-id="25e82-151">现在可以在使用配置内的复合资源时，指定 PsDscRunAsCredential  值。</span><span class="sxs-lookup"><span data-stu-id="25e82-151">You can now specify a value for **PsDscRunAsCredential** when using composite resources inside configurations.</span></span> <span data-ttu-id="25e82-152">如果指定了该值，则可以 RunAs 用户身份运行复合资源内部的所有资源。</span><span class="sxs-lookup"><span data-stu-id="25e82-152">When specified, all resources run inside a composite resource as a RunAs user.</span></span> <span data-ttu-id="25e82-153">如果复合资源调用了另一个复合资源，也将以 RunAs 用户运行所有资源。</span><span class="sxs-lookup"><span data-stu-id="25e82-153">If a composite resource calls another composite resource, all those resources are also executed as RunAs user.</span></span> <span data-ttu-id="25e82-154">RunAs 凭据可以传播到复合资源层次结构的任一级别。</span><span class="sxs-lookup"><span data-stu-id="25e82-154">RunAs credentials are propagated to any level of the composite resource hierarchy.</span></span> <span data-ttu-id="25e82-155">如果复合资源内的任何资源指定了自己的 PsDscRunAsCredential  值，那么会在配置编译期间生成合并错误。</span><span class="sxs-lookup"><span data-stu-id="25e82-155">If any resource inside a composite resource specifies its own value for **PsDscRunAsCredential**, a merge error results during configuration compilation.</span></span>

<span data-ttu-id="25e82-156">本示例演示了在 PSDesiredStateConfiguration 模块中包含的 [WindowsFeatureSet](/powershell/dsc/reference/resources/windows/windowsfeaturesetresource) 复合资源中该属性的使用。</span><span class="sxs-lookup"><span data-stu-id="25e82-156">This example shows usage with the [WindowsFeatureSet](/powershell/dsc/reference/resources/windows/windowsfeaturesetresource) composite resource included in PSDesiredStateConfiguration module.</span></span>

```powershell
Configuration InstallWindowsFeature
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName
    {
        WindowsFeatureSet features
        {
            Name = @("Telnet-Client","SNMP-Service")
            Ensure = "Present"
            IncludeAllSubFeature = $true
            PsDscRunAsCredential = Get-Credential
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName             = 'localhost'
            PSDscAllowDomainUser = $true
            CertificateFile      = 'C:\publicKeys\targetNode.cer'
            Thumbprint           = '7ee7f09d-4be0-41aa-a47f-96b9e3bdec25'
        }
    )
}

InstallWindowsFeature -ConfigurationData $configData
```

## <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a><span data-ttu-id="25e82-157">允许配置中存在完全相同的重复资源</span><span class="sxs-lookup"><span data-stu-id="25e82-157">Allowing for Identical Duplicate Resources in a Configuration</span></span>

<span data-ttu-id="25e82-158">DSC 不允许配置内存在冲突的资源定义，也不处理这样的定义。</span><span class="sxs-lookup"><span data-stu-id="25e82-158">DSC does not allow or handle conflicting resource definitions within a configuration.</span></span> <span data-ttu-id="25e82-159">它不尝试解决冲突，只是无法正常工作。</span><span class="sxs-lookup"><span data-stu-id="25e82-159">Instead of trying to resolve the conflict, it simply fails.</span></span> <span data-ttu-id="25e82-160">随着复合资源中配置重用的利用率增加，冲突将更频繁地发生。</span><span class="sxs-lookup"><span data-stu-id="25e82-160">As configuration reuse becomes more utilized through composite resources, etc. conflicts will occur more often.</span></span> <span data-ttu-id="25e82-161">当冲突资源定义相同时，DSC 应为智能且允许此操作。</span><span class="sxs-lookup"><span data-stu-id="25e82-161">When conflicting resource definitions are identical, DSC should be smart and allow this.</span></span> <span data-ttu-id="25e82-162">通过此版本，我们支持具有相同定义的多个资源实例：</span><span class="sxs-lookup"><span data-stu-id="25e82-162">With this release, we support having multiple resource instances that have identical definitions:</span></span>

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS         #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS      #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

<span data-ttu-id="25e82-163">在早期版本中，如果试图确保已安装“Web-Server”角色，由于 WindowsFeature FE_IIS 和 WindowsFeature Worker_IIS 实例之间的冲突，将造成编译失败。</span><span class="sxs-lookup"><span data-stu-id="25e82-163">In previous releases, the result would be a failed compilation due to a conflict between the WindowsFeature FE_IIS and WindowsFeature Worker_IIS instances trying to ensure the 'Web-Server' role is installed.</span></span> <span data-ttu-id="25e82-164">请注意，这两个配置中所配置的*所有*属性完全相同。</span><span class="sxs-lookup"><span data-stu-id="25e82-164">Notice that *all* of the properties that are being configured are identical in these two configurations.</span></span> <span data-ttu-id="25e82-165">由于这两个资源中的*所有*属性完全相同，现在这将使成功编译。</span><span class="sxs-lookup"><span data-stu-id="25e82-165">Since *all* of the properties in these two resources are identical, this will result in a successful compilation now.</span></span>

<span data-ttu-id="25e82-166">如果两个资源的任何属性之间有所不同，则不会将他们视为相同且编译将失败。</span><span class="sxs-lookup"><span data-stu-id="25e82-166">If any of the properties are different between the two resources, they will not be considered identical and compilation will fail.</span></span>

## <a name="dsc-module-and-configuration-signing-validations"></a><span data-ttu-id="25e82-167">DSC 模块和配置签名验证</span><span class="sxs-lookup"><span data-stu-id="25e82-167">DSC module and configuration signing validations</span></span>

<span data-ttu-id="25e82-168">在 DSC 中，从请求服务器中将配置和模块分发到托管计算机。</span><span class="sxs-lookup"><span data-stu-id="25e82-168">In DSC, configurations and modules are distributed to managed computers from the pull server.</span></span> <span data-ttu-id="25e82-169">如果请求服务器受到攻击，攻击者可能修改请求服务器上的配置和模块，并将其分发到所有托管节点。</span><span class="sxs-lookup"><span data-stu-id="25e82-169">If the pull server is compromised, an attacker can potentially modify the configurations and modules on the pull server and have it distributed to all managed nodes.</span></span>

<span data-ttu-id="25e82-170">在 WMF 5.1 中，DSC 支持验证目录和配置文件 (.MOF) 上的数字签名。</span><span class="sxs-lookup"><span data-stu-id="25e82-170">In WMF 5.1, DSC supports validating the digital signatures on catalog and configuration (.MOF) files.</span></span> <span data-ttu-id="25e82-171">此功能可防止节点执行受信任的签名者未签名的配置或模块文件，或是在受信任的签名者签名后被篡改的配置或模块文件。</span><span class="sxs-lookup"><span data-stu-id="25e82-171">This feature prevents nodes from executing configurations or module files which are not signed by a trusted signer or which have been tampered with after they have been signed by trusted signer.</span></span>

### <a name="how-to-sign-configuration-and-module"></a><span data-ttu-id="25e82-172">如何对配置和模块进行签名</span><span class="sxs-lookup"><span data-stu-id="25e82-172">How to sign configuration and module</span></span>

- <span data-ttu-id="25e82-173">配置文件 (.MOF)：已扩展现有的 PowerShell cmdlet [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) 用于支持 MOF 文件签名。</span><span class="sxs-lookup"><span data-stu-id="25e82-173">Configuration Files (.MOFs): The existing PowerShell cmdlet [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) is extended to support signing of MOF files.</span></span>
- <span data-ttu-id="25e82-174">模块：使用以下步骤对相应的模块目录进行签名，从而完成模块签名：</span><span class="sxs-lookup"><span data-stu-id="25e82-174">Modules: Signing of modules is done by signing the corresponding module catalog using the following steps:</span></span>
  1. <span data-ttu-id="25e82-175">创建目录文件：目录文件包含加密哈希或指纹的集合。</span><span class="sxs-lookup"><span data-stu-id="25e82-175">Create a catalog file: A catalog file contains a collection of cryptographic hashes or thumbprints.</span></span> <span data-ttu-id="25e82-176">每个指纹对应于模块中包含的一个文件。</span><span class="sxs-lookup"><span data-stu-id="25e82-176">Each thumbprint corresponds to a file that is included in the module.</span></span> <span data-ttu-id="25e82-177">增加了新的 cmdlet [New-FileCatalog](/powershell/module/microsoft.powershell.security/new-filecatalog)，支持用户为其模块创建目录文件。</span><span class="sxs-lookup"><span data-stu-id="25e82-177">The new cmdlet [New-FileCatalog](/powershell/module/microsoft.powershell.security/new-filecatalog), has been added to enable users to create a catalog file for their module.</span></span>
  2. <span data-ttu-id="25e82-178">对目录文件进行签名：使用 [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) 对目录文件进行签名。</span><span class="sxs-lookup"><span data-stu-id="25e82-178">Sign the catalog file: Use [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) to sign the catalog file.</span></span>
  3. <span data-ttu-id="25e82-179">将目录文件放在模块文件夹中。</span><span class="sxs-lookup"><span data-stu-id="25e82-179">Place the catalog file inside the module folder.</span></span> <span data-ttu-id="25e82-180">按照约定，模块目录文件应放在与模块同名的模块文件夹下面。</span><span class="sxs-lookup"><span data-stu-id="25e82-180">By convention, module catalog file should be placed under the module folder with the same name as the module.</span></span>

### <a name="localconfigurationmanager-settings-to-enable-signing-validations"></a><span data-ttu-id="25e82-181">用于启用签名验证的 LocalConfigurationManager 设置。</span><span class="sxs-lookup"><span data-stu-id="25e82-181">LocalConfigurationManager settings to enable signing validations</span></span>

#### <a name="pull"></a><span data-ttu-id="25e82-182">请求</span><span class="sxs-lookup"><span data-stu-id="25e82-182">Pull</span></span>

<span data-ttu-id="25e82-183">节点的 LocalConfigurationManager 根据其当前设置执行模块和配置的签名验证。</span><span class="sxs-lookup"><span data-stu-id="25e82-183">The LocalConfigurationManager of a node performs signing validation of modules and configurations based on its current settings.</span></span> <span data-ttu-id="25e82-184">默认情况下，签名验证处于禁用状态。</span><span class="sxs-lookup"><span data-stu-id="25e82-184">By default, signature validation is disabled.</span></span> <span data-ttu-id="25e82-185">你可以将 SignatureValidation 块添加到节点的元配置定义来启用签名验证，如下所示：</span><span class="sxs-lookup"><span data-stu-id="25e82-185">Signature validation can enabled by adding the ‘SignatureValidation’ block to the meta-configuration definition of the node as shown below:</span></span>

```powershell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PULL'
    }

    ConfigurationRepositoryWeb pullserver{
      ConfigurationNames = 'sql'
      ServerURL = 'http://localhost:8080/PSDSCPullServer/PSDSCPullServer.svc'
      AllowUnsecureConnection = $true
      RegistrationKey = 'd6750ff1-d8dd-49f7-8caf-7471ea9793fc' # Replace this with correct registration key.
    }
    SignatureValidation validations{
        # If the TrustedStorePath property is provided then LCM will use the custom path. Otherwise, the LCM will use default trusted store path (Cert:\LocalMachine\DSCStore) to find the signing certificate.
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'
        SignedItemType = 'Configuration','Module'         # This is a list of DSC artifacts, for which LCM need to verify their digital signature before executing them on the node.
    }

}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
```

<span data-ttu-id="25e82-186">在节点上设置上述元配置可以对下载的配置和模块进行签名验证。</span><span class="sxs-lookup"><span data-stu-id="25e82-186">Setting the above metaconfiguration on a node enables signature validation on downloaded configurations and modules.</span></span> <span data-ttu-id="25e82-187">本地配置管理器执行以下步骤来验证数字签名。</span><span class="sxs-lookup"><span data-stu-id="25e82-187">The Local Configuration Manager performs the following steps to verify the digital signatures.</span></span>

1. <span data-ttu-id="25e82-188">使用 `Get-AuthenticodeSignature` cmdlet 验证配置文件 (.MOF) 上的签名是否有效。</span><span class="sxs-lookup"><span data-stu-id="25e82-188">Verify the signature on a configuration file (.MOF) is valid using the `Get-AuthenticodeSignature` cmdlet.</span></span>
2. <span data-ttu-id="25e82-189">验证授权签名人的证书颁发机构是否可信任。</span><span class="sxs-lookup"><span data-stu-id="25e82-189">Verify the certificate authority that authorized the signer is trusted.</span></span>
3. <span data-ttu-id="25e82-190">将配置的模块/资源依赖项下载到临时位置。</span><span class="sxs-lookup"><span data-stu-id="25e82-190">Download module/resource dependencies of the configuration to a temp location.</span></span>
4. <span data-ttu-id="25e82-191">验证模块中是否包含目录的签名。</span><span class="sxs-lookup"><span data-stu-id="25e82-191">Verify the signature of the catalog included inside the module.</span></span>
   - <span data-ttu-id="25e82-192">查找 `<moduleName>.cat` 文件，并使用 `Get-AuthenticodeSignature` 验证其签名。</span><span class="sxs-lookup"><span data-stu-id="25e82-192">Find a `<moduleName>.cat` file and verify its signature using `Get-AuthenticodeSignature`.</span></span>
   - <span data-ttu-id="25e82-193">验证对签名人进行身份验证的证书颁发机构是否可信任。</span><span class="sxs-lookup"><span data-stu-id="25e82-193">Verify the certification authority that authenticated the signer is trusted.</span></span>
   - <span data-ttu-id="25e82-194">验证未使用新的 cmdlet `Test-FileCatalog` 篡改模块的内容。</span><span class="sxs-lookup"><span data-stu-id="25e82-194">Verify the content of the modules has not been tampered using the new cmdlet `Test-FileCatalog`.</span></span>
5. <span data-ttu-id="25e82-195">`Install-Module` 到 `$env:ProgramFiles\WindowsPowerShell\Modules\`</span><span class="sxs-lookup"><span data-stu-id="25e82-195">`Install-Module` to `$env:ProgramFiles\WindowsPowerShell\Modules\`</span></span>
6. <span data-ttu-id="25e82-196">进程配置</span><span class="sxs-lookup"><span data-stu-id="25e82-196">Process configuration</span></span>

> [!NOTE]
> <span data-ttu-id="25e82-197">仅在第一次将配置应用到系统或下载并安装模块时，才执行对模块目录和配置的签名验证。</span><span class="sxs-lookup"><span data-stu-id="25e82-197">Signature validation on module-catalog and configuration is only performed when the configuration is applied to the system for the first time or when the module is downloaded and installed.</span></span>
> <span data-ttu-id="25e82-198">一致性运行不会验证 Current.mof 或其模块依赖项的签名。</span><span class="sxs-lookup"><span data-stu-id="25e82-198">Consistency runs do not validate the signature of Current.mof or its module dependencies.</span></span> <span data-ttu-id="25e82-199">如果在任何阶段验证失败（例如，如果从请求服务器请求获取的配置未签名），那么配置处理会终止，同时显示以下错误，并删除所有临时文件。</span><span class="sxs-lookup"><span data-stu-id="25e82-199">If verification has failed at any stage, for instance, if the configuration pulled from the pull server is unsigned, then processing of the configuration terminates with the error shown below and all temporary files are deleted.</span></span>

![错误输出配置示例](../images/DSC-improvements/PullUnsignedConfigFail.png)

<span data-ttu-id="25e82-201">同样，如果请求获取的模块包含未签名的目录，也会导致以下错误生成：</span><span class="sxs-lookup"><span data-stu-id="25e82-201">Similarly, pulling a module whose catalog is not signed results in the following error:</span></span>

![错误输出模块示例](../images/DSC-improvements/PullUnisgnedCatalog.png)

#### <a name="push"></a><span data-ttu-id="25e82-203">推送</span><span class="sxs-lookup"><span data-stu-id="25e82-203">Push</span></span>

<span data-ttu-id="25e82-204">通过使用推送提供的配置可能会在其提供到节点之前在源处被篡改。</span><span class="sxs-lookup"><span data-stu-id="25e82-204">A configuration delivered by using push might be tampered with at its source before it delivered to the node.</span></span> <span data-ttu-id="25e82-205">本地配置管理器对推送或发布的配置执行类似的签名验证步骤。</span><span class="sxs-lookup"><span data-stu-id="25e82-205">The Local Configuration Manager performs similar signature validation steps for pushed or published configuration(s).</span></span> <span data-ttu-id="25e82-206">下面是针对推送的签名验证的完整示例。</span><span class="sxs-lookup"><span data-stu-id="25e82-206">Below is a complete example of signature validation for push.</span></span>

- <span data-ttu-id="25e82-207">启用针对节点的签名验证。</span><span class="sxs-lookup"><span data-stu-id="25e82-207">Enable signature validation on the node.</span></span>

  ```powershell
  [DSCLocalConfigurationManager()]
  Configuration EnableSignatureValidation
  {
      Settings
      {
          RefreshMode = 'PUSH'
      }
      SignatureValidation validations{
          TrustedStorePath = 'Cert:\LocalMachine\DSCStore'
          SignedItemType =  'Configuration','Module'
      }

  }
  EnableSignatureValidation
  Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
  ```

- <span data-ttu-id="25e82-208">创建示例配置文件。</span><span class="sxs-lookup"><span data-stu-id="25e82-208">Create a sample configuration file.</span></span>

  ```powershell
  # Sample configuration
  Configuration Test
  {

      File foo
      {
          DestinationPath =  "$env:TEMP\signingTest.txt"
          Contents = "ABC"
      }
  }
  Test
  ```

- <span data-ttu-id="25e82-209">尝试将未签名的配置文件推送到节点。</span><span class="sxs-lookup"><span data-stu-id="25e82-209">Try pushing the unsigned configuration file in to the node.</span></span>

  ```powershell
  Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
  ```

  ![ErrorUnsignedMofPushed](../images/DSC-improvements/PushUnsignedMof.png)

- <span data-ttu-id="25e82-211">使用代码签名证书对配置文件进行签名。</span><span class="sxs-lookup"><span data-stu-id="25e82-211">Sign the configuration file using code-signing certificate.</span></span>

  ![SignMofFile](../images/DSC-improvements/SignMofFile.png)

- <span data-ttu-id="25e82-213">请尝试推送已签名的 MOF 文件。</span><span class="sxs-lookup"><span data-stu-id="25e82-213">Try pushing the signed MOF file.</span></span>

  ![SignMofFile](../images/DSC-improvements/PushSignedMof.png)
