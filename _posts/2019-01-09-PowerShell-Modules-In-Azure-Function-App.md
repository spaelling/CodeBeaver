---
layout: post
title:  "PowerShell Modules in Azure Function App"
categories: [Blog]
tags: [PowerShell, AzureFunctionApp]
---

Below are two articles by Microsoft on how to use PowerShell modules in Azure function app. I do not particurly find any of these very useful.

- [https://blogs.msdn.microsoft.com/powershell/2017/02/24/using-powershell-modules-in-azure-functions/](https://blogs.msdn.microsoft.com/powershell/2017/02/24/using-powershell-modules-in-azure-functions/)
- [https://blogs.technet.microsoft.com/thbrown/2018/02/25/add-a-custom-or-non-standard-powershell-module-to-azure-functions/](https://blogs.technet.microsoft.com/thbrown/2018/02/25/add-a-custom-or-non-standard-powershell-module-to-azure-functions/)

Installing a module is rather easy, especially if it is to be found in PSGallery

```powershell
#$ModulePath must not already contain the modules or this may fail

$ModulePath = 'D:\home\lib\PSModules'
New-Item -ItemType Directory -Path $ModulePath -Force | Out-Null

$NuGet = Get-PackageProvider -Name NuGet -ErrorAction SilentlyContinue
if($null -eq $NuGet)
{
    Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force -Scope CurrentUser
}

"Saving modules to $ModulePath"
Save-Module Az -Path $ModulePath -Force

"Listing import commands for every module"
Get-ChildItem -Path $ModulePath -Include "*.psd1" -Recurse | ForEach-Object {
    "Import-Module '$($_.FullName)'"
}
```

And importing likewise easy

```powershell
# Import modules not available by default in Function Apps

$ModulePath = 'D:\home\lib\PSModules'

# Add to PSModulePath
$env:PSModulePath += ";$ModulePath"

# We can list available modules starting with Az
#Get-Module -ListAvailable Az*

# Import specific modules from Az
Import-Module Az.Accounts
Import-Module Az.Resources
```

Code above is maintained at
- [HT_ImportModules.ps1](https://github.com/spaelling/AzureFunctionAppSnippets/blob/master/PowerShell/HT_ImportModules.ps1)
- [HT_InstallModule.ps1](https://github.com/spaelling/AzureFunctionAppSnippets/blob/master/PowerShell/HT_InstallModule.ps1)

Along with other [Function App snippets](https://github.com/spaelling/AzureFunctionAppSnippets)