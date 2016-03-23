# 剪贴板 cmdlet
通过 **Get-Clipboard** 和 **Set-Clipboard**，你可以更轻松地将内容传入和传出 Windows PowerShell 会话。 下面的示例使用文件资源管理器复制三个文件：

现在，可以列表形式轻松访问剪贴板上的内容：

PS C:\\&gt; Get-Clipboard -Format FileDropList

目录：C:\\Users\\slee\\Downloads\\Example

模式 上次写入时间 长度 名称

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt

剪贴板 cmdlet 支持图像、音频文件、文件列表和文本。
<!--HONumber=Mar16_HO2-->
