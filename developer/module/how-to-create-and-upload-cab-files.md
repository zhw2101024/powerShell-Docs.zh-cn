---
title: 如何创建并上载 CAB 文件 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d35f233-5447-48a2-a961-9fbca763262b
caps.latest.revision: 7
ms.openlocfilehash: 9928a0b31a57d42eb39cea1af0509613c483caf7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858643"
---
# <a name="how-to-create-and-upload-cab-files"></a>如何创建和上传 CAB 文件

本主题说明如何创建可更新帮助的 CAB 文件并将其上载到其中的可更新帮助的 cmdlet 可以找到它们的位置。

## <a name="how-to-create-and-upload-updatable-help-cab-files"></a>如何创建和上传可更新帮助的 CAB 文件

可更新帮助功能可用于提供新的或更新的帮助文件中多个语言和文化的模块。 模块的可更新帮助包包含一个 HelpInfo XML 文件和一个或多个 cab 文件 (。CAB) 文件。 每个 CAB 文件包含一个 UI 区域性中的模块的帮助文件。 使用以下过程来创建可更新帮助的 CAB 文件。

1. 通过 UI 区域性组织模块的帮助文件。 每个可更新帮助的 CAB 文件包含一个 UI 区域性中的一个模块的帮助文件。 你可提供多个帮助的模块，每个不同的 UI 区域性的 CAB 文件。

2. 验证的帮助文件包括允许可更新帮助的文件类型并针对帮助文件架构进行验证。 如果`Update-Help`cmdlet 遇到无效或不允许的类型的文件，它不会安装无效的文件，并停止从 CAB 安装文件。 允许的文件类型的列表，请参阅[可更新帮助 CAB 文件中的文件类型允许](./file-types-permitted-in-an-updatable-help-cab-file.md)。

3. 进行数字签名帮助文件。 数字签名不是必需的但它们是一种最佳做法。

4. 包括所有在 UI 中的模块的文件的区域性，而不仅仅是新的文件或已改变的帮助。 如果不完整的 CAB 文件，第一次下载帮助文件或不下载每个更新，用户不会的所有模块的帮助文件。

5. 使用创建 cabinet 文件，如 MakeCab.exe 实用程序。 Windows PowerShell 不包括创建 CAB 文件的 cmdlet。

6. 命名的 CAB 文件。 有关详细信息，请参阅[如何命名可更新帮助 CAB 文件](./how-to-name-an-updatable-help-cab-file.md)。

7. 将该模块的 CAB 文件上载到指定的位置**HelpContentUri**模块的 HelpInfo XML 文件中的元素。 然后将 HelpInfo XML 文件上载到由指定的位置**HelpInfoUri**模块清单的密钥。 **HelpContentUri**并**HelpInfoUri**可以指向同一位置。

> [!CAUTION]
> 值**HelpInfoUri**密钥和**HelpContentUri**元素必须以"http"或"https"开头。 值必须指示 Internet 位置，并且不包含文件名称。