---
title: PowerShell script sample - SIP tester client 
author: LanaChin
ms.author: v-lanac
manager: serdars
ms.topic: article
ms.reviewer: filippse
ms.service: msteams
audience: admin
description: Use this PowerShell script to test basic functionality of a customer-paired SIP trunk with Azure PSTN Edge and Skype Next Gen Core.
localization_priority: Normal
ms.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
appliesto: 
- Microsoft Teams
---

PowerShell script sample - SIP tester client
-------------------------------------------------------------------------

Use this PowerShell script to


## Sample script

````powershell
<#
.SYNOPSIS
    SIP Tester Client

.DESCRIPTION
    This script submits SIP test to PSTN Inspector, waits for final result and presents the result in a human-readable format.
    Please note, that this script will prompt the user for credentials which are needed for AAD auth on PSTN Inspector.
    
    This script needs adal.ps package for execution. If it's not present then script will attempt to install it automatically.
    For this, please run this script in ADMINISTRATOR Mode (first execution only).

    Call flow common to all tests:
	* Outbound call is placed by TeamsOut user to a number specified in the DestinationNumber.
	* SBC receives INVITE and places outbound call back to TeamsIn user's phone number.
	* Call to TeamsIn user is accepted.
	* Media is played/recorded in sequence both ways and validated that is not empty.

    Important note about TeamsOut and TeamsIn* users:
    * It is recommended that users are in different tenants (all TeamsIn* users might be in the same tenant though).
        This shouldn't require special configuration on PSTN partner's SBC under test and therefore more closely replicates real-life call flow.
        In this case DestinationNumber and all TeamsIn* users' IncomingNumbers are real numbers assigned to respective users in Teams backend.
    * These users might be in the same tenant in which case additional configuration is required on PSTN partner's SBC under test.
        Specifically, DestinationNumber and all TeamsIn* users' IncomingNumbers must not be assigned to users in Teams backend but rather contain 
        special prefixes/suffixes that the SBC under test will strip and route the calls back to Teams. 
        As an example, if TeamsIn user's assigned phone number is +12345 then message manipulation and routing rules could be setup on the SBC 
        to route calls placed to +99912345 back to Teams and to +12345.

    Each test run is then represented in the output as series of rows, each indicating the result of the call made as part of the test:
    * Flow - call direction relative to Teams backend, outbound or inbound
    * SipCallId - SIP call ID of SBC under test
    * Code - call result code, 0 for success, non-0 for failure (internal to Teams backend)
    * TrunkFqdn - the actual SBC used for the test
    * ChainId - the internal Teams call ID
    * State - succeeded or failed
    * Phrase - arbitrary phrase indicating the reason for failure if any

    This script returns True value if test passes, False value if test fails.

.PARAMTER TeamsOutUsername
    Username of caller Teams (used to make outbound call)

.PARAMETER TeamsOutPassword
    Password of caller Teams (used to make outbound call)

.PARAMETER TeamsInUsername
    User principal name of callee Teams (used to receive inbound call).

.PARAMETER TeamsInPassword
    Password of callee Teams (used to receive inbound call)

.PARAMETER DestinationNumber
    PSTN number that is routed to TeamsIn user

.PARAMETER TeamsOutDataCenter
    (Optional) Preferred location of Teams client (used to make outbound call), valid values: [APAC-SG, APAC-HK, EMEA-DB, EMEA-AM, NOAM-BL, NOAM-DM]

.PARAMETER TeamsInDataCenter
    (Optional) Preferred location of Teams client (used to receive inbound call), valid values: [APAC-SG, APAC-HK, EMEA-DB, EMEA-AM, NOAM-BL, NOAM-DM]

.PARAMETER TeamsInEscalationUsername
    (Optional) User principal name of the escalation target Teams (used to escalate call)

.PARAMETER TeamsInEscalationPassword
    (Optional) Password of the escalation target Teams (used to escalate call)

.PARAMETER TeamsInEscalationIncomingNumber
    (Optional) PSTN number that is routed to TeamsInEscalation user

.PARAMETER TeamsInEscalationDataCenter
    (Optional) Preferred location of Teams client (used to escalate call), valid values: [APAC-SG, APAC-HK, EMEA-DB, EMEA-AM, NOAM-BL, NOAM-DM]

.PARAMETER TeamsInTransferTargetUsername
    (Optional) User principal name of the transfer target Teams (used to transfer call)

.PARAMETER TeamsInTransferTargetPassword
    (Optional) Password of the transfer target Teams (used to tranfer call)

.PARAMETER TeamsInTransferTargetIncomingNumber
    (Optional) PSTN number that is routed to TeamsInTransferTarget user

.PARAMETER TeamsInTransferTargetDataCenter
    (Optional) Preferred location of Teams client (used to transfer call), valid values: [APAC-SG, APAC-HK, EMEA-DB, EMEA-AM, NOAM-BL, NOAM-DM]

.PARAMETER TeamsInSimulringUsername
    (Optional) User principal name of the simultaneous ring target Teams (used for simultaneous ring)
    
.PARAMETER TeamsInSimulringPassword
    (Optional) Password of the simultaneous ring target Teams (used for simultaneous ring)
    
.PARAMETER TeamsInSimulringIncomingNumber
    (Optional) PSTN number that is routed to TeamsInSimulring user 

.PARAMETER TeamsInSimulringDataCenter
    (Optional) Preferred location of Teams client (used for simultaneous call), valid values: [APAC-SG, APAC-HK, EMEA-DB, EMEA-AM, NOAM-BL, NOAM-DM]

.PARAMETER CertificateContent
    Base64 Certificate content for authentication

.PARAMETER ProviderId 
    (Optional) Used to verify call records for BV users

.PARAMETER CallDurationMinutes
    Duration of the call in minutes

.PARAMETER MediaValidationFrequencyMinutes
    Frequency of media validation during call in minutes

.PARAMETER HideTable
    (Optional) Won't print out table of test results.

.PARAMETER UseUserCredentials
    (Optional) Uses TeamsOut credentials for authentication.  

.EXAMPLE
    .\SipTesterClient.ps1 -TeamsOutUsername user1 -TeamsOutPassword pass1 -TeamsInUsername user2 -TeamsInPassword pass2 -DestinationNumber +12345
    .\SipTesterClient.ps1 -TeamsOutUsername user1 -TeamsOutPassword pass1 -TeamsInUsername user2 -TeamsInPassword pass2 -DestinationNumber +12345 -TeamsInSimulringUsername user3 -TeamsInSimulringPassword pass3 -TeamsInSimulringIncomingNumber +67890
    .\SipTesterClient.ps1 -TeamsOutUsername user1 -TeamsOutPassword pass1 -TeamsInUsername user2 -TeamsInPassword pass2 -DestinationNumber +12345 -TeamsInTransferTargetUsername user3 -TeamsInTransferTargetPassword pass3 -TeamsInTransferTargetIncomingNumber +67890
    .\SipTesterClient.ps1 -TeamsOutUsername user1 -TeamsOutPassword pass1 -TeamsInUsername user2 -TeamsInPassword pass2 -DestinationNumber +12345 -TeamsInEscalationUsername user3 -TeamsInEscalationPassword pass3 -TeamsInEscalationIncomingNumber +67890
#>

[CmdletBinding()]
Param (
    [Parameter(ParameterSetName="Basic", Mandatory=$True)]
    [Parameter(ParameterSetName="Escalation", Mandatory=$True)]
    [Parameter(ParameterSetName="Transfer", Mandatory=$True)]
    [Parameter(ParameterSetName="Simulring", Mandatory=$True)]
    [string]$TeamsOutUsername,

    [Parameter(ParameterSetName="Basic", Mandatory=$True)]
    [Parameter(ParameterSetName="Escalation", Mandatory=$True)]
    [Parameter(ParameterSetName="Transfer", Mandatory=$True)]
    [Parameter(ParameterSetName="Simulring", Mandatory=$True)]
    [string]$TeamsOutPassword,

    [Parameter(ParameterSetName="Basic", Mandatory=$True)]
    [Parameter(ParameterSetName="Escalation", Mandatory=$True)]
    [Parameter(ParameterSetName="Transfer", Mandatory=$True)]
    [Parameter(ParameterSetName="Simulring", Mandatory=$True)]
    [string]$TeamsInUsername,

    [Parameter(ParameterSetName="Basic", Mandatory=$True)]
    [Parameter(ParameterSetName="Escalation", Mandatory=$True)]
    [Parameter(ParameterSetName="Transfer", Mandatory=$True)]
    [Parameter(ParameterSetName="Simulring", Mandatory=$True)]
    [string]$TeamsInPassword,

    [Parameter(ParameterSetName="Basic", Mandatory=$True)]
    [Parameter(ParameterSetName="Escalation", Mandatory=$True)]
    [Parameter(ParameterSetName="Transfer", Mandatory=$True)]
    [Parameter(ParameterSetName="Simulring", Mandatory=$True)]
    [string]$DestinationNumber,

    [Parameter(ParameterSetName="Basic", Mandatory=$False)]
    [Parameter(ParameterSetName="Escalation", Mandatory=$False)]
    [Parameter(ParameterSetName="Transfer", Mandatory=$False)]
    [Parameter(ParameterSetName="Simulring", Mandatory=$False)]
    [int]$CallDurationMinutes = $null,

    [Parameter(ParameterSetName="Basic", Mandatory=$False)]
    [Parameter(ParameterSetName="Escalation", Mandatory=$False)]
    [Parameter(ParameterSetName="Transfer", Mandatory=$False)]
    [Parameter(ParameterSetName="Simulring", Mandatory=$False)]
    [int]$MediaValidationFrequencyMinutes = $null,

    [Parameter(ParameterSetName="Basic", Mandatory=$False)]
    [Parameter(ParameterSetName="Escalation", Mandatory=$False)]
    [Parameter(ParameterSetName="Transfer", Mandatory=$False)]
    [Parameter(ParameterSetName="Simulring", Mandatory=$False)]
    [string]$TeamsOutDataCenter,

    [Parameter(ParameterSetName="Basic", Mandatory=$False)]
    [Parameter(ParameterSetName="Escalation", Mandatory=$False)]
    [Parameter(ParameterSetName="Transfer", Mandatory=$False)]
    [Parameter(ParameterSetName="Simulring", Mandatory=$False)]
    [string]$TeamsInDataCenter,

    [Parameter(ParameterSetName="Escalation", Mandatory=$False)]
    [string]$TeamsInEscalationDataCenter,

    [Parameter(ParameterSetName="Transfer", Mandatory=$False)]
    [string]$TeamsInTransferTargetDataCenter,

    [Parameter(ParameterSetName="Simulring", Mandatory=$False)]
    [string]$TeamsInSimulringDataCenter,

    [Parameter(ParameterSetName="Escalation", Mandatory=$True)]
    [string]$TeamsInEscalationUsername,
    
    [Parameter(ParameterSetName="Escalation", Mandatory=$True)]
    [string]$TeamsInEscalationPassword,
    
    [Parameter(ParameterSetName="Escalation", Mandatory=$False)]
    [string]$TeamsInEscalationIncomingNumber = '',
    
    [Parameter(ParameterSetName="Transfer", Mandatory=$True)]
    [string]$TeamsInTransferTargetUsername,
    
    [Parameter(ParameterSetName="Transfer", Mandatory=$True)]
    [string]$TeamsInTransferTargetPassword,
    
    [Parameter(ParameterSetName="Transfer", Mandatory=$True)]
    [string]$TeamsInTransferTargetIncomingNumber,

    [Parameter(ParameterSetName="Simulring", Mandatory=$True)]
    [string]$TeamsInSimulringUsername,

    [Parameter(ParameterSetName="Simulring", Mandatory=$True)]
    [string]$TeamsInSimulringPassword,

    [Parameter(ParameterSetName="Simulring", Mandatory=$True)]
    [string]$TeamsInSimulringIncomingNumber,

    [string] $EndpointUrl = "https://api.pstnmonitoring.skype.com/v1/sip-tester/test-suites",

    [string]$TestTimeoutInSeconds=180,

    [string]$ProviderId = $null,

    [string]$CertificateContent = $null,

    [string]$Environment = $null,
    
    [Parameter(Mandatory = $false)]    
    [switch] $HideTable,

    [Parameter(Mandatory = $false)]  
    [switch] $UseUserCredentials
)


Function Get-Response([string]$uri, [string]$method, [PSObject]$body, [string]$token, [System.Security.Cryptography.X509Certificates.X509Certificate2]$certificate) {
    $timeoutSeconds = 60

    $headers = @{
	    'Content-Type' = 'application/json';
    	'Authorization' = 'Bearer ' + $token
    }

    Try {
        $resultBucket = New-Object PSObject

    	$testResult = Invoke-WebRequest -Uri $uri -Headers $headers -Method $method -Body $body -Certificate $certificate -UseBasicParsing -TimeoutSec $timeoutSeconds | select -Expand Content	
      
        $resultBucket | Add-Member -Name 'Success' -MemberType Noteproperty -Value $True
        $resultBucket | Add-Member -Name 'Content' -MemberType Noteproperty -Value $testResult
      
    }
    catch [System.Net.WebException] {
        $resultBucket | Add-Member -Name 'Success' -MemberType Noteproperty -Value $False
        $resultBucket | Add-Member -Name 'Content' -MemberType Noteproperty -Value $_.Exception.Message
    }
    Catch {
        $resultBucket | Add-Member -Name 'Success' -MemberType Noteproperty -Value $False
        $resultBucket | Add-Member -Name 'Content' -MemberType Noteproperty -Value 'Unspecified Failure' 
    }

    $resultBucket  
}

Function Run-SIPTest([string]$sipTesterUri, [string]$testBody, [string]$certificateContent) {
    $delayInSeconds = 10

    $authority = "https://login.windows.net/common/oauth2/authorize" 
    $resourceUrl = "https://calltester.pstnhub.microsoft.com" #2c08a8c9-c50a-42b6-b954-f4207adc4947
    $clientId = "1950a258-227b-4e31-a9cf-717495945fc2" #Set well-known client ID for AzurePowerShell

    $accessToken = $Null
    $certificate = New-Object System.Security.Cryptography.X509Certificates.X509Certificate2

    if ([string]::IsNullOrEmpty($certificateContent)) {
        Write-Verbose "Acquiring AAD token..."
        $response = $null

        if ($UseUserCredentials) {
            Import-Module ADAL.PS

            $pwd = ConvertTo-SecureString -AsPlainText $TeamsOutPassword -Force
            $authContext = New-Object "Microsoft.IdentityModel.Clients.ActiveDirectory.AuthenticationContext" -ArgumentList $authority
            $AADcredential = New-Object "Microsoft.IdentityModel.Clients.ActiveDirectory.UserPasswordCredential" -ArgumentList $TeamsOutUsername,$pwd
            $req = [Microsoft.IdentityModel.Clients.ActiveDirectory.AuthenticationContextIntegratedAuthExtensions]::AcquireTokenAsync($authContext,$resourceUrl,$clientId,$AADcredential)
            $response = $req.Result
        } else {
            $response = Get-ADALToken -Resource $resourceUrl -ClientId $clientId -Authority $authority
        }

        $accessToken = $response.AccessToken
        Write-Verbose "Acquiring AAD token...DONE"
    } else {
        $certificate.Import([Convert]::FromBase64String($certificateContent))
    }


    Write-Verbose "Enqueueing test..."
    $enqueueResult = Get-Response $sipTesterUri POST $testBody $accessToken $certificate

    if (!$enqueueResult.Success) {
        Write-Error "Enqueueing test...FAILED: $($enqueueResult.Content)"
        return $null
    }
    Write-Verbose "Enqueueing test...DONE"

    $enqueueContent = $enqueueResult.Content | ConvertFrom-Json
    $statusLink = $enqueueContent.links.status

    Write-Verbose "Test status link: $statusLink"
    Write-Verbose "Checking test status..." 

    do {
        $statusResult = Get-Response $statusLink GET $null $accessToken $certificate # null body
        $statusResult | Add-Member -Name 'BatchId' -MemberType Noteproperty -Value '<Unknown>'

        if (!$statusResult.Success) {
            Write-Verbose "Checking test status...FAILED: $($statusResult.Content)"
            return $statusResult
        }
    
        $statusContent = $statusResult.Content | ConvertFrom-Json
    
        $lastResult = $statusContent.tests[0].lastResult
                
        if ($lastResult.state -eq 'failed' -or $lastResult.state -eq 'succeeded') {
            $statusResult.BatchId = $lastResult.batchId
            return $statusResult
        }
    
        Write-Verbose "Test in '$($lastResult.state)' state; Checking again in $delayInSeconds seconds..."

        Start-Sleep -Seconds $delayInSeconds
    } while($True)  
   
}

$testTitles = @{
    "Basic" = "Outbound to Inbound";
    "Escalation" = "Media Escalation";
    "Simulring" = "Simultaneous Ring";
    "Transfer" = "Consultative Transfer";
}

#Install the ADAL.PS package if it's not installed.
if($CertificateContent -eq $null -and !(Get-Package adal.ps)) { Install-Package -Name adal.ps }

$ErrorActionPreference = "Continue"
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12

$teamsOut = @{username = $teamsOutUsername; password = $teamsOutPassword; dataCenter = $TeamsOutDataCenter}
$teamsIn = @{username = $teamsInUsername; password = $teamsInPassword; incomingNumber = $destinationNumber; dataCenter = $TeamsInDataCenter}
$test = @{teamsOut = $teamsOut; teamsIn = $teamsIn; providerId = $providerId}

if ($CallDurationMinutes){
    $test.Add("callDurationMinutes", $CallDurationMinutes)
}
if ($MediaValidationFrequencyMinutes) {
    $test.Add("mediaValidationFrequencyMinutes", $MediaValidationFrequencyMinutes)
}
if ($Environment) {
    $test.Add("environment", $Environment)
}

switch ($PSCmdlet.ParameterSetName)
{
    "Escalation"{
        $additionalParams = @{username = $TeamsInEscalationUsername; password = $TeamsInEscalationPassword; dataCenter = $TeamsInEscalationDataCenter}
	if('' -ne $TeamsInEscalationIncomingNumber) {
		$additionalParams.Add("incomingNumber", $TeamsInEscalationIncomingNumber)
	}
        $test.Add("teamsInEscalation", $additionalParams)
    }
    "Transfer"{
        $additionalParams = @{username = $TeamsInTransferTargetUsername; password = $TeamsInTransferTargetPassword; incomingNumber = $TeamsInTransferTargetIncomingNumber; dataCenter = $TeamsInTransferTargetDataCenter }
        $test.Add("teamsInTransferTarget", $additionalParams)
    }
    "Simulring"{
        $additionalParams = @{username = $TeamsInSimulringUsername; password = $TeamsInSimulringPassword; incomingNumber = $TeamsInSimulringIncomingNumber; dataCenter = $TeamsInSimulringDataCenter}
        $test.Add("teamsInSimulring", $additionalParams)
    }
}

$tests = @{timeoutSeconds = $testTimeoutInSeconds; tests = @($test)}
$testBody = $tests | ConvertTo-Json -Depth 20

$statusResult = Run-SIPTest $EndpointUrl $testBody $CertificateContent

if($null -ne $statusResult) {

    $statusContent = $statusResult.Content | ConvertFrom-Json
    $lastResult = $statusContent.tests[0].lastResult

    Write-Verbose "Test in '$($lastResult.state)' state"

    $lastResult.teamsOut | Add-Member -Name 'flow' -MemberType Noteproperty -Value 'outbound'
    $lastResult.teamsIn | Add-Member -Name 'flow' -MemberType Noteproperty -Value 'inbound'

    switch ($PSCmdlet.ParameterSetName)
    {
        "Basic" {
            $table = @($lastResult.teamsOut, $lastResult.TeamsIn)
        }
        "Escalation"{
            $lastResult.teamsInEscalation | Add-Member -Name 'flow' -MemberType Noteproperty -Value 'inbound'
            $table = @($lastResult.teamsOut, $lastResult.TeamsIn, $lastResult.TeamsInEscalation)
        }
        "Transfer"{
            $lastResult.teamsInTransferTarget | Add-Member -Name 'flow' -MemberType NoteProperty -Value 'inbound'
            $table = @($lastResult.teamsOut, $lastResult.TeamsIn, $lastResult.TeamsInTransferTarget)
        }
        "Simulring"{
            $lastResult.TeamsInSimulring | Add-Member -Name 'flow' -MemberType NoteProperty -Value 'inbound'
            $table = @($lastResult.teamsOut, $lastResult.teamsIn, $lastResult.TeamsInSimulring)
        }
    }

    if (!$HideTable) {
        Write-Host ( "`r`n`r`nTest: {0}" -f $testTitles[$PSCmdlet.ParameterSetName] )
        Write-Host (($table | Select -Property * -ExcludeProperty callSetupTimeMs) | Format-Table -AutoSize | Out-String -Width 4000)    
    }

    if ($lastResult.state -eq 'failed') {
        Write-Error "Failed test: $($lastResult.batchId)"
    }

    return ($lastResult.state -ne 'failed')
}

return $False
````


