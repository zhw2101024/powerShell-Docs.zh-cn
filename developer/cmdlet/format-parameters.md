---
title: 设置参数的格式 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10e025c5-9aa6-45a5-b851-23d14db1f4cc
caps.latest.revision: 7
ms.openlocfilehash: 0bd3888d81aa6d1dde26c0066f7bca9dac8a8bca
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068107"
---
# <a name="format-parameters"></a><span data-ttu-id="1eeda-102">格式参数</span><span class="sxs-lookup"><span data-stu-id="1eeda-102">Format Parameters</span></span>

<span data-ttu-id="1eeda-103">下表列出了建议的名称和参数，用于设置格式或生成数据的功能。</span><span class="sxs-lookup"><span data-stu-id="1eeda-103">The following table lists recommended names and functionality for parameters that are used to format or to generate data.</span></span>

|<span data-ttu-id="1eeda-104">参数</span><span class="sxs-lookup"><span data-stu-id="1eeda-104">Parameter</span></span>|<span data-ttu-id="1eeda-105">功能</span><span class="sxs-lookup"><span data-stu-id="1eeda-105">Functionality</span></span>|
|---|---|
|<span data-ttu-id="1eeda-106">**As**</span><span class="sxs-lookup"><span data-stu-id="1eeda-106">**As**</span></span><br><span data-ttu-id="1eeda-107">数据类型：关键字</span><span class="sxs-lookup"><span data-stu-id="1eeda-107">Data type: Keyword</span></span>|<span data-ttu-id="1eeda-108">实现此参数来指定 cmdlet 的输出格式。</span><span class="sxs-lookup"><span data-stu-id="1eeda-108">Implement this parameter to specify the cmdlet output format.</span></span> <span data-ttu-id="1eeda-109">例如，可能的值可以是文本或脚本。</span><span class="sxs-lookup"><span data-stu-id="1eeda-109">For example, possible values could be Text or Script.</span></span>|
|<span data-ttu-id="1eeda-110">**二进制文件**</span><span class="sxs-lookup"><span data-stu-id="1eeda-110">**Binary**</span></span><br><span data-ttu-id="1eeda-111">数据类型：SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="1eeda-111">Data type: SwitchParameter</span></span>|<span data-ttu-id="1eeda-112">实现此参数以指示该 cmdlet 处理二进制值。</span><span class="sxs-lookup"><span data-stu-id="1eeda-112">Implement this parameter to indicate that the cmdlet handles binary values.</span></span>|
|<span data-ttu-id="1eeda-113">**编码**</span><span class="sxs-lookup"><span data-stu-id="1eeda-113">**Encoding**</span></span><br><span data-ttu-id="1eeda-114">数据类型：关键字</span><span class="sxs-lookup"><span data-stu-id="1eeda-114">Data type: Keyword</span></span>|<span data-ttu-id="1eeda-115">实现此参数来指定支持的编码类型。</span><span class="sxs-lookup"><span data-stu-id="1eeda-115">Implement this parameter to specify the type of encoding that is supported.</span></span> <span data-ttu-id="1eeda-116">例如，可能的值可能是 ASCII、 UTF8、 Unicode、 UTF7、 BigEndianUnicode、 字节、 和字符串。</span><span class="sxs-lookup"><span data-stu-id="1eeda-116">For example, possible values could be ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte, and String.</span></span>|
|<span data-ttu-id="1eeda-117">**NewLine**</span><span class="sxs-lookup"><span data-stu-id="1eeda-117">**NewLine**</span></span><br><span data-ttu-id="1eeda-118">数据类型：SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="1eeda-118">Data type: SwitchParameter</span></span>|<span data-ttu-id="1eeda-119">实现此参数，以便指定该参数时，支持换行字符。</span><span class="sxs-lookup"><span data-stu-id="1eeda-119">Implement this parameter so that the newline characters are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="1eeda-120">**ShortName**</span><span class="sxs-lookup"><span data-stu-id="1eeda-120">**ShortName**</span></span><br><span data-ttu-id="1eeda-121">数据类型：SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="1eeda-121">Data type: SwitchParameter</span></span>|<span data-ttu-id="1eeda-122">实现此参数，以便指定该参数时，支持的短名称。</span><span class="sxs-lookup"><span data-stu-id="1eeda-122">Implement this parameter so that short names are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="1eeda-123">**Width**</span><span class="sxs-lookup"><span data-stu-id="1eeda-123">**Width**</span></span><br><span data-ttu-id="1eeda-124">数据类型：Int32</span><span class="sxs-lookup"><span data-stu-id="1eeda-124">Data type: Int32</span></span>|<span data-ttu-id="1eeda-125">实现此参数，以便用户可以指定输出设备的宽度。</span><span class="sxs-lookup"><span data-stu-id="1eeda-125">Implement this parameter so that the user can specify the width of the output device.</span></span>|
|<span data-ttu-id="1eeda-126">**Wrap**</span><span class="sxs-lookup"><span data-stu-id="1eeda-126">**Wrap**</span></span><br><span data-ttu-id="1eeda-127">数据类型：SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="1eeda-127">Data type: SwitchParameter</span></span>|<span data-ttu-id="1eeda-128">实现此参数，以便指定该参数时，才支持文本换行。</span><span class="sxs-lookup"><span data-stu-id="1eeda-128">Implement this parameter so that text wrapping is supported when the parameter is specified.</span></span>|
## <a name="see-also"></a><span data-ttu-id="1eeda-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1eeda-129">See Also</span></span>

[<span data-ttu-id="1eeda-130">Cmdlet 参数</span><span class="sxs-lookup"><span data-stu-id="1eeda-130">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="1eeda-131">编写 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1eeda-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="1eeda-132">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="1eeda-132">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
