---
title: Lync Server 2013 release notes
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Release notes
ms:assetid: 9f9e864c-3365-4800-803c-5289bd8fd363
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205120(v=OCS.15)
ms:contentKeyID: 48184930
ms.date: 12/09/2016
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Release notes for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2016-12-08_

Welcome to the Lync Server 2013 Release Notes. Refer to this file for information regarding known issues about Lync Server 2013.

<div>

## About this document

This document contains important information that you should know before you deploy and use Lync Server 2013. For details about Lync Server 2013, refer to the [Microsoft Lync Server 2013](microsoft-lync-server-2013.md) documentation.

This document contains the following sections:

  - Lync 2013 client

  - Lync Server

  - Installation

  - Mobility

  - Conferencing

  - Enterprise Voice

  - Presence

  - Response Group Application and Call Park Application

  - Lync Server Control Panel, Topology Builder, and Planning Tool

  - Localization

  - Copyright

</div>

<span id="LyncClient"></span>

<div>

## Lync 2013 client

<div>

## Transferring a file in an instant message fails if the file is open in another application

**Issue:**

If you attempt to transfer a file, such as a Word document, by including it in an instant message to another Lync user, the transfer will appear to succeed but may actually fail to transfer the file. An icon for the file type will be displayed in the Lync client, but the file cannot be opened by the intended receiver. No error message is displayed to inform you that the transfer was not successfull.

**Workaround:**

To work around this issue, close the open file or application that has it open before attempting to transfer the file in an instant message.

</div>

</div>

<span id="LyncServer"></span>

<div>

## Lync Server

<div>

## If Lync Server Storage Service data replication fails, administrators will need to check performance counters for stale Storage Service queue items

**Issue:**

The Lync Server Storage Service uses Windows Fabric for replication. If data is deleted on a primary Front End Server, but the deletion on a secondary Front End Server fails—for example, if there is an unexpected shutdown or error on the Front End Server—data can be left behind and "orphaned." The orphaned data can cause performance to degrade and waste drive space.

**Workaround:**

To work around this issue, if the events LYSS\_DB\_SPACE\_USED\_ERROR (Id=32058) and LYSS\_DB\_SPACE\_USED\_CRITICAL (Id=32059) are generated in the event log, administrators should check the performance counter on the Front End Server under **LS:LYSS - Storage Service API** with a name of **LYSS - Current number of Storage Service stale queue items**. If this performance counter has a high value—for example, greater than 50,000—then the administrator should run the CleanuUpStorageServiceData.exe tool in the Lync Server 2013 Resource Kit, which will delete all orphaned data from the pool. For details about the tool, see the Lync Server 2013 Resource Kit documentation.

</div>

<div>

## Whenever the IP Address configuration is changed for a server or pool, Lync Server services need to be restarted

**Issue:**

When the IP Address configuration is changed for a Lync Server 2013 deployment, such as changing from IPv4 to Dual Stack, or from Dual Stack to Ipv6, not all server components pick up the configuration change until the services are restarted.

**Workaround:**

To work around this issue, restart Lync Server services after changing the IP Address configuration for the deployment. To do so, run the following cmdlets in the Lync Server Management Shell:

   ```
    Stop-CsWindowsService -graceful
   ```

   ```
    Start-CsWindowsService
   ```

</div>

<div>

## The dial-in conferencing synthetic transaction cmdlet is no longer available in the Lync Server 2013 Management Pack

**Issue:**

The dial-in conferencing synthetic transaction cmdlet **Test-CsDialInConferencing** is no longer available in the Lync Server 2013 Management Pack.

**Workaround:**

Use of the Dial-In Conferencing Synthetic Transaction cmdlet **Test-CsDialInConferencing** is supported only internally to an enterprise.

Administrators may continue to use the cmdlet in Lync Server Management Shell for troubleshooting purposes. If required, an enterprise can also develop a private management pack to run the cmdlet internally.

</div>

<div>

## The Centralized Logging Service stops if network traffic is disrupted when log files are being copied to network share

**Issue:**

When the Centralized Logging Service is configured to use a network path (the value of the CacheFileNetworkFolder parameter of the **Get-CsClsConfiguration** cmdlet is a valid UNC path), cached log files are copied to the network share. If there is a disruption in network traffic while the files are being copied, an exception will occur that will cause the centralized logging service to stop.

The service is configured to automatically restart up to three times, so the service will recover from the first three exceptions.

**Workaround:**

There is no workaround for this issue. To identify the issue, monitor the event log for Event ID 7031 from the "Service Control Manager" that logs when the "Lync Server Centralized Logging Service Agent" service has terminated unexpectedly. If this happens more than three times, manually restart the service by using the **Start-CsWindowService** cmdlet.

</div>

<div>

## Storage Service Queue Items need to be imported manually

**Issue:**

Lync Server 2013 stores data about conferencing and instant messaging, such as archived messages and call detail recording (CDR), on a database on each Front End Server. The data is stored in the database while it is being processed before being delivered to the intended destination. To improve performance, Lync Server 2013 periodically exports the queue items from the local database that are not processed for an extended period of time, and saves them on the file store. If the file store is unavailable, the items are stored on each Front End Server. The same operation occurs to prevent data loss during pool failover.

During the export operation, the Lync Server Storage Service records every stage in the event log with event IDs of 32075 (full flush operation is started), 32076 (full flush is completed), 32082 (maintenance level flush is started), 32083 (maintenance level flush is completed), 32089 (flush occurred due to filling up of database). This data will not automatically be imported back to the system to be processed and delivered to its final destination (SQL Server or Exchange Server).

**Workaround:**

To import the data to the system, administrators will need to use the ImportStorageServiceData tool in the Lync Server Resource Kit, which will add the data back into the system to be processed and delivered to its final destination.

</div>

<div>

## Address Book Web Query searches will fail if the default value for UseNormalizationRules is changed to False

**Issue:**

If the default value for UseNormalizationRules is changed to False, Address Book Web Query searches will fail. After the default value is changed, Lync Client users will not be able to use Lync Address Book web query to search for users.

**Workaround:**

If the default value for UseNormalizationRules is set to False so that users can use phone numbers as defined in Active Directory Domain Services without Lync Server 2013 applying normalization rules, work around this issue by doing the following:

1.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

2.  Do one of the following:
    
      - If your deployment includes only Lync Server 2013 servers, run the following cmdlet at the global level to change the values for UseNormalizationRules and IgnoreGenericRules to True:
        
            Set-CsAddressBookConfiguration -identity <XdsIdentity> -UseNormalizationRules=$true -IgnoreGenericRules=$true
    
      - If your deployment includes a combination of Lync Server 2013 and Lync Server 2010 or Office Communications Server 2007 R2, run the following cmdlet and assign it to each Lync Server 2013 pool in the topology:
        
            new-csAddressBookConfiguration -identity <XdsIdentity> -UseNormalizationRules=$true -IgnoreGenericRules=$true

3.  Wait for CMS replication to occur on all pools.

4.  Modify the phone normalization rules file for your deployment to clear the content. The file is on the file share of each Lync Server 2013 pool. If the file is not present, then create an empty file named "Company\_Phone\_Number\_Normalization\_Rules.txt."

5.  Wait several minutes for all Front End pools to read the new files.

6.  Run the following cmdlet on each Lync Server 2013 pool in your deployment.
    
        Update-csAddressBook

</div>

<div>

## Address Book Server error event 21054 is generated once daily for each Lync 2013 pool

**Issue:**

Lync Server 2013 Address Book Server will generate error event 21054 once every day when performing daily maintenance. The error is also generated every time an administrator runs the **Update-csAddressBook** cmdlet, even when the update is successful. However, this error event can safely be ignored when the update is successful.

**Workaround:**

When you encounter this error event, run the following cmdlet:

    Debug-csAddressBookReplication -Poolfqdn <Pool FQDN for which the event was generated>

If the cmdlet reports that there are no unindexed or abandoned objects, the error event 21054 can be safely ignored.

Additionally, the Key Health Indicator (KHI) "Address Book Users Correctly Indexed" should be turned off in System Center Operations Manager.

</div>

<div>

## Requests may fail when IPv6 is configured on an Edge pool

**Issue:**

When IPv6 is configured on an Edge pool, some requests to the Edge pool may fail.

**Workaround:**

To work around this issue, do not configure an Edge pool with IPv6.

</div>

<div>

## The invoke-csPoolFailback cmdlet may fail during pool failback

**Issue:**

When attempting to fail back a pool, the **invoke-csPoolFailback** cmdlet may fail with the error, "Failed to complete hydration process after repeated attempts."

**Workaround:**

To work around this issue, run the cmdlet again, and wait until the cmdlet succeeds. Note that the failback process can take several minutes to complete. It may take up to 60 minutes for a pool with 20,000 users.

</div>

<div>

## Data loss may occur when you add a Front End Server to an already established pool – Hybrid, Skype for Business Online

**Issue:**

You may encounter this issue in an environment where a pool has more than one Front End Server, and you either restart one of the Front End Servers, or add a new Front End Server that was not previously part of the pool.

Users whose data is being archived may experience data loss until a stable distribution of data archiving is established for the pool. This period of potential data loss is limited to 15 minutes for person-to-person conversations, and 30 minutes for conferences.

**Workaround:**

When you perform maintenance, instead of starting Front End Servers in the pool one by one, you should fail over the pool to another pool, and then perform maintenance tasks on the servers. You can also make the service unavailable before performing maintenance tasks, and then restore availability when maintenance is complete.

</div>

<div>

## Administrators cannot get licensee count by using the Get-CsClientAccessLicense cmdlet

**Issue:**

Administrators cannot get accurate client license usage by using the **Get-CsClientAccessLicense** cmdlet.

**Workaround:**

To check the server license type, you can run the **Get-CsService** cmdlet to retrieve the fully qualified domain names (FDQNs) of all databases. If the FQDN of the Front End Server is the same as the FQDN of the back-end database, the license is a Standard edition license. Otherwise, the license is an Enterprise edition license.

</div>

<div>

## Client licensee count is not accurately reported

**Issue:**

When determining client license counts, you may experience the following conditions:

1.  **Inaccurate license count for mobile users**
    
    The license count is based on the number of unique IP addresses for device-based users. The license count will be limited in the following ways:
    
      - Licenses will be overcounted if the IP address for the user changes during Lync sessions. This can occur when a user connects to Lync Server from more than one location with a desktop client.
    
      - Licenses will be undercounted if a user connects with a mobile client, because the IP address for the device cannot be determined.

2.  **Licenses are counted twice for public switched telephone network (PSTN) calls to Lync client, Lync client calls to PSTN lines, and Lync calls forwarded to PSTN lines**
    
    In the following scenarios, two additional licenses will be counted instead of one because both the phone number and the Lync user are counted to determine the number of licenses used. To obtain accurate licensing data, manually remove the licenses generated by a phone number.
    
      - A PSTN phone call to Lync
    
      - A Lync call to a PSTN line
    
      - A PSTN call to Lync, and then Lync forwards the call to a PSTN line. One of the PSTN lines will be counted.

3.  **A license will not be counted for a logged-on Lync phone**
    
    When a user uses a Lync-certified phone, if the phone logs in and stays connected, which retains its logon status, the phone will not be counted as using a license if the query for licenses occurs after the phone logged in.

4.  **Licenses counted for PSTN phones joining conferences**
    
    When a user joins a conference with a PSTN phone, a license will inaccurately be counted for joining the conference. However, no license is needed to join a conference with a PSTN phone.

**Workaround:**

1.  **Inaccurate license count for mobile users**
    
      - You can manually identify the IP addresses that belong to the same device and then remove one of them in the license count.
    
      - There is no workaround for this issue with mobile devices connecting with Lync client.

2.  **Licenses are counted twice for PSTN calls to Lync client, Lync client calls to PSTN lines, and Lync calls forwarded to PSTN lines**
    
    You will need to manually identify the PSTN phone number and remove the license count generated for it.

3.  **A license will not be counted for a logged-in Lync phone**
    
    You can configure the Lync phone to log off, and then log on again, at a regular interval, such as every 3 months.

4.  **Licenses counted for PSTN phones joining conferences**
    
    You can manually identify the PSTN phone number that is used to join the conference and remove the license generated by the phone number.

</div>

<div>

## The Lync Server Control Panel stops working in a VMware environment after upgrading to Silverlight 5

**Issue:**

If you use the Lync Server Control Panel in a VMware environment, the Lync Server Control Panel may stop working after you upgrade Microsoft Silverlight to version 5.

**Workaround:**

To work around this issue, do one of the following:

  - Uninstall Silverlight 5, and install Silverlight 4 from [https://go.microsoft.com/fwlink/p/?LinkID=149156](https://go.microsoft.com/fwlink/p/?linkid=149156).

  - Access the Lync Server Control Panel from a computer that is not a VMware virtual computer.
    
    To do so, you can start the Lync Server Control Panel from the Windows **Start** menu on the server, if the Lync Server Administration tools are installed on the computer.
    
    You can also access the Lync Server Control Panel by using a web browser. The URL will be similar to https://\<frontend\_pool\_fqdn\>/cscp.

</div>

<div>

## User information in the Address Book Service is not updated after the distinguished name for the user is modified in Active Directory

**Issue:**

If a user’s distinguished name (also known as DN) is changed in Active Directory Domain Services, any additional changes will not be updated in the Address Book Service (ABS). This does not affect sign-in or presence for the user, but it will prevent communication for the user if the SIP address is also changed, because searches will return an outdated SIP address.

**Workaround:**

To work around this issue, do not change a user’s DN. If you revert the DN for the user to the previous value, updates will be reflected in the Address Book Service.

</div>

</div>

<span id="Installation"></span>

<div>

## Installation

<div>

## Using non-ASCII characters may result in Lync server failing to start

**Issue:**

Setup will fail if the destination folder name includes non-ASCII characters (including UNICODE, double-byte character set (DBCS), UTF-8, and UTF-16). In addition, Setup may succeed but the server will not start if non-ASCII characters are contained in any of the following:

  - Computer name

  - Domain name

  - User name

  - User SIP URI

  - Service account name

**Workaround:**

Use only ASCII characters in the destination folder name, computer name, domain name, user name, user SIP URI, and service account names.

</div>

<div>

## The hotfix for "Heap corruption occurs when a module calls the InsertEntityBody method in IIS 7.5" must be installed prior to installing Lync Server 2013

**Issue:**

The hotfix for "Heap corruption occurs when a module calls the InsertEntityBody method in IIS 7.5" ([https://go.microsoft.com/fwlink/p/?LinkId=268602](https://go.microsoft.com/fwlink/p/?linkid=268602)), described in Microsoft Knowledge Base article 264886 ([https://go.microsoft.com/fwlink/p/?LinkId=268603](https://go.microsoft.com/fwlink/p/?linkid=268603)), must be installed prior to installing Lync Server 2013.

**Workaround:**

Download and install the hotfix from the Microsoft Download Center at [https://go.microsoft.com/fwlink/p/?LinkId=268602](https://go.microsoft.com/fwlink/p/?linkid=268602).

</div>

<div>

## Lync Server 2013 fails to install on ITA Windows Server 2012 OS RTM version

**Issue:**

Lync Server 2013 installation fails on ITA Windows Server 2012 due to Windows Fabric installation failing.

Windows Fabric installation fails because fabric traces are created with the time format of HH:MM:SS. However, in ITA Windows Server, the time format is HH.MM.SS.

**Workaround:**

To work around this issue, update the system registry before installing Lync Server 2013. The registry key that needs to be updated is: HKEY\_USERS\\.DEFAULT\\Control Panel\\International\\sTimeFormat. Change the value of sTimeFormat to HH:mm:ss by using the Windows PowerShell command-line interface as follows:

1.  Start Windows PowerShell and run the following cmdlets:
    
       ```
        New-PSDrive -Name HKU -PSProvider Registry -Root HKEY_USERS
       ```
    
       ```
        $a="HKU:\.Default\Control Panel\International"
       ```

2.  To view the current value, run the following cmdlet:
    
        Get-itemproperty $a -Name sTimeFormat
    
    Make note of the current value for sTimeFormat so it can be restored after the installation is complete.

3.  To set to new value, run the following cmdlet:
    
        Set-ItemProperty $a -Name sTimeFormat -Value "HH:mm:ss"

4.  After Lync Server 2013 has been successfully installed, restore the original value for the sTimeFormat by running the following cmdlet:
    
        - Set-ItemProperty $a -Name sTimeFormat -Value "<Value noted down in Step 3. above>"

</div>

</div>

<span id="Mobility"></span>

<div>

## Mobility

<div>

## Issues for mobile clients during the server failover process

**Issue:**

When a Lync Server fails and the failover process begins, the following issues may affect mobile client users:

  - No incoming Lync call or signal for up to 10 minutes after failover begins.

  - Cannot accept incoming Chat requests

  - Cannot join meetings if the failed server is the home server for the user

**Workaround:**

There is no workaround for this issue. Normal functionality will be restored once the failover process is complete.

</div>

<div>

## If a mobile user declines an incoming call from another Lync endpoint, the call is displayed as a missed conversion on Lync Mobile clients

**Issue:**

If a mobile user declines an incoming call, and the call originated from another Lync endpoint, the call is displayed as a missed conversation in the Lync Mobile client instead of a call in the device call list.

**Workaround:**

There is no workaround for this issue.

</div>

<div>

## The mobile client may not display a federated contact’s display name when searching for contacts

**Issue:**

The display name for federated contacts may not be displayed in some scenarios, such as when searching for a federated contact in the contact list. This can occur when the there is no active presence subscription for the contact from the Lync mobile client.

**Workaround:**

There is no workaround for this issue.

</div>

<div>

## In the mobile client, invitee and timestamp information are missing from a missed conversation that is an invitation to a conference

**Issue:**

In the mobile client, when a missed conversation is an invitation to a conference, the invitee and timestamp information is missing from the missed conversation message.

**Workaround:**

There is no workaround for this issue.

</div>

<div>

## Mobile client users making calls using VoIP are not be able to leave voice mail for users whose voice mail is configured in Exchange 2010 or earlier versions

**Issue:**

If a mobile client user is using VoIP to place calls, the user will not be able to leave voice mail messages for users configured to use voice mail in Microsoft Exchange Server 2007 or Microsoft Exchange Server 2010.

**Workaround:**

To work around this issue, use Exchange 2010 with SP1 or later version of Microsoft Exchange Server.

</div>

<div>

## When using Block with URL for Client Version Configuration on mobile clients, an incorrect error message may be displayed

**Issue:**

When using **Block with URL** for Client Version Configuration on mobile clients, an incorrect error message may be displayed when the client version is not supported.

**Workaround:**

To work around this issue, configure Client Version Configuration to use **Block** instead of **Block with URL**.

</div>

</div>

<span id="Conferencing"></span>

<div>

## Conferencing

<div>

## Antivirus software running on Lync Server 2013 Front End Servers can cause Application Domain recycling, which temporarily interrupts service for Lync Web App 2013, Lync Mobile 2010, and Lync Mobile 2013 clients

**Issue:**

Antivirus software can trigger application domain restarts, which can result in Lync Mobility Service 2013 and unified communications (UC) Web API client applications (Lync Web App 2013, Lync Mobile 2010, and Lync Mobile 2013) to lose their state.

**Workaround:**

To work around this issue, exclude the folders containing Web components and .NET framework from antivirus scanning. For details, see Microsoft Knowledge Base article 312592, "PRB: Random application restarts with 'Application is restarting' error in ASP.NET," at [http://go.microsoft.com/fwlink/p/?linkid=3052\&kbid=312592](http://go.microsoft.com/fwlink/p/?linkid=3052%26kbid=312592).

The following folders should be excluded:

  - %ProgramFiles%\\Microsoft Lync Server 2013\\Web Components\\Mcx\\Ext

  - %ProgramFiles%\\Microsoft Lync Server 2013\\Web Components\\Mcx\\Int

  - %ProgramFiles%\\Microsoft Lync Server 2013\\Web Components\\Ucwa\\Int

  - %ProgramFiles%\\Microsoft Lync Server 2013\\Web Components\\Ucwa\\Ext

  - %Windir%\\Microsoft.NET\\Framework64\\v4.0.30319\\Config

</div>

<div>

## ActiveX Controls or native XMLHTTP support must be enabled in Windows Internet Explorer to successfully join conferences

**Issue:**

If a user has disabled both ActiveX Controls and native XMLHTTP support in Windows Internet Explorer Internet browser settings, the user will not be able to join a meeting if Internet Explorer is selected as the default browser.

**Workaround:**

Enable either ActiveX Controls or "native XMLHTTP support" in Internet Explorer.

</div>

<div>

## Lync Server Web Conferencing service cannot recover from critical mode

**Issue:**

If critical mode is turned for archiving, in case of system failures, critical mode will start and the conferences will no longer work for the participants. After the administrator fixes the system failures (such as fixing a database issue), the data conferencing service doesn't automatically recover, and the administrator must manually restart the conferencing service for conferencing to resume.

**Workaround:**

An administrator needs to manually restart the conferencing service after the system failure is fixed.

</div>

<div>

## Web Conferencing service ignores the HTTP proxy for external Office Web App Servers

**Issue:**

If you have deployed an Office Web Apps Server external to the Web Conferencing service (that is, a server that is not in the internal corporate network) in the Internet, perimeter network, and the Web Conferencing service requires an HTTP proxy to connect to this, the Office Web Apps Server discovery will fail. The Web Conferencing service ignores the HTTP proxy setting, as defined in Topology Builder for Office Web Apps Server setup. As a result, the Lync client will not be able to do Microsoft PowerPoint 2010 sharing with other participants in the conference. If you are installing Lync Server on-premises and also configure Office Web Apps Server on-premises in the internal network, a proxy configuration is not required.

**Workaround:**

The only workaround is to not have a deployment configuration that requires the use of HTTP proxy to communicate with an external Office Web Apps Server.

</div>

<div>

## Adding video to an audio conferencing provider conference is not supported

**Issue:**

Adding a video is not supported if the user is joined to an audio conferencing provider conference for audio.

**Workaround:**

There is no workaround for this issue.

</div>

<div>

## Topologies with IPv6 enabled force the Lync Web App Silverlight plug-in auto-update to ensure screen sharing functionality can work from Lync Web App

**Issue:**

When a topology is configured with IPv6 enabled, users cannot share their screen from the Lync Web App client if an earlier version of the screen-sharing plug-in is already installed.

**Workaround:**

To force an update to the most recent version of the screen-sharing plug-in when joining meeting via Lync Web App, modify the value of **MinSupportedBuildVersion** from "4.0.7457.0" to "4.0.7577.380" in both of the following files:

  - %ProgramFiles%\\Microsoft Lync Server 15\\Web Components\\Reach\\Int\\Client\\Plugins\\ReachAppShPluginProperties.xml

  - %ProgramFiles%\\Microsoft Lync Server 15\\Web Components\\Reach\\Ext\\Client\\Plugins\\ReachAppShPluginProperties.xml

</div>

</div>

<span id="EnterpriseVoice"></span>

<div>

## Enterprise Voice

<div>

## In some cases, a Lync client running on a computer configured to use IPv4 and IPv6 dual stack might not support capabilities that rely in the IP subnet of the computer such as E911, Media Bypass, Call Admission Control and Location Based Routing

<div class="">


> [!NOTE]  
> The information in this section pertains to Cumulative Updates for Lync Server 2013: February 2013.



</div>

**Issue:**

When a Lync client is running on a computer that is enabled for IPv4 and IPv6 dual stack and based on the DNS resolution of the proxy server, the client may use the IPv6 address of the computer to sign in. After doing so, the Lync Client will support only the capabilities supported for IPv6, which excludes E911, Media Bypass, Call Admission Control and Location Based Routing.

**Workaround:**

To work around this issue, disable IPv6 support on the client computer.

</div>

<div>

## If Enterprise Voice is not configured for a user, the user will need to use E164 format to dial out from a conference

**Issue:**

If Enterprise Voice is not configured for a user, that user will need to use the E164 format to successfully dial out from a conference. If the E164 format is not used, the user will not be able to dial out from the conference.

**Workaround:**

To work around this issue, users who are not enabled for Enterprise Voice should dial out from a conference by using numbers in the E164 format.

</div>

</div>

<span id="Presence"></span>

<div>

## Presence

<div>

## If a user has selected "Block all invites and communications" while the unified contact store is turned on for the user, Presence status is not rejected when it should be

**Issue:**

If a user has selected "Block all invites and communications" while the unified contact store is turned on for the user, Presence status is not rejected when it should be.

**Workaround:**

To work around this issue, you can turn off the unified contact store for the user. To do so, run the following cmdlets:

    Set-CsUserServicesPolicy -Identity "<user display name>" -UcsAllowed $False

For example:

    Set-CsUserServicesPolicy -Identity "Ken Myer" -UcsAllowed $False

</div>

<div>

## Office Communications Server 2007 R2 users homed on-premises are not able to see the Presence status of Skype for Business Online users in hybrid deployments - Hybrid

**Issue:**

The issue may occur in a hybrid deployment when you are using a Lync Server 2013 Director.

Presence status for users homed to Skype for Business Online is displayed as Presence Unknown for on-premises users. Also, users homed to Skype for Business Online are not able to see presence status for Office Communications Server R2 on-premises users.

**Workaround:**

To partially work around this issue, change the Home Server (msrtcsip-presencehomeserver) of the Skype for Business Online users to point to a Lync Server 2013 on-premises pool instead of the Lync Server 2013 Director. You can modify this setting on the on-premises Front End Server.

This workaround will correctly display the Presence status of users homed to Office Communications Server 2007 R2 to Skype for Business Online users.

</div>

</div>

<span id="ResponseGroup"></span>

<div>

## Response Group application, Call Park application, and Group Call Pickup

<div>

## A caller might hear one second of music-on-hold during the establishment of a call with the retrieving party

<div class="">


> [!NOTE]  
> The information in this section pertains to Cumulative Updates for Lync Server 2013: February 2013.



</div>

**Issue:**

When a call is retrieved via Group Call Pickup, the caller might hear one second of music-on-hold during the establishment of the call with the retriever party.

**Workaround:**

There is no workaround for this issue.

</div>

<div>

## A Response Group agent can sign in and sign out through a Lync Server 2010 Agent Console to Lync Server 2010 formal Agent Groups only

**Issue:**

A Lync Server 2013 Response Group agent can sign in and sign out through a Lync Server 2010 Agent Console to Lync Server 2010 formal Agent Groups only. In the Lync Server 2010 Agent Console, users can see only the Lync Server 2010 Response Group that they belong to. They cannot see any of the Lync Server 2013 Response Groups that they belong to.

**Workaround:**

If the Response Group agent is a Lync Server 2013 user, and part of a Lync Server 2013 formal Agent Group, the user must access the Lync Server 2013 Agent Console directly via a web link in a browser to sign in to and sign out from Lync Server 2013 Agent Groups.

</div>

<div>

## A Lync Server 2010 Response Group agent cannot place calls on behalf of a Lync Server 2013 Response Group

**Issue:**

A Lync Server 2010 user who is an Agent of a Lync Server 2013 Response Group is not able to place a call on behalf of the Response Group. The Lync Server 2013 Response Group will not be available in the Lync Client to place a call.

**Workaround:**

To work around this issue, you must move the Lync Server 2010 user to Lync Server 2013.

</div>

<div>

## Removing a Response Group from Lync Server 2010 after it has been migrated to Lync Server 2013 will prevent the Response Group from accepting any incoming calls

**Issue:**

If a Response Group that has been migrated from Lync Server 2010 to Lync Server 2013 is removed from Lync Server 2010 through the Lync Server Control Panel or the Lync Server Management Shell, the Response Group in Lync Server 2013 will stop receiving any incoming calls.

**Workaround:**

To work around this issue, do not remove any Response Groups from Lync Server 2010 that have been migrated from Lync Server 2010 to Lync Server 2013.

If the Response Group has already been removed, you should redeploy it in Lync Server 2013.

</div>

<div>

## When a new managed workflow is set to inactive when created, deployment of the workflow will fail

**Issue:**

When a new managed workflow is set to inactive when created, deployment of the workflow will fail. This issue is encountered when the workflow is set to inactive when created, but does not affect a workflow that is edited to set it to inactive after is has been deployed.

**Workaround:**

When creating and deploying a workflow, set the workflow as active and then deploy it. After the workflow is successfully deployed, the workflow can be edited and set to inactive.

</div>

<div>

## Removing a Response Group from the Owner pool will prevent the Response Group of the Backup pool from accepting any incoming calls during failover if the Response Group has been imported to the Backup pool

**Issue:**

If a Response Group that is owned by the primary pool has been imported to the backup pool without overwriting the owner, and the Response Group is removed from the owner pool, the Response Group in the Backup pool will not accept any incoming calls during failover.

**Workaround:**

You will need to redeploy the Response Group in the Primary pool. You will then need to export the Response Group configuration from the Primary pool and import it to the Backup pool again.

You can also recreate the Response Group in the Backup pool. In this case, the Backup pool will be the owner pool of the Response Group.

</div>

<div>

## A parked call can't be retrieved from the Call Park application if the retrieve request is done on behalf of a Response Group

**Issue:**

When the following conditions are true, a retrieve request for a parked call will fail:

  - An agent is part of an anonymous Response Group

  - The agent attempts to retrieve a parked call from the Call Park application through the anonymous Response Group

  - The agent attempts to retrieve the call by dialing the orbit number through the Call On Behalf option or through the same option in the Lync attendant client

**Workaround:**

There are no workarounds for this issue. The parked call should be retrieved without doing so on behalf of a Response Group.

</div>

</div>

<span id="TopoBuilder"></span>

<div>

## Lync Server Control Panel, Topology Builder, and Planning Tool

<div>

## Planning Tool Limitations

<div class="">


> [!NOTE]  
> The information in this section pertains to Cumulative Updates for Lync Server 2013: February 2013.



</div>

**Issue:**

The Planning Tool has the following limitations when planning for your deployment:

  - There is a maximum of 10 central sites supported

  - Each central site can have a maximum of 14 branch sites

  - Each central site can have a maximum of 240,000 users

In addition, the Planning Tool does not include values for the following when calculating the recommended topology:

  - The number of users that are homed online

  - The percentage of users that are enabled for XMPP federation

  - Percentage of users that are using Lync Web App

**Workaround:**

There is no workaround for these issues. For more information about the Planning Tool, see [Designing the topology for Lync Server 2013 by using the Planning Tool](lync-server-2013-designing-the-topology-by-using-the-planning-tool.md).

</div>

<div>

## Planning Tool may not use previously defined IP addresses for the Edge network when updating options

**Issue:**

After you complete your design using the Planning Tool, if you make changes to the Edge Network options, additional IP addresses may be added to the design instead of updating the existing IP addresses. This can occur when you are viewing the details of the Edge Network Diagram, select **Click here to update your options**, and then, on the Configuration Options dialog, you select Edge Network select **I want to use the same FQDNs and IP addresses, but different ports for the edge services on my Edge Server**. Applying any changes may result in new IP addresses and Edge servers being added to the design.

**Workaround:**

There is no workaround for this issue at this time.

</div>

<div>

## In Lync Server Control Panel, "Move all users to pool" may not work as expected

**Issue:**

When using the Lync Server Control Panel to move all users from one pool to another pool in a complex Active Directory environment, such as one with multiple Domain Controllers and parent/child domains, an error message may be returned that states, “Specified user is not a legacy user, use Move-CsUser cmdlet instead.” This is a result of longer replication times in complex Active Directory environments.

**Workaround:**

To work around this issue, do one of the following:

  - Use filters in the Lync Server Control Panel to search for legacy users, select those users, and then use the **Move selected users to pool command** instead of **Move all users to pool**.

  - Use the Lync Server Management Shell to move legacy users in batches by using Lync Server cmdlets.

</div>

<div>

## The Lync Server Control Panel stops working in a VMware environment after the Microsoft Silverlight browser plug-in is updated to version 5

**Issue:**

If you use the Lync Server Control Panel in a VMware environment, the Lync Server Control Panel may stop working after you upgrade Silverlight to version 5.

**Workaround:**

To work around this issue, do one of the following:

  - Uninstall Silverlight 5, and then install Silverlight 4 from [https://go.microsoft.com/fwlink/p/?LinkID=149156\&v=4.0](https://go.microsoft.com/fwlink/p/?linkid=149156%26v=4.0).

  - Open the Lync Server Control Panel from a computer that is not a VMware virtual computer.
    
    To open the Lync Server Control Panel from a remote computer, install Lync Server Administration tools on the computer, and then start the Lync Server Control Panel from the Windows **Start** menu.
    
    You can also open the Lync Server Control Panel by entering the URL in a web browser. The URL will be similar to https://\<frontend\_pool\_fqdn\>/cscp.

</div>

<div>

## An administrator cannot run the Uninstall-csMirrorDB cmdlet after removing the mirroring database in Topology Builder

**Issue:**

When an administrator disables a mirroring database in Topology Builder, and then deletes the mirroring database in Topology Builder, a message is displayed in the To do list for the administrator to run the **Uninstall-csMirrorDatabase** cmdlet to remove mirroring from SQL Server. When the administrator attempts to run the cmdlet, it fails.

**Workaround:**

To remove SQL mirroring of a pool in Topology Builder, you must first use a cmdlet to remove the mirror in SQL Server. You can then use Topology Builder to remove the mirror from the topology. To remove the mirror in SQL Server, use the following cmdlet:

    Uninstall-CsMirrorDatabase -SqlServerFqdn <SQLServer FQDN> [-SqlInstanceName <SQLServer instance name>] -DatabaseType <Application | Archiving | CentralMgmt | Monitoring | User | BIStaging | PersistentChat | PersistentChatCompliance> [-DropExistingDatabasesOnMirror] [-Verbose]

For example, to remove mirroring and drop the databases for the user databases, type the following:

    Uninstall-CsMirrorDatabase -SqlServerFqdn primaryBE.contoso.com -SqlInstanceName rtc -Verbose -DatabaseType User -DropExistingDatabasesOnMirror

The *DropExistingDatabasesOnMirror* parameter causes the affected databases to be deleted from the mirror. Then, to remove the mirror from the topology, do the following:

1.  In Topology Builder, right-click the pool and click **Edit Properties**.

2.  Clear **Enable SQL Store Mirroring** and click **OK**.

3.  Publish the topology.

<div class="">


> [!IMPORTANT]  
> Whenever you make a change to a back-end database mirroring relationship, you must restart all the Front End Servers in the pool.



</div>

</div>

<div>

## Validation errors are returned in Topology Builder when an administrator attempts to remove a deployment with a Front End pool that has an associated witness store

**Issue:**

If an administrator attempts to use the **Remove Deployment** command in Topology Builder to remove a deployment that includes a Front End pool with an associated witness store, a validation error is displayed in Topology Builder and the action will not proceed.

**Workaround:**

To work around this issue, do one of the following:

  - Remove the witness store before attempting to remove the deployment.

  - Add a witness store for the Front End pool and then remove it.

</div>

<div>

## Persistent Chat Server deployment information is inconsistent between the Planning Tool and Topology Builder

**Issue:**

When the Lync Server 2013, Planning Tool outputs the site topology diagram for a Persistent Chat Server deployment with disaster recovery enabled, the site topology diagram includes multiple (physical) sites, with evenly assigned Persistent Chat Servers at each site. In Topology Builder, all Persistent Chat Servers are represented as belonging to a single (logical) site, and are listed under the same Persistent Chat Server pool node.

**Workaround:**

Currently, we do not have a workaround for this issue. The user should analyze the output of the Planning Tool for the Persistent Chat Server deployment, and modify the plan to meet their specific needs.

</div>

</div>

<span id="Localization"></span>

<div>

## Localization

<div>

## Monitoring

<div>

## The Deploy Monitoring Reports wizard displays incorrect characters under certain circumstances when using the East Asian version of Lync Server

**Issue:**

When using an East Asian version of Lync Server 2013—for example, Chinese (Simplified), Chinese (Traditional), Japanese, or Korean—on an operating system that has the system locale not set to an East Asian language, the Deploy Monitoring Reports wizard will display question marks or other characters instead of localized messages.

**Workaround:**

To correct this issue, set the locale for the operating system and Lync Server 2013 to the same language, which will display all messages correctly.

</div>

</div>

<div>

## Lync Server Control Panel

<div>

## In certain cases, the first item in the top navigation bar on a page of Lync Server Control Panel disappears when the last item in the top navigation bar is clicked

**Issue:**

There are three known cases where clicking the last item in the top navigation bar on a page of the Lync Server Control Panel will cause the first item in the top navigation bar to disappear:

  - In the French of version, on the page "Féderation et accès externe," the item "Stratégie d'accès externe" will disappear when "Partenaires fédérés XMPP" is clicked.

  - In the German version, on the "Clients" page, the item "Clientversionskonfiguration" disappears when "Pushbenachrichtigungskonfiguration" is clicked.

  - In the Russian version, on "Конфигурация сети" page, the item "Глобально" disappears when "Маршрут региона" is clicked.

**Workaround:**

To work around this issue, refresh the page of the Lync Server Control Panel in your browser. The page will load in the browser with all of the items in the top navigation bar displayed.

</div>

</div>

<div>

## Address Book

<div>

## Indexing in the Address Book does not work as expected in some languages

<div class="">


> [!NOTE]  
> The information in this section pertains to Cumulative Updates for Lync Server 2013: February 2013.



</div>

If a user’s properties contain an indexed field, and that field contains only characters that cannot be indexed, then the user will not appear in searches performed in the Address Book.

The following characters and locales cannot be indexed:

  - Upper-case Cyrillic, Greek, and Armenian characters

  - Upper-case accented characters

  - Thai

  - Lao

  - Myanmar

  - Devanagari

  - Ethiopic

  - Tibetan

  - Bengali

  - Gujarati

  - Telugu

  - All other Indic scripts

</div>

</div>

<div>

## Lync Web App, Web Scheduler, and Web components

<div>

## Language fallback for certain languages in Lync Web Scheduler, Dial-In, Join Launcher, Persistent Chat Room Management, and OCTab might not work as expected

**Issue:**

When selecting a neutral locale in a web browser (in Internet Explorer, for example, the language name without further specification, like "Norwegian \[no\]") instead of a locale specifying language, script and locale (such as "Norwegian, Bokmål (Norway) \[nb-NO\]") might lead to unexpected display behavior for certain languages in Lync Web Scheduler, Dial-In, Join Launcher, Persistent Chat Room Management, and OCTab. For example, users might see the English page when one of the following languages is selected:

  - Norwegian

  - Portuguese

  - Serbian

**Workaround:**

If you want to select a language with a neutral locale, always make sure that you also add the language with a specific locale (with script and/or country code) as an additional language in your browser's language preference list.

</div>

<div>

## There is limited support for Azeri and Uzbek locales when using Lync Web Scheduler, Dial-In, Join Launcher, Persistent Chat Room Management, and OCTab in some web browsers

<div class="">


> [!NOTE]  
> The information in this section pertains to Cumulative Updates for Lync Server 2013: February 2013.



</div>

**Issue:**

When you use Internet Explorer 8 or Internet Explorer 9, and set the browser language to Azeri (Latin) or Uzbek (Latin), the Dial-in and Join Launcher pages will be displayed in English or the preferred language set in the browser.

When you use Firefox or Chrome browsers, and you set the browser language to Azeri (Latin) or Uzbek (Latin), the Lync Web App, Lync Web Scheduler, and RGS OCTab will be shown in English or the preferred language set for the browser.

The Uzbek (Latin) locale is not supported in the Safari browser.

**Workaround:**

There is not workaround for these issues.

</div>

</div>

<div>

## The drop-down arrow is missing for "Join meeting from" list in the Romanian version of Lync Web App

**Issue:**

When a user who is using the Romanian version of Lync Web App performs the following steps, the drop-down arrow is not displayed for **Join meeting** in drop-down list:

1.  Select **Remember me on this computer** on the **General** tab.

2.  Select the **Phone** tab.

3.  Click the drop-down list for **Join meeting from**.
    
    Users will not see an arrow that indicates that there are more options than the default **Lync Web App**, which include: **Don't join audio** (in Romanian, "Nu se asociaža la componenta audio") and **New number**" (in Romanian, "Număr nou").

**Workaround:**

Even though the arrow for this drop-down list is not displayed, users can still select the additional settings in the list by clicking on the default value.

</div>

<div>

## When using the Turkish version of Lync Web Scheduler, a meeting cannot be saved when using the "People I choose" option under "Who is a presenter"

**Issue:**

When creating or editing a meeting in the Turkish version of the Lync Web Scheduler, the option "People I choose" under "Who is a presenter" is not supported. When this option is selected, the meeting can't be saved. Instead, an error message appears, indicating that one or more people cannot be made presenters.

**Workaround:**

To work around this issue, users can use the default option of "People from my company," or any other choice, such as "Only Organizer" or "Everyone including people outside of my company." The organizer can demote or promote people to their correct roles later, after they have joined the meeting.

Alternatively, users who understand another language can change the language selection in their browser to one of the other 43 supported languages and attempt to use the “People I choose” option.

</div>

</div>

<span id="Copyright"></span>

<div>

## Copyright

This document supports a preliminary release of a software product that may be changed substantially prior to final commercial release, and is the confidential and proprietary information of Microsoft Corporation. It is disclosed pursuant to a non-disclosure agreement between the recipient and Microsoft. This document is provided for informational purposes only and Microsoft makes no warranties, either express or implied, in this document. Information in this document, including URL and other Internet website references, is subject to change without notice. The entire risk of the use or the results from the use of this document remains with the user. Unless otherwise noted, the companies, organizations, products, domain names, email addresses, logos, people, places, and events depicted in examples herein are fictitious. No association with any real company, organization, product, domain name, email address, logo, person, place, or event is intended or should be inferred. Complying with all applicable copyright laws is the responsibility of the user. Without limiting the rights under copyright, no part of this document may be reproduced, stored in or introduced into a retrieval system, or transmitted in any form or by any means (electronic, mechanical, photocopying, recording, or otherwise), or for any purpose, without the express written permission of Microsoft Corporation.

Microsoft may have patents, patent applications, trademarks, copyrights, or other intellectual property rights covering subject matter in this document. Except as expressly provided in any written license agreement from Microsoft, the furnishing of this document does not give you any license to these patents, trademarks, copyrights, or other intellectual property.

© 2012 Microsoft Corporation. All rights reserved.

Microsoft, Windows, Windows Live, Active Directory, Internet Explorer, MSN, Outlook, and SQL Server are either registered trademarks or trademarks of Microsoft Corporation in the United States and/or other countries/regions.

All other trademarks are property of their respective owners.

</div>

</div>

<span> </span>

</div>

</div>

</div>

