---
title: Get-CsApplicationEndpoint
ms.prod: SKYPEFORBUSINESS
ms.assetid: 820d3bbd-0348-4272-bdb3-c3d612d0836a
---


# Get-CsApplicationEndpoint
[]
Retrieves endpoints for the Application service. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Get-CsApplicationEndpoint [-Identity <UserIdParameter>] [-ApplicationId <String>] [-Credential <PSCredential>] [-DomainController <Fqdn>] [-Filter <String>] [-OU <OUIdParameter>] [-PoolFqdn <Fqdn>] [-ResultSize <Unlimited>]

```


## Examples


  
    
    

### EXAMPLE 1

This example retrieves information about all application endpoints defined within the Skype for Business Server 2015 deployment.
  
    
    

```

Get-CsApplicationEndpoint
```


### EXAMPLE 2

Example 2 retrieves all application endpoints that have the string "endpoint" anywhere within their display name. To do this, the command uses the Filter parameter. The value of the parameter filters to find endpoint objects that have a display name (DisplayName) that contains (-like) the string endpoint (*endpoint* - the wildcard characters indicate that any characters can come before or after the string endpoint, meaning endpoint can be anywhere within the display name).
  
    
    

```
Get-CsApplicationEndpoint -Filter {DisplayName -like "*endpoint*"}
```


### EXAMPLE 3

Example 3 returns all application endpoints associated with the application urn:application:tapp2. This is accomplished by passing the ID tapp2 to the ApplicationId parameter. Notice that we didn't supply a pool FQDN; this means that if an application with the ID tapp2 exists on more than one pool, endpoints for all those applications will be retrieved. The next part of this command pipes the returned object or objects to the **Select-Object** cmdlet, which displays only the Identity, SipAddress, DisplayName, and OwnerUrn properties of those objects.
  
    
    

```
Get-CsApplicationEndpoint -ApplicationId tapp2 | Select-Object Identity, SipAddress, DisplayName, OwnerUrn
```


## Detailed Description

This cmdlet retrieves one or more application contacts from Active Directory Domain Services. These objects are stored in Active Directory in the Application Contacts container of the RTC service.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _ApplicationId_ <br/> |Optional  <br/> |System.String  <br/> |The application ID of the application endpoint you want to retrieve. The application ID is the value of the endpoint's OwnerUrn property. For example, if the OwnerUrn property has a value of urn:application:Caa, the application ID is urn:application:Caa. However, you can enter only the suffix, in this case Caa, to retrieve the endpoint. For example:  `-ApplicationId Caa` <br/> |
| _Credential_ <br/> |Optional  <br/> |System.Management.Automation.PSCredential  <br/> |Alternate credentials under which the Get operation will proceed. You can retrieve a PSCredential object by calling the Windows PowerShell cmdlet **Get-Credential**. <br/> |
| _DomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Allows you to specify a domain controller. If no domain controller is specified, the first available will be used.  <br/> |
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to limit the returned data by filtering on specific attributes for Skype for Business Server 2015. For example, you can limit returned data to contacts whose display names or SIP addresses match a certain wildcard pattern.  <br/> The Filter parameter uses the same Windows PowerShell filtering syntax that is used by the **Where-Object** cmdlet. For example, a filter that returns only contacts that have been enabled for Enterprise Voice would look like this: {EnterpriseVoiceEnabled -eq $True}, with EnterpriseVoiceEnabled representing the Active Directory attribute, -eq representing the comparison operator (equal to), and $True (a built-in Windows PowerShell variable) representing the filter value. <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.AD.UserIdParameter  <br/> |The Identity, SIP address, or display name of the application endpoint to retrieve. The Identity consists of the distinguished name of the endpoint. This will typically contain a globally unique identifier (GUID) as part of the CN, for example: CN={8811fefe-e0bb-4fab-ae39-7aaeddd423dc},CN=Application Contacts,CN=RTC Service,CN=Services,CN=Configuration,DC=Vdomain,DC=com.  <br/> |
| _OU_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.AD.OUIdParameter  <br/> |The organizational unit (OU) in which the endpoint resides.  <br/> |
| _PoolFqdn_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |The fully qualified domain name (FQDN) of the pool on which the application endpoint resides.  <br/> |
| _ResultSize_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.ADConnect.Core.Unlimited  <br/> |The maximum number of endpoint records to retrieve.  <br/> |
   

## Input Types

String. Accepts a pipelined string value representing the Identity of the application endpoint.
  
    
    

## Return Types

Retrieves an object of type Microsoft.Rtc.Management.ADConnect.Schema.OCSADApplicationContact.
  
    
    

## See also


#### 


  
    
    
 [Move-CsApplicationEndpoint](move-csapplicationendpoint.md)
