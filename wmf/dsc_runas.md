# 对 DSC 资源的自动 RunAs 支持
对 DSC RunAs 凭据的支持
--------------------------------

WMF 5.0 预览版 2015 年 4 月版支持以使用 PsDscRunAsCredential 属性指定的一组凭据为基础，运行**任意** DSC 资源。 通过它可实现各种方案，例如在特定用户环境中安装 MSI 包、访问用户的注册表配置单元、访问用户的特定本地目录以及访问网络共享等。

下面显示了在 DSC 中使用 PsDscRunAsCredential 属性更改用户命令提示符背景色的示例。

配置 ChangeCmdBackGroundColor

{

    Node ("localhost")

    {

        Registry CmdPath

        {

            Key = "HKEY\_CURRENT\_USER\\\\Software\\Microsoft\\\\Command Processor"

            ValueName = "DefaultColor"

            ValueData = '1F'

            ValueType = "DWORD"

            Ensure = "Present"

            Force = $true

            Hex = $true

            PsDscRunAsCredential = get-credential

        }

    }

}

$configData = @{

AllNodes = @(

@{

NodeName="localhost";

CertificateFile = "C:\\publicKeys\\targetNode.cer"

}

)

}

ChangeCmdBackGroundColor -ConfigurationData $configData

## 已知问题

在此版本中，以下是 DSC RunAs 凭据功能的已知问题：

-   WindowsProcess 资源不支持 RunAs 凭据。

<!--HONumber=Mar16_HO2-->
