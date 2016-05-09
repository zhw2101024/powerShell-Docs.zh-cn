
# MSFT_DSCLocalConfigurationManager 类的 ApplyConfiguration 方法

使用配置代理应用处于挂起状态的配置。 

如果没有挂起的配置，此方法将重新应用当前配置。


## 语法
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## 参数
----------

*force* \[in\]  
如果为 **true**，将会重新应用当前配置，即使存在挂起的配置。

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


