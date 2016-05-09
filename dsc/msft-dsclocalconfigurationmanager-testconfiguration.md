---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: '将配置文档发送到托管节点，并针对当前配置进行测试。'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_testconfiguration'
MSHAttr: 'PreferredLib:/library'
title: 'MSFT_DSCLocalConfigurationManager 类的 TestConfiguration 方法'
---

# MSFT_DSCLocalConfigurationManager 类的 TestConfiguration 方法

将配置文档发送到托管节点并针对该文档验证当前配置。

语法
------

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

参数
----------

*configurationData* \[in\]  
配置的环境数据。

*InDesiredState* \[out\]  
返回时，指定托管节点是否处于配置文档指定的状态。

*ResourcesInDesiredState* \[out\]  
返回时，包含 **MSFT_ResourceInDesiredState** 类的嵌入实例，该类指定处于所需状态的资源。

*ResourcesNotInDesiredState* \[out\]  
返回时，包含 **MSFT_ResourceNotInDesiredState** 类的嵌入实例，该类指定未在所需状态的资源。

## 返回值
------------

如果成功，则返回零；否则返回错误代码。

## 备注

这是一种静态方法。

## 要求
------------
>**MOF：** DscCore.mof

>**命名空间**：Root\Microsoft\Windows\DesiredStateConfiguration


## 另请参阅


[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)


 

 





<!--HONumber=Apr16_HO2-->


