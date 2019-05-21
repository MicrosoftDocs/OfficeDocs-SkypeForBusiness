---
title: 'Configuring port ranges and a Quality of Service policy for your Conferencing, Application, and Mediation servers'
ms.reviewer: 
ms:assetid: 4d6eaa5d-0127-453f-be6a-e55384772d83
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204872(v=OCS.15)
ms:contentKeyID: 48184074
mtps_version: v=OCS.15
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "This article describes how to configure port ranges and a Quality of Service policy for your Conferencing, Application, and Mediation servers."
---

# Configuring port ranges and a Quality of Service policy for your Conferencing, Application, and Mediation servers

This article describes how to configure port ranges and a Quality of Service policy for your Conferencing, Application, and Mediation servers.

## Configure port ranges

To implement Quality of Service, you should configure identical port ranges for audio, video, and application sharing on your Conferencing, Application, and Mediation servers; furthermore, those port ranges must not overlap in any way. To use a simple example, suppose you use ports 10000 through 10999 for video on your Conferencing servers. That means that you must also reserve ports 10000 through 10999 for video on your Application and Mediation servers. If you do not, QoS will not work as expected.

Similarly, suppose you reserve ports 10000 through 10999 for video, but then reserve ports 10500 through 11999 for audio. This can create problems for Quality of Service, because the port ranges overlap. With QoS, each modality must have a unique set of ports: if you use ports 10000 through 10999 for video, then you'll have to use a different range (for example, 11000 through 11999, for audio).

By default, audio and video port ranges do not overlap in Skype for Business Server; however, the port ranges assigned to application sharing overlap with both the audio and video port ranges. (Which, in turn, means that none of these ranges are unique.) You can verify the existing port ranges for your Conferencing, Application, and Mediation servers by running the following three commands from within the Skype for Business Server Management Shell:

    Get-CsService -ConferencingServer | Select-Object Identity, AudioPortStart, AudioPortCount, VideoPortStart, VideoPortCount, AppSharingPortStart, AppSharingPortCount
    
    Get-CsService -ApplicationServer | Select-Object Identity, AudioPortStart, AudioPortCount
    
    Get-CsService -MediationServer | Select-Object Identity, AudioPortStart, AudioPortCount

> [!WARNING]  
> As you can see in the preceding commands, each port type – audio, video, and application sharing – is assigned two separate property values: the port start and the port count. The port start indicates the first port used for that modality; for example, if the audio port start is equal to 50000 that means that the first port used for audio traffic is port 50000. If the audio port count is 2 (which is not a valid value, but is used here for illustration purposes), that means that only two ports are allocated for audio. If the first port is port 50000 and there are a total of two ports, that means the second port must be port 50001 (port ranges have to be contiguous). As a result, the port range for audio would be ports 50000 through 50001, inclusive.<BR><br>Note, too that Application server and Mediation server only support QoS for audio; you do not need to change video or application sharing ports in your Application servers or Mediation servers.

If you run the preceding three commands, you'll see that that the default port values for Skype for Business Server are configured like this:

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Conferencing Server</th>
<th>Application Server</th>
<th>Mediation Server</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>AudioPortStart</p></td>
<td><p>49152</p></td>
<td><p>49152</p></td>
<td><p>49152</p></td>
</tr>
<tr class="even">
<td><p>AudioPortCount</p></td>
<td><p>8348</p></td>
<td><p>8348</p></td>
<td><p>8348</p></td>
</tr>
<tr class="odd">
<td><p>VideoPortStart</p></td>
<td><p>57501</p></td>
<td><p>--</p></td>
<td><p>--</p></td>
</tr>
<tr class="even">
<td><p>VideoPortCount</p></td>
<td><p>8034</p></td>
<td><p>--</p></td>
<td><p>--</p></td>
</tr>
<tr class="odd">
<td><p>ApplicationSharingPortStart</p></td>
<td><p>49152</p></td>
<td><p>--</p></td>
<td><p>--</p></td>
</tr>
<tr class="even">
<td><p>ApplicationSharingPortCount</p></td>
<td><p>16383</p></td>
<td><p>--</p></td>
<td><p>--</p></td>
</tr>
</tbody>
</table>

As noted previously, when configuring Skype for Business Server ports for QoS, you should ensure that: 1) audio port settings are identical across yours Conferencing, Application, and Mediation servers; and, 2) port ranges do not overlap. If you look closely at the preceding table, you will see that the port ranges are identical across the three server types. For example, the starting audio port is set to port 49152 on each server type, and the total number of ports reserved for audio in each server is also identical: 8348. However, the port ranges overlap: audio ports start at port 49152, but so do the ports set aside for application sharing. In order to make optimal use of Quality of Service, application sharing should be reconfigured to use a unique port range. For example, you could configure application sharing to start at port 40803 and to use 8348 ports. (Why 8348 ports? If you add those values together -- 40803 + 8348 -- that means that application sharing will use ports 40803 through port 49150. Because audio ports do not begin until port 49152, you will no longer have any overlapping port ranges.)

After you have selected the new port range for application sharing, you can make your change by using the Set-CsConferencingServer cmdlet. This change does not need to be made on your Application servers or on your Mediation servers, because these servers do not handle application sharing traffic. You only need to change port values on these servers if you decide to reassign the ports used for audio traffic.

To modify the port values for application sharing on a single Conferencing server, run a command similar to this from within the Skype for Business Server Management Shell:

    Set-CsConferenceServer -Identity ConferencingServer:atl-cs-001.litwareinc.com -AppSharingPortStart 40803 -AppSharingPortCount 8348

If you want to make these changes on all your Conferencing servers, you can run this command instead:

    Get-CsService -ConferencingServer | ForEach-Object {Set-CsConferenceServer -Identity $_.Identity -AppSharingPortStart 40803 -AppSharingPortCount 8348}

After changing port settings, you should stop and then restart each service affected by the changes.

It is not mandatory that your Conferencing servers, Application servers, and Mediation servers share the exact same port range; the only true requirement is that you set aside unique port ranges on all your servers. However, administration will typically be easier if you use the same set of ports on all your servers.

## Configure a Quality of Service policy in Skype for Business Server for your Conferencing, Application, and Mediation servers

Configuring port ranges facilitates the use of Quality of Service by ensuring that all traffic of a specified type (for example, all audio traffic) travels through the same set of ports. This makes it easy for the system to identify and mark a given packet: if port 49152 is reserved for audio traffic, then any packet traveling through port 49152 can be marked with a DSCP code that indicates that this is an audio packet. In turn, this enables routers to identify the packet as an audio packet, and give it higher priority than unmarked packets (such as packets used to copy a file from one server to another).

However, simply restricting a set of ports to a specific type of traffic does not result in packets traveling through those ports being marked with the appropriate DSCP code. In addition to defining port ranges, you must also create Quality of Service policies that specify the DSCP code to be associated with each port range. For Skype for Business Server, that typically means creating two policies: one for audio and one for video.

Quality of Service policies are most easily created, and managed, by using Group Policy. (These same policies can also be created by using local security policies. However, that requires you to repeat the same procedure on each and every computer.) Your initial set of QoS policies (one for audio and one for video) should be applied only to Skype for Business Server computers running the Conferencing server, Application server, and/or Mediation server services. If all of these computers are located in the same Active Directory OU, you can simply assign the new Group Policy object (GPO) to that OU. Alternatively, you can take other steps to target the new policy to the specified computers; for example, you can place the appropriate computers in a security group, then use Group Policy security filtering to apply the GPO just to that security group.

To create a Quality of Service policy for managing audio, log on to a computer where Group Policy Management has been installed. Open Group Policy Management (click **Start**, point to **Administrative Tools**, and then click **Group Policy Management**) and then complete the following procedure:

1.  In Group Policy Management, locate the container where the new policy should be created. For example, if all your Skype for Business Server computers are located in an OU named Skype for Business Server, then the new policy should be created in the Skype for Business Server OU.

2.  Right-click the appropriate container, and then click **Create a GPO in this domain, and Link it here**.

3.  In the **New GPO** dialog box, type a name for the new Group Policy object in the **Name** box (for example, **Skype for Business Server QoS**), and then click **OK**.

4.  Right-click the newly-created policy, and then click **Edit**.

5.  In the Group Policy Management Editor, expand **Computer Configuration**, expand **Policies**, expand **Windows Settings**, right-click **Policy-based QoS**, and then click **Create new policy**.

6.  In the **Policy-based QoS** dialog box, on the opening page, type a name for the new policy (e.g., **Skype for Business Server QoS**) in the **Name** box. Select **Specify DSCP Value** and set the value to **46**. Leave **Specify Outbound Throttle Rate** unselected, and then click **Next**.

7.  On the next page, make sure that **All applications** is selected, and then click **Next**. This simply ensures that all applications will match packets from the specified port range with the specified DSCP code.

8.  On the third page, make sure that both **Any source IP address and Any destination IP address** are selected, and then click **Next**. These two settings ensure that packets will be managed regardless of which computer (IP address) sent those packets and which computer (IP address) will receive those packets.

9.  On page four, select **TCP and UDP** from the **Select the protocol this QoS policy applies to** dropdown list. TCP (Transmission Control Protocol) and UDP (User Datagram Protocol) are the two networking protocols most-commonly used by Skype for Business Server and its client applications.

10. Under the heading **Specify the source port number**, select **From this source port or range**. In the accompanying text box, type the port range reserved for audio transmissions. For example, if you reserved ports 49152 through ports 57500 for audio traffic, enter the port range using this format: **49152:57500**. Click **Finish**.

> [!NOTE]  
> The DSCP value of 46 is somewhat arbitrary: although DSCP 46 is often used for marking audio packets, you do not have to use DSCP 46 for audio communications. If you have already implemented QoS and you are using a different DSCP code for audio (for example, DSCP 40), you should configure your Quality of Service policy to use that same code (i.e., 40 for audio). If you are just now implementing Quality of Service, then it is recommended that you use DSCP 46 for audio, simply because that value is commonly used to mark audio packets.

After you have created the QoS policy for audio traffic, you should then create a second policy for video traffic (and, optionally, a third policy for managing application sharing traffic). To create a policy for video, follow the same basic procedure you followed when creating the audio policy, making these substitutions:

  - Use a different (and unique) policy name (for example, **Skype for Business Server Video**).

  - Set the DSCP value to **34** instead of 46. (Note that you do not have to use a DSCP value of 34. The only requirement is that you use a different DSCP value for video than you used for audio.)

  - Use the previously configured port range for video traffic. For example, if you have reserved ports 57501 through 65535 for video, set the port range to this: **57501:65535**.

If you decide to create a policy for managing application sharing traffic, you must create a third policy, making the following substitutions:

  - Use a different (and unique) policy name (for example, **Skype for Business Server Application Sharing**).

  - Set the DSCP value to **24** instead of 46. (Again, you do not have to use a DSCP value of 24. The only requirement is that you use a different DSCP value for application sharing than you used for audio or for video.)

  - Use the previously configured port range for video traffic. For example, if you have reserved ports 40803 through 49151 for application sharing, set the port range to this: **40803:49151**.

The new policies you have created will not take effect until Group Policy has been refreshed on your Skype for Business Server computers. Although Group Policy periodically refreshes on its own, you can force an immediate refresh by running the following command on each computer where Group Policy needs to be refreshed:

    Gpupdate.exe /force

This command can be run from within the Skype for Business Server Management Shell or from any command window that is running under administrator credentials. To run a command window under administrator credentials, click **Start**, right-click **Command Prompt**, and then click **Run as administrator**.

To verify that the new QoS policies have been applied, do the following:

1.  On a Skype for Business Server computer, click **Start**, and then click **Run**.

2.  In the **Run** dialog box, type **regedit**, and then press ENTER.

3.  In Registry Editor, expand **Computer**, expand **HKEY\_LOCAL\_MACHINE**, expand **SOFTWARE**, expand **Policies**, expand **Microsoft**, expand **Windows**, and then click **QoS**. Under **QoS** you should see registry keys for each of the QoS policies you just created. For example, if you created two new policies (one named Skype for Business Server Audio QoS and the other named Skype for Business Server Video QoS), you should see registry entries for Skype for Business Server Audio QoS and Skype for Business Server Video QoS.

To help ensure that network packets are marked with the appropriate DSCP value, you should also create a new registry entry on each computer by completing the following procedure:

1.  Click **Start**, and then click **Run**.

2.  In the **Run** dialog box, type **regedit**, and then press ENTER.

3.  In the Registry Editor, expand **HKEY\_LOCAL\_MACHINE**, expand **SYSTEM**, expand **CurrentControlSet**, expand **services**, and then expand **Tcpip**.

4.  Right-click **Tcpip**, point to **New**, and then click **Key**. After the new registry key is created, type **QoS**, and then press ENTER to rename the key.

5.  Right-click **QoS**, point to **New**, and then click **String Value**. After the new registry value is created, type **Do not use NLA**, and then press ENTER to rename the value.

6.  Double-click **Do not use NLA**. In the **Edit String** dialog box, type **1** in the **Value data** box, and then click **OK**.

7.  Close the Registry Editor and reboot your computer.
