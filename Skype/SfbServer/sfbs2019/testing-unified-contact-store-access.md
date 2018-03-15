---
title: "Testing Unified Contact Store access in Lync Server 2013"
ms.author: jambirk
author: jambirk
manager: laurawi
ms.date: 5/15/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 761f46bd-2e14-4f40-82b9-afa1eaa816b0

description: "In this articleDescriptionRunning the testDetermining success or failureReasons why the test might have failed"
---

# Testing Unified Contact Store access in Lync Server 2013
[]
 **In this article**
  
[Description](#sectionSection0)
  
[Running the test](#sectionSection1)
  
[Determining success or failure](#sectionSection2)
  
[Reasons why the test might have failed](#sectionSection3)
  
****

|||
|:-----|:-----|
|Verification schedule  <br/> |Daily  <br/> |
|Testing tool  <br/> |Windows PowerShell  <br/> |
|Permissions required  <br/> |When run locally using the Lync Server Management Shell, users must be members of the RTCUniversalServerAdmins security group.  <br/> When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the **Test-CsUnifiedContactStore** cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:  <br/> ```Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsUnifiedContactStore"}```|
   
## Description
<a name="sectionSection0"> </a>

The unified contact store introduced in Lync Server 2013 gives administrators the option of storing a user's contacts in Microsoft Exchange Server 2013 instead of in Lync Server. This allows the user to access the same set of contacts in Outlook Web Access in addition to Lync 2013. (Or, you can continue to store contacts in Lync Server. In that case, users will have to maintain two separate sets of contacts: one for use with Outlook and Outlook Web Access, and one for use with Lync 2013.)
  
You can determine whether or not a user's contacts were moved to the unified contact store by running the **Test-CsUnifiedContactStore** cmdlet. The **Test-CsUnifiedContactStore** cmdlet will take the specified user account, connect to the unified contact store, and attempt to retrieve a contact for the user. If no contacts can be retrieved then the command will fail together with the message "No contacts were received for the user. Verify that contacts exist for the user." 
  
Note that the **Test-CsUnifiedContactStore** cmdlet will fail if the user has successfully migrated to the unified contact store but has no contacts on his or her Contacts list. The specified user must have at least one contact for the **Test-CsUnifiedContactStore** cmdlet to complete successfully. 
  
## Running the test
<a name="sectionSection1"> </a>

The commands shown in in the following example determine whether contacts for the user litwareinc\kenmyer can be found in the unified contact store. To do this, the first command in the example uses the **Get-Credential** cmdlet to create a Windows PowerShell command-line interface credentials object for the user litwareinc\kenmyer. Note that you must supply the password for this account to create a valid credentials object and to make sure that the **Test-CsUnifiedContactStore** cmdlet can run its check. 
  
The second command in the example uses the supplied credentials object ($x) and the SIP address of the user litwareinc\kenmyer to determine whether his contacts can be found in the unified contact store.
  
```
$credential = Get-Credential "litwareinc\kenmyer"
Test-CsUnifiedContactStore -TargetFqdn "atl-cs-001.litwareinc.com" -UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $credential
```

## Determining success or failure
<a name="sectionSection2"> </a>

If access to the contact store is configured correctly, you'll receive output similar to this, with the Result property marked as **Success:**
  
Target Fqdn : atl-cs-001.litwareinc.com
  
Result : Success
  
Latency : 00:00:14.9862716
  
Error Message :
  
Diagnosis :
  
If access to the contact store is not configured correctly, the Result will be shown as **Failure**, and additional information will be recorded in the Error and Diagnosis properties:
  
WARNING: Failed to read Registrar port number for the given fully qualified
  
domain name (FQDN). Using default Registrar port number. Exception:
  
System.InvalidOperationException: No matching cluster found in topology.
  
 at 
  
Microsoft.Rtc.Management.SyntheticTransactions.SipSyntheticTransaction.TryRetri
  
eveRegistrarPortFromTopology(Int32&amp; registrarPortNumber)
  
Target Fqdn : atl-cs-001.litwareinc.com
  
Result : Failure
  
Latency : 00:00:00
  
Error Message : 10060, A connection attempt failed because the connected party
  
 did not properly respond after a period of time, or 
  
 established connection failed because connected host has 
  
 failed to respond 10.188.116.96:5061 
  
 Inner Exception:A connection attempt failed because the 
  
 connected party did not properly respond after a period of 
  
 time, or established connection failed because connected host 
  
 has failed to respond 10.188.116.96:5061 
  
Diagnosis :
  
## Reasons why the test might have failed
<a name="sectionSection3"> </a>

Here are some common reasons why **Test-CsUnifiedContactStore** might fail: 
  
- An incorrect parameter value was supplied. If used, the optional parameters must be configured correctly or the test will fail. Rerun the command without the optional parameters and see whether that succeeds. 
    
- Connect to the unified contact store failed, and the attempt to retrieve a contact for the user was not possible. There may be network connectivity issues. 
    
## See also
<a name="sectionSection3"> </a>

#### 

[New-CsUserServicesPolicy](new-csuserservicespolicy.md)
  
[Set-CsUserServicesPolicy](set-csuserservicespolicy.md)

