---
title: 安全参数 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e199bba3-90d3-41ca-9d78-cb502e58508d
caps.latest.revision: 6
ms.openlocfilehash: c8b3f907a80d1f6125a5ac04236245503db76ed0
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251296"
---
# <a name="security-parameters"></a>安全性参数

下表列出了建议的名称和使用提供的操作，如参数指定证书密钥和特权信息的安全信息的参数的功能。

|参数|功能|
|---|---|
|**ACL**<br>数据类型：字符串|实现此参数以指定的目录或为统一资源标识符 (URI) 保护的访问控制级别。|
|**CertFile**<br>数据类型：字符串|实现此参数，以便用户可以指定包含以下项之一的文件的名称：<br>-A Base64 或可分辨编码规则 (DER) 编码的 x.509 证书<br>的包含至少一个证书和密钥公钥加密标准 (PKCS) #12 文件|
|**CertIssuerName**<br>数据类型：字符串|实现此参数，以便用户可以指定证书的颁发者的名称或，以便用户可以指定子字符串。|
|**CertRequestFile**<br>数据类型：字符串|实现此参数以指定包含 Base64 或 DER 编码的 PKCS #10 证书申请的文件的名称。|
|**CertSerialNumber**<br>数据类型：字符串|实现此参数以指定由证书颁发机构颁发的序列号。|
|**CertStoreLocation**<br>数据类型：字符串|实现此参数，以便用户可以指定证书存储区的位置。 该位置通常是文件路径。|
|**CertSubjectName**<br>数据类型：字符串|实现此参数，以便用户可以指定证书的颁发者或，以便用户可以指定子字符串。|
|**CertUsage**<br>数据类型：字符串|实现此参数以指定的密钥用法或增强型密钥用法。 可以表示密钥的位掩码，有点，对象标识符 (OID)，或一个字符串。|
|**凭据**<br>数据类型：[System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)|实现此参数，使该 cmdlet 将自动提示用户输入用户名或密码。 如果未直接提供完整的凭据，则会显示两个提示。|
|**CSPName**<br>数据类型：字符串|实现此参数，以便用户可以指定证书服务提供商 (CSP) 的名称。|
|**CSPType**<br>数据类型：整数|实现此参数，以便用户可以指定 CSP 的类型。|
|**组**<br>数据类型：字符串|实现此参数，以便用户可以指定用于访问权限的主体的集合。 有关详细信息，请参阅的说明**主体**参数。|
|**KeyAlgorithm**<br>数据类型：字符串|实现此参数，以便用户可以指定要用于安全密钥生成算法。|
|**KeyContainerName**<br>数据类型：字符串|实现此参数，以便用户可以指定密钥容器的名称。|
|**KeyLength**<br>数据类型：整数|实现此参数，以便用户可以以位为单位指定的密钥的长度。|
|**Operation**<br>数据类型：字符串|实现此参数，以便用户可以指定可在受保护的对象执行的操作。|
|**主体**<br>数据类型：字符串|实现此参数，以便用户可以指定访问权限的唯一标识实体。|
|**特权**<br>数据类型：字符串|实现此参数，以便用户可以指定一个 cmdlet 需要对其执行的特定实体的操作的权限。|
|**权限**<br>数据类型：权限的数组|实现此参数，以便用户可以指定一个 cmdlet 需要用来执行其操作特定的项的权限。|
|**Role**<br>数据类型：字符串|实现此参数，以便用户可以指定一组可由一个实体执行的操作。|
|**SaveCred**<br>数据类型：SwitchParameter|实现此参数，以便指定该参数时，将使用已由用户以前保存的凭据。|
|**范围**<br>数据类型：字符串|实现此参数，以便用户可以指定有关该 cmdlet 的受保护对象的组。|
|**SID**<br>数据类型：字符串|实现此参数，以便用户可以指定表示一个主体的唯一标识符。|
|**受信任**<br>数据类型：SwitchParameter|实现此参数，以便指定该参数时，支持信任级别。|
|**TrustLevel**<br>数据类型：关键字|实现此参数，以便用户可以指定支持的信任级别。 例如，可能值包括 internet、 intranet 和 fulltrust。|

## <a name="see-also"></a>另请参阅

[Cmdlet 参数](./cmdlet-parameters.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
