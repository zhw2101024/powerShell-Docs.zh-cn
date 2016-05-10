# 剪贴板 cmdlet
通过 **Get-Clipboard** 和 **Set-Clipboard**，你可以更轻松地将内容传入和传出 Windows PowerShell 会话。 例如，如果你使用 Windows 资源管理器复制三个文件
到剪贴板上（例如，通过选择它们并按 `ctrl-c`），然后就可以轻松地以文件列表的方式访问剪贴板的内容：

```powershell 
PS C:\\&gt; Get-Clipboard -Format FileDropList

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt
```


剪贴板 cmdlet 支持图像、音频文件、文件列表和文本。


<!--HONumber=Apr16_HO3-->


