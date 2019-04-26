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
# <a name="helpinfo-xml-schema"></a><span data-ttu-id="86b4f-102">HelpInfo XML 架构</span><span class="sxs-lookup"><span data-stu-id="86b4f-102">HelpInfo XML Schema</span></span>

<span data-ttu-id="86b4f-103">本主题包含可更新帮助信息文件，通常称为"HelpInfo XML 文件。"的 XML 架构</span><span class="sxs-lookup"><span data-stu-id="86b4f-103">This topic contains the XML schema for Updatable Help Information files, commonly known as "HelpInfo XML files."</span></span>

## <a name="helpinfo-xml-schema"></a><span data-ttu-id="86b4f-104">HelpInfo XML 架构</span><span class="sxs-lookup"><span data-stu-id="86b4f-104">HelpInfo XML Schema</span></span>

<span data-ttu-id="86b4f-105">HelpInfo XML 文件基于下面的 XML 架构。</span><span class="sxs-lookup"><span data-stu-id="86b4f-105">HelpInfo XML files are based on the following XML schema.</span></span>

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

## <a name="helpinfo-xml-elements"></a><span data-ttu-id="86b4f-106">HelpInfo XML 元素</span><span class="sxs-lookup"><span data-stu-id="86b4f-106">HelpInfo XML Elements</span></span>

<span data-ttu-id="86b4f-107">HelpInfo XML 文件包含以下元素。</span><span class="sxs-lookup"><span data-stu-id="86b4f-107">The HelpInfo XML file includes the following elements.</span></span>

<span data-ttu-id="86b4f-108">HelpContentURI 包含帮助有关模块的 CAB 文件的位置的 URI。</span><span class="sxs-lookup"><span data-stu-id="86b4f-108">HelpContentURI Contains the URI of the location of the help CAB files for the module.</span></span> <span data-ttu-id="86b4f-109">URI 必须以"http"或"https"开头。</span><span class="sxs-lookup"><span data-stu-id="86b4f-109">The URI must begin with "http" or "https".</span></span> <span data-ttu-id="86b4f-110">URI 应指定 Internet 位置，但不能包含 CAB 文件的名称。</span><span class="sxs-lookup"><span data-stu-id="86b4f-110">The URI should specify an Internet location, but must not include the CAB file name.</span></span> <span data-ttu-id="86b4f-111">**HelpContentURI**值可以是相同或不同于**HelpInfoURI**值。</span><span class="sxs-lookup"><span data-stu-id="86b4f-111">The **HelpContentURI** value can be the  same or different from the **HelpInfoURI** value.</span></span>

<span data-ttu-id="86b4f-112">SupportedUICultures 表示所有 UI 区域性中的模块的帮助文件。</span><span class="sxs-lookup"><span data-stu-id="86b4f-112">SupportedUICultures Represents the module help files in all UI cultures.</span></span> <span data-ttu-id="86b4f-113">包含**UICulture**元素，其中每个表示一组指定的 UI 区域性中的模块的帮助文件。</span><span class="sxs-lookup"><span data-stu-id="86b4f-113">Contains **UICulture** elements, each of which represents a set of help files for the module in a specified UI culture.</span></span>

<span data-ttu-id="86b4f-114">UICulture 表示一组指定的 UI 区域性中的模块的帮助文件。</span><span class="sxs-lookup"><span data-stu-id="86b4f-114">UICulture Represents a set of help files for the module in a specified UI culture.</span></span> <span data-ttu-id="86b4f-115">添加**UICulture**为编写的帮助文件所用的每个 UI 区域性的元素。</span><span class="sxs-lookup"><span data-stu-id="86b4f-115">Add a **UICulture** element for each UI culture in which the help files are written.</span></span>

<span data-ttu-id="86b4f-116">UICultureName Contains 编写帮助文件所用的 UI 区域性的语言代码。</span><span class="sxs-lookup"><span data-stu-id="86b4f-116">UICultureName Contains the language code for the UI culture in which the help files are written.</span></span>

<span data-ttu-id="86b4f-117">UICultureVersion 4 部分构成的版本中包含号码"N1。N2。N3。N4"表示版本的 UI 区域性中的帮助 CAB 文件的格式。</span><span class="sxs-lookup"><span data-stu-id="86b4f-117">UICultureVersion Contains a 4-part version number in "N1.N2.N3.N4" format that represents the version of the help CAB file in the UI culture.</span></span> <span data-ttu-id="86b4f-118">此版本号每当上传新的帮助中由指定的 UI 区域性的 CAB 文件便会递增**UICultureName**。</span><span class="sxs-lookup"><span data-stu-id="86b4f-118">Increment this version number whenever you upload new help CAB files in the UI culture that is specified by **UICultureName**.</span></span> <span data-ttu-id="86b4f-119">此值的详细信息，请参阅"版本中的类 （系统）"MSDN。</span><span class="sxs-lookup"><span data-stu-id="86b4f-119">For more information about this value, see "Version Class (System)" in MSDN.</span></span>