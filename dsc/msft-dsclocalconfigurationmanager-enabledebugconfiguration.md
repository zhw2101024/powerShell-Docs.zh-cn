---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: '启用调试 DSC 配置。'
MS-HAID: 'cimwin32a.msft\_dsclocalconfigurationmanager\_enabledebugconfiguration'
MSHAttr: 'PreferredLib:/library'
title: 'MSFT_DSCLocalConfigurationManager 类的 EnableDebugConfiguration 方法'
---

# MSFT_DSCLocalConfigurationManager 类的 EnableDebugConfiguration 方法

启用 DSC 资源调试。

语法
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

参数
----------

*BreakAll* \[in\]  
在资源脚本中的每一行设置断点。

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


