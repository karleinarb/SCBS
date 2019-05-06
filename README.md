# SideCarBehaviourScript
SideCarBehaviourScript adds super powers to the Microsoft Intune Management Extension

**Disclaimer: This is a working PoC, but not tested extensively - use at own risk!**

## This script adds the following funtionality to the Intune Management Extensions:
- Force Reloading (specific) PowerShell scripts every 90 minutes.
- Force Reloading (specific) PowerShell scripts at user logon.

## The script can be installed in the following ways:
- Manually (copying files, and running the configure-scheduledtasks.ps1 file (don't move the files afterwards!))
- Through SCCM with App Deployent toolkit (example in repo)
- Through Intune as an MSI
- Through Intune as a Win32executable

## Specifying behaviour for specific scripts.
In order to have the script correctly identify scripts that you want either Reloaded at logon, or repetitively.
You have to output two very specific lines as the first output of your scripts, as it will be written to the registry by the Intune Management Extensions - The SideCarBehaviourScript looks for these lines in the registry.

- Example for a "ATSTARTUP" script:
```
Write-Output "<scriptfile name>"
Write-Output "##SideCarBehaviour##ATSTARTUP"  
```
  
- Example for a "RELOAD" script:
```
Write-Output "<scriptfile name>"
Write-Output "##SideCarBehaviour##RELOAD" 
```
