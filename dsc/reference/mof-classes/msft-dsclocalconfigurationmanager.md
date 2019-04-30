---
ms.date: 06/12/2017
keywords: dsc,powershell,配置,安装程序
title: MSFT_DSCLocalConfigurationManager 类
ms.openlocfilehash: 7f6aaf209601e99b0120407eb301d32fcfda9eb8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078055"
---
# <a name="msftdsclocalconfigurationmanager-class"></a>MSFT_DSCLocalConfigurationManager 类

控制配置文件的状态并使用配置代理应用配置的本地配置管理器 (LCM)。

以下语法从托管对象格式 (MOF) 代码中简化，包括所有继承的属性。

## <a name="syntax"></a>语法

```
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## <a name="members"></a>成员

**MSFT_DSCLocalConfigurationManager** 类拥有以下成员：

- [Methods][]

### <a name="methods"></a>方法

**MSFT_DSCLocalConfigurationManager** 类拥有这些方法。

|方法 |说明 |
|:--- |:---|
| [ApplyConfiguration](msft-dsclocalconfigurationmanager-applyconfiguration.md)| 使用配置代理应用处于挂起状态的配置。|
| [DisableDebugConfiguration](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| 禁用 DSC 资源调试。|
| [EnableDebugConfiguration](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| 启用 DSC 资源调试。|
| [GetConfiguration](msft-dsclocalconfigurationmanager-getconfiguration.md)| 将配置文档发送到托管节点，并使用配置代理的 **Get** 方法以应用配置。|
| [GetConfigurationResultOutput](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| 获取与特定作业相关的配置代理输出。|
| [GetConfigurationStatus](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| 获取配置状态历史记录。|
| [GetMetaConfiguration](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| 获取用于控制配置代理的 LCM 设置。|
| [PerformRequiredConfigurationChecks](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| 启动一致性检查。|
| [RemoveConfiguration](msft-dsclocalconfigurationmanager-removeconfiguration.md)| 删除配置文件。|
| [ResourceGet](msft-dsclocalconfigurationmanager-resourceget.md)| 直接调用 DSC 资源的 **Get** 方法。|
| [ResourceSet](msft-dsclocalconfigurationmanager-resourceset.md)| 直接调用 DSC 资源的 **Set** 方法。|
| [ResourceTest](msft-dsclocalconfigurationmanager-resourcetest.md)| 直接调用 DSC 资源的 **Test** 方法。|
| [RollBack](msft-dsclocalconfigurationmanager-rollback.md)| 回滚到以前的配置。|
| [SendConfiguration](msft-dsclocalconfigurationmanager-sendconfiguration.md)| 将配置文档发送到托管节点并将其保存为挂起的更改。|
| [SendConfigurationApply](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| 将配置文档发送到托管节点，并使用配置代理应用配置。|
| [SendConfigurationApplyAsync](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| 将配置文档发送到托管节点，并开始使用配置代理应用配置。 使用 GetConfigurationResultOutput 检索结果输出。|
| [SendMetaConfigurationApply](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| 设置用于控制配置代理的 LCM 设置。|
| [StopConfiguration](msft-dsclocalconfigurationmanager-stopconfiguration.md)| 停止正在进行的配置。|
| [TestConfiguration](msft-dsclocalconfigurationmanager-testconfiguration.md)| 将配置文档发送到托管节点并针对该文档验证当前配置。|

## <a name="requirements"></a>要求

**MOF：** DscCore.mof

**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration