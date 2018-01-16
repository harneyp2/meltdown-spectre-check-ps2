# meltdown-spectre-check-ps2
Modification of Speculation Control Validation PowerShell Script

# Introduction

This is a minor modification to the script issued by Microsoft available [here](https://gallery.technet.microsoft.com/scriptcenter/Speculation-Control-e36f0050/) to allow the module to work on legacy machines running PowerShell v2.

Output can be interpreted using the [guidance](https://support.microsoft.com/en-us/help/4074629/understanding-the-output-of-get-speculationcontrolsettings-powershell) issued by Microsoft.

# Usage
$SaveExecutionPolicy = Get-ExecutionPolicy
Set-ExecutionPolicy RemoteSigned -Scope Currentuser
Import-Module .\SpeculationControl.psd1
Get-SpeculationControlSettings
Set-ExecutionPolicy $SaveExecutionPolicy -Scope Currentuser