## <a name="microsoft-open-source-code-of-conduct"></a>Microsoft 开放源代码行为准则

此项目采用了 [Microsoft 开放源代码行为准则](https://opensource.microsoft.com/codeofconduct/)。
有关详细信息，请参阅[行为准则常见问题](https://opensource.microsoft.com/codeofconduct/faq/)，或如果有任何其他问题或意见，请与 [opencode@microsoft.com ](mailto:opencode@microsoft.com) 联系。

[![生成状态](https://ci.appveyor.com/api/projects/status/onshefxnc4g4pv87/branch/staging?svg=true)](https://ci.appveyor.com/project/PowerShell/powershell-docs/branch/staging)

# <a name="powershell-documentation"></a>PowerShell 文档

欢迎使用 PowerShell 文档存储库，其中包含官方 Windows PowerShell 文档。 

## <a name="repository-structure"></a>存储库结构
此存储库中的每个文件夹均发布到 [MSDN](https://msdn.microsoft.com/en-us/powershell)。 这些文件夹对应于以下 PowerShell 资产：
* [/dsc/](https://msdn.microsoft.com/en-us/powershell/dsc/) 对应于 Desired State Configuration 功能
* [/gallery/](https://msdn.microsoft.com/powershell/gallery) 对应于 [PowerShell 库](https://www.powershellgallery.com/)
* [/jea/](https://msdn.microsoft.com/powershell/jea/) 对应于 Just Enough Administration 功能
* [/reference/](https://msdn.microsoft.com/powershell/reference/) 对应于跨版本 2.0、3.0、4.0、5.0、5.1 和 6.0 的 PowerShell 模块引用
  * 此内容以后将由 `Get-Help` cmdlet 进行检索
* [/scripting/](https://msdn.microsoft.com/en-us/powershell/scripting/) 为一般性 PowerShell 参考内容
* [/wmf](https://msdn.microsoft.com/en-us/powershell/wmf/readme) 包含 Windows Management Framework 的发行说明，该软件包用于将 PowerShell 的新版本分发到之前版本的 Windows。 



## <a name="contributing"></a>贡献文档

通过[拉取请求](https://help.github.com/articles/using-pull-requests/)到临时分支，我们正积极将贡献文档并入此存储库。 请注意在提交拉取请求前，必须签订[文档贡献许可协议](https://cla.microsoft.com/)，以确保社区成员可免费使用你的文档。
有关贡献文档的详细信息，请阅读[贡献文档指南](CONTRIBUTING.md)。
在参与之前，需要参阅[风格指南](./STYLE.md)草稿。
请使用“问题和提取请求”模板来帮助文档在各版本之间保持一致性。 
