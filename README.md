# meltdown-spectre-check-ps2
Modification of Speculation Control Validation PowerShell Script

# Introduction

This is a minor modification to the script issued by Microsoft available [here](https://gallery.technet.microsoft.com/scriptcenter/Speculation-Control-e36f0050/) to allow the module to work on legacy machines running PowerShell v2.

Output can be interpreted using the [guidance](https://support.microsoft.com/en-us/help/4074629/understanding-the-output-of-get-speculationcontrolsettings-powershell) issued by Microsoft.

This resolves the following error.

'''
Import-Module : The '.\SpeculationControl.psd1' module cannot be imported because its manifest contains one or more members that are not valid. The valid manifest members are ('ModuleToProcess', 'NestedModules', 'GUID', 'Author', 'CompanyName', 'Copyright', 'ModuleVersion', 'Description', 'PowerShellVersion', 'PowerShellHostName', 'PowerShellHostVersion', 'CLRVersion', 'DotNetFrameworkVersion', 'ProcessorArchitecture', 'RequiredModules', 'TypesToProcess', 'FormatsToProcess', 'ScriptsToProcess', 'PrivateData', 'RequiredAssemblies', 'ModuleList', 'FileList', 'FunctionsToExport', 'VariablesToExport', 'AliasesToExport', 'CmdletsToExport'). Remove the members that are not valid ('RootModule'), then try to import the module again.
At line:1 char:14
+ Import-Module <<<<  .\SpeculationControl.psd1
    + CategoryInfo          : InvalidData: (.\SpeculationControl.psd1:String) [Import-Module], InvalidOperationException
    + FullyQualifiedErrorId : Modules_InvalidManifestMember,Microsoft.PowerShell.Commands.ImportModuleCommand
'''

# Usage
```powershell
$SaveExecutionPolicy = Get-ExecutionPolicy
Set-ExecutionPolicy RemoteSigned -Scope Currentuser
Import-Module .\SpeculationControl.psd1
Get-SpeculationControlSettings
Set-ExecutionPolicy $SaveExecutionPolicy -Scope Currentuser
```
