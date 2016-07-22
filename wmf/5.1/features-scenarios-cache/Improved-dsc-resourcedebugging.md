---
title: "DSC 资源调试改进"
author: jaimeo
contributor: amitsara
translationtype: Human Translation
ms.sourcegitcommit: e39aa2e5cbda0c83e24e21c4459d957d8baaff25
ms.openlocfilehash: 33c3fcffdeb281b205ecc48f7cdd470b79e9e068

---


## DSC 资源调试改进

在 WMF 5.0 中，PowerShell 调试器无法直接在类资源方法（Get/Set/Test）处停止。
我们已经修复了这个问题，和基于 mof 的资源方法一样，现在调试器也可以在类资源方法处停止。



<!--HONumber=Jul16_HO3-->


