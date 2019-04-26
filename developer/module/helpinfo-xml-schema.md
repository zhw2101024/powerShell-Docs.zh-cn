---
title: HelpInfo XML 架构 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74dcb396-c295-4457-b84c-4432bdaa8df3
caps.latest.revision: 7
ms.openlocfilehash: 0f965f4ee1ef92a6a538b52b4348c04366cabf66
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082458"
---
# <a name="helpinfo-xml-schema"></a>HelpInfo XML 架构

本主题包含可更新帮助信息文件，通常称为"HelpInfo XML 文件。"的 XML 架构

## <a name="helpinfo-xml-schema"></a>HelpInfo XML 架构

HelpInfo XML 文件基于下面的 XML 架构。

```xml
<?xml version="1.0" encoding="utf-8"?>
<schema targetNamespace="http://schemas.microsoft.com/powershell/help/2010/05" xmlns="http://www.w3.org/2001/XMLSchema">
  <element name="HelpInfo">
    <complexType>
      <sequence>
        <element name="HelpContentURI" type="anyURI" minOccurs="1" maxOccurs="1" />
        <element name="SupportedUICultures" minOccurs="1" maxOccurs="1">
          <complexType>
            <sequence>
              <element name="UICulture" minOccurs="1" maxOccurs="unbounded">
                <complexType>
                  <sequence>
                    <element name="UICultureName" type="language" minOccurs="1" maxOccurs="1" />
                    <element name="UICultureVersion" type="string" minOccurs="1" maxOccurs="1" />
                  </sequence>
                </complexType>
              </element>
            </sequence>
          </complexType>
        </element>
      </sequence>
    </complexType>
  </element>
</schema>
```

## <a name="helpinfo-xml-elements"></a>HelpInfo XML 元素

HelpInfo XML 文件包含以下元素。

HelpContentURI 包含帮助有关模块的 CAB 文件的位置的 URI。 URI 必须以"http"或"https"开头。 URI 应指定 Internet 位置，但不能包含 CAB 文件的名称。 **HelpContentURI**值可以是相同或不同于**HelpInfoURI**值。

SupportedUICultures 表示所有 UI 区域性中的模块的帮助文件。 包含**UICulture**元素，其中每个表示一组指定的 UI 区域性中的模块的帮助文件。

UICulture 表示一组指定的 UI 区域性中的模块的帮助文件。 添加**UICulture**为编写的帮助文件所用的每个 UI 区域性的元素。

UICultureName Contains 编写帮助文件所用的 UI 区域性的语言代码。

UICultureVersion 4 部分构成的版本中包含号码"N1。N2。N3。N4"表示版本的 UI 区域性中的帮助 CAB 文件的格式。 此版本号每当上传新的帮助中由指定的 UI 区域性的 CAB 文件便会递增**UICultureName**。 此值的详细信息，请参阅"版本中的类 （系统）"MSDN。