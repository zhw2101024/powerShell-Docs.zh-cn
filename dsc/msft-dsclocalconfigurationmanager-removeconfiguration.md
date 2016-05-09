---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: '删除配置文件。'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_removeconfiguration'
MSHAttr: 'PreferredLib:/library'
title: 'MSFT_DSCLocalConfigurationManager 类的 RemoveConfiguration 方法'
---

# MSFT_DSCLocalConfigurationManager 类的 RemoveConfiguration 方法

删除配置文件。

语法
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

参数
----------

*Stage* \[in\]  
指定要删除的配置文档。 下面的值是有效的：

|值 |说明 |
|:--- |:---|
|**1** | **当前**配置文档 (current.mof)。 |
|**2** | **挂起的**配置文档 (pending.mof)。  |
|**4** | **以前的**配置文档 (previous.mof)。 |

*Force* \[in\]  
为 **true**，则强制删除配置。

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


