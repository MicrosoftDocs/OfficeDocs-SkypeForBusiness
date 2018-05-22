---
title: "Configure call data connector"
ms.author: jambirk
author: jambirk
manager: serdars
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
description: "Instructions for configuring the Cloud Call Data Connector feature, which allows telemetry from Skype for Business on-premises to be viewed using Skype for Business online tools."
---

# Configure Call Data Connector

[!INCLUDE [disclaimer](../disclaimer.md)]

This article explains how to configure viewing Skype for Business server Call Quality Data using the Skype for Business Online Call Quality Dashboard(CQD) and Call Analytics(CA). This configuration can be done using a wizard built into the Skype for Business Server Control Panel or by using Skype for businesss Server Management Shell commands.  


Before configuring Call Data Connector (CDC), all the required configurations must be complete. See the planning document for information about this feature, benefits, and requirements:  [Plan Call Data Connector](plan-call-data-connector.md).

To perform these tasks, you will need to be authenticated to your Office 365 Tenant and be a Server Admin for Skype for Business Server and also a Global Administrator in Office 365.


##  Server configuration

### Enable monitoring 

Data generated from enabling Call Data Recording (CDR) and Quality of Experience (QoE) must be configured, otherwise Call Quality Dashboard doesn't get information to display.

Follow the steps provided in [Deploy monitoring in Skype for Business Server 2015](../../SfbServer/deploy/deploy-monitoring/deploy-monitoring.md) to configure both CDR and QoE.

**HAS THE UI FOR CONTROL PANEL CHANGED ENOUGH THAT WE NEED TO UPDATE THIS TOPIC?<BR> ANY CHANGES TO THE CDR AND QOE COMMANDS MENTIONED THERE?**

###  Configuring hybrid and other dependencies

Call Data Connector requires previously enabling Split-domain hybrid and  all the features described in [Requirements](plan-call-data-connector.md#requirements).


### Enable Call Data Connector
Once all the requirements are set up, you can run the Hybrid Setup Wizard in the Skype for Business Control Panel. If all the requirements are met, at the end of the wizard you  see a checkbox option to turn on Call Data Connector. Select the box labeled **Yes, Turn on**. 

Once CDC is enabled, you can set or confirm specific CDC settings for scope the same way you can set CDR and QoE settings, which have their own tabs in the Control Panel.

To do this from within the Skype for Business Server Control Panel, complete the following procedure:
  
1. Click **Monitoring and Archiving**.
    
2. On the **Call Detail Recording** tab, check the **Call Data Connector** box for each site you wish to monitor online, or uncheck sites as desired, and then click **Commit**.


If you do not turn on the connector during the  hybrid configuration wizard, or later on need to refresh the token cached on-premises, at any time  (provided you are logged in to Office 365 as the hybrid wizard requires) you can run the following series of cmdlets:
```
New-CsCloudCallDataCollector | Set-CsCloudCallDataConnection
```
This will establish an Aria tenant if it has not already been enabled, or refresh the token cache as needed. 

> [!NOTE]
>  New-CsCloudCallDataCollector is an online cmdlet that establishes an Aria collector, and Set-CsCloudCallDataConnection is on-premises.


## CQD Online

If you have not already done so, turn on CQD online as described in [Turning on and using Call Quality Dashboard for Microsoft Teams and Skype for Business Online](../../SfbOnline/using-call-quality-in-your-organization/turning-on-and-using-call-quality-dashboard.md)


**Is activation as described there the same as for pure SfBOL?** 

### Viewing onprem data through the online dashboard

<!--Since CQD OL now covers Teams too, I'm guessing:-->

 Once CQD is Acivated, you can switch between online Skype for Business, Teams, and Skype foir Business Server data views as described in  [Selecting product data to see in reports](../../SfbOnline/using-call-quality-in-your-organization/turning-on-and-using-call-quality-dashboard.md#selecting-product-data-to-see-in-reports).


## Call Data Connector options

You can enable and disable Call Data Connector(CDC) for a particular site or for your entire Skype for Business Server deployment; that can be done with the Control Panel or with the Management Shell using a command as simple as this:
  
```
Set-CsCloudCallDataConnection -Identity "global" -EnableCallDataConnector $True
```

 Values for the most commonly-used setting used by CDC are shown in the following table:
  
|Property|Description|Default Value|
|:-----|:-----|:-----|
|EnableCallDataConnector  <br/> |Indicates whether or not CDC is enabled. If True, Monitoring records will be forwarded to online monitoring.  <br/> |True  <br/> |
| Identity | Determines the scope level for the command: global or site.   | $True  |

If you need to modify these global settings you can do so by using the Set-CsCloudCallDataConnectorConfiguration cmdlet. For example, this command (run from within the Skype for Business Server Management Shell) disables CDC at the global scope; that's done by setting the EnableCallDataConnector property to False ($False):
  
```
Set-CsCloudCallDataConnection -Identity "global" -EnableCallDataConnector $False
```

Disabling CDC does not dissociate the monitoring store from the Front End pool, nor does it uninstall or otherwise affect the backend monitoring database. When you use Skype for Business Server Management Shell to disable CDC all you really do is temporarily stop Skype for Business Server from forwarding monitoring data to the online CQD dashboard. If you want to resume forwarding to the online dashboard, all you need to do is set the EnableCallDataConnector property back to True ($True):
  
```
Set-CsCloudCallDataConnection -Identity "global" -EnableCallDataConnector $True
```
In addition to the global settings, CDC configuration settings can be assigned to the site scope. This provides additional management flexibility when it comes to monitoring; for example, an administrator can enable CDC forwarding for the Redmond site but disable CDC forwarding for the Dublin site. To create new CDC forwarding configuration settings at the site scope, use a command similar to this:
  
```
New-CsCloudCallDataCollector -Identity "site:Redmond" -EnableCallDataConnector $False
```

Keep in mind that settings configured at the site scope take precedence over settings configured at the global scope. For example, suppose CDC forwarding is enabled at the global scope, but disabled at the site scope (for the Redmond site). That means that call detail recording  and QoE information will not be forwarded for users in the Redmond site. However, users in other sites (that is, users managed by the global settings instead of the Redmond site settings) will have their call detail recording and QoE information forwarded.
  

For more information, type the following commands from within the Skype for Business Server Management Shell:
  
```
Get-Help New-CsCloudCallDataCollector | more
Get-Help Set-CsCloudCallDataConnection | more
```

**Other than using scope to say which sites do or don't get forwarded online, is the actual type of data collected and forwarded changing? <br> <br>Is it any more customizable than it was in 2015 or 2013, and if so how?**