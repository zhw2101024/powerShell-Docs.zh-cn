---
title: "改进的请求服务器注册"
author: jaimeo
contributor: Indhu Sivaramakrishnan
translationtype: Human Translation
ms.sourcegitcommit: e39aa2e5cbda0c83e24e21c4459d957d8baaff25
ms.openlocfilehash: d9f7dea63e6541b673ac6be5ccad59368b301440

---

## 改进的请求服务器注册 ##

在 WMF 的早期版本中，在使用 ESENT 数据库时同时向 DSC 请求服务器注册或向其报告请求，将导致 LCM 无法注册和/或报告，具体视情况而定。 在这种情况下，请求服务器上的事件日志将显示错误“Instance Name already in use.（实例名称正在使用中。）”
这是由于在多线程情况下使用不正确的模式访问 ESENT 数据库。 在 WMF 5.1 中已修复此问题。 在 WMF 5.1 中并发的注册或报告（涉及 ESENT 数据库）可以正常工作。 此问题仅适用于 ESENT 数据库，并不适用于 OLEDB 数据库。 



<!--HONumber=Jul16_HO3-->


