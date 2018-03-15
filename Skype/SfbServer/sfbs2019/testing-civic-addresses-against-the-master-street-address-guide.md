---
title: "Testing civic addresses against the master street address guide in Lync Server 2013"
ms.author: jambirk
author: jambirk
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: dc680de9-2a0f-4fd3-a99e-9bab0bc30ae5

description: "In this articleDescriptionRunning the testDetermining success or failureReasons why the test might have failed"
---

# Testing civic addresses against the master street address guide in Lync Server 2013
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
|Permissions required  <br/> |When run locally using the Lync Server Management Shell, users must be members of the RTCUniversalServerAdmins security group.  <br/> When run using a remote instance of Windows PowerShell, users must be assigned an RBAC role that has permission to run the Test-CsRegistration cmdlet. To see a list of all RBAC roles that can use this cmdlet, run the following command from the Windows PowerShell prompt:  <br/> ```Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsLisCivicAddress "}```|
   
## Description
<a name="sectionSection0"> </a>

The Test-CsLisCivicAddress cmdlet is used to verify locations that were added to your Location Information service (LIS) database. The cmdlet works by comparing locations against the locations found in the Master Street Address Guide (MSAG) that belongs to your E9-1-1 Network Routing Provider. If you do not have a network routing provider or if the provider cannot be reached, then your tests will fail.
  
If you add the optional switch parameter UpdateValidationStatus to your command, then the corresponding MSAGValid database property will be set to True for each address passing the test.
  
## Running the test
<a name="sectionSection1"> </a>

The Test-CsLisCivicAddress cmdlet can be used to test individual addresses or to test multiple addresses. For example, this command tests a single address located in Redmond, WA: 
  
```
Test-CsLisCivicAddress -HouseNumber 1234 -HouseNumberSuffix "" -PreDirectional "" -StreetName Main -StreetSuffix St -PostDirectional "" -City Redmond -State WA -PostalCode 98052 -Country US -UpdateValidationStatus
```

By comparison, this command tests all the addresses currently in your LIS database: 
  
```
Get-CsLisCivicAddress | Test-CsLisCivicAddress -UpdateValidationStatus
```

For more information, see the Help documentation for the [Test-CsRegistration](test-csregistration.md) cmdlet. 
  
## Determining success or failure
<a name="sectionSection2"> </a>

Test-CsLisCivicAddress will report back Success or Failure for the supplied addresses. An address test will fail if the address cannot be found or if the service provider cannot be contacted.
  
## Reasons why the test might have failed
<a name="sectionSection3"> </a>

Here are some common reasons why Test-CsLisCivicAddress might fail:
  
- The LIS service provider might not be available. You can retrieve the URL of your LIS service provider by running the Get-CsLisConfiguration cmdlet: 
    
  ```
  Get-CsLisConfiguration 
  ```

    You can then ping that URL to verify that the service provider is available.
    

