---
title: "Configure Call Data Connector"
ms.author: jambirk
author: jambirk
manager: serdars
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
description: "Instructions for configuring Cloud Call Data Connector, which allows telemetry from Skype for Business on-premises to be viewed using Skype for Business Online tools."
---

# Configure Call Data Connector

[!INCLUDE [disclaimer](../disclaimer.md)]

This article explains how to configure Call Data Connector--a single toolset that enables viewing Skype for Business Server Call Quality Data using Skype for Business Online Call Quality Dashboard (CQD) and Call Analytics (CA) tools. You can configure Call Data Connector <!--using a wizard built into the Skype for Business Server Control Panel or--> by using Skype for Business Server Management Shell commands.  

> [!NOTE]
> At beta release, only Call Analytics data is availaby by using Call Data Connector.

For more information about Call Data Connector benefits and pre-requisites, such as role requirements and setting up hybrid connectivity, see  [Plan Call Data Connector](plan-call-data-connector.md).

## Enable Monitoring 
You must configure the data generated from enabling Call Data Recording (CDR) and Quality of Experience (QoE), otherwise the Call Analytics and Call Quality Dashboards won’t get information to display. Before you Configure Call Data Connector, follow the steps provided in [Deploy monitoring in Skype for Business Server 2015](../../SfbServer/deploy/deploy-monitoring/deploy-monitoring.md) to configure both CDR and QoE.
<!--The enable monitoring section might be better placed in the planning topic. or it might belong in both topics. CR:  I think we should leave it here.  It is a configuratino task so I think it belongs here.-->

## Enable Call Data Connector
<!--Once all the requirements are set up, you can run the Hybrid Setup Wizard in the Skype for Business Control Panel. If all the requirements are met, at the end of the wizard you  see a checkbox option to turn on Call Data Connector. Select the box labeled **Yes, Turn on**. 

Once CDC is enabled, you can set or confirm specific CDC settings for scope the same way you can set CDR and QoE settings, which have their own tabs in the Control Panel.

To do this from within the Skype for Business Server Control Panel, complete the following procedure:
  
1. Click **Monitoring and Archiving**.
    
2. On the **Call Detail Recording** tab, check the **Call Data Connector** box for each site you wish to monitor online, or uncheck sites as desired, and then click **Commit**.  -->
To enable Call Data Connector, you'll use the following cmdlets:

**IS THE FOLLOWING CORRECT?  NOTE THAT RAHUL'S FEEDBACK AND THE SPEC HAVE CONFLICTING INFO.  THE FOLLOWING IS BASED ON RAHUL'S FEEDBACK:**

**WE NEED HELP VERIFYING CMDLET NAMES AND PURPOSES.  FEEDBACK, SPECS, AND THE NAMES THEMSELVES ARE A BIT CONFUSING:  New-CsCloudCallDataConnection, New-CsCloudCallDataConnector, Set-CsCloudCallDataConnectorConfiguration

- New-CsCLoudCallDataConnection is an online cmdlet that establishes an online data collector.
- Set-CsCLoudCallDataConnector is an on-premises cmdlet that establishes the connection with the online data connector. **TRUE?**

For example:

1.	Log in to Skype for Business Online as an administrator.
2.	If enabling the connector for the first time, run the command: 

    ``` 
    New-CsCloudCallDataConnection | Set-CsCloudCallDataConnector   
    ```
3.	If you get an error that the connection already exists, this means that the cloud call data connection already exists for your tenant. In this case, run the command: 

    ```
    Get-CsCloudCallDataConnection | Set-CsCloudCallDataConnector  
    ```

<!--You can also replace the `tenant_id` part with something like  `-TenantId (Get-CsTenant).TenantID`.
**What effect will that have?**-->

You can enable Call Data Connector (CDC) for a particular site or for your entire Skype for Business Server deployment by using the Set-CsCloudCallDataConnectorConfiguration cmdlet.  For example, the following command enables CDC at the global scope:

```
Set-CsCloudCallDataConnectorConfiguration -Identity "global" -EnableCallDataConnector $True
```
In addition to the global settings, CDC configuration settings can be assigned to the site scope. This provides additional management flexibility when it comes to monitoring; for example, an administrator can enable CDC forwarding for the Redmond site but disable CDC forwarding for the Dublin site, as shown in the following example:
  
```
New-CsCloudCallDataConnectorConfiguration -Identity "site:Redmond" -EnableCallDataConnector $True
```

```
New-CsCloudCallDataConnectorConfiguration -Identity "site:Dublin" -EnableCallDataConnector $False
```

Keep in mind that settings configured at the site scope take precedence over settings configured at the global scope. For example, suppose CDC forwarding is enabled at the global scope, but disabled at the site scope (for the Redmond site). That means that call detail recording  and QoE information will not be forwarded for users in the Redmond site. However, users in other sites (that is, users managed by the global settings instead of the Redmond site settings) will have their call detail recording and QoE information forwarded.

Values for the most commonly-used setting used by CDC are shown in the following table:  
|Property|Description|Default Value|
|:-----|:-----|:-----|
|EnableCallDataConnector  <br/> |Indicates whether or not CDC is enabled. If True, monitoring records will be forwarded to online monitoring.  <br/> |$True  <br/> |
| Identity | Determines the scope level for the command: global or site.   | $True  |



**Disable Call Data Connector**

Disabling CDC does not dissociate the monitoring store from the Front End pool, nor does it uninstall or otherwise affect the backend monitoring database. When you disable CDC, you temporarily stop Skype for Business Server from forwarding the monitoring data to the online CQD dashboard. 

The following command disables CDC at the global scope by setting the EnableCallDataConnector property to False ($False):
  
```
Set-CsCloudCallDataConnectorConfiguration -Identity "global" -EnableCallDataConnector $False
```

If you want to resume forwarding to the online dashboard, set the EnableCallDataConnector property back to $True, as shown in the following example:

```
Set-CsCloudCallDataConnectorConfiguration -Identity "global" -EnableCallDataConnector $True
```

## View on-premises data through the online dashboard

 After CQD is activated, you can switch between Skype for Business Online, Teams, and Skype for Business Server data views as described in  [Selecting product data to see in reports](../../SfbOnline/using-call-quality-in-your-organization/turning-on-and-using-call-quality-dashboard.md#selecting-product-data-to-see-in-reports).


## Refresh your Call Data Connector

Provided you are logged in to Office 365, you can refresh the token cached on-premises at any time by running the following series of cmdlets:

```
New-CsCloudCallDataConnection | Set-CsCloudCallDataConnector 
```
This will establish an online data collector if it has not already been enabled, and refresh the token. **Still not clear why token refresh would be needed**

##For more information

For more information on the cmdlets, you can specify the Get-Help command from within the Skype for Business Server Management Shell.  For example:
  
```
Get-Help New-CsCloudCallDataConnector | more
Get-Help Set-CsCloudCallDataConnectorConfiguration | more
Get-Help Set-CsCloudCallDataConnector | more 
```
