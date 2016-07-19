---
title: "“using module”的 FullyQuilifiedModuleName"
author: jaimeo
contributor: vors
translationtype: Human Translation
ms.sourcegitcommit: e39aa2e5cbda0c83e24e21c4459d957d8baaff25
ms.openlocfilehash: e09cfe0994ac523fd10658955731a93b6c176c88

---

“using module”的 FullyQuilifiedModuleName
=========================

现在，`using module` 的行为方式与 PowerShell 中其他与模块相关的构造相同。

WMF 5.0 问题
----------

* 用户无法在 `using module` 中指定模块版本。
* 如果系统上有多个版本的模板可用，则用户会收到错误。

WMF 5.1
----------

* 用户可以使用 `ModuleSpecification` [哈希表](https://msdn.microsoft.com/en-us/library/jj136290(v=vs.85).aspx)。 此哈希表具有与以下对象相同的格式： `Get-Module -FullyQualifiedName`

**例如：** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

* 如果有多个版本的模块，则 powershell 会使用与 `Import-Module` **相同的解析逻辑**，不会出错。

* 这使 `using module` 与 `Import-Module` 和 `Import-DscResource` 一致。



<!--HONumber=Jul16_HO3-->


