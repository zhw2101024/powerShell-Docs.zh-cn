---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "简介"
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: e6b5107b7222708dcceff14bc26f0e12ef98d728
ms.openlocfilehash: 00d568234b1453b9161b60d20117374ee4111ab3

---

# 简介

##  **动机**  
当对某人授予你系统的特许访问权时，即将信任边界扩展至此人。
这会带来风险 -- 管理员会成为受攻击面。
内部攻击和凭据盗窃真实存在并且很常见。

##  **不是新问题**  
你可能非常熟悉最小特权的原则，并将某种形式的基于角色的访问控制 (RBAC) 用于提供最小特权的应用程序。
但是，这些解决方案的有效性和可管理性常受限于其广泛性和不精确性。
此外，RBAC 作用范围中存在缺口。
例如，在 Windows 中，特许访问权很大程度上是一个二进制开关，在将用户添加到“管理员”组时会强制你授予其不必要的权限。

##  **Just Enough Administration (JEA)** 
通过 PowerShell 远程处理提供基于角色的访问控制 (RBAC) 平台。
*它允许特定用户在服务器上执行特定管理任务，而不授予其管理员权限。*
这让你能够填补现有 RBAC 解决方案之间的缺口，并简化了这些设置的管理。




<!--HONumber=Jul16_HO1-->


