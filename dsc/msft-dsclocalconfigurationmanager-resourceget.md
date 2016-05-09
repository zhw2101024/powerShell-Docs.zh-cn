---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: '在提供程序上直接执行 Get。'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_resourceget'
MSHAttr: 'PreferredLib:/library'
title: 'MSFT_DSCLocalConfigurationManager 类的 ResourceGet 方法'
---

# MSFT_DSCLocalConfigurationManager 类的 ResourceGet 方法

直接调用 DSC 资源的 **Get** 方法。

语法
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

参数
----------

*ResourceType* \[in\]  
要调用的资源的名称。

*ModuleName* \[in\]  
包含要调用的资源的模块名称。

*resourceProperty* \[in\]  
分别在哈希表中将资源属性名称及其值指定为键和值。 使用
[Get-dscresource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet 以发现资源属性及其类型。

*configurations* \[out\]  
在返回时包含配置的嵌入实例。

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


