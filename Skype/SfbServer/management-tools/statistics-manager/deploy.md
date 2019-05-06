---
title: "Deploy Statistics Manager for Skype for Business Server"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: 37b2bb9c-c5d4-4fb0-a976-670b7594b82f
description: "Summary: Read this topic to learn how to deploy Statistics Manager for Skype for Business Server."
---

# Deploy Statistics Manager for Skype for Business Server
 
**Summary:** Read this topic to learn how to deploy Statistics Manager for Skype for Business Server.
  
 Statistics Manager for Skype for Business Server is a powerful tool that allows you to view Skype for Business Server health and performance data in real time. You can poll performance data across hundreds of servers every few seconds, and view the results instantly on the Statistics Manager Website.
  
Before you attempt to install Statistics Manager, be sure you are familiar with the software, networking, and hardware requirements. For more information, see [Plan for Statistics Manager for Skype for Business Server](plan.md).
  
> [!NOTE]
> If you are upgrading from a previous version of Statistics Manager, see [Upgrade Statistics Manager for Skype for Business Server](upgrade.md). 
  
> [!NOTE]
> The Statistics Manager Website has been tested and works correctly on Internet Explorer 11+, Edge 20.10240+ , and Chrome 46+ (current evergreen version). 
  
You can find the Statistics Manager downloadable at [https://aka.ms/StatsManDownload](https://aka.ms/StatsManDownload). 
  
This topic contains the following sections:
  
- [Deploy Statistics Manager](deploy.md#BKMK_Deploy)
    
- [Troubleshoot your deployment](deploy.md#BKMK_Troubleshoot)
    
- [Create a self-signed certificate](deploy.md#BKMK_SelfCert)
    
## Deploy Statistics Manager
<a name="BKMK_Deploy"> </a>

To deploy Statistics Manager, follow these steps:
  
1. Prepare the Listener host machine by installing the Redis in-memory caching system, and by ensuring that you have installed the appropriate certificates.
    
2. Install the Listener service on the host machine. 
    
3. Install the Website on the host machine.
    
4. Install an Agent on each Skype for Business Server machine you wish to monitor.
    
5. Import the topology for the servers you are monitoring.
    
> [!NOTE]
> Redis, the Listener service, and the Website must all be installed on the same host machine. Be sure the host machine does not have Skype for Business Server installed. 
  
### Prepare the Listener host machine

To prepare the host machine, you will need to install the Redis in-memory caching system, and ensure that a valid certificate is on the machine. Microsoft recommends that you install the latest stable build of Redis 3.0. Statistics Manager version 2.0 was tested with Redis 3.2.100. 
  
1. Download Redis from the following site: [https://github.com/MSOpenTech/redis](https://github.com/MSOpenTech/redis). 
    
    Unsigned installers can be downloaded from [https://github.com/MSOpenTech/redis/releases](https://github.com/MSOpenTech/redis/releases)
    
    If required, signed binaries are available through popular package managers: [Nuget](https://www.nuget.org/packages/Redis-64/) and [Choclatey](https://chocolatey.org/packages/redis-64).
    
   - Run the provided msi and follow the prompts.
    
   - Do not check the box to add a firewall rule.
    
2. The Listener service requires a certificate. Microsoft strongly recommends that you have a certificate signed by a trusted certificate authority. 
    
    If you want to use a self-signed certificate--for testing purposes in a lab, for example--see [Create a self-signed certificate](deploy.md#BKMK_SelfCert).
    
    Note that the Agent uses certificate thumbprint verification (instead of chain verification). It will not do full certificate validation because it is possible to use self-signed certificates.
    
### Install the Listener service

Install the Listener service on the host machine by running the StatsManPerfAgentListener.msi and specifying the following:
  
1. Review the License Agreement, and if you agree, select **I accept the terms in the license agreement**, and then click **Next**. 
    
2. On the next page, specify the following information:
    
   - **Service Password:** This is the password the remote Agents will use to authenticate to the Listener service.
    
   - **Service Port:** This is the HTTPS port number that the Listener will use to communicate with the Agents. During installation, this port will be allowed through the local firewall, a URL ACL will be created, and an SSL cert will be bound to this port. The default is 8443.
    
   - **Certificate Thumbprint:** This is the certificate thumbprint the Listener will use to encrypt the HTTPS protocol. Network Service must have read access to the private key.
    
     Click the **Select...** button to choose the thumbprint.
    
     You can find the Certificate thumbprint by using Certificate Manager or by using the following PowerShell command:
    
   ```
   Get-ChildItem -path cert:\LocalMachine\My
   ```

   - **Install Dir:** This is the directory on which the binaries will be installed. You may change it from the default by using the **Browse...** button.
    
   - **AppData Dir:** This is the directory where the Logs folder and other data will be stored. You may change it from the default. It will not be deleted on uninstall.
    
3. Click **Install**.
    
To validate the installation, perform the following steps:
  
1. Open a browser and navigate to https://localhost:\<service-port\>/healthcheck/
    
    By default, the service port is 8443 (unless you specified another port).
    
2. To ensure the Listener has installed properly, look for the following:
    
   - If the healthcheck page shows up, the Listener installation was successful.
    
   - If the KnownServerCount is 1 or higher, then the connection to Redis is established.
    
   - After waiting a few minutes, and after at least one Agent has been installed, check to see that the ValuesWritten counter is incrementing.
    
### Install the Website

Install the Website on the host machine by running the StatsManWebSite.msi (included with [Skype for Business Server, Real-Time Statistics Manager (64-bit)](https://www.microsoft.com/en-in/download/details.aspx?id=57518)) and specifying the following:
  
1. Review the License Agreement, and if you agree, select **I accept the terms in the license agreement**, and then click **Next**. 
    
2. On the next page, specify the following information:
    
   - **Service Port:** This is the port number the web site will listen on. You can change it later by using IIS manager binding. During installation, this port will be allowed through the local firewall.
    
   - **Install Dir:** This is the directory where the binaries will be installed. You may change it from the default by using the **Browse...** button.
    
   - **AppData Dir:** This is the directory where the Logs folder and other data will be stored. You may change it from the default. It will not be deleted on uninstall.
    
3. Click **Install**.
    
To view the Website, open a browser, and navigate to: http://localhost,webport\>/.
  
To view health information only, open a browser, and navigate to: http://localhost:\<webport\>/healthcheck/.
  
By default, the web port number is 8080. You can change the port binding of the website by using IIS manager.
  
The web installer adds a local security group, called StatsManWebSiteUsers. You can add accounts to this security group to grant access to the Website. 
  
### Install the Agents

Install an Agent on each Skype for Business Server that you wish to monitor by running the StatsManPerfAgent.msi and specifying the following:
  
1. Review the License Agreement, and if you agree, select **I accept the terms in the license agreement**, and then click **Next**. 
    
2. On the next page, specify the following information:
    
   - **Service Password:** This is the password the remote agent will use to authenticate to the Listener service.
    
   - **Service URI:** This is the URI where the Listener resides. It should use the https://name:port format.
    
     You can use a NETBIOS name or a FQDN. You can use the name that is also specified as the **Subject** or **Subject Alternative Names** of the certificate on the Listener service, but this is not a requirement.
    
   - **Service Thumbprint:** This is the thumbprint of the SSL certificate the Listener is using. The Agent will use this thumbprint to authenticate to the Listener. (It will not do full certificate validation because it is possible to use self-signed certificates.)
    
   - **Install Dir:** This is the directory on which the binaries will be installed. You may change it from the default by using the **Browse...** button.
    
   - **AppData Dir:** This is the directory where the Logs folder and the encrypted password.txt file will be stored. You may thanks change it from the default. It will not be deleted on uninstall.
    
3. Click **Install**.
    
If you are installing an Agent on numerous machines, you will probably want to do this in unattended mode. For example: 
  
```
msiexec /l install.log /i StatsManPerfAgent.msi SERVICE_THUMBPRINT=<thumbprint> SERVICE_PASSWORD=<password> SERVICE_URI=https://<hostname>:<servicePort>/[INSTALLDIR=<directory>][DIR_	STATSMANAPPDATA=<directory>]
```

### Import the topology
<a name="BKMK_ImportTopology"> </a>

After Statistics Manager is installed and running, you need to import the Skype for Business Server topology so that Statistics Manager knows the Site, Pool, and Role of each server. To import your Skype for Business Server topology, you will use the [Get-CsPool](https://docs.microsoft.com/powershell/module/skype/get-cspool?view=skype-ps) cmdlet to retrieve information about each pool in use in your organization, then import this information into Statistics Manager.
  
To import the Skype for Business Server topology, follow these steps:
  
1. On a host that has the Skype for Business Server PowerShell cmdlets:
    
    a. Run the following command: 
    
   ```
   Get-CsPool | Export-Clixml -Path mypoolinfo.xml
   ```
    b. Copy the "mypoolinfo.xml" file to the server that runs the Listener.
    
2. On the host that runs the Listener:
    
   a. Run PowerShell.
    
   b. Navigate to the directory on which the Listener is installed. The default is: 
    
   ```
   cd C:\Program Files\Skype for Business Server StatsMan Listener
   ```

3. To confirm which servers are being added and updated, run the following command:
    
   ```
  	.\Update-StatsManServerInfo.ps1 -CsPoolFile  <path to mypoolinfo.xml>
   ```

The following command enables you to view all options:
  
```
Get-Help .\Update-StatsManServerInfo.ps1 -Detailed 
```

To see your currently imported server information, run the following script: 
  
```
.\Get-StatsManServerInfo.ps1
```

If you would like to monitor servers that are not in your Skype for Business Server topology--an Exchange Server, for example--you can do a single-server import on the host that runs the Listener. To do a single-server import, follow these steps:
  
1. Navigate to the directory on which the Listener is installed. The default is: 
    
   ```
   cd C:\Program Files\Skype for Business Server StatsMan Listener
   ```

2. Run the following command:
    
   ```
  	.\Update-StatsManServerInfo.ps1 -HostName <hostname> -SiteName <name of site> -PoolName <poolName> -Roles <role1>[,<role2>,<roleN>]
   ```

## Troubleshoot your deployment
<a name="BKMK_Troubleshoot"> </a>

If an Agent fails to start, check for the following: 
  
- Is the agent registered in Statistics Manager?
    
1. Make sure you followed the instructions for importing the topology. See [Import the topology](deploy.md#BKMK_ImportTopology).
    
2. If the Agent is on a server that is not listed in the topology (for example, the nodes in a SQL AlwaysOn cluster), you will need to add the Agent manually by following the instructions in [Import the topology](deploy.md#BKMK_ImportTopology).
    
- Can the Agent contact the Listener?
    
1. Make sure the Listener service is running. 
    
    If it is not running, make sure Redis is running, and then try to restart the Listener.
    
2. Make sure the port is open to the Listener service, and that the Agent computer can communicate with the port.
    
- To ensure that Statistics Manager is collecting data, you can check the CSV file as follows. 
    
    The following command retrieves the counter storage names: 
    
  ```
  .\PerfAgentStorageManager.exe -redis=localhost -a=listcounterstoragenames -mode=verbose | findstr /i processor
  ```

    The next command retrieves the values for the specified counters: 
    
  ```
  .\PerfAgentStorageManager.exe -redis=localhost -a=getcountervalues  -counter="\\*\Processor Information\% Processor Time_Mean_Mean\_Total" -file:all-processor.csv
  ```

For information about all the events you might see in the application event log, see [Troubleshoot Statistics Manager for Skype for Business Server](troubleshoot.md).
  
## Create a self-signed certificate
<a name="BKMK_SelfCert"> </a>

Microsoft strongly recommends that you use a certificate signed by a trusted certificate authority. However, if you want to use a self-signed certificate for testing purposes, do the following: 
  
1. From a PowerShell console while logged on as Administrator, type the following:
    
   ```
   New-SelfSignedCertificate -DnsName StatsManListener -CertStoreLocation Cert:\LocalMachine\My
   ```

2. Type  `certlm.msc`. This will open the Certificate Manager for the local machine.
    
3. Navigate to **Personal**, and then open **Certificates**.
    
4. Right click on **StatsManListener-\>All Tasks-\>Manage Private Keys…**
    
5. Click **Add**.
    
6. In the **Enter the object names to select** box, type the following: Network Service
    
7. Click **OK**.
    
8. Under **Full Control**, un-check the **Allow** check box. (Only Read access is necessary.)
    
9. Click **OK**.
    
## For more information
<a name="BKMK_SelfCert"> </a>

For more information, see the following:
  
- [Plan for Statistics Manager for Skype for Business Server](plan.md)
    
- [Upgrade Statistics Manager for Skype for Business Server](upgrade.md)
    
- [Troubleshoot Statistics Manager for Skype for Business Server](troubleshoot.md)
ß
