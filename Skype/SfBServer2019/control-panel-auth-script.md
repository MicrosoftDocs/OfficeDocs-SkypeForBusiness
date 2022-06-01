---
title: "Skype for Business Server 2019 control panel authentication script"
ms.reviewer: rogupta
ms.author: heidip
author: MicrosoftHeidi
manager: serdars
ms.date: 07/23/2019
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.collection: IT_Skype16
description: "Helper script to configure SFB 2019 control panel authentication with Microsoft 365 or Office 365 via OAuth protocol."
---

# Skype for Business Server 2019 control panel authentication script

Following are the authentication related helper scripts for Modern Admin Control Panel (MACP).

## Configure MACP authentication with Microsoft 365 or Office 365

This script should be run after installing Skype for Business Server 2019 Cumulative Update 1 or later, as part of the set-up for the new Control Panel. 

```powershell
<#
 .SYNOPSIS
 Helper script to configure SFB 2019 control panel authentication with Office 365 via OAuth protocol. This script will create an Azure AD Application on Azure. This will help in signing into Microsoft 365 or Office 365 using OAuth in the new Control Panel.

 .DESCRIPTION
 Copyright (c) Microsoft Corporation. All rights reserved.

 THIS CODE IS MADE AVAILABLE AS IS, WITHOUT WARRANTY OF ANY KIND. THE ENTIRE RISK
 OF THE USE OR THE RESULTS FROM THE USE OF THIS CODE REMAINS WITH THE USER.

 .EXAMPLE
 Creates a native client application on azure active directory with name "MACP"
#>

Write-Host "Getting external FQDN of SFB pools"
$externalFqdns = (Get-CsService -WebServer).ExternalFqdn

Write-Host "Getting internal FQDN of SFB pools"
$internalFqdns = (Get-csService -WebServer).poolfqdn

$replyUrls = New-Object System.Collections.Generic.List[string]

Write-Host "Generating Redirect URIs for modern admin control panel"
#Generating replyUrls using external fqdns
foreach ($externalFqdn in $externalFqdns) {
  if ($externalFqdn -ne $null) {
    $replyUrls.Add('https://' + $externalFqdn + '/macp/iframe.html');
  }
}

#Generating replyUrls using internal fqdns
foreach($internalFqdn in $internalFqdns) {
  if ($internalFqdn -ne $null) {
    $replyUrls.Add('https://' + $internalFqdn + '/macp/iframe.html');
  }
}

$simplifiedUrl = Read-Host -Prompt "Enter Admin Control Panel application's simplified URL eg. https://admin.contoso.com. Press Enter to skip "

if (![string]::IsNullOrWhiteSpace($simplifiedUrl))
{
    if ($simplifiedUrl.StartsWith('http://'))
    {
        $simplifiedUrl = $simplifiedUrl.Replace('http://', '')
    }

    if (!$simplifiedUrl.StartsWith('https://'))
    {
        $simplifiedUrl = "https://" + $simplifiedUrl
    }

    $simplifiedUrl = $simplifiedUrl.TrimEnd('/')

    $replyUrls.Add($simplifiedUrl + '/macp/iframe.html')
}


if (Get-Module -ListAvailable -Name "AzureAd") {
  Write-Host "AzureAD module exists"
}
else {
  Write-Host "Installing AzureAD module";
  Install-Module -name AzureAD
}

$uniqueReplyUrls = $replyUrls | sort -Unique

#Importing AzureAd module
Write-Host "Importing AzureAD module";
Import-module AzureAD

Write-Host "Connect to Azure AD using your azure tenant admin credentials"
Connect-azureAd

# Resource: https://api.interfaces.records.teams.microsoft.com/user_impersonation
$requiredResourceAccess1 = New-Object -TypeName "Microsoft.Open.AzureAD.Model.RequiredResourceAccess"
$requiredResourceAccess1.ResourceAccess = New-Object -TypeName "Microsoft.Open.AzureAD.Model.ResourceAccess" -ArgumentList "e60370c1-e451-437e-aa6e-d76df38e5f15","Scope"
$requiredResourceAccess1.ResourceAppId = "48ac35b8-9aa8-4d74-927d-1f4a14a0b239"

# Resource: https://graph.microsoft.com/User.Read
$requiredResourceAccess2 = New-Object -TypeName "Microsoft.Open.AzureAD.Model.RequiredResourceAccess"
$requiredResourceAccess2.ResourceAccess = New-Object -TypeName "Microsoft.Open.AzureAD.Model.ResourceAccess" -ArgumentList "e1fe6dd8-ba31-4d61-89e7-88639da4683d","Scope"
$requiredResourceAccess2.ResourceAppId = "00000003-0000-0000-c000-000000000000"

$requiredResourceAccess = New-Object System.Collections.Generic.List[Microsoft.Open.AzureAD.Model.RequiredResourceAccess]
$requiredResourceAccess.Add($requiredResourceAccess1)
$requiredResourceAccess.Add($requiredResourceAccess2)

$azureADApplication = Get-AzureADApplication -Filter "DisplayName eq 'MACP'"

if ($azureADApplication -eq $null) {
  Write-Host "Creating Azure AD application for modern admin control panel (MACP)"
  $azureADApplication = New-AzureADApplication -DisplayName "MACP" -PublicClient $true -Oauth2AllowImplicitFlow $true -ReplyUrls $uniqueReplyUrls -RequiredResourceAccess $requiredResourceAccess
}
else {
  Write-Host "Azure ad application for modern admin control panel (MACP) already exists with displayName: " $azureADApplication.DisplayName ". Updating the properties"
  Write-Host $uniqueReplyUrls
  Set-AzureADApplication -ObjectId $azureADApplication.ObjectId -PublicClient $true -Oauth2AllowImplicitFlow $true -ReplyUrls $uniqueReplyUrls -RequiredResourceAccess $requiredResourceAccess
}

Write-Host "Updating the AzureAD application Id in CMS"
Set-CsHybridConfiguration -ClientId $azureADApplication.AppId


```
## Configure MACP application in ADFS Farm

This script should be run after installing Skype for Business Server 2019 latest Cumulative Update, as part of the set-up for the new Control Panel.

```powershell
<#
 .SYNOPSIS
 Helper script to configure MACP Application in ADFS Farm.

 .DESCRIPTION
 Copyright (c) Microsoft Corporation. All rights reserved.

 THIS CODE IS MADE AVAILABLE AS IS, WITHOUT WARRANTY OF ANY KIND. THE ENTIRE RISK
 OF THE USE OR THE RESULTS FROM THE USE OF THIS CODE REMAINS WITH THE USER.

 .EXAMPLE
 Creates an application in ADFS Farm with name "MACPApp"
#>

$confirmation = Read-Host -Prompt "Are you running this script on an ADFS Farm server. Confirm[y/n]"

if ($confirmation -match '[^yY]')
{
    if ($confirmation -match '[nN]')
    {
        Write-Host "`n`rPlease run this script only on ADFS Farm servers."  -ForeGroundColor Red
    }
    else
    {
        Write-Host "`n`rInvalid Input." -ForeGroundColor Red
    }

    Write-Host "`n`rAborting Process." -ForeGroundColor Red
    return
}

Write-Host "ADFS application group and native client application for Admin Control Panel can be setup only on ADFS Farm servers running on Windows Server 2016 or above. Checking the current server version ..."
$version = [System.Environment]::OSVersion.Version.Major

# Version reference for Windows Server here:
# https://docs.microsoft.com/windows/win32/sysinfo/operating-system-version
if ($version -lt 10)
{
    Write-Host "`n`rInvalid Window Server version. Please run this script on ADFS farm servers running on Windows Server 2016 or above." -ForeGroundColor Red
    return
}

Write-Host "Valid Windows Server Version." -ForeGroundColor Green

Write-Host "`n`rCreating an ADFS application group and native client application for Admin Control Panel in the ADFS Farm."

# Creating ApplicationGroup.
$groupName = Read-Host -Prompt "Enter ADFS Application Group Name for Admin Control Panel. Press enter to use default name as 'MACP' "
if([string]::IsNullOrWhiteSpace($groupName))
{
	$groupName = "MACP"
}

try
{
    New-AdfsApplicationGroup -Name $groupName
}
catch
{
    Write-Error "`nError in creating Application Group $groupName. Please ensure that you have enabled and configured WindowsFeature ADFS-Federation for this server. Aborting Process."
    throw
    exit
}

# Creating a new native MACP App under above Application Group.
$appName = Read-Host -Prompt "Enter Admin Control Panel Application Name. Press ENTER to use default name as 'MACPApp' "
if([string]::IsNullOrWhiteSpace($appName))
{
    $appName = "MACPApp"
}

$clientIdentifier = [guid]::NewGuid()

$computerDetails = Get-WmiObject win32_computersystem

if (($computerDetails -eq $null) -OR
    ($computerDetails.DNSHostName -eq $null) -OR
    ($computerDetails.Domain -eq $null))
{
    # Unable to find computer details.
    # We will return false in that case.
    Write-Error "`nUnable to find host and domain details. Aborting process."
    return
}

$defaultDomain = $computerDetails.Domain

$domain = Read-Host -Prompt "Enter Admin Control Panel application's domain name e.g. contoso.com. Press ENTER to keep  $defaultDomain"
if([string]::IsNullOrWhiteSpace($domain))
{
    $domain = $defaultDomain
}

$extDomain = Read-Host -Prompt "Enter Admin Control Panel application's external domain name if its different from $domain or else ADFS OAuth wouldn't work for external website for Admin Control Panel "

[string[]] $poolList= @()
$poolList = (Read-Host -Prompt "Enter all the front end pool names in a comma separated manner without the domain name e.g. pool0,pool1,pool2 etc")
$poolList = $poolList.Split(',').Split(' ')

if($poolList.Count -eq 0)
{
    Write-Error "`nAt least 1 pool machine name is mandatory. Please run the script again once you are ready with the names. Deleting $groupName."
    Remove-AdfsApplicationGroup -TargetApplicationGroupIdentifier $groupName
    exit
}

foreach($poolName in $poolList)
{
    if ($poolName -match "^(\w+).$domain$" -or `
        (![string]::IsNullOrWhiteSpace($extDomain) -and `
         $poolName -match "^(\w+).$extDomain$"))
    {
        Write-Error "Enter pool name $poolName without domain name."
        Remove-AdfsApplicationGroup -TargetApplicationGroupIdentifier $groupName
        exit
    }
}

[string[]] $redirectUrls = @()
foreach ($poolName in $poolList)
{
    $redirectUrls += "https://" + $poolName + "." + $domain + "/macp/login"
    $redirectUrls += "https://" + $poolName + "." + $domain + "/macp/logout"
    $redirectUrls += "https://" + $poolName + "." + $domain + "/macp/portal_oauth_iframe.html"

    if (![string]::IsNullOrWhiteSpace($extDomain))
    {
        $redirectUrls += "https://" + $poolName + "." + $extDomain + "/macp/login"
        $redirectUrls += "https://" + $poolName + "." + $extDomain + "/macp/logout"
        $redirectUrls += "https://" + $poolName + "." + $extDomain + "/macp/portal_oauth_iframe.html"
    }
}

# Handling entry for simplifiedUrl.
$simplifiedUrl = Read-Host -Prompt "Enter Admin Control Panel application's simplified URL eg. https://admin.contoso.com. Press ENTER to skip "

if (![string]::IsNullOrWhiteSpace($simplifiedUrl))
{
    if ($simplifiedUrl.StartsWith('http://'))
    {
        $simplifiedUrl = $simplifiedUrl.Replace('http://', '')
    }

    if (!$simplifiedUrl.StartsWith('https://'))
    {
        $simplifiedUrl = "https://" + $simplifiedUrl
    }

    $simplifiedUrl = $simplifiedUrl.TrimEnd('/')

    $redirectUrls += $simplifiedUrl + "/login"
    $redirectUrls += $simplifiedUrl + "/logout"
    $redirectUrls += $simplifiedUrl + "/macp/portal_oauth_iframe.html"
}


try
{
    Add-AdfsNativeClientApplication -ApplicationGroupIdentifier $groupName -Name $appName -Identifier $clientIdentifier -RedirectUri $redirectUrls
}
catch
{
    Write-Error "`nUnable to create Admin Control Panel Native Client App. Deleting $groupName. Aborting process."
    Remove-AdfsApplicationGroup -TargetApplicationGroupIdentifier $groupName
    throw
    exit
}

Write-Host "`nAdmin Control panel Native App created successfully with client Id: $clientIdentifier." -ForeGroundColor Green

Write-Host "`nDetails of the App are:`n"
Get-AdfsNativeClientApplication -Identifier $clientIdentifier
```
## Configure OAuth for MACP

This script should be run after installing Skype for Business Server 2019 latest Cumulative Update, as part of the set-up for the new Control Panel.

```powershell
<#
 .SYNOPSIS
 Helper script to configure SFB 2019 control panel with ADFS OAuth.

 .DESCRIPTION
 Copyright (c) Microsoft Corporation. All rights reserved.

 THIS CODE IS MADE AVAILABLE AS IS, WITHOUT WARRANTY OF ANY KIND. THE ENTIRE RISK
 OF THE USE OR THE RESULTS FROM THE USE OF THIS CODE REMAINS WITH THE USER.

 .PARAMETER AdfsClientId
 Specify the client identifier application created for the admin control panel in the ADFS.

 .PARAMETER AdfsMetadataPublicUri
 OAuth metadata public URI for the admin control panel in the ADFS.

 .PARAMETER AdfsIssuerName
 Issuer Name for the admin control panel in the ADFS.

 .PARAMETER AdfsOAuthInstance
 ADFS farm instance (FQDN) where the admin control panel is registered for ADFS OAuth.

 .PARAMETER SimplifiedUrlPrefix
 The Simple URL prefix .

 .PARAMETER Pools
 List of pool names in which ADFS OAuth is to be setup for the admin control panel in a comma separated format. By default OAuth will setup for all FE pools deployed with Skype for Business 2019.

#>

function GetCurrentPoolName($computerDetails)
{
    $computerDnsHostName = $computerDetails.DNSHostName
    $domainName = $computerDetails.Domain

    $computerFqdn = $computerDnsHostName + "." + $domainName

    $poolName = (Get-CsComputer -Identity $computerFqdn).Pool

    return $poolName
}

function GetAllSfBW17Pools()
{
    $allFEPools = Get-csservice -Registrar | Where-Object {$_.Version -gt 7}
    $poolNamesArray = @()

    foreach ($pool in $allFEPools)
    {
        $poolNamesArray += ($pool.PoolFqdn)
    }

    return $poolNamesArray
}

function GeneratePoolNameArray($pools, $computerDetails)
{
    $poolNames = $pools.Split(',')
    $poolNamesArray = @()

    $domainName = $computerDetails.Domain
    foreach ($poolName in $poolNames)
    {
        if ($poolName -match "^(\w+.)$domainName$")
        {
            $poolNamesArray += ($poolName)
        }
        else
        {
            $poolNamesArray += ($poolName + "." + $domainName)
        }
    }

    return $poolNamesArray
}

function VerifyRoleAndVersionOfSelectedPools($poolArrays)
{
    foreach ($poolName in $poolArrays)
    {
        $services = Get-CsService -PoolFqdn $poolName

        if ($services -eq $null)
        {
            # Unable to find services for this pool.
            # We will mark it as not a Front-End machine.
            Write-Error "Didn't find any Services on Pool : $poolName"
            return $false
        }

        $found = $false

        foreach ($service in $services)
        {
            # Performing a case insensitive search here.
            if ($service.Role.ToLower().Equals("registrar") -AND
                $service.Version -gt 7)
            {
                # Found the Registrar role for the pool.
                # Hence, a Front-End machine.
                $found = $true
                break
            }
        }

        if ($found -eq $false)
        {
            Write-Error "Pool : $poolName is not Front End pool. Aborting process."
            return $false
        }
    }

    return $true
}

function VerifyMacpVersionOnFrontEndPools($cred, $pools, $macpRegistryPath, $minVersion)
{
    $returnVal = $true
    foreach ($poolName in $pools)
    {
        $computers = (Get-CsComputer -Pool $poolName).Identity
        $versionString = $null

        foreach ($computer in $computers)
        {
            $psSession = New-PSSession -computerName $computer -credential $cred
            $currentVersionStr = Invoke-Command -Session $psSession -ArgumentList $macpRegistryPath -ScriptBlock {
                param($macpRegistryPath)
                Get-ItemPropertyValue -Path $macpRegistryPath -Name "Version"
            }

            if ($psSession)
            {
                Remove-PSSession -Session $psSession
            }

            if (!$currentVersionStr)
            {
                Write-Error "Could not fetch current version of Admin Control Panel on $computer. Please check your connection or the credentials provided. Aborting process."
                $returnVal = $false;
            }
            else
            {
                Write-Host "`n`rInstalled version of Admin Control Panel on $computer : $currentVersionStr"

                if ($versionString -eq $null)
                {
                    $versionString = $currentVersionStr
                }
                else
                {
                    if ($currentVersionStr -ne $versionString)
                    {
                        Write-Error "Product version doesn't match across servers in Front-End pool: $poolName"
                        $returnVal = $false
                    }
                }

                if (([System.Version]$currentVersionStr -lt [System.Version]$minVersion) -OR
                    ([System.Version]$currentVersionStr -eq [System.Version]$minVersion))
                {
                    Write-Error "Install updates on Server: $computer in Front-End pool : $poolName to active ADFS OAuth Support for Admin Control Panel."
                    $returnVal = $false
                }
            }

            if ($returnVal -eq $false)
            {
                break
            }
        }
    }

    return $returnVal
}

function GetEditedFileContentForWebConfig($disableAdfsOAuth, $relativePath, $macpRegistryPath, $adfsClientId, $adfsMetadataPublicUri, $adfsIssuerName, $adfsOAuthInstance)
{
    $installDir = Get-ItemPropertyValue -Path $macpRegistryPath -Name "InstallDir"
    $filePath = Join-Path -Path $installDir -ChildPath $relativePath
    $fileContent = Get-Content -Path $filePath

    # We handle the case of replace the vdirAuth for web.config.
    # If the search string is not found or more than one instance is found we simply skip.
    $webConfigVdirSearchStr = $fileContent -match "<vdirAuth authType(.*)"
    if ($webConfigVdirSearchStr.Length -eq 1)
    {
        $searchVal = $webConfigVdirSearchStr[0]
        $searchedStrTrimmed = $searchVal.Trim()

        $adfsOAuthLineMatch = $fileContent -match "<adfsOAuth (.*)"
        if ($adfsOAuthLineMatch.Length -eq 1)
        {
            $adfsOAuthStr = $adfsOAuthLineMatch[0]
            $fileContent = $fileContent.Replace($adfsOAuthStr, '')
        }

        if ($disableAdfsOAuth -ne $true)
        {
            # Falling from WebTicket -> ADFSOnPrem,
            # Also adding the tokenized adfsOAuth settings entry.
            $countOfWhiteSpacesNeeded = $searchVal.Length - $searchedStrTrimmed.Length + 2
            $replaceStr = "<vdirAuth authType=`"ADFSOnPrem`">"
            $replaceStr = $replaceStr + "`r`n" + $(" " * $countOfWhiteSpacesNeeded) + `
            "<adfsOAuth adfsMetadataPublicUri=`"$adfsMetadataPublicUri`" adfsClientId=`"$adfsClientId`" adfsIssuerName=`"$adfsIssuerName`" />"
        }
        else
        {
            # Falling back from ADFSOnPrem -> WebTicket,
            # Removing the adfsOAuth settings entry.
            $replaceStr = "<vdirAuth authType=`"WebTicket`">"
        }

        $fileContent = $fileContent.Replace($searchedStrTrimmed, $replaceStr)
    }

    # Removing all empty lines
    $fileContent = $fileContent.Where({$_ -ne ''})

    return $fileContent
}

function GetEditedFileContentForIndexAspx($disableAdfsOAuth, $relativePath, $macpRegistryPath, $adfsClientId, $adfsOAuthInstance, $simplifiedUrlPrefix)
{
    $installDir = Get-ItemPropertyValue -Path $macpRegistryPath -Name "InstallDir"
    $filePath = Join-Path -Path $installDir -ChildPath $relativePath
    $fileContent = Get-Content -Path $filePath

    $patternString = '${{{0}}}'

    # Handling replacements back to tokens in index.aspx file
    $searchedStr = $fileContent -match "`"instance`": (.*)"

    if ($searchedStr.Length -gt 0)
    {
        foreach ($searchVal in $searchedStr)
        {
            $matchVal = $searchVal.ToLower().Contains("microsoftonline")
            if ($matchVal -eq $false)
            {
                $newReplacementValue = $patternString -f "AdfsOAuthInstance"
                $newStr = "`"instance`": `"$newReplacementValue`","
                $fileContent = $fileContent.Replace($searchVal.Trim(), $newStr)
                break
            }
        }
    }

    $searchedStr = $fileContent -match "`"clientId`": (.*)"
    if ($searchedStr.Length -eq 1)
    {
        $newReplacementValue = $patternString -f "AdfsClientId"
        $newStr = "`"clientId`": `"$newReplacementValue`","
        $fileContent = $fileContent.Replace($searchedStr[0].Trim(), $newStr)
    }

    $searchedStr = $fileContent -match "`"adfsOAuthEnabled`": (.*)"
    if ($searchedStr.Length -eq 1)
    {
        $newReplacementValue = $patternString -f "AdfsOAuthEnabled"
        $newStr = "`"adfsOAuthEnabled`": `"$newReplacementValue`","
        $fileContent = $fileContent.Replace($searchedStr[0].Trim(), $newStr)
    }

    $searchedStr = $fileContent -match "`"simplifiedUrlPrefix`": (.*)"
    if ($searchedStr.Length -eq 1)
    {
        $newReplacementValue = $patternString -f "SimplifiedUrlPrefix"
        $newStr = "`"simplifiedUrlPrefix`": `"$newReplacementValue`","
        $fileContent = $fileContent.Replace($searchedStr[0].Trim(), $newStr)
    }

    $adfsOAuthEnabled = $false
    if ($disableAdfsOAuth -ne $true)
    {
        $fileContent = $fileContent.Replace($patternString -f "AdfsClientId", $adfsClientId)
        $fileContent = $fileContent.Replace($patternString -f "AdfsOAuthInstance", $adfsOAuthInstance)
        $fileContent = $fileContent.Replace($patternString -f "SimplifiedUrlPrefix", $simplifiedUrlPrefix)
        $adfsOAuthEnabled = $true
    }

    $fileContent = $fileContent.Replace($patternString -f "AdfsOAuthEnabled", $adfsOAuthEnabled)
    # Removing all empty lines
    $fileContent = $fileContent.Where({$_ -ne ''})

    return $fileContent
}

function GenerateHttpsPrefix($inputVal)
{
    if ($inputVal.StartsWith('http://'))
    {
        $inputVal = $inputVal.Replace('http://', '')
    }

    if (!$inputVal.StartsWith('https://'))
    {
        $inputVal = "https://" + $inputVal
    }

    return $inputVal
}

function SetupOAuthOnFrontEndPools($cred, $pools, $macpRegistryPath, $disableAdfsOAuth, $relativePathToContentMap, $adfsClientId, $adfsMetadataPublicUri, $adfsIssuerName, $adfsOAuthInstance)
{
    foreach ($poolName in $pools)
    {
        $computers = (Get-CsComputer -Pool $poolName).Identity

        foreach ($computer in $computers)
        {
            $psSession = New-PSSession -computerName $computer -credential $cred
            Invoke-Command -Session $psSession `
            -ArgumentList $macpRegistryPath, $disableAdfsOAuth, $relativePathToContentMap, $adfsClientId, `
            $adfsMetadataPublicUri, $adfsIssuerName, $adfsOAuthInstance `
            -ScriptBlock {
                param($macpRegistryPath, $disableAdfsOAuth, $relativePathToContentMap, $adfsClientId, $adfsMetadataPublicUri, $adfsIssuerName, $adfsOAuthInstance)
                $installDir = Get-ItemPropertyValue -Path $macpRegistryPath -Name "InstallDir"

                foreach ($val in $relativePathToContentMap.GetEnumerator())
                {
                    $relativePath = $($val.Name)
                    $fileContent = $($val.Value)
                    $filePath = Join-Path -Path $installDir -ChildPath $relativePath
                    Set-Content -Path $filePath -Value $fileContent
                }

                $adfsOAuthEnabled = $true
                if ($disableAdfsOAuth -eq $true)
                {
                    $adfsOAuthEnabled = $false
                }

                Set-ItemProperty -Path $macpRegistryPath -Name "AdfsOAuthEnabled" -Value $adfsOAuthEnabled
                Set-ItemProperty -Path $macpRegistryPath -Name "AdfsClientId" -Value $adfsClientId
                Set-ItemProperty -Path $macpRegistryPath -Name "AdfsMetadataPublicUri" -Value $adfsMetadataPublicUri
                Set-ItemProperty -Path $macpRegistryPath -Name "AdfsIssuerName" -Value $adfsIssuerName
                Set-ItemProperty -Path $macpRegistryPath -Name "AdfsOAuthInstance" -Value $adfsOAuthInstance

                # Changing the application pool of Macp app to make it same as that of Skype for Business Server Web Site. This is needed for URL rewrite to work in case of Simple URL.
                # This is important to note that this change is required only for the Simple URL feature. However, we chose to make this change whenever ADFS is configured.
                # This change may not be reverted when we fall back to WebTicket. And that is alright.
                Import-Module WebAdministration
                Set-ItemProperty -Path 'IIS:\Sites\Skype for Business Server Internal Web Site\Macp' -Name applicationPool -Value LyncIntFeature
                Set-ItemProperty -Path 'IIS:\Sites\Skype for Business Server External Web Site\Macp' -Name applicationPool -Value LyncExtFeature

                iisreset
            }

            Remove-PSSession -Session $psSession
        }
    }
}

# Script execution start

$disableAdfsOAuth = $null
$adfsOAuthInstance = $null
$adfsClientId = $null
$adfsMetadataPublicUri = $null
$adfsIssuerName = $null
$simplifiedUrlPrefix = $null
$pools = $null

$mode = Read-Host -Prompt "Do you want to Enable [e] or Disable [d] ADFS OAuth for Admin Control Panel. Confirm[e/d]"
if([string]::IsNullOrWhiteSpace($mode))
{
  $mode = 'e'
}

if ($mode -match '^[eE]$')
{
  $disableAdfsOAuth = $false
  Write-Host "`n`rStarting script to enable ADFS OAuth." -ForeGroundColor Green

  $adfsOAuthInstance = Read-Host -Prompt "Enter the ADFS farm instance (FQDN) where the Admin Control Panel is registered for ADFS OAuth"
  $adfsOAuthInstance = GenerateHttpsPrefix -input $adfsOAuthInstance
  # Make sure that instance name has a trailing slash
  $adfsOAuthInstance = $adfsOAuthInstance.TrimEnd('/') + '/'

  $defaultAdfsMetadataPublicUri = $adfsOAuthInstance + 'FederationMetadata/2007-06/FederationMetadata.xml'
  $adfsMetadataPublicUri = Read-Host -Prompt "Enter OAuth Metadata Public URI for the Admin Control Panel in the ADFS. Press ENTER to use default $defaultAdfsMetadataPublicUri "
  if([string]::IsNullOrWhiteSpace($adfsMetadataPublicUri))
  {
      $adfsMetadataPublicUri = $defaultAdfsMetadataPublicUri
  }
  else
  {
    $adfsMetadataPublicUri = GenerateHttpsPrefix -input $adfsMetadataPublicUri
  }

  $adfsIssuerNameDefault = $adfsOAuthInstance.TrimEnd('/') + '/adfs'
  $adfsIssuerName = Read-Host -Prompt "Enter Issuer Name for the Admin Control Panel in the ADFS. Press ENTER to use default  $adfsIssuerNameDefault"
  if([string]::IsNullOrWhiteSpace($adfsIssuerName))
  {
      $adfsIssuerName = $adfsIssuerNameDefault
  }

  $adfsClientId = Read-Host -Prompt "Enter Client Identifier of the application created for the Admin Control Panel in the ADFS"

  if([string]::IsNullOrWhiteSpace($adfsClientId))
  {
    Write-Host "`n`rClient identifier cannot be empty" -ForeGroundColor Red
    Write-Host "`n`rAborting Process." -ForeGroundColor Red
    return
  }

  $simplifiedUrlPrefix = Read-Host -Prompt "Enter the Simple URL prefix for the Admin Control Panel (if configured). Press ENTER to use default 'admin.' "
  if([string]::IsNullOrWhiteSpace($simplifiedUrlPrefix))
  {
      $simplifiedUrlPrefix = 'admin.'
  }

}
elseif ($mode -match '^[dD]$')
{
  $disableAdfsOAuth = $true
  Write-Host "`n`rStarting script to disable ADFS OAuth."-ForeGroundColor Green
}
else
{
  Write-Host "`n`rInvalid Input." -ForeGroundColor Red
  Write-Host "`n`rAborting Process." -ForeGroundColor Red
  return
}

$pool = Read-Host -Prompt "Enter pool names in which ADFS OAuth is to be setup for the admin control panel in a comma separated format. Press ENTER to setup OAuth for all FE pools deployed with Skype for Business 2019"

# This is the registry path for Admin Control Panel for SfB 2019 machines.
$macpRegPath = "HKLM:\SOFTWARE\Microsoft\Real-Time Communications\{D00E3324-D7F8-4735-B4CF-206FE63FD577}"

# This is the min version string above which ADFS OAuth is enabled for Admin Control Panel.
$cu3VersionStr = "7.0.2046.216"

$poolArray=@()
$computerDetails = Get-WmiObject win32_computersystem

if (($computerDetails -eq $null) -OR
    ($computerDetails.DNSHostName -eq $null) -OR
    ($computerDetails.Domain -eq $null))
{
    # Unable to find computer details.
    # We will return false in that case.
    Write-Error "Unable to find host and domain details. Aborting process."
    return
}

if ($pools -eq $null)
{
    $poolName = GetAllSfBW17Pools
    if ($poolName.length -eq 0)
    {
        Write-Error "Error generating list of FE pool FQDN. Aborting process."
        return
    }

    $poolArray += ($poolName)
}
else
{
    $poolArray = GeneratePoolNameArray -pools $pools -computerDetails $computerDetails

    if ($poolArray.length -eq 0)
    {
        Write-Error "Error parsing pool names."
        return
    }
}

$status = VerifyRoleAndVersionOfSelectedPools -poolArray $poolArray

if ($status -eq $false)
{
    Write-Error "Not all the pools mentioned are Front end pool or deployed with SfB 2019. Aborting process."
    return
}

Write-Host "`n`rStarting modification to all the servers in Skype for Business 2019 FE pools (or Pools mentioned using -Pools parameter). Please provide Administrator credentials."
$cred = Get-Credential

if ($cred -eq $null)
{
    Write-Error "Credential is not defined. Aborting process."
    return
}

if ($disableAdfsOAuth.Equals($false))
{
    $adfsOAuthInstance = GenerateHttpsPrefix -input $adfsOAuthInstance
    $adfsMetadataPublicUri = GenerateHttpsPrefix -input $adfsMetadataPublicUri
    $adfsIssuerName = GenerateHttpsPrefix -input $adfsIssuerName

    # Removing any trailing slash from the issuer name
    $adfsIssuerName = $adfsIssuerName.TrimEnd('/')

    # Make sure that instance name has a trailing slash
    $adfsOAuthInstance = $adfsOAuthInstance.TrimEnd('/') + '/'
}

$status = VerifyMacpVersionOnFrontEndPools -cred $cred -pools $poolArray -macpRegistryPath $macpRegPath -minVersion $cu3VersionStr

if ($status -eq $false)
{
    Write-Error "Not all the pools have the required CU installed for MacpWebComponents. Please update to the latest version. Aborting process."
    return
}

$internalOcsPswsPath = "Web Components\OcsPsws\Int\"
$externalOcsPswsPath = "Web Components\OcsPsws\Ext\"
$internalMacpPath = "Web Components\Macp\Int\"
$externalMacpPath = "Web Components\Macp\Ext\"

$ocsPswsInternalWebConfigPath = Join-Path -Path $internalOcsPswsPath -ChildPath "web.config"
$ocsPswsExternalWebConfigPath = Join-Path -Path $externalOcsPswsPath -ChildPath "web.config"
$macpInternalIndexAspxPath = Join-Path -Path $internalMacpPath -ChildPath "index.aspx"
$macpExternalIndexAspxPath = Join-Path -Path $externalMacpPath -ChildPath "index.aspx"

$internalOcsPswsWebConfigContent = GetEditedFileContentForWebConfig -disableAdfsOAuth $disableAdfsOAuth -relativePath $ocsPswsInternalWebConfigPath `
-macpRegistryPath $macpRegPath -adfsClientId $adfsClientId -adfsMetadataPublicUri $adfsMetadataPublicUri -adfsIssuerName $adfsIssuerName -adfsOAuthInstance $adfsOAuthInstance

$externalOcsPswsWebConfigContent = GetEditedFileContentForWebConfig -disableAdfsOAuth $disableAdfsOAuth -relativePath $ocsPswsExternalWebConfigPath `
-macpRegistryPath $macpRegPath -adfsClientId $adfsClientId -adfsMetadataPublicUri $adfsMetadataPublicUri -adfsIssuerName $adfsIssuerName -adfsOAuthInstance $adfsOAuthInstance

$internalIndexAspxContent = GetEditedFileContentForIndexAspx -disableAdfsOAuth $disableAdfsOAuth -relativePath $macpInternalIndexAspxPath `
-macpRegistryPath $macpRegPath -adfsClientId $adfsClientId -adfsOAuthInstance $adfsOAuthInstance -simplifiedUrlPrefix $simplifiedUrlPrefix

$externalIndexAspxContent = GetEditedFileContentForIndexAspx -disableAdfsOAuth $disableAdfsOAuth -relativePath $macpExternalIndexAspxPath `
-macpRegistryPath $macpRegPath -adfsClientId $adfsClientId -adfsOAuthInstance $adfsOAuthInstance -simplifiedUrlPrefix $simplifiedUrlPrefix

$finalRelativePathToContentMap = @{}
$key = Join-Path -Path $internalOcsPswsPath -ChildPath "web.config"
$finalRelativePathToContentMap[$key] = $internalOcsPswsWebConfigContent

$key = Join-Path -Path $externalOcsPswsPath -ChildPath "web.config"
$finalRelativePathToContentMap[$key] = $externalOcsPswsWebConfigContent

$key = Join-Path -Path $internalMacpPath -ChildPath "index.aspx"
$finalRelativePathToContentMap[$key] = $internalIndexAspxContent

$key = Join-Path -Path $externalMacpPath -ChildPath "index.aspx"
$finalRelativePathToContentMap[$key] = $externalIndexAspxContent

SetupOAuthOnFrontEndPools -cred $cred -pools $poolArray -macpRegistryPath $macpRegPath `
-disableAdfsOAuth $disableAdfsOAuth -relativePathToContentMap $finalRelativePathToContentMap -adfsClientId $adfsClientId `
-adfsMetadataPublicUri $adfsMetadataPublicUri -adfsIssuerName $adfsIssuerName -adfsOAuthInstance $adfsOAuthInstance

if ($disableAdfsOAuth -eq $true)
{
    Write-Host "`n`rADFS OAuth has been disabled for the admin control panel." -ForeGroundColor Green
}
else
{
    Write-Host "`n`rADFS OAuth has been enabled for the admin control panel." -ForeGroundColor Green
}
```
