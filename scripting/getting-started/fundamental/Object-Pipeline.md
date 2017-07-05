---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "对象管道"
ms.assetid: 523d8ae4-d743-47a4-b79a-806130ca688a
ms.openlocfilehash: 3fa41cc744cf3ab66fc5ef186ead8eb919429a76
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2017
---
# <a name="object-pipeline"></a>对象管道
管道的行为就像一系列连接的管道段一样。 沿着管道移动的项会通过每个管道段。 若要在 Windows PowerShell 中创建管道，请使用管道运算符“|”将命令连接在一起。 每个命令的输出都将被用作下一命令的输入。

管道可能是命令行界面中使用的最有价值的概念。 正确使用管道不仅可以减少输入复杂命令的工作量，还可使查看命令中的工作流变得更加简单。 管道的相关有用特征是：因为它们单独对每个项进行操作，所以不需要基于你将在管道中拥有零个、一个或多个项而对其进行修改。 此外，管道中的每个命令（称为管道元素）通常将其输出逐项传递到管道中的下一个命令。 这通常会降低复杂命令的资源需求，可让你立即开始获取输出。

在本章中，我们将讲述 Windows PowerShell 管道与最常用 shell 的管道的不同之处，然后介绍一些可用于控制管道输出并查看管道运作方式的基本工具。

