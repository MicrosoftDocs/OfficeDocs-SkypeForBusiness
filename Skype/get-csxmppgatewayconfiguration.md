---
title: Get-CsXmppGatewayConfiguration
ms.prod: SKYPEFORBUSINESS
ms.assetid: 4c9ee876-de89-420c-bda9-9901cef47799
---


# Get-CsXmppGatewayConfiguration
[]
Returns information about the XMPP gateway configuration settings in use in the organization. The extensible Messaging and Presence Protocol (XMPP) is an open-standard communications protocol for exchanging messages using XML. XMPP gateways enable Skype for Business Server 2015 users to exchange instant message and presence information with users belonging to IM and presence providers that employ XMPP. This cmdlet was introduced in Lync Server 2013.
  
    
    


```

Get-CsXmppGatewayConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```


## Examples
<a name="Examples"> </a>


### Example 1

In Example 1, information is returned for the XMPP gateway settings currently in use in the organization. Because Skype for Business Server 2015 only allows for a single, global collection of gateway settings you do not need to include the Identity parameter in order to get back information for the global settings.
  
    
    

```

Get-CsXmppGatewayConfiguration
```


## Detailed Description
<a name="DetailedDescription"> </a>

The Extensible Messaging and Presence Protocol (XMPP) is a standard communications protocol (based on XML) used for sending messages across the Internet. XMPP was originally named Jabber, and is supported by a number of Internet messaging and communication applications, including Google Talk and Facebook Chat.
  
    
    
The XMPP gateway that enables Skype for Business to communicate with users on an XMPP network was originally released as an add-on to Microsoft Lync Server 2010; in Skype for Business Server 2015, this functionality is built into the software. This means that your users can communicate with XMPP users provided that you:
  
    
    


  
    
    
> Configure the XMPP gateway settings.
    
  

  
    
    
> Configure the other XMPP network (for example, Google Talk) as an allowed XMPP partner.
    
  
Note that Skype for Business Server 2015 provides only a single, global set of XMPP configuration settings: you cannot selectively enable or disable XMPP for a given site or a given Registrar pool. In fact you cannot enable or disable XMPP at all: XMPP is always enabled. If you do not want users communicating with XMPP networks then you should remove all the allowed XMPP partners. Users can only communicate with an XMPP network if that network has been configured as an allowed partner.
  
    
    
 **Skype for Business Server Control Panel:** The functions carried out by the **Get-CsXmppGatewayConfiguration** cmdlet are not available in the Skype for Business Server Control Panel.
  
    
    

## Parameters
<a name="DetailedDescription"> </a>



|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Filter_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to use wildcard values when referencing a collection of XMPP gateway configuration settings. Because you can only have a single, global instance of these settings there is no reason to use the Filter parameter. However, if you prefer you can use the following syntax to reference the global settings:  <br/>  `-Filter "g*"` <br/> That syntax brings back all the XMPP gateway configuration settings that have an Identity that begins with the letter "g".  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the XMPP gateway configuration settings. Because you can only have a single, global instance of these settings, you do not need to specify an Identity when calling the **Get-CsXmppGatewayConfiguration** cmdlet. If you prefer, however, you can use the following syntax to reference the global settings: <br/>  `-Identity global` <br/> |
| _LocalStore_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Retrieves the XMPP gateway data from the local replica of the Central Management store rather than from the Central Management store itself.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   

## Input Types
<a name="InputTypes"> </a>

None. The **Get-CsXmppGatewayConfiguration** cmdlet does not accept pipelined input.
  
    
    

## Return Types
<a name="ReturnTypes"> </a>

The **Get-CsXmppGatewayConfiguration** cmdlet returns instances of the Microsoft.Rtc.Management.WritableConfig.Settings.XmppFederation.XmppGatewaySettings object.
  
    
    

## See also
<a name="ReturnTypes"> </a>


#### 


  
    
    
 [Set-CsXmppGatewayConfiguration](set-csxmppgatewayconfiguration.md)
