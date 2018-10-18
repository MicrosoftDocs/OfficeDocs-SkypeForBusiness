﻿---
title: 'Configuring a Quality of Service policy for your A/V Edge Servers'
TOCTitle: Configuring a Quality of Service policy for your A/V Edge Servers
ms:assetid: 119ee1f5-45b9-40ba-98e5-c694dd2fc5c2
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204681(v=OCS.15)
ms:contentKeyID: 48183444
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring a Quality of Service policy for your A/V Edge Servers in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-19_

In addition to creating QoS policies for your Conferencing, Application, and Mediation servers, you must also create both audio and video policies for the internal side of your A/V Edge servers. However, the policies used on your Edge servers are different from the policies used on your Conferencing, Application, and Mediation servers. For the Conferencing, Application, and Mediation servers you specified a source port range; with Edge servers, you need to specify a destination port range. Because of that you cannot simply apply the Conferencing, Application, and Mediation server QoS policies to your Edge servers: these policies simply won't work. Instead, you must create new policies and apply those policies to your Edge servers only.

The following procedure describes the process for creating Active Directory Group Policy objects that can be used to manage Quality of Service on Edge Servers. Of course, it's possible that your Edge servers are stand-alone servers that do not have Active Directory accounts. If that's the case, you can use local Group Policy instead of Active Directory Group Policy: the only difference is that you must create these local policies using the Local Group Policy Editor, and must individually create the same set of policies on each Edge Server. To start the Local Group Policy Editor on an Edge server do the following:

1.  Click **Start** and then click **Run**.

2.  In the **Run** dialog box, type **gpedit.msc** and then press ENTER.

If you are creating Active Directory-based policies, then you should log on to a computer where Group Policy Management has been installed. In that case, open Group Policy Management (click **Start**, point to **Administrative Tools**, and then click **Group Policy Management**) and then complete the following steps:

1.  In Group Policy Management, locate the container where the new policy should be created. For example, if all your Lync Server computers are located in an OU named Lync Server then the new policy should be created in the Lync Server OU.

2.  Right-click the appropriate container and then click **Create a GPO in this domain, and Link it here**.

3.  In the **New GPO** dialog box, type a name for the new Group Policy object in the **Name** box (for example, **Lync Server Audio**) and then click **OK**.

4.  Right-click the newly-created policy and then click **Edit**.

From here the process is identical regardless of whether you are creating an Active Directory policy or a local policy:

1.  In the Group Policy Management Editor or the Local Group Policy Editor, expand **Computer Configuration**, expand **Policies**, expand **Windows Settings**, right-click **Policy-based QoS**, and then click **Create new policy**.

2.  In the **Policy-based QoS** dialog box, on the opening page, type a name for the new policy (e.g., **Lync Server Audio**) in the **Name** box. Select **Specify DSCP Value** and set the value to **46**. Leave **Specify Outbound Throttle Rate** unselected, and then click **Next**.

3.  On the next page, make sure that **All applications** is selected and then click **Next**. This setting instructs the network to look for all packets with a DSCP marking of 46, not just packets created by a specific application.

4.  On the third page, make sure that both **Any source IP address** and **Any destination IP address** are selected and then click **Next**. These two settings ensure that packets will be managed regardless of which computer (IP address) sent those packets and which computer (IP address) will receive those packets.

5.  On page four, select **TCP and UDP** from the **Select the protocol this QoS policy applies to** dropdown list. TCP (Transmission Control Protocol) and UDP (User Datagram Protocol) are the two networking protocols most-commonly used by Lync Server and its client applications.

6.  Under the heading **Specify the destination port number**, select **From this destination port or range**. In the accompanying text box, type the port range reserved for audio transmissions. For example, if you reserved ports 49152 through ports 57500 for audio traffic then enter the port range using this format: **49152:57500**. Click **Finish**.

After you have created the QoS policy for audio traffic you should create a second policy for video traffic. To create a policy for video, follow the same basic procedure you followed when creating the audio policy, making these substitutions:

  - Use a different (and unique) policy name (for example, **Lync Server Video**).

  - Set the DSCP value to **34** instead of 46. (Note that you do not have to use a DSCP value of 34. The only requirement is that you use a different DSCP value for video than you used for audio.)

  - Use the previously-configured port range for video traffic. For example, if you have reserved ports 57501 through 65535 for video, then set the port range to this: **57501:65535**. Again, this should be configured as the destination port range.

If you decide to create a policy for managing application sharing traffic you must create a third policy, making the following substitutions:

  - Use a different (and unique) policy name (for example, **Lync Server Application Sharing**).

  - Set the DSCP value to **24** instead of 46. (Again, you do not have to use a DSCP value of 24. The only requirement is that you use a different DSCP value for application sharing than you used for audio or for video.)

  - Use the previously-configured port range for video traffic. For example, if you have reserved ports 40803 through 49151 for application sharing, then set the port range to this: **40803:49151**.

The new policies you have created will not take effect until Group Policy has been refreshed on your Edge servers. Although Group Policy periodically refreshes on its own, you can force an immediate refresh by running the following command on each computer where Group Policy needs to be refreshed:

    Gpudate.exe /force

This command can be run from within the Lync Server or from any command window that is running under administrator credentials. To run a command window under administrator credentials, click **Start**, right-click **Command Prompt**, and then click **Run as administrator**. Note that you might need to restart the Edge server even after running Gpudate.exe.

To help ensure that network packets are marked with the appropriate DSCP value, you should also create a new registry entry on each computer by completing the following procedure:

1.  Click **Start** and then click **Run**.

2.  In the **Run** dialog box, type **regedit** and then press ENTER.

3.  In the Registry Editor, expand **HKEY\_LOCAL\_MACHINE**, expand **SYSTEM**, expand **CurrentControlSet**, expand **services**, and then expand **Tcpip**.

4.  Right-click **Tcpip**, point to **New**, and then click **Key**. After the new registry key is created, type **QoS** and then press ENTER to rename the key.

5.  Right-click **QoS**, point to **New**, and then click **String Value**. After the new registry value is created, type **Do not use NLA** and then press ENTER to rename the value.

6.  Double-click **Do no use NLA**. In the **Edit String** dialog box, type **1** in the **Value data** box and then click **OK**.

7.  Close the Registry Editor and then reboot your computer.

</div>

<span> </span>

</div>

</div>

</div>

