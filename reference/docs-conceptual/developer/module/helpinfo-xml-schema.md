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
ms.openlocfilehash: 8142a620f0f71de3d2a6b33fc2e45092b5743a54
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/04/2020
ms.locfileid: "76996009"
---
# <a name="helpinfo-xml-schema"></a><span data-ttu-id="92143-102">HelpInfo XML 架构</span><span class="sxs-lookup"><span data-stu-id="92143-102">HelpInfo XML Schema</span></span>

<span data-ttu-id="92143-103">本主题包含可更新帮助信息文件（通常称为 "HelpInfo XML 文件"）的 XML 架构。</span><span class="sxs-lookup"><span data-stu-id="92143-103">This topic contains the XML schema for Updatable Help Information files, commonly known as "HelpInfo XML files."</span></span>

## <a name="helpinfo-xml-schema"></a><span data-ttu-id="92143-104">HelpInfo XML 架构</span><span class="sxs-lookup"><span data-stu-id="92143-104">HelpInfo XML Schema</span></span>

<span data-ttu-id="92143-105">HelpInfo XML 文件基于以下 XML 架构。</span><span class="sxs-lookup"><span data-stu-id="92143-105">HelpInfo XML files are based on the following XML schema.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<schema targetNamespace="https://schemas.microsoft.com/powershell/help/2010/05" xmlns="http://www.w3.org/2001/XMLSchema">
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

## <a name="helpinfo-xml-elements"></a><span data-ttu-id="92143-106">HelpInfo XML 元素</span><span class="sxs-lookup"><span data-stu-id="92143-106">HelpInfo XML Elements</span></span>

<span data-ttu-id="92143-107">HelpInfo XML 文件包含以下元素。</span><span class="sxs-lookup"><span data-stu-id="92143-107">The HelpInfo XML file includes the following elements.</span></span>

<span data-ttu-id="92143-108">HelpContentURI 包含模块的帮助 CAB 文件所在位置的 URI。</span><span class="sxs-lookup"><span data-stu-id="92143-108">HelpContentURI Contains the URI of the location of the help CAB files for the module.</span></span> <span data-ttu-id="92143-109">URI 必须以 "http" 或 "https" 开头。</span><span class="sxs-lookup"><span data-stu-id="92143-109">The URI must begin with "http" or "https".</span></span> <span data-ttu-id="92143-110">URI 应指定 Internet 位置，但不得包含 CAB 文件名称。</span><span class="sxs-lookup"><span data-stu-id="92143-110">The URI should specify an Internet location, but must not include the CAB file name.</span></span> <span data-ttu-id="92143-111">**HelpContentURI**值可以与**HelpInfoURI**值相同或不同。</span><span class="sxs-lookup"><span data-stu-id="92143-111">The **HelpContentURI** value can be the  same or different from the **HelpInfoURI** value.</span></span>

<span data-ttu-id="92143-112">SupportedUICultures 表示所有 UI 区域性中的模块帮助文件。</span><span class="sxs-lookup"><span data-stu-id="92143-112">SupportedUICultures Represents the module help files in all UI cultures.</span></span> <span data-ttu-id="92143-113">包含**UICulture**元素，其中每个元素都表示一组指定 UI 区域性中的模块的帮助文件。</span><span class="sxs-lookup"><span data-stu-id="92143-113">Contains **UICulture** elements, each of which represents a set of help files for the module in a specified UI culture.</span></span>

<span data-ttu-id="92143-114">UICulture 表示指定 UI 区域性中的模块的一组帮助文件。</span><span class="sxs-lookup"><span data-stu-id="92143-114">UICulture Represents a set of help files for the module in a specified UI culture.</span></span> <span data-ttu-id="92143-115">为在其中编写帮助文件的每个 UI 区域性添加一个**UICulture**元素。</span><span class="sxs-lookup"><span data-stu-id="92143-115">Add a **UICulture** element for each UI culture in which the help files are written.</span></span>

<span data-ttu-id="92143-116">UICultureName 包含用于编写帮助文件的 UI 区域性的语言代码。</span><span class="sxs-lookup"><span data-stu-id="92143-116">UICultureName Contains the language code for the UI culture in which the help files are written.</span></span>

<span data-ttu-id="92143-117">UICultureVersion 在 "N1. 中包含由四部分构成的版本号N2.N3.N4 "格式，表示 UI 区域性中 help CAB 文件的版本。</span><span class="sxs-lookup"><span data-stu-id="92143-117">UICultureVersion Contains a 4-part version number in "N1.N2.N3.N4" format that represents the version of the help CAB file in the UI culture.</span></span> <span data-ttu-id="92143-118">每次上传**UICultureName**指定的 UI 区域性中的新帮助 CAB 文件时，请递增此版本号。</span><span class="sxs-lookup"><span data-stu-id="92143-118">Increment this version number whenever you upload new help CAB files in the UI culture that is specified by **UICultureName**.</span></span> <span data-ttu-id="92143-119">有关此值的详细信息，请参阅 MSDN 中的 "版本类（系统）"。</span><span class="sxs-lookup"><span data-stu-id="92143-119">For more information about this value, see "Version Class (System)" in MSDN.</span></span>