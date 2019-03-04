---
title: HelpInfo XML 示例文件 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6544070f-5549-407f-8603-5df60fe9e013
caps.latest.revision: 7
ms.openlocfilehash: 11804db56ec47554e82f04fe6954920ad9577370
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856633"
---
# <a name="helpinfo-xml-sample-file"></a><span data-ttu-id="b1363-102">HelpInfo XML 示例文件</span><span class="sxs-lookup"><span data-stu-id="b1363-102">HelpInfo XML Sample File</span></span>

<span data-ttu-id="b1363-103">本主题将显示格式正确的可更新帮助信息文件，通常称为"HelpInfo XML 文件。"的示例</span><span class="sxs-lookup"><span data-stu-id="b1363-103">This topic displays a sample of a well-formed Updatable Help Information file, commonly known as "HelpInfo XML file."</span></span> <span data-ttu-id="b1363-104">此示例文件中的 UI 区域性元素是按字母顺序排列的 UI 区域性名称。</span><span class="sxs-lookup"><span data-stu-id="b1363-104">In this sample file, the UI culture elements are arranged in alphabetical order by UI culture name.</span></span> <span data-ttu-id="b1363-105">按字母顺序排序最佳做法，但不需要。</span><span class="sxs-lookup"><span data-stu-id="b1363-105">Alphabetical ordering is a best practice, but it is not required.</span></span>

## <a name="helpinfo-xml-sample-file"></a><span data-ttu-id="b1363-106">HelpInfo XML 示例文件</span><span class="sxs-lookup"><span data-stu-id="b1363-106">HelpInfo XML Sample File</span></span>

```xml

<?xml version="1.0" encoding="utf-8"?>
<HelpInfo xmlns="http://schemas.microsoft.com/powershell/help/2010/05">
   <HelpContentURI>http://go.microsoft.com/fwlink/?LinkID=141553</HelpContentURI>
   <SupportedUICultures>
    <UICulture>
      <UICultureName>de-DE</UICultureName>
      <UICultureVersion>2.15.0.10</UICultureVersion>
    </UICulture>
    <UICulture>
      <UICultureName>en-US</UICultureName>
      <UICultureVersion>3.2.0.7</UICultureVersion>
    </UICulture>
    <UICulture>
      <UICultureName>it-IT</UICultureName>
      <UICultureVersion>1.1.0.5</UICultureVersion>
    </UICulture>
    <UICulture>
      <UICultureName>ja-JP</UICultureName>
      <UICultureVersion>3.2.0.4</UICultureVersion>
    </UICulture>
   </SupportedUICultures>
</HelpInfo>

```