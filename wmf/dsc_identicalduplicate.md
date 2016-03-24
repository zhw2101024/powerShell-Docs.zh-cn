# 允许配置中存在完全相同的重复资源

DSC 不允许配置内存在冲突的资源定义，也不处理这样的定义。 它不尝试解决冲突，只是无法正常工作。 随着复合资源中配置重用的利用率增加，冲突将更频繁地发生。 当冲突资源定义相同时，DSC 应为智能且允许此操作。 通过此版本，我们支持具有相同定义的多个资源实例：

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS         #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS      #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

在早期版本中，如果试图确保已安装“Web-Server”角色，由于 WindowsFeature FE_IIS 和 WindowsFeature Worker_IIS 实例之间的冲突，将造成编译失败。 请注意，这两个配置中所配置的*所有*属性完全相同。 由于这两个资源中的*所有*属性完全相同，现在这将使成功编译。 

如果两个资源的任何属性之间有所不同，则不会将他们视为相同且编译将失败：

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS
    {
        Ensure = 'Present'     # Ensure is Present here
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS
    {
        Ensure = 'Absent'      # Ensure property is Absent instead of Present
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

这个非常相似的配置将失败，因为 WindowsFeature FE_IIS 和 WindowsFeature Worker_IIS 资源由于不再完全相同而发生冲突。<!--HONumber=Mar16_HO2-->
