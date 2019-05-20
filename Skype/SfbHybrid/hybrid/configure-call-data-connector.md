---
title: "Configure Call Data Connector"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
description: "Instructions for configuring Call Data Connector, which allows telemetry from Skype for Business on-premises to be viewed using Skype for Business Online tools."
---

# Configure Call Data Connector

This article describes how to configure Call Data Connector--a single toolset that enables viewing Skype for Business Server Call Quality Data using Skype for Business Online Call Quality Dashboard (CQD) and Call Analytics (CA) tools. 

> [!NOTE]
> At public preview release, only Call Analytics dashboard is available.

For more information about Call Data Connector benefits and pre-requisites, such as role requirements and setting up hybrid connectivity, see [Plan Call Data Connector](plan-call-data-connector.md).

## Enable Monitoring
 
You must configure Call Data Recording (CDR) and Quality of Experience (QoE) data collection in your front end pool Monitoring,with local LCSCdr and QoEMetrics databases; otherwise, the Call Analytics and Call Quality Dashboards won’t get data to work with. Before you Configure Call Data Connector, follow the steps provided in [Deploy monitoring in Skype for Business Server](../../SfbServer/deploy/deploy-monitoring/deploy-monitoring.md) to configure both CDR and QoE as well as basic Monitoring.

> [!IMPORTANT]
> Call Data Connector will not function if Monitoring is not enabled on the front end pool.

## Enable Call Data Connector

To configure and enable Call Data Connector, you will use the following cmdlets:

| Cmdlet| Description|
| :-----------------|---------------:|
| New-CsCloudCallDataConnection | An online cmdlet that establishes an online data collector.|
| Get-CsCloudCallDataConnection | An online cmdlet that retrieves an existing online data collector.|  
| Get-CsCloudCallDataConnector | An on-premises cmdlet that retrieves the connection information created by the New-CsCloudCallDataConnection cmdlet. |
| Set-CsCloudCallDataConnector | An on-premises cmdlet that saves an on-premises copy of the connection information created by the New-CsCloudCallDataConnection cmdlet. |  
| Set-CsCloudCallDataConnectorConfiguration | An on-premises cmdlet that allows you to enable or disable the connector and customize the scope level.|

### Configure your environment 

To configure your environment to enable an online data collector, you must first log in to Skype for Business Online PowerShell as an administrator. For more information, see [Manage Skype for Business Online with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell).

There are two methods for logging in to Skype for Business Online PowerShell:

- From the Skype for Business Server 2019 management shell (recommended method)
- From another PowerShell session

#### Log in to Skype for Business Online PowerShell from the Skype for Business Server management shell (recommended method)

1. If enabling the connector for the first time, run the following command:

   ```
   New-CsCloudCallDataConnection | Set-CsCloudCallDataConnector -TenantId <tenant_id>
   ```

2. If you get an error that the connection already exists, this means that the call data connection already exists for your tenant. In this case, run the command: 

   ```
   Get-CsCloudCallDataConnection | Set-CsCloudCallDataConnector -TenantId <tenant_id>
   ```


#### Log in to Skype for Business Online PowerShell from another PowerShell session (optional method)

1.  If enabling the connector for the first time, run the following command: 

    ``` 
    New-CsCloudCallDataConnection 
    ```

2.  If you get an error that the connection already exists, this means that the call data connection already exists for your tenant. In this case, run the command: 

    ```
    Get-CsCloudCallDataConnection  
    ```

The output of the above commands contains a token value, which you will need when configuring your on-premises environment as follows:

From within the Skype for Business Server management shell, specify the following command:

```
Set-CsCloudCallDataConnector -Identity Global -TenantId <tenant_id> -Token <token-copied-from-online>
```

### Configure the scope

You can enable Call Data Connector for a particular site or for your entire Skype for Business Server deployment by using the Set-CsCloudCallDataConnectorConfiguration cmdlet from within the Skype for Business Server management shell. For example, the following command enables Call Data Connector at the global scope:

```
Set-CsCloudCallDataConnectorConfiguration -Identity "global" -EnableCallDataConnector $True
```

In addition to the global settings, Call Data Connector configuration settings can be assigned to the site scope. This provides additional management flexibility when it comes to monitoring. For example, an administrator can enable Call Data Connector forwarding for the Redmond site but disable Call Data Connector forwarding for the Dublin site, as shown in the following example:

```
Set-CsCloudCallDataConnectorConfiguration -Identity "site:Redmond" -EnableCallDataConnector $True
```

```
Set-CsCloudCallDataConnectorConfiguration -Identity "site:Dublin" -EnableCallDataConnector $False
```

Settings configured at the site scope take precedence over settings configured at the global scope. For example, suppose Call Data Connector forwarding is enabled at the global scope, but disabled at the site scope (for the Redmond site). That means that call detail recording and QoE information will not be forwarded for users in the Redmond site. However, users in other sites (that is, users managed by the global settings instead of the Redmond site settings) will have their call detail recording and QoE information forwarded.

Values for the most commonly used settings used by Call Data Connector are shown in the following table:  

|Property|Description|Default value|
|:-----|:-----|:-----|
|EnableCallDataConnector  <br/> |Indicates whether Call Data Connector is enabled. If True, monitoring records will be forwarded to online monitoring.  <br/> |$False  <br/> |
| Identity | Determines the scope level for the command: global or site.   | global  |

## Disable Call Data Connector

Disabling Call Data Connector does not disassociate the monitoring store from the Front End pool, nor does it uninstall or otherwise affect the backend monitoring database. When you disable Call Data Connector, you stop Skype for Business Server from uploading call data to the cloud. 

You disable Call Data Connector by using the Set-CsCloudCallDataConnectorConfiguration cmdlet from within the Skype for Business Server management shell. For example, the following command disables Call Data Connector at the global scope by setting the EnableCallDataConnector property to $False:

```
Set-CsCloudCallDataConnectorConfiguration -Identity "global" -EnableCallDataConnector $False
```

If you want to resume uploading call data to the cloud, set the EnableCallDataConnector property back to $True, as shown in the following example:

```
Set-CsCloudCallDataConnectorConfiguration -Identity "global" -EnableCallDataConnector $True
```

## View on-premises data through the online dashboard

 After Call Data Connector is enabled, you can view your on-premises call data on the Call Analytics dashboard as described in  [Use Call Analytics to troubleshoot poor quality](https://docs.microsoft.com/skypeforbusiness/using-call-quality-in-your-organization/use-call-analytics-to-troubleshoot-poor-call-quality).


## For more information

For more information on the cmdlets, you can use the Get-Help command from the Skype for Business Server Management Shell. For example:

Get-Help Get-CsCloudCallDataConnector | more

Get-Help Set-CsCloudCallDataConnector | more

Get-Help Set-CsCloudCallDataConnectorConfiguration | more
