---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: '启动一致性检查。'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_performrequiredconfigurationchecks'
MSHAttr: 'PreferredLib:/library'
title: 'MSFT_DSCLocalConfigurationManager 类的 PerformRequiredConfigurationChecks 方法'
---

# MSFT_DSCLocalConfigurationManager 类的 PerformRequiredConfigurationChecks 方法

使用任务计划程序启动一致性检查。

语法
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

参数
----------

*Flags* \[in\]  
指定要运行的一致性检查类型的位掩码。 以下值有效，并可以通过 **OR** 位运算组合：

|值 |说明 |
|:--- |:---|
|**1** | 常规的一致性检查。 |
|**2** | 重启后一致性检查的延续。 此值不应与其他值组合。 |
|**4** | 应从节点的元配置中指定的请求服务器请求配置。 此值应始终与 **1** 组合，以获得为 **5** 的值。 |
|**8** | 将状态发送到报表服务器。 |

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


