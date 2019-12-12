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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367136"
---
# <a name="how-to-update-help-files"></a>如何更新帮助文件

本主题说明如何为支持可更新帮助的模块更新帮助文件。

## <a name="updating-help-files"></a>正在更新帮助文件

更新帮助文件的原因有很多，例如，纠正错误、阐明概念、回答经常询问的问题、添加新文件，或者添加更好的更好的示例。

更新帮助文件：

1. 更改文件。

2. 将文件转换为其他 UI 区域性。

3. 收集每个 UI 区域性中的模块的所有帮助文件（新增、更改和未更改）。

4. 对照 XML 架构验证文件。

5. 重新生成每个 UI 区域性的 CAB 文件。

6. 在 HelpInfo XML 文件中，为每个 UI 区域性递增 CAB 文件的版本号。

7. 将新的 CAB 文件上传到 HelpInfo XML 文件中的**HelpContentUri**元素的值指定的位置。 将较旧的 CAB 文件替换为新的 CAB 文件。

8. 将更新后的 HelpInfo XML 文件上传到模块清单中的**HelpInfoUri**键指定的位置。 用新文件替换旧的 HelpInfo XML 文件。