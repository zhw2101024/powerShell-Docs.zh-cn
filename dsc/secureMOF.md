---
ms.date: 10/31/2017
keywords: dsc,powershell,配置,安装程序
title: 保护 MOF 文件
ms.openlocfilehash: f17c95c951151c0c11057ac0bce172c4ec73c91d
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893257"
---
# <a name="securing-the-mof-file"></a><span data-ttu-id="6b5c8-103">保护 MOF 文件</span><span class="sxs-lookup"><span data-stu-id="6b5c8-103">Securing the MOF File</span></span>

> <span data-ttu-id="6b5c8-104">适用于：Windows PowerShell 4.0 和 Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="6b5c8-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="6b5c8-105">DSC 通过应用存储于 MOF 文件中的信息来管理服务器节点的配置，其中本地配置管理器 (LCM) 在该文件中实现所需的结束状态。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-105">DSC manages the configuration of server nodes by applying information stored in a MOF file, where the Local Configuration Manager (LCM) implements the desired end state.</span></span>
<span data-ttu-id="6b5c8-106">由于此文件包含配置的详细信息，因此确保其安全非常重要。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-106">Because this file contains the details of the configuration, it’s important to keep it secure.</span></span>
<span data-ttu-id="6b5c8-107">本主题介绍如何确保目标节点已加密文件。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-107">This topic describes how to ensure the target node has encrypted the file.</span></span>

<span data-ttu-id="6b5c8-108">自 PowerShell 版本 5.0 起，在将 MOF 文件应用于使用 `Start-DSCConfiguration` cmdlet 的节点时，默认情况下将加密整个 MOF 文件。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-108">Beginning with PowerShell version 5.0, the entire MOF file is encrypted by default when it is applied to the node using the `Start-DSCConfiguration` cmdlet.</span></span>
<span data-ttu-id="6b5c8-109">仅在使用请求服务协议实现解决方案（如果证书未被托管）时，才需用到本文所述相关过程，以确保目标节点下载的配置在被应用之前可由系统解密和读取（例如 Windows Server 中可用的请求服务）。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-109">The process described in this article is required only when implementing a solution using the pull service protocol if certificates are not managed, to ensure configurations downloaded by the target node can be decrypted and read by the system before they are applied (for example, the pull service available in Windows Server).</span></span>
<span data-ttu-id="6b5c8-110">注册到 [Azure 自动化 DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview) 的节点将自动安装证书并使其由服务进行托管，无需承担管理开销。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-110">Nodes registered to [Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview) will automatically have certificates installed and managed by the service with no administrative overhead required.</span></span>

> [!NOTE]
> <span data-ttu-id="6b5c8-111">本主题讨论用于加密的证书。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-111">This topic discusses certificates used for encryption.</span></span>
> <span data-ttu-id="6b5c8-112">对于加密，自签名证书就已足够，因为私钥始终保密，而加密并不表示信任该文档。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-112">For encryption, a self-signed certificate is sufficient, because the private key is always kept secret and encryption does not imply trust of the document.</span></span>
> <span data-ttu-id="6b5c8-113">自签名证书*不*得用于身份验证目的。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-113">Self-signed certificates should *not* be used for authentication purposes.</span></span>
> <span data-ttu-id="6b5c8-114">应使用来自受信任的证书颁发机构 (CA) 的证书进行任何身份验证。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-114">You should use a certificate from a trusted Certification Authority (CA) for any authentication purposes.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6b5c8-115">必备条件</span><span class="sxs-lookup"><span data-stu-id="6b5c8-115">Prerequisites</span></span>

<span data-ttu-id="6b5c8-116">要成功加密所用凭据以保护 DSC 配置，请确保你有以下各项：</span><span class="sxs-lookup"><span data-stu-id="6b5c8-116">To successfully encrypt the credentials used to secure a DSC configuration, make sure you have the following:</span></span>

- <span data-ttu-id="6b5c8-117">**颁发和分发证书的方法**。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-117">**Some means of issuing and distributing certificates**.</span></span> <span data-ttu-id="6b5c8-118">本主题及其中示例假定你使用 Active Directory 证书颁发机构。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-118">This topic and its examples assume you are using Active Directory Certification Authority.</span></span> <span data-ttu-id="6b5c8-119">有关 Active Directory 证书服务的更多背景信息，请参阅 [Active Directory 证书服务概述](https://technet.microsoft.com/library/hh831740.aspx)和 [Windows Server 2008 中的 Active Directory 证书服务](https://technet.microsoft.com/windowsserver/dd448615.aspx)。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-119">For more background information on Active Directory Certificate Services, see [Active Directory Certificate Services Overview](https://technet.microsoft.com/library/hh831740.aspx) and [Active Directory Certificate Services in Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).</span></span>
- <span data-ttu-id="6b5c8-120">**对目标节点的管理访问权限**。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-120">**Administrative access to the target node or nodes**.</span></span>
- <span data-ttu-id="6b5c8-121">**每个目标节点的个人存储区中均保存了可加密的证书**。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-121">**Each target node has an encryption-capable certificate saved its Personal Store**.</span></span> <span data-ttu-id="6b5c8-122">在 Windows PowerShell 中，该存储区的路径为 Cert:\LocalMachine\My。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-122">In Windows PowerShell, the path to the store is Cert:\LocalMachine\My.</span></span> <span data-ttu-id="6b5c8-123">本主题中的示例使用“工作站身份验证”模板，你可以在[默认证书模板](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx)中找到它（以及其他证书模板）。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-123">The examples in this topic use the “workstation authentication” template, which you can find (along with other certificate templates) at [Default Certificate Templates](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).</span></span>
- <span data-ttu-id="6b5c8-124">如果你将在计算机而不是目标节点上运行此配置，请**导出证书的公钥**，然后将其导入到你将要从中运行配置的计算机。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-124">If you will be running this configuration on a computer other than the target node, **export the public key of the certificate**, and then import it to the computer you will run the configuration from.</span></span> <span data-ttu-id="6b5c8-125">请确保仅导出**公**钥；保护私钥安全。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-125">Make sure that you export only the **public** key; keep the private key secure.</span></span>

## <a name="overall-process"></a><span data-ttu-id="6b5c8-126">整体过程</span><span class="sxs-lookup"><span data-stu-id="6b5c8-126">Overall process</span></span>

 1. <span data-ttu-id="6b5c8-127">设置证书、密钥和指纹，确保每个目标节点具有证书的副本，且配置计算机具有公钥和指纹。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-127">Set up the certificates, keys, and thumbprints, making sure that each target node has copies of the certificate and the configuration computer has the public key and thumbprint.</span></span>
 2. <span data-ttu-id="6b5c8-128">创建包含公钥的路径和指纹的配置数据块。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-128">Create a configuration data block that contains the path and thumbprint of the public key.</span></span>
 3. <span data-ttu-id="6b5c8-129">创建配置脚本，该脚本定义目标节点的所需配置，并通过命令本地配置管理器使用证书及其指纹解密配置数据来设置目标节点上的解密。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-129">Create a configuration script that defines your desired configuration for the target node and sets up decryption on the target nodes by commanding the Local Configuration manager to decrypt the configuration data using the certificate and its thumbprint.</span></span>
 4. <span data-ttu-id="6b5c8-130">运行配置，这将设置本地配置管理器设置并启动 DSC 配置。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-130">Run the configuration, which will set the Local Configuration Manager settings and start the DSC configuration.</span></span>

![Diagram1](images/CredentialEncryptionDiagram1.png)

## <a name="certificate-requirements"></a><span data-ttu-id="6b5c8-132">证书要求</span><span class="sxs-lookup"><span data-stu-id="6b5c8-132">Certificate Requirements</span></span>

<span data-ttu-id="6b5c8-133">若要执行凭据加密，公钥证书必须在受用于创作 DSC 配置的计算机**信任**的_目标节点_上可用。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-133">To enact credential encryption, a public key certificate must be available on the _Target Node_ that is **trusted** by the computer being used to author the DSC configuration.</span></span>
<span data-ttu-id="6b5c8-134">若要将此公钥证书用于 DSC 凭据加密，它需具有以下特定要求：</span><span class="sxs-lookup"><span data-stu-id="6b5c8-134">This public key certificate has specific requirements for it to be used for DSC credential encryption:</span></span>

1. <span data-ttu-id="6b5c8-135">**密钥用法**：</span><span class="sxs-lookup"><span data-stu-id="6b5c8-135">**Key Usage**:</span></span>
   - <span data-ttu-id="6b5c8-136">必须包含：“KeyEncipherment”和“DataEncipherment”。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-136">Must contain: 'KeyEncipherment' and 'DataEncipherment'.</span></span>
   - <span data-ttu-id="6b5c8-137">_不_应包含：“数字签名”。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-137">Should _not_ contain: 'Digital Signature'.</span></span>
2. <span data-ttu-id="6b5c8-138">**增强型密钥用法**：</span><span class="sxs-lookup"><span data-stu-id="6b5c8-138">**Enhanced Key Usage**:</span></span>
   - <span data-ttu-id="6b5c8-139">必须包含：文档加密 (1.3.6.1.4.1.311.80.1)。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-139">Must contain: Document Encryption (1.3.6.1.4.1.311.80.1).</span></span>
   - <span data-ttu-id="6b5c8-140">_不_应包含：客户端身份验证 (1.3.6.1.5.5.7.3.2) 和服务器身份验证 (1.3.6.1.5.5.7.3.1)。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-140">Should _not_ contain: Client Authentication (1.3.6.1.5.5.7.3.2) and Server Authentication (1.3.6.1.5.5.7.3.1).</span></span>
3. <span data-ttu-id="6b5c8-141">证书的私钥在\*目标节点_上可用。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-141">The Private Key for the certificate is available on the \*Target Node_.</span></span>
4. <span data-ttu-id="6b5c8-142">证书的**提供程序**必须是“Microsoft RSA SChannel Cryptographic Provider”。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-142">The **Provider** for the certificate must be "Microsoft RSA SChannel Cryptographic Provider".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6b5c8-143">虽然你可以使用包含“数字签名”密钥用法或某个身份验证 EKU 的证书，但这会导致加密密钥更容易被误用，而且更容易受到攻击。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-143">Although you can use a certificate with containing a Key Usage of 'Digital Signature' or one of the Authentication EKU's, this will enable the encryption key to be more easily misused and vulnerable to attack.</span></span> <span data-ttu-id="6b5c8-144">因此，最好是使用为保护 DSC 凭据而专门创建的省略了这些密钥用法和 EKU 的证书。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-144">So it is best practice to use a certificate created specifically for the purpose of securing DSC credentials that omits these Key Usage and EKUs.</span></span>

<span data-ttu-id="6b5c8-145">_目标节点_上满足这些条件的任何现有证书都可以用于保护 DSC 凭据。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-145">Any existing certificate on the _Target Node_ that meets these criteria can be used to secure DSC credentials.</span></span>

## <a name="certificate-creation"></a><span data-ttu-id="6b5c8-146">证书创建</span><span class="sxs-lookup"><span data-stu-id="6b5c8-146">Certificate creation</span></span>

<span data-ttu-id="6b5c8-147">可以采用两种方法创建和使用所需的加密证书（公钥-私钥对）。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-147">There are two approaches you can take to create and use the required Encryption Certificate (public-private key pair).</span></span>

1. <span data-ttu-id="6b5c8-148">在**目标节点**上创建密钥对，并仅将公钥导出到**创作节点**</span><span class="sxs-lookup"><span data-stu-id="6b5c8-148">Create it on the **Target Node** and export just the public key to the **Authoring Node**</span></span>
2. <span data-ttu-id="6b5c8-149">在**创作节点**上创建密钥对，并将整个密钥对导出到**目标节点**</span><span class="sxs-lookup"><span data-stu-id="6b5c8-149">Create it on the **Authoring Node** and export the entire key pair to the **Target Node**</span></span>

<span data-ttu-id="6b5c8-150">建议使用方法 1，因为用于解密 MOF 中凭据的私钥始终停留在目标节点上。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-150">Method 1 is recommended because the private key used to decrypt credentials in the MOF stays on the Target Node at all times.</span></span>

### <a name="creating-the-certificate-on-the-target-node"></a><span data-ttu-id="6b5c8-151">在目标节点上创建证书</span><span class="sxs-lookup"><span data-stu-id="6b5c8-151">Creating the Certificate on the Target Node</span></span>

<span data-ttu-id="6b5c8-152">私钥必须是保密的，因为它可用于解密**目标节点**上的 MOF。为此，最简单的方法是在**目标节点**上创建私钥证书，并将**公钥证书**复制到用于将 DSC 配置编写到 MOF 文件中的计算机内。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-152">The private key must be kept secret, because is used to decrypt the MOF on the **Target Node** The easiest way to do that is to create the private key certificate on the **Target Node**, and copy the **public key certificate** to the computer being used to author the DSC configuration into a MOF file.</span></span>
<span data-ttu-id="6b5c8-153">以下示例：</span><span class="sxs-lookup"><span data-stu-id="6b5c8-153">The following example:</span></span>

1. <span data-ttu-id="6b5c8-154">在**目标节点**上创建证书</span><span class="sxs-lookup"><span data-stu-id="6b5c8-154">creates a certificate on the **Target node**</span></span>
2. <span data-ttu-id="6b5c8-155">在**目标节点**上导出公钥证书。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-155">exports the public key certificate on the **Target node**.</span></span>
3. <span data-ttu-id="6b5c8-156">将公钥证书导入到**创作节点**上**我的**证书存储。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-156">imports the public key certificate into the **my** certificate store on the **Authoring node**.</span></span>

#### <a name="on-the-target-node-create-and-export-the-certificate"></a><span data-ttu-id="6b5c8-157">在目标节点上：创建并导出证书</span><span class="sxs-lookup"><span data-stu-id="6b5c8-157">On the Target Node: create and export the certificate</span></span>

> <span data-ttu-id="6b5c8-158">目标节点：Windows Server 2016 和 Windows 10</span><span class="sxs-lookup"><span data-stu-id="6b5c8-158">Target Node: Windows Server 2016 and Windows 10</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```

<span data-ttu-id="6b5c8-159">一旦导出完成，需要将 `DscPublicKey.cer` 复制到**创作节点**。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-159">Once exported, the `DscPublicKey.cer` would need to be copied to the **Authoring Node**.</span></span>

> <span data-ttu-id="6b5c8-160">目标节点：Windows Server 2012 R2/Windows 8.1 及更早版本</span><span class="sxs-lookup"><span data-stu-id="6b5c8-160">Target Node: Windows Server 2012 R2/Windows 8.1 and earlier</span></span>
> [!WARNING]
> <span data-ttu-id="6b5c8-161">因为 Windows 10 和 Windows Server 2016 之前版本的 Windows 操作系统上的 `New-SelfSignedCertificate` cmdlet 不支持 Type 参数，因此，在这些操作系统上创建此证书需要其他方法。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-161">Because the `New-SelfSignedCertificate` cmdlet on Windows Operating Systems prior to Windows 10 and Windows Server 2016 do not support the **Type** parameter, an alternate method of creating this certificate is required on these operating systems.</span></span>
>
> <span data-ttu-id="6b5c8-162">在这种情况下，可以使用 `makecert.exe` 或者 `certutil.exe` 来创建证书。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-162">In this case you can use `makecert.exe` or `certutil.exe` to create the certificate.</span></span>
>
><span data-ttu-id="6b5c8-163">一种替代方法是[从 Microsoft 脚本中心下载 New-SelfSignedCertificateEx.ps1 脚本](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) 并改为使用它来创建证书：</span><span class="sxs-lookup"><span data-stu-id="6b5c8-163">An alternate method is to [download the New-SelfSignedCertificateEx.ps1 script from Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) and use it to create the certificate instead:</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
# and in the folder that contains New-SelfSignedCertificateEx.ps1
. .\New-SelfSignedCertificateEx.ps1
New-SelfsignedCertificateEx `
    -Subject "CN=${ENV:ComputerName}" `
    -EKU 'Document Encryption' `
    -KeyUsage 'KeyEncipherment, DataEncipherment' `
    -SAN ${ENV:ComputerName} `
    -FriendlyName 'DSC Credential Encryption certificate' `
    -Exportable `
    -StoreLocation 'LocalMachine' `
    -KeyLength 2048 `
    -ProviderName 'Microsoft Enhanced Cryptographic Provider v1.0' `
    -AlgorithmName 'RSA' `
    -SignatureAlgorithm 'SHA256'
# Locate the newly created certificate
$Cert = Get-ChildItem -Path cert:\LocalMachine\My | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```

<span data-ttu-id="6b5c8-164">一旦导出完成，需要将 ```DscPublicKey.cer``` 复制到**创作节点**。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-164">Once exported, the ```DscPublicKey.cer``` would need to be copied to the **Authoring Node**.</span></span>

#### <a name="on-the-authoring-node-import-the-certs-public-key"></a><span data-ttu-id="6b5c8-165">在创作节点上：导入证书的公钥</span><span class="sxs-lookup"><span data-stu-id="6b5c8-165">On the Authoring Node: import the cert’s public key</span></span>

```powershell
# Import to the my store
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

### <a name="creating-the-certificate-on-the-authoring-node"></a><span data-ttu-id="6b5c8-166">在创作节点上创建证书</span><span class="sxs-lookup"><span data-stu-id="6b5c8-166">Creating the Certificate on the Authoring Node</span></span>

<span data-ttu-id="6b5c8-167">或者，可以在**创作节点**上创建加密证书，并与**私钥**以 PFX 文件导出，然后在**目标节点**上导入。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-167">Alternately, the encryption certificate can be created on the **Authoring Node**, exported with the **private key** as a PFX file and then imported on the **Target Node**.</span></span>
<span data-ttu-id="6b5c8-168">这是当前用于在 _Nano Server_ 上实现 DSC 凭据加密的方法。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-168">This is the current method for implementing DSC credential encryption on _Nano Server_.</span></span>
<span data-ttu-id="6b5c8-169">尽管 PFX 使用密码保护，但在传输过程中也应保证其安全性。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-169">Although the PFX is secured with a password it should be kept secure during transit.</span></span>
<span data-ttu-id="6b5c8-170">以下示例：</span><span class="sxs-lookup"><span data-stu-id="6b5c8-170">The following example:</span></span>

1. <span data-ttu-id="6b5c8-171">在**创作节点**上创建证书</span><span class="sxs-lookup"><span data-stu-id="6b5c8-171">creates a certificate on the **Authoring node**.</span></span>
2. <span data-ttu-id="6b5c8-172">在**创作节点**上导出证书（包括私钥）。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-172">exports the certificate including the private key on the **Authoring node**.</span></span>
3. <span data-ttu-id="6b5c8-173">从**创作节点**中删除私钥，但将公钥证书保留在**我的**存储。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-173">removes the private key from the **Authoring node**, but keeps the public key certificate in the **my** store.</span></span>
4. <span data-ttu-id="6b5c8-174">将私钥证书导入到目标节点上的 My(Personal) 证书存储。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-174">imports the private key certificate into the My(Personal) certificate store on the **Target node**.</span></span>
   - <span data-ttu-id="6b5c8-175">必须将其添加到根存储，以便受到**目标节点**的信任。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-175">it must be added to the root store so that it will be trusted by the **Target node**.</span></span>

#### <a name="on-the-authoring-node-create-and-export-the-certificate"></a><span data-ttu-id="6b5c8-176">在创作节点上：创建并导出证书</span><span class="sxs-lookup"><span data-stu-id="6b5c8-176">On the Authoring Node: create and export the certificate</span></span>

> <span data-ttu-id="6b5c8-177">目标节点：Windows Server 2016 和 Windows 10</span><span class="sxs-lookup"><span data-stu-id="6b5c8-177">Target Node: Windows Server 2016 and Windows 10</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the private key certificate
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
$cert | Export-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -Password $mypwd -Force
# remove the private key certificate from the node but keep the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
$cert | Remove-Item -Force
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

<span data-ttu-id="6b5c8-178">一旦导出完成，需要将 `DscPrivateKey.pfx` 复制到**目标节点**。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-178">Once exported, the `DscPrivateKey.pfx` would need to be copied to the **Target Node**.</span></span>

> <span data-ttu-id="6b5c8-179">目标节点：Windows Server 2012 R2/Windows 8.1 及更早版本</span><span class="sxs-lookup"><span data-stu-id="6b5c8-179">Target Node: Windows Server 2012 R2/Windows 8.1 and earlier</span></span>
> [!WARNING]
> <span data-ttu-id="6b5c8-180">因为 Windows 10 和 Windows Server 2016 之前版本的 Windows 操作系统上的 `New-SelfSignedCertificate` cmdlet 不支持 Type 参数，因此，在这些操作系统上创建此证书需要其他方法。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-180">Because the `New-SelfSignedCertificate` cmdlet on Windows Operating Systems prior to Windows 10 and Windows Server 2016 do not support the **Type** parameter, an alternate method of creating this certificate is required on these operating systems.</span></span>
>
> <span data-ttu-id="6b5c8-181">在这种情况下，可以使用 `makecert.exe` 或者 `certutil.exe` 来创建证书。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-181">In this case you can use `makecert.exe` or `certutil.exe` to create the certificate.</span></span>
>
> <span data-ttu-id="6b5c8-182">一种替代方法是[从 Microsoft 脚本中心下载 New-SelfSignedCertificateEx.ps1 脚本](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) 并改为使用它来创建证书：</span><span class="sxs-lookup"><span data-stu-id="6b5c8-182">An alternate method is to [download the New-SelfSignedCertificateEx.ps1 script from Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) and use it to create the certificate instead:</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
# and in the folder that contains New-SelfSignedCertificateEx.ps1
. .\New-SelfSignedCertificateEx.ps1
New-SelfsignedCertificateEx `
    -Subject "CN=${ENV:ComputerName}" `
    -EKU 'Document Encryption' `
    -KeyUsage 'KeyEncipherment, DataEncipherment' `
    -SAN ${ENV:ComputerName} `
    -FriendlyName 'DSC Credential Encryption certificate' `
    -Exportable `
    -StoreLocation 'LocalMachine' `
    -KeyLength 2048 `
    -ProviderName 'Microsoft Enhanced Cryptographic Provider v1.0' `
    -AlgorithmName 'RSA' `
    -SignatureAlgorithm 'SHA256'
# Locate the newly created certificate
$Cert = Get-ChildItem -Path cert:\LocalMachine\My | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
$cert | Export-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -Password $mypwd -Force
# remove the private key certificate from the node but keep the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
$cert | Remove-Item -Force
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

#### <a name="on-the-target-node-import-the-certs-private-key-as-a-trusted-root"></a><span data-ttu-id="6b5c8-183">在目标节点上：将证书的私钥导入为受信任的根</span><span class="sxs-lookup"><span data-stu-id="6b5c8-183">On the Target Node: import the cert’s private key as a trusted root</span></span>

```powershell
# Import to the root store so that it is trusted
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
Import-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -CertStoreLocation Cert:\LocalMachine\My -Password $mypwd > $null
```

## <a name="configuration-data"></a><span data-ttu-id="6b5c8-184">配置数据</span><span class="sxs-lookup"><span data-stu-id="6b5c8-184">Configuration data</span></span>

<span data-ttu-id="6b5c8-185">配置数据块定义在哪个目标节点上进行操作、是否加密凭据、加密方式以及其他信息。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-185">The configuration data block defines which target nodes to operate on, whether or not to encrypt the credentials, the means of encryption, and other information.</span></span> <span data-ttu-id="6b5c8-186">有关配置数据块的详细信息，请参阅[分隔配置和环境数据](configData.md)。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-186">For more information on the configuration data block, see [Separating Configuration and Environment Data](configData.md).</span></span>

<span data-ttu-id="6b5c8-187">可以为与凭据加密相关的每个节点配置的元素有：</span><span class="sxs-lookup"><span data-stu-id="6b5c8-187">The elements that can be configured for each node that are related to credential encryption are:</span></span>

- <span data-ttu-id="6b5c8-188">**NodeName** - 为其配置凭据加密的目标节点的名称。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-188">**NodeName** - the name of the target node that the credential encryption is being configured for.</span></span>
- <span data-ttu-id="6b5c8-189">**PsDscAllowPlainTextPassword** - 是否允许将未加密的凭据传递给此节点。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-189">**PsDscAllowPlainTextPassword** - whether unencrypted credentials will be allowed to be passed to this node.</span></span> <span data-ttu-id="6b5c8-190">**不建议**使用此元素。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-190">This is **not recommended**.</span></span>
- <span data-ttu-id="6b5c8-191">**Thumbprint** -将用于在_目标节点_上的 DSC 配置中解密凭据的证书的指纹。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-191">**Thumbprint** - the thumbprint of the certificate that will be used to decrypt the credentials in the DSC Configuration on the _Target Node_.</span></span> <span data-ttu-id="6b5c8-192">**此证书必须存在于目标节点上的本地计算机证书存储中。**</span><span class="sxs-lookup"><span data-stu-id="6b5c8-192">**This certificate must exist in the Local Machine certificate store on the Target Node.**</span></span>
- <span data-ttu-id="6b5c8-193">**CertificateFile** - 应该用于为_目标节点_加密凭据的证书文件（只包含公钥）。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-193">**CertificateFile** - the certificate file (containing the public key only) that should be used to encrypt the credentials for the _Target Node_.</span></span> <span data-ttu-id="6b5c8-194">它必须是 DER 编码的二进制 X.509 或 Base-64 编码的 X.509 格式证书文件。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-194">This must be either a DER encoded binary X.509 or Base-64 encoded X.509 format certificate file.</span></span>

<span data-ttu-id="6b5c8-195">此示例显示了一个配置数据块，该数据块指定了要操作的名为 targetNode 的目标节点、公钥证书文件（名为 targetNode.cer）的路径和公钥的指纹。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-195">This example shows a configuration data block that specifies a target node to act on named targetNode, the path to the public key certificate file (named targetNode.cer), and the thumbprint for the public key.</span></span>

```powershell
$ConfigData= @{
    AllNodes = @(
            @{
                # The name of the node we are describing
                NodeName = "targetNode"

                # The path to the .cer file containing the
                # public key of the Encryption Certificate
                # used to encrypt credentials for this node
                CertificateFile = "C:\publicKeys\targetNode.cer"


                # The thumbprint of the Encryption Certificate
                # used to decrypt the credentials on target node
                Thumbprint = "AC23EA3A9E291A75757A556D0B71CBBF8C4F6FD8"
            };
        );
    }
```

## <a name="configuration-script"></a><span data-ttu-id="6b5c8-196">配置脚本</span><span class="sxs-lookup"><span data-stu-id="6b5c8-196">Configuration script</span></span>

<span data-ttu-id="6b5c8-197">在配置脚本中，使用 `PsCredential` 参数确保凭据存储时间尽可能短。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-197">In the configuration script itself, use the `PsCredential` parameter to ensure that credentials are stored for the shortest possible time.</span></span> <span data-ttu-id="6b5c8-198">运行提供的示例时，DSC 将提示你输入凭据，然后使用配置数据块中与目标节点相关联的 CertificateFile 加密 MOF 文件。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-198">When you run the supplied example, DSC will prompt you for credentials and then encrypt the MOF file using the CertificateFile that is associated with the target node in the configuration data block.</span></span> <span data-ttu-id="6b5c8-199">此代码示例将文件从受保护共享复制到用户。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-199">This code example copies a file from a share that is secured to a user.</span></span>

```powershell
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
        )


    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\Server\share\path\file.ext"
            DestinationPath = "C:\destinationPath"
            Credential = $credential
        }
    }
}
```

## <a name="setting-up-decryption"></a><span data-ttu-id="6b5c8-200">设置加密</span><span class="sxs-lookup"><span data-stu-id="6b5c8-200">Setting up decryption</span></span>

<span data-ttu-id="6b5c8-201">必须使用 CertificateID 资源验证证书的指纹，从而告知每个目标节点上的本地配置管理器用于解密凭据的证书，[`Start-DscConfiguration`](https://technet.microsoft.com/library/dn521623.aspx) 方可生效。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-201">Before [`Start-DscConfiguration`](https://technet.microsoft.com/library/dn521623.aspx) can work, you have to tell the Local Configuration Manager on each target node which certificate to use to decrypt the credentials, using the CertificateID resource to verify the certificate’s thumbprint.</span></span> <span data-ttu-id="6b5c8-202">此示例函数将查找适当的本地证书（你可能需要对它进行自定义，以便它准确地找到你想使用的证书）：</span><span class="sxs-lookup"><span data-stu-id="6b5c8-202">This example function will find the appropriate local certificate (you might have to customize it so it will find the exact certificate you want to use):</span></span>

```powershell
# Get the certificate that works for encryption
function Get-LocalEncryptionCertificateThumbprint
{
    (dir Cert:\LocalMachine\my) | %{
        # Verify the certificate is for Encryption and valid
        if ($_.PrivateKey.KeyExchangeAlgorithm -and $_.Verify())
        {
            return $_.Thumbprint
        }
    }
}
```

<span data-ttu-id="6b5c8-203">使用证书指纹标识证书后，即可更新配置脚本以使用该值：</span><span class="sxs-lookup"><span data-stu-id="6b5c8-203">With the certificate identified by its thumbprint, the configuration script can be updated to use the value:</span></span>

```powershell
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
        )


    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\Server\share\path\file.ext"
            DestinationPath = "C:\destinationPath"
            Credential = $credential
        }

        LocalConfigurationManager
        {
             CertificateId = $node.Thumbprint
        }
    }
}
```

## <a name="running-the-configuration"></a><span data-ttu-id="6b5c8-204">运行配置</span><span class="sxs-lookup"><span data-stu-id="6b5c8-204">Running the configuration</span></span>

<span data-ttu-id="6b5c8-205">此时，你可以运行配置，此操作将输出两个文件：</span><span class="sxs-lookup"><span data-stu-id="6b5c8-205">At this point, you can run the configuration, which will output two files:</span></span>

- <span data-ttu-id="6b5c8-206">\*.meta.mof 文件，它将本地配置管理器配置为使用存储在本地计算机存储区上、并由其指纹标识的证书来解密凭据。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-206">A \*.meta.mof file that configures the Local Configuration Manager to decrypt the credentials using the certificate that is stored on the local machine store and identified by its thumbprint.</span></span> <span data-ttu-id="6b5c8-207">[`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/library/dn521621.aspx) 应用 \*.meta.mof 文件。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-207">[`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/library/dn521621.aspx) applies the \*.meta.mof file.</span></span>
- <span data-ttu-id="6b5c8-208">实际应用配置的 MOF 文件。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-208">A MOF file that actually applies the configuration.</span></span> <span data-ttu-id="6b5c8-209">Start-DscConfiguration 应用配置。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-209">Start-DscConfiguration applies the configuration.</span></span>

<span data-ttu-id="6b5c8-210">这些命令将完成这些步骤：</span><span class="sxs-lookup"><span data-stu-id="6b5c8-210">These commands will accomplish those steps:</span></span>

```powershell
Write-Host "Generate DSC Configuration..."
CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample

Write-Host "Setting up LCM to decrypt credentials..."
Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose

Write-Host "Starting Configuration..."
Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
```

<span data-ttu-id="6b5c8-211">此示例将 DSC 配置推送到目标节点。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-211">This example would push the DSC configuration to the target node.</span></span>
<span data-ttu-id="6b5c8-212">还可以使用 DSC 请求服务器（如果可用）来应用 DSC 配置。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-212">The DSC configuration can also be applied using a DSC Pull Server if one is available.</span></span>

<span data-ttu-id="6b5c8-213">有关使用 DSC 请求服务器应用 DSC 配置的详细信息，请参阅[设置 DSC 请求客户端](pullClient.md)。</span><span class="sxs-lookup"><span data-stu-id="6b5c8-213">See [Setting up a DSC pull client](pullClient.md) for more information on applying DSC configurations using a DSC Pull Server.</span></span>

## <a name="credential-encryption-module-example"></a><span data-ttu-id="6b5c8-214">凭据加密模块示例</span><span class="sxs-lookup"><span data-stu-id="6b5c8-214">Credential Encryption Module Example</span></span>

<span data-ttu-id="6b5c8-215">以下是包含所有步骤的完整示例，以及用于导出和复制公钥的帮助程序 cmdlet：</span><span class="sxs-lookup"><span data-stu-id="6b5c8-215">Here is a full example that incorporates all of these steps, plus a helper cmdlet that exports and copies the public keys:</span></span>

```powershell
# A simple example of using credentials
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
        )


    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\server\share\file.txt"
            DestinationPath = "C:\Users\user"
            Credential = $credential
        }

        LocalConfigurationManager
        {
            CertificateId = $node.Thumbprint
        }
    }
}

# A Helper to invoke the configuration, with the correct public key
# To encrypt the configuration credentials
function Start-CredentialEncryptionExample
{
    [CmdletBinding()]
    param ($computerName)


    [string] $thumbprint = Get-EncryptionCertificate -computerName $computerName -Verbose
    Write-Verbose "using cert: $thumbprint"

    $certificatePath = join-path -Path "$env:SystemDrive\$script:publicKeyFolder" -childPath "$computername.EncryptionCertificate.cer"

    $ConfigData=    @{
        AllNodes = @(
                        @{
                            # The name of the node we are describing
                            NodeName = "$computerName"

                            # The path to the .cer file containing the
                            # public key of the Encryption Certificate
                            CertificateFile = "$certificatePath"

                            # The thumbprint of the Encryption Certificate
                            # used to decrypt the credentials
                            Thumbprint = $thumbprint
                        };
                    );
    }

    Write-Verbose "Generate DSC Configuration..."
    CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample `
        -credential (Get-Credential -UserName "$env:USERDOMAIN\$env:USERNAME" -Message "Enter credentials for configuration")

    Write-Verbose "Setting up LCM to decrypt credentials..."
    Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose

    Write-Verbose "Starting Configuration..."
    Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose

}


#region HelperFunctions

# The folder name for the exported public keys
$script:publicKeyFolder = "publicKeys"

# Get the certificate that works for encryptions
function Get-EncryptionCertificate
{
    [CmdletBinding()]
    param ($computerName)
    $returnValue= Invoke-Command -ComputerName $computerName -ScriptBlock {
            $certificates = dir Cert:\LocalMachine\my

            $certificates | %{
                    # Verify the certificate is for Encryption and valid
                    if ($_.PrivateKey.KeyExchangeAlgorithm -and $_.Verify())
                    {
                        # Create the folder to hold the exported public key
                        $folder= Join-Path -Path $env:SystemDrive\ -ChildPath $using:publicKeyFolder
                        if (! (Test-Path $folder))
                        {
                            md $folder | Out-Null
                        }

                        # Export the public key to a well known location
                        $certPath = Export-Certificate -Cert $_ -FilePath (Join-Path -path $folder -childPath "EncryptionCertificate.cer")

                        # Return the thumbprint, and exported certificate path
                        return @($_.Thumbprint,$certPath);
                    }
                  }
        }
    Write-Verbose "Identified and exported cert..."
    # Copy the exported certificate locally
    $destinationPath = join-path -Path "$env:SystemDrive\$script:publicKeyFolder" -childPath "$computername.EncryptionCertificate.cer"
    Copy-Item -Path (join-path -path \\$computername -childPath $returnValue[1].FullName.Replace(":","$"))  $destinationPath | Out-Null

    # Return the thumbprint
    return $returnValue[0]
}

Start-CredentialEncryptionExample
```