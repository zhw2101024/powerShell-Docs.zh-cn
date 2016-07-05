---
title: "对象管道"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 523d8ae4-d743-47a4-b79a-806130ca688a
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: 56aa32d40d8e5e61f5328d5a373ca5a1bd7ca6e3

---

# 对象管道
管道的行为就像一系列连接的管道段一样。 沿着管道移动的项会通过每个管道段。 若要在 Windows PowerShell 中创建管道，请使用管道运算符“|”将命令连接在一起。 每个命令的输出都将被用作下一命令的输入。

管道可能是命令行界面中使用的最有价值的概念。 正确使用管道不仅可以减少输入复杂命令的工作量，还可使查看命令中的工作流变得更加简单。 管道的相关有用特征是：因为它们单独对每个项进行操作，所以不需要基于你将在管道中拥有零个、一个或多个项而对其进行修改。 此外，管道中的每个命令（称为管道元素）通常将其输出逐项传递到管道中的下一个命令。 这通常会降低复杂命令的资源需求，可让你立即开始获取输出。

在本章中，我们将讲述 Windows PowerShell 管道与最常用 shell 的管道的不同之处，然后介绍一些可用于控制管道输出并查看管道运作方式的基本工具。




<!--HONumber=Jun16_HO4-->


