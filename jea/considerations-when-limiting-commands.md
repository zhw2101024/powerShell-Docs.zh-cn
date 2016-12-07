---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "限制命令时的注意事项"
ms.technology: powershell
ms.openlocfilehash: 0b4396ee130d99c42f613c1b79193c236ad472e7
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
### <a name="considerations-when-limiting-commands"></a>限制命令时的注意事项
执行此步骤时有一个重点。
将通过 JEA 公开的所有功能置于仅限管理员的区域，这至关重要。
非管理员用户应不能修改通过 JEA 终结点使用的脚本。

关于这一点请注意，切勿允许 JEA 用户覆盖 JEA 配置和其 JEA 会话中已列入白名单的脚本。
公开 `Copy-Item` 等命令时请格外小心！

