# NoNewLine 参数
**Out-file**、**Add-content**和 **Set-content** 现在具有新的 **–NoNewline** 开关，它将在输出后直接省略换行。
```PowerShell
PS C:\> "This is " | Out-File -FilePath Example.txt -NoNewline

PS C:\>; "a single " | Add-Content -Path Example.txt -NoNewline

PS C:\> "sentence." | Add-Content -Path Example.txt -NoNewline

PS C:\> Get-Content .\Example.txt

This is a single sentence.
```
如果不指定 **–NoNewline**，每个片段将出现在单独的行上：
```PowerShell
PS C:\> "This is " | Out-File -FilePath Example.txt

PS C:\> "a single " | Add-Content -Path Example.txt

PS C:\> "sentence." | Add-Content -Path Example.txt

PS C:\> Get-Content .\Example.txt

This is

a single

sentence.
```


<!--HONumber=Jun16_HO4-->


