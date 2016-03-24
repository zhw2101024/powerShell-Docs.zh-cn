# 对 FileInfo 对象的更新
文件版本信息可能会产生误导，尤其是在对文件进行了修补的情况下。 此版本的 WMF 生产预览向 FileInfo 对象添加了新的 **FileVersionRaw** 和 **ProductVersionRaw** 脚本属性。 以下是为 powershell.exe 显示的属性：

PS C:\\&gt; Get-Process -Id $pid -FileVersionInfo | fl \*version\* -Force

FileVersionRaw : 10.0.10055.0

ProductVersionRaw : 10.0.10055.0

FileVersion : 10.0.10055.0 (fbl\_srv2.150402-1826)

ProductVersion : 10.0.10055.0
<!--HONumber=Mar16_HO2-->
