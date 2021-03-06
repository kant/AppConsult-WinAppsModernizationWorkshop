﻿# Information Manager

This is an application developed by [jbe2277](https://github.com/jbe2277) as a sample to demonstrate the power of Win Application Framework (WAF), a framework to create well-structured WPF applications. The original sample is part of the following repository [https://github.com/jbe2277/waf](https://github.com/jbe2277/waf).

### Important things to consider during the migration

1. Some libraries included in the solution are already targeting .NET Standard, so you won't have to migrate them.
2. The solution contains multiple applications and libraries which are targeting, instead, the full .NET Framework. They must be migrated to .NET Core 3.0.
3. The WAF framework has been ported to .NET Core, but it's available only [in a separate branch](https://github.com/jbe2277/waf/tree/netcoreapp3.0) of the original repository. It isn't available yet as a standalone NuGet package. However, the existing .NET Framework version will work just fine with the .NET Core 3.0 application in compatibility mode, so you can safely install the package from NuGet and ignore the warnings that will be prompted.
3. Make sure to specify the **AssemblyName** and the **RootNamespace** properties in both .csproj files, otherwise the project won't work as expected.
4. The application is modular, meaning that it's made by multiple applications loaded at runtime which aren't referenced in Visual Studio. As a consequence, the original applications' projects copy the build output to a shared folder placed in the root of the solution called **out**. When you migrate the projects to .NET Core 3.0 make sure to carry on also this configuration using the following attribute:

```xml
<OutputPath>..\out\InformationManager\$(Configuration)</OutputPath>
```

In case you get stuck, you can find the already migrated project at the following link [https://github.com/Microsoft/AppConsult-WinAppsModernizationWorkshop/tree/master/Samples-NetCore/InformationManager](https://github.com/Microsoft/AppConsult-WinAppsModernizationWorkshop/tree/master/Samples-NetCore/InformationManager)