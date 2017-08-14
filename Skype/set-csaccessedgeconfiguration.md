---
title: Set-CsAccessEdgeConfiguration
ms.prod: SKYPEFORBUSINESS
ms.assetid: f3108b59-1ab2-4288-a470-57d741e7e569
---


# Set-CsAccessEdgeConfiguration
[]
Modifies the property values of an existing collection of Access Edge configuration settings for computers running the Access Edge service. The Access Edge service running on these computers (also known as Edge servers) provides a way for users outside your internal network to communicate with users inside that internal network. This cmdlet was introduced in Lync Server 2010.
  
    
    


```

Set-CsAccessEdgeConfiguration [-AllowAnonymousUsers <$true | $false>] [-AllowFederatedUsers <$true | $false>] [-AllowOutsideUsers <$true | $false>] [-CertificatesDeletedPercentage <UInt32>] [-DiscoveredPartnerReportPeriodMinutes <UInt32>] [-DiscoveredPartnerStandardRate <UInt32>] [-DnsSrvCacheRecordCount <UInt32>] [-EnableArchivingDisclaimer <$true | $false>] [-EnableDiscoveredPartnerContactsLimit <$true | $false>] [-EnableUserReplicator <$true | $false>] [-Identity <XdsIdentity>] [-KeepCrlsUpToDateForPeers <$true | $false>] [-MarkSourceVerifiableOnOutgoingMessages <$true | $false>] [-MaxAcceptedCertificatesStored <UInt32>] [-MaxContactsPerDiscoveredPartner <UInt32>] [-MaxRejectedCertificatesStored <UInt32>] [-OutgoingTlsCountForFederatedPartners <UInt32>] [-SkypeSearchUrl <String>] <COMMON PARAMETERS>

```


## Examples


  
    
    

### EXAMPLE 1

In Example 1, two properties of the Access Edge configuration settings are modified: the AllowAnonymousUsers property is set to True and the VerificationLevel property is set to UseSourceVerification.
  
    
    

```

Set-CsAccessEdgeConfiguration -AllowAnonymousUsers $True -VerificationLevel "UseSourceVerification"
```


### EXAMPLE 2

The command shown in Example 2 changes the routing method for the Edge server to default routing. In order to do this the command must include both the UseDefaultRouting parameter and the DefaultRouteFqdn parameter, along with a parameter value that specifies the fully qualified domain name of the Edge server.
  
    
    

```
Set-CsAccessEdgeConfiguration -UseDefaultRouting -DefaultRouteFqdn "atl-edge-001.litwareinc.com"
```


### EXAMPLE 3

Example 3 changes the routing method for the Edge server to DNS server routing. This requires the use of two parameters: UseDnsSrvRouting (with no parameter value) and EnablePartnerDiscovery (with the parameter value $True).
  
    
    

```
Set-CsAccessEdgeConfiguration -UseDnsSrvRouting -EnablePartnerDiscovery $True
```


## Detailed Description

Edge servers (also known as access proxy servers) provide a way for you to extend the capabilities of Skype for Business Server 2015 to people who are not logged on to your internal network. For example, if you have remote users, authenticated users who log on to Skype for Business Server 2015 over the Internet rather than through the internal network, you will need to set up an Edge server in order to provide access to these users. Likewise, Edge Servers are required if you want to establish federation with another organization, or if you want to give your users the right to communicate with people who have accounts with a public instant messaging service such as Yahoo!, AOL, or MSN. Access Edge servers are located on the perimeter network, and are used to make and validate SIP connections between users inside and users outside your internal network.
  
    
    
In Skype for Business Server 2015, the Access Edge servers are managed using a single, global collection of configuration settings; the **Set-CsAccessEdgeConfiguration** cmdlet enables you to modify these global settings. Note that the properties that can be modified depend on the routing type you choose for your Edge Servers. For example, if you choose to use Domain Name System (DNS) service routing, you will see and be able to change the property values BeClearinghouse and EnablePartnerDiscovery. If you use default routing, those two property values will not be available. Instead, you will see and be able to change the property values VerificationLevel and IsPublicProvider.
  
    
    

## Parameters



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _AllowAnonymousUsers_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether or not anonymous users (that is, unauthenticated users) are allowed to cross the firewall and join meetings and conferences. The default value is False.  <br/> |
| _AllowFederatedUsers_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether internal users are allowed to communicate with users from federated domains. This property also determines whether internal users can communicate with users in a split domain scenario. (In a split domain, some of your users have accounts hosted on-premises, while others have accounts hosted off-premises.) The default value is False.  <br/> |
| _AllowOutsideUsers_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether users can access Skype for Business Server 2015 across the Internet. This includes both anonymous users and remote users who are trying to log on to the system. The default value is True.  <br/> |
| _BeClearingHouse_ <br/> |Optional  <br/> |System.Boolean  <br/> |Indicates whether your Edge servers are directly connected to other organizations. The default value is False. This parameter should not be changed unless you are instructed to do so by Microsoft support personnel.  <br/> |
| _CertificatesDeletedPercentage_ <br/> |Optional  <br/> |System.UInt32  <br/> |The default value is 20.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _DefaultRouteFqdn_ <br/> |Optional  <br/> |System.String  <br/> |Fully qualified domain name (FQDN) of the server used for federation requests. This parameter is required if you use default routing.  <br/> Note that you must delete all your hosting providers and all your public providers before you can assign a new default route.  <br/> |
| _DiscoveredPartnerReportPeriodMinutes_ <br/> |Optional  <br/> |System.UInt32  <br/> |The default value is 60.  <br/> |
| _DiscoveredPartnerStandardRate_ <br/> |Optional  <br/> |System.UInt32  <br/> |The default value is 20.  <br/> |
| _DiscoveredPartnerVerificationLevel_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.Edge.VerificationLevelType  <br/> |Sets the verification level for messages sent to and from the discovered partner. Allowed values are:  <br/> * AlwaysVerifiable  <br/> * AlwaysUnverifiable  <br/> * UseSourceVerification  <br/> |
| _DnsSrvCacheRecordCount_ <br/> |Optional  <br/> |System.UInt32  <br/> |Maximum number of DNS SRV records that can be maintained in the cache. SRV records are used to specify service locations and port numbers.  <br/> |
| _EnableArchivingDisclaimer_ <br/> |Optional  <br/> |System.Boolean  <br/> |If set to True, Edge Servers send an archiving notification header to federated and clearinghouse partners. This notification (which informs people that instant messaging (IM) conversations might be archived) can be displayed in the conversation window of a federated or clearinghouse user. The default value is False.  <br/> |
| _EnableDiscoveredPartnerContactsLimit_ <br/> |Optional  <br/> |System.Boolean  <br/> |When set to True (the default value), enables user enumeration protection for Discovered Partner federated peers.  <br/> |
| _EnablePartnerDiscovery_ <br/> |Optional  <br/> |System.Boolean  <br/> |If True, Skype for Business Server 2015 will use DNS records to try and discover partner domains not listed in the AllowedDomains list. If False, Skype for Business Server 2015 will only federate with domains found on the AllowedDomains list. This parameter is required if you use DNS service routing. The default value is False.  <br/> |
| _EnableUserReplicator_ <br/> |Optional  <br/> |System.Boolean  <br/> |The default value is False ($False).  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier of the Access Edge configuration settings to be returned. Because you can only have a single, global instance of these settings, you do not have to include the Identity when calling the **Set-CsAccessEdgeConfiguration** cmdlet. However, if you prefer, you can use the following syntax to modify the global settings: `-Identity global`.  <br/> |
| _Instance_ <br/> |Optional  <br/> |DisplayAccessEdgeSettingsDnsSrvRouting object or DisplayAccessEdgeSettingsDefaultRoute object  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _IsPublicProvider_ <br/> |Optional  <br/> |System.Boolean  <br/> |Must be set to True if the default route requires a public instant messaging license.  <br/> |
| _KeepCrlsUpToDateForPeers_ <br/> |Optional  <br/> |System.Boolean  <br/> |Determines whether or not Edge servers periodically check the certificate revocation lists (CRLs) for federated domain certificates. The default value is True.  <br/> |
| _MarkSourceVerifiableOnOutgoingMessages_ <br/> |Optional  <br/> |System.Boolean  <br/> |If True, outgoing messages are marked as verifiable; this enables federated domains to determine the verification level for each message. If False, outgoing messages are all marked as unverifiable. The default value is True.  <br/> |
| _MaxAcceptedCertificatesStored_ <br/> |Optional  <br/> |System.UInt32  <br/> |Maximum number of allowed certificates cached by the Edge Server. The default value is 1000.  <br/> |
| _MaxContactsPerDiscoveredPartner_ <br/> |Optional  <br/> |System.UInt32  <br/> |Maximum number of contacts allowed per discovered partner. The default value is 1000.  <br/> |
| _MaxRejectedCertificatesStored_ <br/> |Optional  <br/> |System.UInt32  <br/> |Maximum number of rejected certificates cached by the Edge Server. The default value is 500.  <br/> |
| _OutgoingTlsCountForFederatedPartners_ <br/> |Optional  <br/> |System.UInt32  <br/> |Specifies the maximum number of Transport Layer Security (TLS) connections that can be used for each federated partner. The minimum number of TLS connections is 1, and the maximum number is 4. By default, OutgoingTlsCountForFederatedPartners is set to 4. This parameter should not be changed unless you are instructed to do so by Microsoft support personnel.  <br/> |
| _SkypeSearchUrl_ <br/> |Optional  <br/> |System.String  <br/> |URL for the Skype Graph Search service. This service enables Skype for Business to search for Skype contacts.  <br/> |
| _UseDefaultRouting_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Indicates that administrators must specify the fully qualified domain name of the server used to send and receive federation requests. If you include the UseDefaultRouting parameter then you must also include the DefaultRouteFqdn parameter.  <br/> |
| _UseDnsSrvRouting_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Indicates that Edge servers should rely on DNS SRV records when sending and receiving federation requests. This is the default routing method.  <br/> |
| _VerificationLevel_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.Edge.VerificationLevelType  <br/> |If you are using default routing, the VerificationLevel property is used to monitor and assess the verification level of incoming messages. Valid values are:  <br/> AlwaysVerifiable: All requests received on the default route are marked as verified. If a verification header is not present it will automatically be added to the message.  <br/> AlwaysUnverifiable: Messages are passed only if the addressee (the user the message is intended for) has configured an Allow ACE (access control entry) for the person who sent the message.  <br/> UseSourceVerification: Message verification is based on the verification level included with the message. If no verification header is present then the message will be marked as unverified.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _EnablePartnerMonitoringCosmosOutput_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types

None. The **Set-CsAccessEdgeConfiguration** cmdlet does not accept pipelined input.
  
    
    

## Return Types

The **Set-CsAccessEdgeConfiguration** cmdlet does not return any objects or values.
  
    
    

## See also


#### 


  
    
    
 [Get-CsAccessEdgeConfiguration](get-csaccessedgeconfiguration.md)
