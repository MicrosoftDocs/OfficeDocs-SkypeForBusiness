---
title: 'Lync Server 2013: Configuring Quality of Service policies for clients running on Windows 7 or Windows 8'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configuring Quality of Service policies for clients running on Windows 7 or Windows 8
ms:assetid: efff2b98-b3fb-4183-a4f0-329a9105ce2c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205371(v=OCS.15)
ms:contentKeyID: 48185785
ms.date: 03/29/2016
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring Quality of Service policies in Lync Server 2013 for clients running on Windows 7 or Windows 8

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2016-03-29_

In addition to specifying port ranges for use by your Lync clients you must also create separate Quality of Service policies that will be applied to client computers. (The Quality of Service policies created for Conferencing, Application, and Mediation servers should not be applied to client computers.) This information applies only to computers running the Lync 2013 client and either Windows 7 or Windows 8.

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


To create a Quality of Service audio policy for Windows 7 or Windows 8 computers, first log on to a computer where Group Policy Management has been installed. Open Group Policy Management (click **Start**, point to **Administrative Tools**, and then click **Group Policy Management**) and then complete the following procedure:

1.  In Group Policy Management, locate the container where the new policy should be created. For example, if all your client computers are located in an OU named Clients then the new policy should be created in the Client OU.

2.  Right-click the appropriate container and then click **Create a GPO in this domain, and Link it here**.

3.  In the **New GPO** dialog box, type a name for the new Group Policy object in the **Name** box (for example, **Lync Audio**) and then click **OK**.

4.  Right-click the newly-created policy and then click **Edit**.

5.  In the Group Policy Management Editor, expand **Computer Configuration**, expand **Policies**, expand **Windows Settings**, right-click **Policy-based QoS**, and then click **Create new policy**.

6.  In the **Policy-based QoS** dialog box, on the opening page, type a name for the new policy (e.g., **Lync Audio**) in the **Name** box. Select **Specify DSCP Value** and set the value to **46**. Leave **Specify Outbound Throttle Rate** unselected, and then click **Next**.

7.  On the next page, make sure that **All applications** is selected and then click **Next**. This setting instructs the network to look for all packets with a DSCP marking of 46, not just packets created by a specific application.

8.  On the third page, make sure that both **Any source IP address** and **Any destination IP address** are selected and then click **Next**. These two settings ensure that packets will be managed regardless of which computer (IP address) sent those packets and which computer (IP address) will receive those packets.

9.  On page four, select **TCP and UDP** from the **Select the protocol this QoS policy applies to** dropdown list. TCP (Transmission Control Protocol) and UDP (User Datagram Protocol) are the two networking protocols most-commonly used by Lync Server and its client applications.

10. Under the heading **Specify the source port number**, select **From this source port or range**. In the accompanying text box, type the port range reserved for audio transmissions. For example, if you reserved ports 50020 through ports 50039 for audio traffic enter the port range using this format: **50020:50039**. Click **Finish**.

After you have created the QoS policy for audio you should then create a second policy for video. To create a policy for video, follow the same basic procedure you followed when creating the audio policy, making these substitutions:

  - Use a different (and unique) policy name (for example, **Lync Video**).

  - Set the DSCP value to **34** instead of 46. (As noted previously, you do not have to use the DSCP value 34; you simply must assign a different DSCP value than the one used for audio.)

  - Use the previously-configured port range for video traffic. For example, if you have reserved ports 58000 through 58019 for video, then set the port range to this: **58000:58019**.

If you decide to create a policy for managing application sharing traffic make these substitutions:

  - Use a different (and unique) policy name (for example, **Lync Server Application Sharing**).

  - Set the DSCP value to **24** instead of 46. (Again, this value does not have to be 24; it simply must be different than the DSCP values used for audio and for video.)

  - Use the previously-configured port range for video traffic. For example, if you have reserved ports 42000 through 42019 for application sharing, then set the port range to this: **42000:42019**.

For a file transfer policy:

  - Use a different (and unique) policy name (for example, **Lync Server File Transfers**).

  - Set the DSCP value to **14**. (Again, this value does not have to be 14; it simply must be a unique DSCP code.)

  - Use the previously-configured port range for application. For example, if you have reserved ports 42020 through 42039 for application sharing, then set the port range to this: **42020:42039**.

The new policies you have created will not take effect until Group Policy has been refreshed on your client computers. Although Group Policy periodically refreshes on its own, you can force an immediate refresh by running the following command on each computer where Group Policy needs to be refreshed:

    Gpudate.exe /force

This command can be run from any command window that is running under administrator credentials. To run a command window under administrator credentials, click **Start**, right-click **Command Prompt**, and then click **Run as administrator**.

Keep in mind that these policies should be targeted towards your client computers. They should not be applied to servers running Lync Server.

To help ensure that network packets are marked with the appropriate DSCP value, you should also create a new registry entry on each computer by completing the following procedure:

1.  Click **Start** and then click **Run**.

2.  In the **Run** dialog box, type **regedit** and then press ENTER.

3.  In the Registry Editor, expand **HKEY\_LOCAL\_MACHINE**, expand **SYSTEM**, expand **CurrentControlSet**, expand **services**, and then expand **Tcpip**.

4.  Right-click **Tcpip**, point to **New**, and then click **Key**. After the new registry key is created, type **QoS** and then press ENTER to rename the key.

5.  Right-click **QoS**, point to **New**, and then click **String Value**. After the new registry value is created, type **Do not use NLA** and then press ENTER to rename the value.

6.  Double-click **Do not use NLA**. In the **Edit String** dialog box, type **1** in the **Value data** box and then click **OK**.

7.  Close the Registry Editor and then reboot your computer.

<div>

## Configuring Quality of Service on Computers with Multiple Network Adapters

If you have a computer that has multiple network adapters you might occasionally run into issues where DSCP values are shown as 0x00 rather than the configured value. This will typically occur on computers where one or more of the network adapters are not able to access your Active Directory domain (for example, if these adapters are used for a private network). In cases like that, DSCP values will be tagged for the adapters that can access the domain, but will not be tagged for adapters that cannot access the domain.

If you would like to tag DSCP values for all the network adapters in a computer, including adapters that do not have access to your domain, then you will need to add and configure a value to the registry. That can be done by completing the following procedure:

1.  Click **Start** and then click **Run**.

2.  In the **Run** dialog box, type **regedit** and then press ENTER.

3.  In the Registry Editor, expand **HKEY\_LOCAL\_MACHINE**, expand **SYSTEM**, expand **CurrentControlSet**, expand **services**, and then expand **Tcpip**.

4.  If you do not see a registry key labeled **QoS** then right-click **Tcpip**, point to **New**, and then click **Key**. After the new key is created, type **QoS** and then press ENTER to rename the key.

5.  Right-click **QoS**, point to **New**, and then click **String Value**. After the new registry value is created, type **Do not use NLA** and then press ENTER to rename the value.

6.  Double-click **Do not use NLA**. In the **Edit String** dialog box, type **1** in the **Value data** box and then click **OK**.

After creating and configuring the new registry value you will need to reboot your computer in order for the changes to take effect.

</div>

</div>

<span> </span>

</div>

</div>

</div>

