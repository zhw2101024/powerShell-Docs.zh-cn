---
ms.date: 09/10/2018
contributor: JKeithB
keywords: 库,powershell,cmdlet,psgallery
title: 管理 API 密钥
ms.openlocfilehash: 954eb27c25babdb8efe50c13caf5f2d287c6b3e3
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002507"
---
# <a name="managing-api-keys"></a>管理 API 密钥

PowerShell 库支持创建多个 API 密钥以支持一系列发布要求。 API 密钥可应用于一个或多个包，授予特定权限，并具有到期日期。

> [!IMPORTANT]
> 在引入作用域 API 密钥之前发布到 PowerShell 库的用户将具有“完全访问 API 密钥”。 完全访问密钥没有内置于作用域 API 密钥的安全性改进。 完全访问密钥永不过期并适用于用户拥有的所有内容。 若删除此密钥，则无法重新创建。

下图显示了创建作用域 API 密钥时可用的选项。

![正在创建 API 密钥](../../Images/PSGallery_KeyScoped.png)

在此示例中，我们创建了一个名为 AzureRMDataFactory 的 API 密钥。 此密钥值可用于推送名称以“AzureRM.DataFactory”开头并且有效期为 365 天的包。 这是同一组织中不同团队处理不同包的典型方案。 团队成员拥有密钥，可授予他们所处理的特定包的权限。
到期值可防止使用过期或遗忘的密钥。

## <a name="using-glob-patterns"></a>使用 glob 模式

若要处理多个包，可使用通配模式将多个包作为一个组进行匹配。 API 密钥权限适用于与 glob 模式匹配的所有新建包。 例如，前面的示例使用“AzureRM.DataFactory *”的 Glob 模式值。 可使用此密钥推送名为“AzureRm.DataFactoryV2.Netcore”的包，因为该包与 glob 模式匹配。

## <a name="create-api-keys-securely"></a>安全创建 API 密钥

为了安全起见，屏幕上永远不会显示新创建的密钥值，只能使用“复制”按钮，如下所示。

![获取新的 API 密钥值](../../Images/PSGallery_CopyCreatedKey.png)

> [!IMPORTANT]
> 只可在创建或刷新后立即复制 API 密钥值。 将不会显示该密钥值，且无法在刷新页面后再次访问。 若丢失了密钥值，则必须使用“重新生成”，并在重新生成后复制该密钥。

## <a name="key-permissions-and-expiration"></a>密钥权限和到期时间

作用域 API 密钥可分配以下任何权限：

- 推送新建包
- 推送新建包或更新包
- 取消列出包

每个新密钥都有到期时间。 到期时间以天为单位。 到期时间的值可能为：

- 1 天
- 90 天
- 180 天
- 270 天
- 365 天（默认值）

创建密钥后，不能更改这些设置。 无法创建永不过期的新密钥。

## <a name="editing-and-deleting-existing-api-keys"></a>编辑和删除现有 API 密钥

可更改现有密钥的某些设置。 如上文所述，无法修改现有 API 密钥的安全作用域或更改到期时间。 可更改的选项如下面的屏幕截图所示：

![获取新的 API 密钥值](../../Images/PSGallery_EditAPIKey.png)

若要更改由密钥控制的包，可从列表中选择单个包，或更改 glob 模式。

单击“重新生成”创建一个新密钥值。 就像最初创建密钥时一样，必须在更新后立即“复制”密钥值。 离开此页后，“复制”选项不可用。

单击“删除”将显示一条确认消息。 删除密钥后，密钥将不可用。

## <a name="key-expiration"></a>密钥到期时间

在到期前十天，PowerShell 库会向 API 密钥的帐户持有者发送警告电子邮件。 到期后，该密钥将不可用。 API 密钥管理页面顶部将显示一条警告消息，显示不再有效的密钥。 可生成一个新密钥值。
