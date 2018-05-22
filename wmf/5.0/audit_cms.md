---
ms.date: 06/12/2017
keywords: wmf,powershell,安装程序
ms.openlocfilehash: 14208e3b5d5c2fef80fa42a87cc00aeee81bd042
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2018
---
# <a name="cryptographic-message-syntax-cms-cmdlets"></a><span data-ttu-id="59975-102">加密消息语法 (CMS) cmdlet</span><span class="sxs-lookup"><span data-stu-id="59975-102">Cryptographic Message Syntax (CMS) cmdlets</span></span>

<span data-ttu-id="59975-103">加密消息语法 cmdlet 对使用 IETF 标准格式加密保护消息的内容提供加密和解密支持，如 [RFC5652](https://tools.ietf.org/html/rfc5652).中所述。</span><span class="sxs-lookup"><span data-stu-id="59975-103">The Cryptographic Message Syntax cmdlets support encryption and decryption of content using the IETF standard format for cryptographically protecting messages as documented by [RFC5652](https://tools.ietf.org/html/rfc5652).</span></span>

```powershell
Get-CmsMessage [-Content] <string>
Get-CmsMessage [-Path] <string>
Get-CmsMessage [-LiteralPath] <string>
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Content] <string> [[-OutFile] <string>]
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-Path] <string> [[-OutFile] <string>]
Protect-CmsMessage [-To] <CmsMessageRecipient[]> [-LiteralPath] <string> [[-OutFile] <string>]
Unprotect-CmsMessage [-EventLogRecord] <EventLogRecord> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
Unprotect-CmsMessage [-Content] <string> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
Unprotect-CmsMessage [-Path] <string> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
Unprotect-CmsMessage [-LiteralPath] <string> [[-To] <CmsMessageRecipient[]>] [-IncludeContext]
```

<span data-ttu-id="59975-104">CMS 加密标准采用公钥加密系统，其中用来加密内容的密匙（*公匙*）和用来解密内容的密匙（*私匙*）是分离的。</span><span class="sxs-lookup"><span data-stu-id="59975-104">The CMS encryption standard implements public key cryptography, where the keys used to encrypt content (the *public key*) and the keys used to decrypt content (the *private key*) are separate.</span></span>

<span data-ttu-id="59975-105">公匙可以广泛共享，它不是敏感数据。</span><span class="sxs-lookup"><span data-stu-id="59975-105">Your public key can be shared widely, and is not sensitive data.</span></span> <span data-ttu-id="59975-106">如果用此公匙加密了任何内容，只有你的私匙可以解密它。</span><span class="sxs-lookup"><span data-stu-id="59975-106">If any content is encrypted with this public key, only your private key can decrypt it.</span></span> <span data-ttu-id="59975-107">有关详细信息，请参阅 [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography)（公钥加密）。</span><span class="sxs-lookup"><span data-stu-id="59975-107">For more information, see [Public-key cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="59975-108">若要在 PowerShell 中进行识别，加密证书需要唯一的密匙用法标识符 (EKU) 将它们识别为数据加密证书（如“代码签名”标识符、“加密邮件”标识符）。</span><span class="sxs-lookup"><span data-stu-id="59975-108">To be recognized in PowerShell, encryption certificates require a unique key usage identifier (EKU) to identify them as data encryption certificates (like the identifiers for 'Code Signing', 'Encrypted Mail').</span></span>

<span data-ttu-id="59975-109">下面是创建适用于文档加密的证书的示例：</span><span class="sxs-lookup"><span data-stu-id="59975-109">Here is an example of creating a certificate that is good for Document Encryption:</span></span>

```powershell
(Change the text in **Subject** to your name, email, or other identifier), and put in a file (i.e.: DocumentEncryption.inf):
[Version]
Signature = "$Windows NT$"
[Strings]
szOID\_ENHANCED\_KEY\_USAGE = "2.5.29.37"
szOID\_DOCUMENT\_ENCRYPTION = "1.3.6.1.4.1.311.80.1"
[NewRequest]
Subject = "<cn=me@somewhere.com>"
MachineKeySet = false
KeyLength = 2048
KeySpec = AT\_KEYEXCHANGE
HashAlgorithm = Sha1
Exportable = true
RequestType = Cert
KeyUsage = "CERT\_KEY\_ENCIPHERMENT\_KEY\_USAGE | CERT\_DATA\_ENCIPHERMENT\_KEY\_USAGE"
ValidityPeriod = "Years"
ValidityPeriodUnits = "1000"
[Extensions]
%szOID\_ENHANCED\_KEY\_USAGE% = "{text}%szOID\_DOCUMENT\_ENCRYPTION%"
```

<span data-ttu-id="59975-110">然后运行：</span><span class="sxs-lookup"><span data-stu-id="59975-110">Then run:</span></span>
```powershell
certreq -new DocumentEncryption.inf DocumentEncryption.cer
```

<span data-ttu-id="59975-111">现在你可以加密和解密内容：</span><span class="sxs-lookup"><span data-stu-id="59975-111">And you can now encrypt and decrypt content:</span></span>

```powershell
$protected = "Hello World" | Protect-CmsMessage -To "\*me@somewhere.com\*[](mailto:*leeholm@microsoft.com*)"
$protected
-----BEGIN CMS-----
MIIBqAYJKoZIhvcNAQcDoIIBmTCCAZUCAQAxggFQMIIBTAIBADA0MCAxHjAcBgNVBAMMFWxlZWhv
bG1AbWljcm9zb2Z0LmNvbQIQQYHsbcXnjIJCtH+OhGmc1DANBgkqhkiG9w0BAQcwAASCAQAnkFHM
proJnFy4geFGfyNmxH3yeoPvwEYzdnsoVqqDPAd8D3wao77z7OhJEXwz9GeFLnxD6djKV/tF4PxR
E27aduKSLbnxfpf/sepZ4fUkuGibnwWFrxGE3B1G26MCenHWjYQiqv+Nq32Gc97qEAERrhLv6S4R
G+2dJEnesW8A+z9QPo+DwYU5FzD0Td0ExrkswVckpLNR6j17Yaags3ltNVmbdEXekhi6Psf2MLMP
TSO79lv2L0KeXFGuPOrdzPAwCkV0vNEqTEBeDnZGrjv/5766bM3GW34FXApod9u+VSFpBnqVOCBA
DVDraA6k+xwBt66cV84OHLkh0kT02SIHMDwGCSqGSIb3DQEHATAdBglghkgBZQMEASoEEJbJaiRl
KMnBoD1dkb/FzSWAEBaL8xkFwCu0e1ZtDj7nSJc=
-----END CMS-----

$protected | Unprotect-CmsMessage
Hello World
```

<span data-ttu-id="59975-112">类型 **CMSMessageRecipient** 的所有参数都支持下列格式的标识符：</span><span class="sxs-lookup"><span data-stu-id="59975-112">Any parameter of type **CMSMessageRecipient** supports identifiers in the following formats:</span></span>
- <span data-ttu-id="59975-113">实际证书（从证书提供程序检索到的）</span><span class="sxs-lookup"><span data-stu-id="59975-113">An actual certificate (as retrieved from the certificate provider)</span></span>
- <span data-ttu-id="59975-114">指向包含证书的文件的路径</span><span class="sxs-lookup"><span data-stu-id="59975-114">Path to the a file containing the certificate</span></span>
- <span data-ttu-id="59975-115">指向包含证书的目录的路径</span><span class="sxs-lookup"><span data-stu-id="59975-115">Path to a directory containing the certificate</span></span>
- <span data-ttu-id="59975-116">证书的指纹（用于在证书存储区查找）</span><span class="sxs-lookup"><span data-stu-id="59975-116">Thumbprint of the certificate (used to look in the certificate store)</span></span>
- <span data-ttu-id="59975-117">证书的使用者名称（用于在证书存储区查找）</span><span class="sxs-lookup"><span data-stu-id="59975-117">Subject name of the certificate (used to look in the certificate store)</span></span>

<span data-ttu-id="59975-118">若要在证书提供程序中查看文档加密证书，可以使用 **-DocumentEncryptionCert** 动态参数：</span><span class="sxs-lookup"><span data-stu-id="59975-118">To view document encryption certificates in the certificate provider, you can use the **-DocumentEncryptionCert** dynamic parameter:</span></span>

```powershell
dir -DocumentEncryptionCert
```
