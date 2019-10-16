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
ms.openlocfilehash: 9b4d83aeaf45eab1365dec5fbf48c3c796ed5bde
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369496"
---
# <a name="security-parameters"></a>安全性参数

下表列出了用于为操作提供安全信息的参数的建议名称和功能，如用于指定证书密钥和特权信息的参数。

|参数|功能|
|---|---|
|**ACL**<br>数据类型：字符串|实现此参数可以指定目录或统一资源标识符（URI）的访问控制级别。|
|**CertFile**<br>数据类型：字符串|实现此参数，以便用户可以指定包含以下其中一项的文件的名称：<br>-Base64 或可辨别编码规则（DER）编码的 x.509 证书<br>-公钥加密标准（PKCS） #12 文件，其中至少包含一个证书和密钥|
|**CertIssuerName**<br>数据类型：字符串|实现此参数，以便用户可以指定证书的颁发者的名称，或使用户能够指定子字符串。|
|**CertRequestFile**<br>数据类型：字符串|实现此参数可指定包含 Base64 或 DER 编码的 PKCS #10 证书申请的文件的名称。|
|**CertSerialNumber**<br>数据类型：字符串|实现此参数以指定证书颁发机构颁发的序列号。|
|**CertStoreLocation**<br>数据类型：字符串|实现此参数，以便用户可以指定证书存储区的位置。 位置通常是文件路径。|
|**CertSubjectName**<br>数据类型：字符串|实现此参数，以便用户可以指定证书的颁发者，或使用户能够指定子字符串。|
|**CertUsage**<br>数据类型：字符串|实现此参数以指定密钥用法或增强型密钥用法。 键可以表示为位掩码、位、对象标识符（OID）或字符串。|
|**Credential**<br>数据类型： [system.object](/dotnet/api/System.Management.Automation.PSCredential)|实现此参数以使 cmdlet 自动提示用户输入用户名或密码。 如果未直接提供完整凭据，则将显示这两个系统的提示。|
|**CSPName**<br>数据类型：字符串|实现此参数，以便用户可以指定证书服务提供程序（CSP）的名称。|
|**CSPType**<br>数据类型：整数|实现此参数，以便用户可以指定 CSP 的类型。|
|**组**<br>数据类型：字符串|实现此参数，以便用户可以指定访问主体的集合。 有关详细信息，请参阅**Principal**参数的描述。|
|**KeyAlgorithm**<br>数据类型：字符串|实现此参数，以便用户可以指定要用于安全的密钥生成算法。|
|**Cspparameters.keycontainername**<br>数据类型：字符串|实现此参数，以便用户可以指定密钥容器的名称。|
|**KeyLength**<br>数据类型：整数|实现此参数以使用户能够以位为单位指定密钥的长度。|
|**运作**<br>数据类型：字符串|实现此参数，以便用户可以指定可以对受保护的对象执行的操作。|
|**作主**<br>数据类型：字符串|实现此参数，以便用户可以指定唯一可识别的实体进行访问。|
|**特权**<br>数据类型：字符串|实现此参数，以便用户可以指定 cmdlet 对特定实体执行操作所需的权限。|
|**权限**<br>数据类型：权限阵列|实现此参数，以便用户可以指定 cmdlet 对特定条目执行其操作所需的权限。|
|**职位**<br>数据类型：字符串|实现此参数，以便用户可以指定可由实体执行的一组操作。|
|**SaveCred**<br>数据类型： SwitchParameter|实现此参数，以便在指定参数时使用之前保存的凭据。|
|**内**<br>数据类型：字符串|实现此参数，以便用户可以为 cmdlet 指定受保护的对象组。|
|**SID**<br>数据类型：字符串|实现此参数，以便用户可以指定表示主体的唯一标识符。|
|**受信任**<br>数据类型： SwitchParameter|实现此参数，以便在指定参数时支持信任级别。|
|**TrustLevel**<br>数据类型：关键字|实现此参数，以便用户可以指定受支持的信任级别。 例如，可能的值包括 internet、intranet 和 fulltrust。|

## <a name="see-also"></a>另请参阅

[Cmdlet 参数](./cmdlet-parameters.md)

[编写 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
