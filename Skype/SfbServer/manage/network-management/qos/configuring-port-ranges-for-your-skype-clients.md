---
title: 'Configuring port ranges and a Quality of Service policy for your clients'
ms.reviewer: 
ms:assetid: 287d5cea-7ada-461c-9b4a-9da2af315e71
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204760(v=OCS.15)
ms:contentKeyID: 48183694
mtps_version: v=OCS.15
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "This article describes how to configure port ranges for your clients and configuring Quality of Service policies in Skype for Business Server for clients running on Windows 10."
---

# Configuring port ranges and a Quality of Service policy for your clients in Skype for Business Server

This article describes how to configure port ranges for your clients and configuring Quality of Service policies in Skype for Business Server for clients running on Windows 10.

## Configure port ranges

By default, Skype for Business client applications can use any port between ports 1024 and 65535 when involved in a communication session; this is because specific port ranges are not automatically enabled for clients. In order to use Quality of Service, however, you will need to reassign the various traffic types (audio, video, media, application sharing, and file transfer) to a series of unique port ranges. This can be done by using the Set-CsConferencingConfiguration cmdlet.

> [!NOTE]  
> End users cannot make these changes themselves. Port changes can only be made by administrators using the Set-CsConferencingConfiguration cmdlet.


You can determine which port ranges are currently used for communication sessions by running the following command from within the Skype for Business Server Management Shell:

    Get-CsConferencingConfiguration

Assuming that you have not made any changes to your conferencing settings since you installed Skype for Business Server, you should get back information that includes these property values:

    ClientMediaPortRangeEnabled : False
    ClientAudioPort             : 5350
    ClientAudioPortRange        : 40
    ClientVideoPort             : 5350
    ClientVideoPortRange        : 40
    ClientAppSharingPort        : 5350
    ClientAppSharingPortRange   : 40
    ClientFileTransferPort      : 5350
    ClientTransferPortRange     : 40

If you look closely at the preceding output, you'll see two things of importance. First, the ClientMediaPortRangeEnabled property is set to False:

    ClientMediaPortRangeEnabled : False

That's important because, when this property is set to False, Skype for Business clients will use any available port between ports 1024 and 65535 when involved in a communication session; this is true regardless of any other port settings (for example, ClientMediaPort or ClientVideoPort). If you want to restrict usage to a specified set of ports (and this is something you do want to do if you plan on implementing Quality of Service), then you must first enable client media port ranges. That can be done using the following Windows PowerShell command:

    Set-CsConferencingConfiguration -ClientMediaPortRangeEnabled $True

The preceding command enables client media port ranges for the global collection of conferencing configuration settings; however, these settings can also be applied to the site scope and/or the service scope (for the Conferencing Server service only). To enable client media port ranges for a specific site or server, specify the Identity of that site or server when calling Set-CsConferencingConfiguration:

    Set-CsConferencingConfiguration -Identity "site:Redmond" -ClientMediaPortRangeEnabled $True

Alternatively, you can use this command to simultaneously enable port ranges for all your conferencing configuration settings:

    Get-CsConferencingConfiguration | Set-CsConferencingConfiguration  -ClientMediaPortRangeEnabled $True

The second thing of importance you will notice is that the sample output shows that, by default, the media port ranges set for each type of network traffic are identical:

    ClientAudioPort             : 5350
    ClientVideoPort             : 5350
    ClientAppSharingPort        : 5350
    ClientFileTransferPort      : 5350

In order to implement QoS, each of these port ranges will need to be unique. For example, you might configure the port ranges like this:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Client Traffic Type</th>
<th>Port Start</th>
<th>Port Range</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Audio</p></td>
<td><p>50020</p></td>
<td><p>20</p></td>
</tr>
<tr class="even">
<td><p>Video</p></td>
<td><p>58000</p></td>
<td><p>20</p></td>
</tr>
<tr class="odd">
<td><p>Application sharing</p></td>
<td><p>42000</p></td>
<td><p>20</p></td>
</tr>
<tr class="even">
<td><p>File transfer</p></td>
<td><p>42020</p></td>
<td><p>20</p></td>
</tr>
</tbody>
</table>


In the preceding table, client port ranges represent a subset of the port ranges configured for your servers. For example, on the servers, application sharing was configured to use ports 40803 through 49151; on the client computers, application sharing is configured to use ports 42000 through 42019. This, too, is done primarily to make administration of QoS easier: client ports do not have to represent a subset of the ports used on the server. (For example, on the client computers you could configure application sharing to use, say, ports 10000 through 10019.) However, it is recommended that you make your client port ranges a subset of your server port ranges.

In addition, you might have noticed that 8348 ports were set aside for application sharing on the servers, but only 20 ports were set aside for application sharing on the clients. This, too, is recommended, but is not a hard-and-fast rule. In general, you can consider each available port to represent a single communication session: if you have 100 ports available in a port range, that means that the computer in question could participate in, at most, 100 communication sessions at any given time. Because servers will likely take part in many more conversations than clients, it makes sense to open many more ports on servers than on clients. Setting aside 20 ports for application sharing on a client means that a user could participate in 20 application sharing sessions on the specified device, and all at the same time. That should prove sufficient for the vast majority of your users.

To assign the preceding port ranges to your global collection of conferencing configuration settings, you can use the following Skype for Business Server Management Shell command:

    Set-CsConferencingConfiguration -Identity global -ClientAudioPort 50020 -ClientAudioPortRange 20 -ClientVideoPort 58000 -ClientVideoPortRange 20 -ClientAppSharingPort 42000 -ClientAppSharingPortRange 20 -ClientFileTransferPort 42020 -ClientFileTransferPortRange 20

Or, use this command to assign these same port ranges for all your conferencing configuration settings:

    Get-CsConferencingConfiguration | Set-CsConferencingConfiguration -ClientAudioPort 50020 -ClientAudioPortRange 20 -ClientVideoPort 58000 -ClientVideoPortRange 20 -ClientAppSharingPort 42000 -ClientAppSharingPortRange 20 -ClientFileTransferPort 42020 -ClientFileTransferPortRange 20

Individual users must log off from Skype for Business and then log back on before these changes will actually take effect.

> [!NOTE]  
> You can also enable client media port ranges, and then assign those port ranges, using a single command. For example:<BR><CODE>Set-CsConferencingConfiguration -ClientMediaPortRangeEnabled $True -ClientAudioPort 50020 -ClientAudioPortRange 20 -ClientVideoPort 58000 -ClientVideoPortRange 20 -ClientAppSharingPort 42000 -ClientAppSharingPortRange 20 -ClientFileTransferPort 42020 -ClientFileTransferPortRange 20</CODE>

## Configure Quality of Service policies for clients running on Windows 10

In addition to specifying port ranges for use by your Skype for Business clients, you must also create separate Quality of Service policies that will be applied to client computers. (The Quality of Service policies created for Conferencing, Application, and Mediation servers should not be applied to client computers.) This information applies only to computers running the Skype for Business client and Windows 10.

The following example uses this set of port ranges to create an audio policy and a video policy:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Client Traffic Type</th>
<th>Port Start</th>
<th>Port Range</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Audio</p></td>
<td><p>50020</p></td>
<td><p>20</p></td>
</tr>
<tr class="even">
<td><p>Video</p></td>
<td><p>58000</p></td>
<td><p>20</p></td>
</tr>
<tr class="odd">
<td><p>Application sharing</p></td>
<td><p>42000</p></td>
<td><p>20</p></td>
</tr>
<tr class="even">
<td><p>File transfer</p></td>
<td><p>42020</p></td>
<td><p>20</p></td>
</tr>
</tbody>
</table>

To create a Quality of Service audio policy for Windows 10 computers, first log on to a computer where Group Policy Management has been installed. Open Group Policy Management (click **Start**, point to **Administrative Tools**, and then click **Group Policy Management**), and then complete the following procedure:

1.  In Group Policy Management, locate the container where the new policy should be created. For example, if all your client computers are located in an OU named Clients, the new policy should be created in the Client OU.

2.  Right-click the appropriate container, and then click **Create a GPO in this domain, and Link it here**.

3.  In the **New GPO** dialog box, type a name for the new Group Policy object in the **Name** box, and then click **OK**.

4.  Right-click the newly-created policy, and then click **Edit**.

5.  In the Group Policy Management Editor, expand **Computer Configuration**, expand **Windows Settings**, right-click **Policy-based QoS**, and then click **Create new policy**.

6.  In the **Policy-based QoS** dialog box, on the opening page, type a name for the new policy in the **Name** box. Select **Specify DSCP Value** and set the value to **46**. Leave **Specify Outbound Throttle Rate** unselected, and then click **Next**.

7.  On the next page, make sure that **All applications** is selected, and then click **Next**. This setting instructs the network to look for all packets with a DSCP marking of 46, not just packets created by a specific application.

8.  On the third page, make sure that both **Any source IP address** and **Any destination IP address** are selected, and then click **Next**. These two settings ensure that packets will be managed regardless of which computer (IP address) sent those packets and which computer (IP address) will receive those packets.

9.  On page four, select **TCP and UDP** from the **Select the protocol this QoS policy applies to** dropdown list. TCP (Transmission Control Protocol) and UDP (User Datagram Protocol) are the two networking protocols most-commonly used by Skype for Business Server and its client applications.

10. Under the heading **Specify the source port number**, select **From this source port or range**. In the accompanying text box, type the port range reserved for audio transmissions. For example, if you reserved ports 50020 through ports 50039 for audio traffic enter the port range using this format: **50020:50039**. Click **Finish**.

After you have created the QoS policy for audio you should then create a second policy for video. To create a policy for video, follow the same basic procedure you followed when creating the audio policy, making these substitutions:

  - Use a different (and unique) policy name.

  - Set the DSCP value to **34** instead of 46. (As noted previously, you do not have to use the DSCP value 34; you simply must assign a different DSCP value than the one used for audio.)

  - Use the previously configured port range for video traffic. For example, if you have reserved ports 58000 through 58019 for video, set the port range to this: **58000:58019**.

If you decide to create a policy for managing application sharing traffic, make these substitutions:

  - Use a different (and unique) policy name (for example, **Skype for Business Server Application Sharing**).

  - Set the DSCP value to **24** instead of 46. (Again, this value does not have to be 24; it simply must be different than the DSCP values used for audio and for video.)

  - Use the previously configured port range for video traffic. For example, if you have reserved ports 42000 through 42019 for application sharing, set the port range to this: **42000:42019**.

For a file transfer policy:

  - Use a different (and unique) policy name (for example, **Skype for Business Server File Transfers**).

  - Set the DSCP value to **14**. (Again, this value does not have to be 14; it simply must be a unique DSCP code.)

  - Use the previously configured port range for application. For example, if you have reserved ports 42020 through 42039 for application sharing, set the port range to this: **42020:42039**.

The new policies you have created will not take effect until Group Policy has been refreshed on your client computers. Although Group Policy periodically refreshes on its own, you can force an immediate refresh by running the following command on each computer where Group Policy needs to be refreshed:

    Gpudate.exe /force

This command can be run from any command window that is running under administrator credentials. To run a command window under administrator credentials, click **Start**, right-click **Command Prompt**, and then click **Run as administrator**.

Keep in mind that these policies should be targeted towards your client computers. They should not be applied to servers running Skype for Business Server.

To help ensure that network packets are marked with the appropriate DSCP value, you should also create a new registry entry on each computer by completing the following procedure:

1.  Click **Start**, and then click **Run**.

2.  In the **Run** dialog box, type **regedit**, and then press ENTER.

3.  In the Registry Editor, expand **HKEY\_LOCAL\_MACHINE**, expand **SYSTEM**, expand **CurrentControlSet**, expand **services**, and then expand **Tcpip**.

4.  Right-click **Tcpip**, point to **New**, and then click **Key**. After the new registry key is created, type **QoS**, and then press ENTER to rename the key.

5.  Right-click **QoS**, point to **New**, and then click **String Value**. After the new registry value is created, type **Do not use NLA**, and then press ENTER to rename the value.

6.  Double-click **Do not use NLA**. In the **Edit String** dialog box, type **1** in the **Value data** box, and then click **OK**.

7.  Close the Registry Editor and eboot your computer.

### Configure Quality of Service on computers with multiple network adapters

If you have a computer that has multiple network adapters, you might occasionally run in to issues where DSCP values are shown as 0x00 rather than the configured value. This will typically occur on computers where one or more of the network adapters are not able to access your Active Directory domain (for example, if these adapters are used for a private network). In cases like that, DSCP values will be tagged for the adapters that can access the domain, but will not be tagged for adapters that cannot access the domain.

If you would like to tag DSCP values for all the network adapters in a computer, including adapters that do not have access to your domain, you will need to add and configure a value to the registry. That can be done by completing the following procedure:

1.  Click **Start**, and then click **Run**.

2.  In the **Run** dialog box, type **regedit**, and then press ENTER.

3.  In the Registry Editor, expand **HKEY\_LOCAL\_MACHINE**, expand **SYSTEM**, expand **CurrentControlSet**, expand **services**, and then expand **Tcpip**.

4.  If you do not see a registry key labeled **QoS** then right-click **Tcpip**, point to **New**, and then click **Key**. After the new key is created, type **QoS**, and then press ENTER to rename the key.

5.  Right-click **QoS**, point to **New**, and then click **String Value**. After the new registry value is created, type **Do not use NLA**, and then press ENTER to rename the value.

6.  Double-click **Do not use NLA**. In the **Edit String** dialog box, type **1** in the **Value data** box, and then click **OK**.

After creating and configuring the new registry value, you will need to reboot your computer for the changes to take effect.

## See also

[Create a Group Policy Object in Windows 10](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-firewall/create-a-group-policy-object)
