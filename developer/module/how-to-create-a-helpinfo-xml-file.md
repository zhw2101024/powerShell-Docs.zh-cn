---
title: 如何创建 HelpInfo XML 文件 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3971ce1f-271c-4938-a9d3-47ff3aaf7219
caps.latest.revision: 9
ms.openlocfilehash: 7df9764fd573b75f285fec592448a550e481bea3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853263"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a>如何创建 HelpInfo XML 文件

本部分中的本主题说明如何创建和填充的帮助信息文件，通常称为"HelpInfo XML 文件，"Windows PowerShell 可更新帮助功能。

## <a name="helpinfo-xml-file-overview"></a>HelpInfo XML 文件概述

HelpInfo XML 文件是模块的有关可更新帮助信息的主要来源。 它包括模块、 支持的 UI 区域性和可更新帮助使用来确定用户是否具有最新帮助文件的版本号的帮助文件的位置。

每个模块具有一个 HelpInfo XML 文件，即使该模块包含多个 UI 区域性的多个帮助文件。 模块作者创建 HelpInfo XML 文件，并将其放置在由指定的 Internet 位置**HelpInfoUri**密钥模块清单中。 当模块帮助文件进行更新，并上传时，模块作者更新 HelpInfo XML 文件，并使用新版本替换原始的 HelpInfo XML 文件。

请仔细维护 HelpInfo XML 文件至关重要。 如果上传新文件，但忘记递增版本号，可更新帮助将下载到用户的计算机的新文件。 如果你添加为新的 UI 区域性，帮助文件，但不更新 HelpInfo XML 文件或将其放在正确的位置，可更新的帮助不会下载新文件。

## <a name="in-this-section"></a>本部分内容

本部分包括以下主题。

- [HelpInfo XML 架构](./helpinfo-xml-schema.md)

- [HelpInfo XML 示例文件](./helpinfo-xml-sample-file.md)

- [如何命名 HelpInfo XML 文件](./how-to-name-a-helpinfo-xml-file.md)

- [如何设置 HelpInfo XML 版本号](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a>另请参阅

[支持可更新帮助](./supporting-updatable-help.md)