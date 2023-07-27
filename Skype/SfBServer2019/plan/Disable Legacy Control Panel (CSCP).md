---
title: "Disable Legacy Control Panel (CSCP)"
ms.reviewer: 
ms.author: akprakash
author: akprakash
manager: rahulgup
ms.date: 07/27/2023
audience: ITPro
ms.topic: article
ms.service: skype-for-business-server
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.collection: IT_Skype16
description: "This article provides a script to disable the Old Control Panel."
---




# Disable Legacy Control Panel (CSCP)

In Skype for Business Server build 2019 2046.523, we are adding a support for two new registry Keys that, when present, validates the input and disables the original Control Panel (CSCP) from the launch option menu. We recommend customers to use Modern Admin Control Panel. 

**SOFTWARE\Microsoft\Real-Time Communications\{5DC8C4D5-5133-4CE5-BF4E-8C459BF419D6}\OCP :** 
Registry Key for disabling the original Control Panel (CSCP)

**SOFTWARE\Microsoft\Real-Time Communications\{5DC8C4D5-5133-4CE5-BF4E-8C459BF419D6}\DMR :** 
Adds validation for the Monitoring Server  

> [!NOTE]
> If the Registry Keys are not present, then there will be no change to the Control Panel launch behavior. This is a pre requisite for our customers in China.

Please run below mentioned PowerShell script adds the two new Registry Keys, if desired. 

```powershell
[CmdletBinding()]
param (
    [switch]$Undo
)

# IIS site details
$iisSiteName = "Skype for Business Server Internal Web Site"
$iisAppName = "cscp"
$iisAppPhysicalPathOld = "C:\Program Files\Skype for Business Server 2019\Web Components\AdminUI"
$iisAppPhysicalPath = "C:\Program Files\Skype for Business Server 2019\Web Components"

# Load the WebAdministration module
Import-Module WebAdministration

if ($Undo) {
    # Undo the changes made by the script
    $parentKey = "HKLM:\SOFTWARE\Microsoft\Real-Time Communications\{5DC8C4D5-5133-4CE5-BF4E-8C459BF419D6}"
    $registryKeys = @("DMR", "OCP")

    foreach ($key in $registryKeys) {
        $registryKey = "$parentKey\$key"
        # Check if the key exists before removing it
        if (Test-Path $registryKey) {
            Remove-Item -Path $registryKey -Recurse -Force
            Write-Host "Registry key '$registryKey' removed."
        } else {
            Write-Host "Registry key '$registryKey' does not exist. No changes were made."
        }
    }

     # IIS application changes
    # Check if the IIS site exists
    if ($iisSite = Get-Website $iisSiteName -ErrorAction SilentlyContinue) {
        # Check if the application exists
        $existingApp = Get-WebApplication -Site $iisSiteName | Where-Object { $_.Path -eq "/$iisAppName" }
        if ($existingApp) {
            # If the application exists, change the Physical Path using Set-WebConfigurationProperty
            Set-WebConfigurationProperty -Filter "/system.applicationHost/sites/site[@name='$iisSiteName']/application[@path='/$iisAppName']/virtualDirectory[@path='/']" -Name "physicalPath" -Value $iisAppPhysicalPathOld
            Write-Host "IIS application '$iisAppName' Physical Path changed to '$iisAppPhysicalPathOld'."
        } else {
            Write-Host "IIS application '$iisAppName' does not exist. The Physical Path cannot be changed."
        }
    } else {
        Write-Host "IIS site '$iisSiteName' does not exist. The application cannot be changed."
    }
}
else {
    # Apply the changes

    # Registry changes
    $parentKey = "HKLM:\SOFTWARE\Microsoft\Real-Time Communications\{5DC8C4D5-5133-4CE5-BF4E-8C459BF419D6}"
    $registryKeys = @("DMR", "OCP")

    foreach ($key in $registryKeys) {
        $registryKey = "$parentKey\$key"
        # Check if the key exists
        if (-Not (Test-Path $registryKey)) {
            # If the key does not exist, create it with a default value or add any necessary subkeys or values
            New-Item -Path $registryKey -Force | Out-Null
            Write-Host "Registry key '$registryKey' and values created."
        } else {
            Write-Host "Registry key '$registryKey' already exists."
        }
    }

    # IIS application changes
    # Check if the IIS site exists
    if ($iisSite = Get-Website $iisSiteName -ErrorAction SilentlyContinue) {
        # Check if the application exists
        $existingApp = Get-WebApplication -Site $iisSiteName | Where-Object { $_.Path -eq "/$iisAppName" }
        if ($existingApp) {
            # If the application exists, change the Physical Path using Set-WebConfigurationProperty
            Set-WebConfigurationProperty -Filter "/system.applicationHost/sites/site[@name='$iisSiteName']/application[@path='/$iisAppName']/virtualDirectory[@path='/']" -Name "physicalPath" -Value $iisAppPhysicalPath
            Write-Host "IIS application '$iisAppName' Physical Path changed to '$iisAppPhysicalPath'."
        } else {
            Write-Host "IIS application '$iisAppName' does not exist. The Physical Path cannot be changed."
        }
    } else {
        Write-Host "IIS site '$iisSiteName' does not exist. The application cannot be changed."
    }
}

Write-Host "Restarting IIS Server"
# Perform IIS reset
iisreset
Write-Host "Done"
```
> [!NOTE]
If you have accidently run the script and want to revert the changes then run the PowerShell script with -Undo parameter.

