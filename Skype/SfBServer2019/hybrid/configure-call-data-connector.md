---
title: "Configure Call Data Connector"
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 1/31/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
description: "Instructions for configuring Call Data Connector, which allows telemetry from Skype for Business on-premises to be viewed using Skype for Business Online tools."
---

# Configure Call Data Connector

[!INCLUDE [disclaimer](../disclaimer.md)]

This article describes how to configure Call Data Connector--a single toolset that enables viewing Skype for Business Server Call Quality Data using Skype for Business Online Call Quality Dashboard (CQD) and Call Analytics (CA) tools. You can configure Call Data Connector <!--using a wizard built into the Skype for Business Server Control Panel or--> by using Skype for Business Server Management Shell commands.  

> [!NOTE]
> At public preview release, only Call Analytics dashboard will be available.

For more information about Call Data Connector benefits and pre-requisites, such as role requirements and setting up hybrid connectivity, see  [Plan Call Data Connector](plan-call-data-connector.md).

## Enable Monitoring 
You must configure the data generated from enabling Call Data Recording (CDR) and Quality of Experience (QoE), otherwise the Call Analytics and Call Quality Dashboards won’t get information to display. Before you Configure Call Data Connector, follow the steps provided in [Deploy monitoring in Skype for Business Server](../../SfbServer/deploy/deploy-monitoring/deploy-monitoring.md) to configure both CDR and QoE.
<!--The enable monitoring section might be better placed in the planning topic. or it might belong in both topics. CR:  I think we should leave it here.  It is a configuratino task so I think it belongs here.-->

## Enable Call Data Connector
<!--Once all the requirements are set up, you can run the Hybrid Setup Wizard in the Skype for Business Control Panel. If all the requirements are met, at the end of the wizard you  see a checkbox option to turn on Call Data Connector. Select the box labeled **Yes, Turn on**. 

Once Call Data Connector is enabled, you can set or confirm specific Call Data Connector settings for scope the same way you can set CDR and QoE settings, which have their own tabs in the Control Panel.

To do this from within the Skype for Business Server Control Panel, complete the following procedure:
  
1. Click **Monitoring and Archiving**.
    
2. On the **Call Detail Recording** tab, check the **Call Data Connector** box for each site you wish to monitor online, or uncheck sites as desired, and then click **Commit**.  -->
To enable Call Data Connector, you will use the following cmdlets:

| Cmdlet| Description|
| :-----------------|---------------:|
| New-CsCloudCallDataConnection | An online cmdlet that establishes an online data collector.|
| Get-CsCloudCallDataConnection | An online cmdlet that retrieves an existing online data collector.|  
| Get-CsCloudCallDataConnector | An on-premises cmdlet that retrieves the connection information created by the New-CsCloudCallDataConnection cmdlet. |
| Set-CsCloudCallDataConnector | An on-premises cmdlet that saves an on-premises copy of the connection information created by the New-CsCloudCallDataConnection cmdlet. |  
| Set-CsCloudCallDataConnectorConfiguration | An on-premises cmdlet that enables you to enable or disable the connector and to customize the scope level.|

###Configure your environment 

To configure your environment to enable an online data collector, you must first log in to Skype for Business Online PowerShell as an administrator. For more information, see [Manage Skype for Business Online with Office 365 PowerShell](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell).

There are two methods for logging in to Skype for Business Online PowerShell:

- From within the Skype for Business Server 2019 management shell.   (Recommended)
- From within another PowerShell session.   

####Log in to Skype for Business Online PowerShell from within the Skype for Business Server management shell (Recommended method)

1. If enabling the connector for the first time, run the command:

   ```
   New-CsCloudCallDataConnection | Set-CsCloudCallDataConnector -TenantId <tenant_id>
   ```

2. If you get an error that the connection already exists, this means that the call data connection already exists for your tenant. In this case, run the command: 

   ```Get-CsCloudCallDataConnection | Set-CsCloudCallDataConnector -TenantId <tenant_id>```


####Log in to Skype for Business Online PowerShell from another PowerShell session:

1.	If enabling the connector for the first time, run the command: 

    ``` 
    New-CsCloudCallDataConnection 
    ```

2.	If you get an error that the connection already exists, this means that the call data connection already exists for your tenant. In this case, run the command: 

    ```
    Get-CsCloudCallDataConnection  
    ```

3. The output of the above commands contains a token value, which you will need when configuring your on-premises environment as follows:

```
Set-CsCloudCallDataConnector -Identity Global -TenantId <tenant_id> -Token <token-copied-from-online>
```

###Configure the scope

You can enable Call Data Connector for a particular site or for your entire Skype for Business Server deployment by using the Set-CsCloudCallDataConnectorConfiguration cmdlet.  For example, the following command enables Call Data Connector at the global scope:

```
Set-CsCloudCallDataConnectorConfiguration -Identity "global" -EnableCallDataConnector $True
```

In addition to the global settings, Call Data Connector configuration settings can be assigned to the site scope. This provides additional management flexibility when it comes to monitoring; for example, an administrator can enable Call Data Connector forwarding for the Redmond site but disable Call Data Connector forwarding for the Dublin site, as shown in the following example:
  
```
Set-CsCloudCallDataConnectorConfiguration -Identity "site:Redmond" -EnableCallDataConnector $True
```

```
Set-CsCloudCallDataConnectorConfiguration -Identity "site:Dublin" -EnableCallDataConnector $False
```

Settings configured at the site scope take precedence over settings configured at the global scope. For example, suppose Call Data Connector forwarding is enabled at the global scope, but disabled at the site scope (for the Redmond site). That means that call detail recording and QoE information will not be forwarded for users in the Redmond site. However, users in other sites (that is, users managed by the global settings instead of the Redmond site settings) will have their call detail recording and QoE information forwarded.

Values for the most commonly-used setting used by Call Data Connector are shown in the following table:  
|Property|Description|Default Value|
|:-----|:-----|:-----|
|EnableCallDataConnector  <br/> |Indicates whether or not Call Data Connector is enabled. If True, monitoring records will be forwarded to online monitoring.  <br/> |$True  <br/> |
| Identity | Determines the scope level for the command: global or site.   | $True  |

## Disable Call Data Connector

Disabling Call Data Connector does not disassociate the monitoring store from the Front End pool, nor does it uninstall or otherwise affect the backend monitoring database. When you disable Call Data Connector, you stop Skype for Business Server from uploading the call data to the cloud. 

The following command disables Call Data Connector at the global scope by setting the EnableCallDataConnector property to $False:
  
```
Set-CsCloudCallDataConnectorConfiguration -Identity "global" -EnableCallDataConnector $False
```

If you want to resume uploading call data to the cloud, set the EnableCallDataConnector property back to $True, as shown in the following example:

```
Set-CsCloudCallDataConnectorConfiguration -Identity "global" -EnableCallDataConnector $True
```

## View on-premises data through the online dashboard

 After Call Data Connector is enabled, you can view your on-premises call data on the Call Analytics dashboard as described in  [Use Call Analytics to troubleshoot poor Skype for Business call quality](https://docs.microsoft.com/en-us/skypeforbusiness/using-call-quality-in-your-organization/use-call-analytics-to-troubleshoot-poor-call-quality).


## For more information

For more information on the cmdlets, you can specify the Get-Help command from within the Skype for Business Server Management Shell.  For example:
  
```
Get-Help New-CsCloudCallDataConnection | more
Get-Help Set-CsCloudCallDataConnectorConfiguration | more
Get-Help Set-CsCloudCallDataConnector | more 
```