# 已知问题和限制

PowerShell 快捷方式在第一次使用时中断
------------------------------------------------------------

**解决方法：**执行下列操作之一：

1.  右键单击 PowerShell 快捷方式。 选择“Windows PowerShell”以在非提升模式下启动。
2.  右键单击 PowerShell 快捷方式。 右键单击“Windows PowerShell”并选择“以管理员身份运行”，以在提升模式下启动。

执行以上任一操作后，即可使用 PowerShell 快捷方式。 这些操作仅需要执行一次。


在运行 Windows 7 操作系统的计算机上，PowerShell 模块和 DSC 资源报告有关 ExecutionPolicy 的错误
-------------------------------------------------------------------------------------
在运行 Windows 7 操作系统的计算机上，使用 PowerShell 模块和 DSC 资源可能导致报告有关 ExecutionPolicy 的错误。

**解决方法：**通过在提升的 PowerShell 会话中运行以下命令（以管理员身份运行），将 ExecutionPolicy 设置为 RemoteSigned：

```powershell
Set-ExecutionPolicy RemoteSigned
```

连接到旧的远程 Exchange 终结点引发故障
------------------------------------------------------------

旧的 Exchange 终结点重定向到新的终结点。 引发故障的重定向逻辑中存在 Bug。

**解决方法：**直接连接到新终结点。


在 Windows Server 2012 R2 上安装 WMF 5.0 后，错误地停止软件清单日志记录功能
-------------------------------------------------------------------------------------------------------------

当在已运行 SIL 的 Windows Server 2012 R2 上安装 WMF 5.0 时，安装完成后错误地停止软件清单日志记录功能。

**解决方法：**在 WMF 安装后立即运行 Start-SilLogging cmdlet，因为安装过程将错误地停止软件清单日志记录功能。

如果将 LiteralPath 和 -Recurse 一起使用，Get-ChildItem 将失效
--------------------------------------------------------------------------

如果目录名称包含无效的通配符，则当同时
使用 -LiteralPath 和 -Recurse 时，Get-ChildItem 不会产生预期结果。

**解决方法：**尽管不理想，但当前的解决方法是在脚本中实现递归，而不是依赖 cmdlet。


Sysprep 在安装 WMF 5.0 后无法正常工作
----------------------------------------

该问题有两种解决方法，具体取决于正在运行的 Windows Server 版本。

**解决方案：**
- 对于运行 **Windows Server 2008 R2** 的系统
  1.    以管理员身份打开 PowerShell
  2.    运行以下命令
   ```powershell
    Set-SilLogging –TargetUri https://BlankTarget –CertificateThumbprint 0123456789
   ```
  3.    按预期运行命令并忽略错误。
   ```powershell
    Publish-SilData
   ```
  4.    删除 \Windows\System32\Logfiles\SIL\ 目录中的文件
  ```powershell
  Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
  ```
  5.    安装所有可用的重要 Windows 更新，并正常开始 Sysyprep 操作。
  
- 对于运行 **Windows Server 2012** 的系统
  1.    在要执行 Sysprep 的服务器上安装 WMF 5.0 后，以管理员身份登录。
  2.    将 Generize.xml 从目录 \Windows\System32\Sysprep\ActionFiles\ 复制到 Windows 目录（比如 C:\）之外的位置。
  3.    使用记事本打开 Generalize.xml 副本。
  4.    查找并删除以下文本，需要删除每个文本的一个实例（它们将位于接近文档结尾的地方）。
    ```
    <sysprepOrder order="0x3200"></sysprepOrder>
    
    <sysprepOrder order="0x3300"></sysprepOrder>
    ```
  5.    保存编辑过的 Generalize.xml 副本并关闭该文件。
  6.    以管理员身份打开命令提示符
  7.    运行以下命令，以获得 system32 文件夹中的 Generalize.xml 文件的所有权：
    ```
      Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml 
    ```
  8.    运行以下命令以设置文件的适当权限：
    ```
      Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F 
    ```
      * 提示进行确认时回答“是”。 
      * 请注意，`<AdministratorUserName>` 应替换为计算机管理员的用户名。 例如，“Administrator”。
      
  9.    使用以下命令将编辑并保存好的文件复制到 Sysprep 目录：
      ```
      xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml 
      ```
      * 回答“是”进行覆盖（注意，如果没有任何覆盖提示，请再次检查输入的路径）。
      * 假定你编辑的 Generalize.xml 副本已复制到 C:\。
  10.   Generalize.xml 中现已更新解决方法。 请在启用通用选项的情况下运行 Sysprep。



<!--HONumber=May16_HO1-->


