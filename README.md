## Welcome to GitHub Pages

testing code 
```
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

```
<#
$ModulePath must not already contain the modules or this may fail
#>

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

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/spaelling/CodeBeaver/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
