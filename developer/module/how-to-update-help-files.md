---
title: 如何更新帮助文件 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 495869a6-080e-4401-9ddc-16edd2f86857
caps.latest.revision: 6
ms.openlocfilehash: 2c1fbd70aab1f65f33ea206b7ab1e2bd3dfd8c7a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855523"
---
# <a name="how-to-update-help-files"></a>如何更新帮助文件

本主题说明如何更新支持可更新帮助的模块的帮助文件。

## <a name="updating-help-files"></a>更新帮助文件

原因有很多更新帮助文件，例如更正错误、 阐明概念、 回答常见问题的问题、 添加新文件，或添加新的和更好的示例。

若要更新的帮助文件：

1. 更改的文件。

2. 将文件转换为其他 UI 区域性。

3. 收集有关每个 UI 区域性中模块的所有帮助文件 （new、 已更改，而不变）。

4. 验证针对 XML 架构文件。

5. 重新生成每个 UI 区域性的 CAB 文件。

6. HelpInfo XML 文件中递增每个 UI 区域性的 CAB 文件的版本号。

7. 将新的 CAB 文件上传到指定的值的位置**HelpContentUri** HelpInfo XML 文件中的元素。 较旧的 CAB 文件替换为新的 CAB 文件。

8. 将更新的 HelpInfo XML 文件上传到由指定的位置**HelpInfoUri**密钥模块清单中。 将新文件替换为较早的 HelpInfo XML 文件。