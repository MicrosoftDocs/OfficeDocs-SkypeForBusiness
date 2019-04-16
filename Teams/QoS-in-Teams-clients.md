---
title: Implement Quality of Service in Microsoft Teams clients
author: jambirk
ms.author: jambirk
manager: Serdars
ms.date: 2/17/2019
ms.topic: article
ms.service: msteams
ms.reviewer: rowille
description: Implement Quality of Service (QoS) for  Microsoft Teams clients.
localization_priority: Normal
search.appverid: MET150
MS.collection: 
- Teams_ITAdmin_PracticalGuidance 
- M365-voice 
appliesto:
- Microsoft Teams
---

# Set QoS on Windows clients

You can use policy-based QoS within Group Policy to set the source port range for the predefined DSCP value in the Teams client. The port ranges specified in the following table are a starting point to create a policy for each workload.

_Recommended initial port ranges_

Media traffic type| Client source port range |Protocol|DSCP value|DSCP class|
|:--- |:--- |:--- |:--- |:--- |
|Audio| 50,000–50,019|TCP/UDP|46|Expedited Forwarding (EF)|
|Video| 50,020–50,039|TCP/UDP|34|Assured Forwarding (AF41)|
|Application/Screen Sharing| 50,040–50,059|TCP/UDP|18|Assured Forwarding (AF21)|
| | | | |

Wherever possible, configure policy-based QoS settings within a Group Policy object. The following steps are very similar to  [Configuring port ranges and a Quality of Service policy for your clients on Skype for Business Server](https://docs.microsoft.com/SkypeForBusiness/manage/network-management/qos/configuring-port-ranges-for-your-skype-clients#configure-quality-of-service-policies-for-clients-running-on-windows-10), which has some additional details that may not be necessary.

To create a QoS audio policy for domain-joined Windows 10 computers, first log on to a computer on which Group Policy Management has been installed. Open Group Policy Management (click Start, point to Administrative Tools, and then click Group Policy Management), and then complete the following steps:

1. In Group Policy Management, locate the container where the new policy should be created. For example, if all your client computers are located in an OU named **Clients**, the new policy should be created in the Client OU.

2. Right-click the appropriate container, and then click **Create a GPO in this domain, and Link it here**.

3. In the **New GPO** dialog box, type a name for the new Group Policy object in the **Name** box, and then click **OK**.

4. Right-click the newly created policy, and then click **Edit**.

5. In the Group Policy Management Editor, expand **Computer Configuration**, expand **Windows Settings**, right-click **Policy-based QoS**, and then click **Create new policy**.

6. In the **Policy-based QoS** dialog box, on the opening page, type a name for the new policy in the **Name** box. Select **Specify DSCP Value** and set the value to **46**. Leave **Specify Outbound Throttle Rate** unselected, and then click **Next**.

7. On the next page, select **Only applications with this executable name** and enter the name **Teams.exe**, and then click **Next**. This setting instructs the policy to only prioritize matching traffic from the Teams client.

8. On the third page, make sure that both **Any source IP address** and **Any destination IP address** are selected, and then click **Next**. These two settings ensure that packets will be managed regardless of which computer (IP address) sent the packets and which computer (IP address) will receive the packets.

9. On page four, select **TCP and UDP** from the **Select the protocol this QoS policy applies to** drop-down list. TCP (Transmission Control Protocol) and UDP (User Datagram Protocol) are the two networking protocols most commonly used.

10. Under the heading **Specify the source port number**, select **From this source port or range**. In the accompanying text box, type the port range reserved for audio transmissions. For example, if you reserved ports 50000 through ports 50019 for audio traffic, enter the port range using this format: **50000:50019**. Click **Finish**.

11. Repeat steps 5-10 to create policies for Video and Application/Desktop Sharing, substituting the appropriate values in steps 6 and 10.

The new policies you’ve created won’t take effect until Group Policy has been refreshed on your client computers. Although Group Policy periodically refreshes on its own, you can force an immediate refresh by following these steps:

1. On each computer for which you want to refresh Group Policy, open a command console. Ensure that the command console is set to run as administrator.

2. At the command prompt, enter

   ``` powershell
    gpupdate.exe /force
   ```

## Verify DSCP markings in the Group Policy object

To verify that the values from the Group Policy object have been set, perform the following steps.

1. Open a command console. Ensure that the command console is set to run as administrator.

2. At the command prompt, enter:

   ``` powershell
   gpresult /R > gp.txt
   ```

   This will generate a report and send it to a text file named gp.txt. Alternatively, you can enter the following command to produce the same data in a more readable HTML report named gp.html:

   ``` powershell
   gpresult /H >gp.html
   ```

   ![Screenshot of the console window running the gpresult command.](media/Qos-in-Teams-Image3.png "Screenshot of the console window running the gpresult command.")

3. In the generated file, look for the heading **Applied Group Policy Objects** and verify that the names of the Group Policy objects created earlier are in the list of applied policies.

4. Open the Registry Editor, and go to:

   HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows\QoS\

   Verify the values for the registry entries listed in Table 4.

   _Table 4. Values for Windows registry entries for QoS_

   |          Name          |  Type  |    Data     |
   |         :---:          |:---:   |    :---:    |
   |    Application Name    | REG_SZ |  Teams.exe  |
   |       DSCP Value       | REG_SZ |     46      |
   |        Local IP        | REG_SZ |     \*      |
   | Local IP Prefix Length | REG_SZ |     \*      |
   |       Local Port       | REG_SZ | 50000-50019 |
   |        Protocol        | REG_SZ |     \*      |
   |       Remote IP        | REG_SZ |     \*      |
   |    Remote IP Prefix    | REG_SZ |     \*      |
   |      Remote Port       | REG_SZ |     \*      |
   |     Throttle Rate      | REG_SZ |     -1      |

5. Verify that the value for the Application Name entry is correct for the client you’re using, and verify that both the DSCP Value and Local Port entries reflect the settings in the Group Policy object.
