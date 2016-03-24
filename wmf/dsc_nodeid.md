# 节点和配置 ID 的分离

## 概述

为了在请求模式下使用 DSC 时提供更加灵活和精简的体验，我们在此版本中添加了大量功能。 这些功能旨在使你能够灵活地跨多个节点轻松设置和部署配置，同时对于每个节点仍单独跟踪状态和报告信息。 这些功能如下：

* 标识计算机配置的配置名称。 此名称可由多个目标节点共享 
* 唯一标识单个节点的代理 ID
* 仅在目标节点第一次连接到请求服务器时出现的注册步骤

**注意：**这些特色和功能是添加进来的，它们不取代现有的请求功能和概念。 你可以将这些新功能或将较旧的功能用于此版本中发布的新请求服务器。

## 代理 ID

此功能适用于不希望为每个目标节点设置和管理唯一标识符的用户。 现在，无需更多 GUID 簿记。 DSC 自动生成它在与请求服务器通信时使用的代理 ID。 请求服务器使用此 ID 为给定节点唯一地标识所有信息。 它还意味着无需为每个目标节点设置包含唯一 ID 的唯一元配置，因此，许多目标节点可以使用单个元配置，同时仍然保留每个节点的唯一标识。 

## 配置名称

配置名称是定义目标节点将应用配置名称的友好名称。 与此关联的更改如下：  

### 友好命名

它可以是任意字符串！ 它不需要为 GUID 格式，因此可将设置 SQL Server 的配置简单命名为“SQL_Server”。 这样一来，可以更轻松地标识给定配置的用途。

### 分配

在请求服务器上集中管理已分配目标节点的配置。 可通过在元配置中定义 ConfigrationName 属性来引导启动它，但此操作仅限用于注册期间。 注册后，服务器将告知目标节点其将获得的配置。 对于本地请求服务器，只能在注册过程中完成配置和目标节点之间这种映射，但在 Azure 自动化中，可以在 UI 中或者通过其 cmdlet 轻松完成这些更改。 若要更改分配给本地请求服务器目标节点的配置，可以重新运行注册。

### 多个/部分配置

如果将多个配置名称分配给单个目标节点，它们将被视为部分配置。 为了使这种方式生效，必须配置目标节点上的元配置，使其接受部分配置。 **注意：**仅本地请求服务器上支持这种操作。 Azure 自动化不支持部分配置。

## 注册

由于配置名称不再是 GUID（它们现在是友好名称），因此任何人都可能猜到它们。 为了缓解与此相关的固有安全性问题，我们在节点可以从服务器开始请求配置前添加了一个注册步骤。 节点将使用（节点和服务器均已知的）共享密钥和它将请求的配置的名称（可选）将其自身注册到请求服务器。 此共享密钥对每台计算机不必是唯一的。 假设：共享密钥是难以猜测的标识符，比如 GUID。 此共享密钥由目标节点元配置中的 **RegistrationKey** 属性定义。

### 示例元配置

```powershell
[DscLocalConfigurationManager()]
Configuration SampleMetaConfig
{
    Settings
    {
        RefreshMode = "PULL";
        AllowModuleOverwrite = $true;
        RebootNodeIfNeeded = $true;
        ConfigurationModeFrequencyMins = 60;
    }

    ConfigurationRepositoryWeb ConfigurationManager
    {
        ServerURL = “https://PullServerMachine:8080/psdscpullserver.svc”
        RegistrationKey = "140a952b-b9d6-406b-b416-e0f759c9c0e4"
        ConfigurationNames = @(“WebRole”)
    }
}

SampleMetaConfig
```

必须由请求服务器在其上定义 RegistrationKey 值。 为了在设置请求服务器时执行此操作，请在特定位置创建名为 **RegistrationKeys.txt** 的文本文件，然后在请求服务器的 web.config 中设置此位置，如下所示。  

```XML
<add key="ConfigurationPath" value="C:\Program Files\WindowsPowerShell\DscService\Configuration">

<add key="ModulePath" value="C:\Program Files\WindowsPowerShell\DscService\Modules">

<add key="RegistrationKeyPath" value="C:\Program Files\WindowsPowerShell\DscService">
```

使用 xDSCWebService DSC 资源的最新版本完全部署与此搭配使用的本地请求服务器。 请参阅[示例配置](https://github.com/grayzu/PSSummitEU2015/blob/master/PullServer/02%20-%20PullServer%20Config.ps1)以获取完整配置。

**注意：**将请求服务器设置为文件共享时不支持此功能。 仅基于 Web 的请求服务器支持它。<!--HONumber=Mar16_HO2-->
