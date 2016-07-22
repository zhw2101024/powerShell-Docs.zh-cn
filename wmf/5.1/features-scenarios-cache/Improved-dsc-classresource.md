---
title: "DSC 类资源改进"
author: jaimeo
contributor: amitsara
translationtype: Human Translation
ms.sourcegitcommit: e39aa2e5cbda0c83e24e21c4459d957d8baaff25
ms.openlocfilehash: b24e70c1e1aaf71487b00fbccaf6edb0f375b888

---

## DSC 类资源改进

在本版本中，我们解决了 WMF 5.0 中已知的以下问题：
* 如果基于类的 DSC 资源的 Get() 函数返回复杂/哈希表类型，则 Get-DscConfiguration 可能会返回空值 (null) 或错误。
* 如果在 DSC 配置中使用 RunAs 凭据，Get-DscConfiguration 将返回错误。
* 不能在复合配置中使用基于类的资源。
* 如果基于类的资源具有和自己类型一样的属性，Start-DscConfiguration 将挂起。
* 基于类的资源不能用作独占资源。



<!--HONumber=Jul16_HO3-->


