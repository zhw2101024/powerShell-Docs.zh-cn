# 适用于 Linux 的 DSC nxUser 资源

PowerShell Desired State Configuration (DSC) 中的 **nxUser** 资源提供了在 Linux 节点上管理本地用户的机制。

## 语法

```
nxUser <string> #ResourceName
{
    UserName = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ FullName = <string> ]
    [ Description = <string> ]
    [ Password = <string> ]
    [ Disabled = <bool> ]
    [ PasswordChangeRequired = <bool> ]
    [ HomeDirectory = <string> ]
    [ Mode = <string> ]
    [ GroupID = <string> ]
    [ DependsOn = <string[]> ]

}
```

## “属性”

|  属性 |  指示要确保其特定状态的帐户名。 | 
|---|---|
| UserName| 指定你想确保其中文件或目录状态的位置。| 
| Ensure| 指定帐户是否存在。 将此属性设置为“Present”以确保该帐户存在，将其设置为“Absent”以确保该帐户不存在。| 
| FullName| 包含用于用户帐户的完整名称的字符串。| 
| 说明| 用户帐户的说明。| 
| 密码| 适用于 Linux 计算机的形式的用户密码哈希。 通常情况下，这是加盐的 SHA-256 或 SHA-512 哈希。 在 Debian 和 Ubuntu Linux 上，可以使用 mkpasswd 命令生成此值。 对于其他 Linux 发行版本，可以使用 Python 加密库的加密方法生成此哈希。| 
| 禁用| 指示帐户是否已启用。 将此属性设置为 **$true** 以确已禁用保此帐户，将其设置为 **$false** 以确保已启用此帐户。| 
| PasswordChangeRequired| 指示用户是否可以更改密码。 将此属性设置为 **$true** 以确保用户无法更改密码，将其设置为 **$false** 以允许用户更改密码。 默认值为 **$false**。 仅当创建以前不存在的用户帐户时，才会计算此属性。| 
| HomeDirectory| 用户的主目录| 
| GroupID| 用户的主要组 ID| 
| DependsOn | 指示必须先运行其他资源的配置，再配置此资源。 例如，如果你想要首先运行 ID 为“ResourceName”、类型为“ResourceType”的资源配置脚本块，则使用此属性的语法为 `DependsOn = "[ResourceType]ResourceName"`。| 

## 示例

以下示例可确保用户“monuser”存在且为组“DBusers”的成员。

```
Import-DSCResource -Module nx 

Node $node {
nxUser UserExample{
   UserName = "monuser"
   Description = "Monitoring user"
   Password  =    '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
   Ensure = "Present"
   HomeDirectory = "/home/monuser"
}
 
nxGroup GroupExample{
   GroupName = "DBusers"
   Ensure = "Present"
   MembersToInclude = "monuser"
   DependsOn = "[nxUser]UserExample"            
}
}
```
<!--HONumber=Feb16_HO4-->
