# 加密消息语法 (CMS) cmdlet

加密消息语法 cmdlet 对使用 IETF 标准格式加密保护消息的内容提供加密和解密支持，如 [RFC5652](http://tools.ietf.org/html/rfc5652).中所述。

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

CMS 加密标准采用公钥加密系统，其中用来加密内容的密匙（*公匙*）和用来解密内容的密匙（*私匙*）是分离的。

公匙可以广泛共享，它不是敏感数据。 如果用此公匙加密了任何内容，只有你的私匙可以解密它。 有关公钥加密的详细信息，请参阅：<http://en.wikipedia.org/wiki/Public-key_cryptography>。

若要在 PowerShell 中进行识别，加密证书需要唯一的密匙用法标识符 (EKU) 将它们识别为数据加密证书（如“代码签名”标识符、“加密邮件”标识符）。

下面是创建适用于文档加密的证书的示例：

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

然后运行：
```powershell
certreq -new DocumentEncryption.inf DocumentEncryption.cer
```

现在你可以加密和解密内容：

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

类型 **CMSMessageRecipient** 的所有参数都支持下列格式的标识符：
- 实际证书（从证书提供程序检索到的）
- 指向包含证书的文件的路径
- 指向包含证书的目录的路径
- 证书的指纹（用于在证书存储区查找）
- 证书的使用者名称（用于在证书存储区查找）

若要在证书提供程序中查看文档加密证书，可以使用 **-DocumentEncryptionCert** 动态参数：

```powershell
dir -DocumentEncryptionCert
```

<!--HONumber=Jun16_HO4-->


