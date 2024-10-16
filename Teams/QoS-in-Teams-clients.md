---
title: Implement Quality of Service (QoS) in Microsoft Teams desktop clients on Windows
ms.author: crowe
author: CarolynRowe
manager: pamgreen
ms.topic: article
ms.service: msteams
ms.reviewer: siunies
ms.date: 09/27/2023
audience: admin
description: Learn how to use Quality of Service (QoS) to optimize network traffic for the Microsoft Teams desktop client.
ms.localizationpriority: medium
search.appverid: MET150
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
appliesto: 
  - Classic Microsoft Teams
  - New Microsoft Teams
ms.custom: 
  - seo-marvel-mar2020
  - seo-marvel-apr2020
---

# Implement Quality of Service (QoS) in Microsoft Teams desktop clients on Windows

There are multiple methods you can use to set the Differentiated Services Code Point (DSCP) markings for Teams desktop clients running on Windows. This article assumes you're using the default source port ranges as defined in [Implement QoS in Teams](qos-in-teams.md#step-3-choose-initial-port-ranges-for-each-media-type). If you've customized the source port ranges for your environment, you'll need to adjust the following guidance to reflect the source ports being used.

## Configuring DSCP markings using Intune

Microsoft Intune (and other Mobile Device Management (MDM) providers) use the eXtensible Markup Language (XML)-based Open Mobile Alliance-Device Management (OMA-DM) protocol for policy settings management. Windows implements OMA-DM XML via Configuration Service Providers (CSPs) - and for Quality of Service (QoS), the [NetworkQoSPolicy](/windows/client-management/mdm/networkqospolicy-csp) CSP is leveraged.

To create the device configuration policy for QoS for Teams clients on Windows:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** > **Configuration** > **Create**.
3. Enter the following properties:

    - **Platform**: Select **Windows 10 and later**.
    - **Profile type**: Select **Templates** and then select **Custom**.

4. Select **Create**.
5. In **Basics**, enter the following properties:

    - **Name**: Enter a descriptive name for the profile. Name your profiles so you can easily identify them later. For example, **Windows: Teams QoS DSCP Markings**
    - **Description**: Enter a description for the profile. This setting is optional, but recommended.

6. Select **Next**.

7. In **Configuration settings**, select **Add**. Use the following tables to fill in the required OMA-URI settings (repeat for each row in the table). 

    **For the new Teams client, using the following table.**

    *Table 1. Intune OMA-URI Settings for new Teams*

    |**Name**|**Description**|**OMA-URI**|**Data Type**|**Value** |
    |:-----:|:-----:|:-----:|:-----:|:-----:|
    |Teams Audio: Application|New Teams executable name.|./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsAudio/AppPathNameMatchCondition|String|ms-teams.exe|
    |Teams Audio: Ports|Audio source ports used by the Teams client.|./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsAudio/SourcePortMatchCondition|String|50000-50019|
    |Teams Audio: DSCP Marking|Marking applied for audio (EF46)|./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsAudio/DSCPAction|Integer|46|
    |Teams Video: Application|New Teams executable name.|./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsVideo/AppPathNameMatchCondition|String|ms-teams.exe|
    |Teams Video: Ports|Video source ports used by the Teams client.|./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsVideo/SourcePortMatchCondition|String|50020-50039|
    |Teams Video: DSCP Marking|Marking applied for video (AF41)|./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsVideo/DSCPAction|Integer|34|
    |Teams Screenshare: Application|New Teams executable name.|./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsScreenshare/AppPathNameMatchCondition|String|ms-teams.exe|
    |Teams Screenshare: Ports|Screen sharing ports used by the Teams client.|./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsScreenshare/SourcePortMatchCondition|String|50040-50059|
    |Teams Screenshare: DSCP Marking|Marking applied for screen sharing (AF21)|./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsScreenshare/DSCPAction|Integer|18|
    |Teams Calling-Meeting Signaling: Application|New Teams executable name.|./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsCMSignaling/AppPathNameMatchCondition|String|ms-teams.exe|
    |Teams Calling-Meeting Signaling: Ports|Calling and Meeting Signaling source ports used by the Teams client.|./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsCMSignaling/SourcePortMatchCondition|String|50070-50089|
    |Teams Calling-Meeting Signaling: DSCP Marking|Marking applied for calling and meeting signaling (EF46)|./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsCMSignaling/DSCPAction|Integer|46|

    **For the classic Teams client, using the following table.**
    
    *Table 2. Intune OMA-URI Settings for classic Teams*

    |**Name**|**Description**|**OMA-URI**|**Data Type**|**Value**|
    |:-----:|:-----:|:-----:|:-----:|:-----:|
    |Classic Teams Audio: Application|Classic Teams executable name.|./Device/Vendor/MSFT/NetworkQoSPolicy/ClassicTeamsAudio/AppPathNameMatchCondition|String|teams.exe|
    |Classic Teams Audio: Ports|Audio source ports used by the Teams client.|./Device/Vendor/MSFT/NetworkQoSPolicy/ClassicTeamsAudio/SourcePortMatchCondition|String|50000-50019|
    |Classic Teams Audio: DSCP Marking|Marking applied for audio (EF46)|./Device/Vendor/MSFT/NetworkQoSPolicy/ClassicTeamsAudio/DSCPAction|Integer|46|
    |Classic Teams Video: Application|Classic Teams executable name.|./Device/Vendor/MSFT/NetworkQoSPolicy/ClassicTeamsVideo/AppPathNameMatchCondition|String|teams.exe|
    |Classic Teams Video: Ports|Video source ports used by the Teams client.|./Device/Vendor/MSFT/NetworkQoSPolicy/ClassicTeamsVideo/SourcePortMatchCondition|String|50020-50039|
    |Classic Teams Video: DSCP Marking|Marking applied for video (AF41)|./Device/Vendor/MSFT/NetworkQoSPolicy/ClassicTeamsVideo/DSCPAction|Integer|34|
    |Classic Teams Screenshare: Application|Classic Teams executable name.|./Device/Vendor/MSFT/NetworkQoSPolicy/ClassicTeamsScreenshare/AppPathNameMatchCondition|String|teams.exe|
    |Classic Teams Screenshare: Ports|Screen sharing ports used by the Teams client.|./Device/Vendor/MSFT/NetworkQoSPolicy/ClassicTeamsScreenshare/SourcePortMatchCondition|String|50040-50059|
    |Classic Teams Screenshare: DSCP Marking|Marking applied for screen sharing (AF21)|./Device/Vendor/MSFT/NetworkQoSPolicy/ClassicTeamsScreenshare/DSCPAction|Integer|18|
    |Classic Teams Calling-Meeting Signaling: Application|New Teams executable name.|./Device/Vendor/MSFT/NetworkQoSPolicy/ClassicTeamsCMSignaling/AppPathNameMatchCondition|String|teams.exe|
    |Classic Teams Calling-Meeting Signaling: Ports|Calling and Meeting Signaling source ports used by the Teams client.|./Device/Vendor/MSFT/NetworkQoSPolicy/ClassicTeamsCMSignaling/SourcePortMatchCondition|String|50070-50089|
    |Classic Teams Calling-Meeting Signaling: DSCP Marking|Marking applied for calling and meeting signaling (EF46)|./Device/Vendor/MSFT/NetworkQoSPolicy/ClassicTeamsCMSignaling/DSCPAction|Integer|46|

9. Select **Next**
10. In **Assignments**, select the group or groups that you want to target with this policy. The group membership must include Windows devices (and not user accounts) as this is a device policy.
11. Select **Next**
12. In **Applicability Rules**, define and desired rules (optional).
13. Select **Next**.
14. In **Review + create**, review the settings for accuracy, and when finished select **Create**.


## Configuring DSCP markings using PowerShell commands

Endpoint DSCP markings can be set in PowerShell using the [New-NetQosPolicy](/powershell/module/netqos/new-netqospolicy) command. In the examples below, there are two commands each for audio, video, and application sharing. The following commands show creating policies for both the new Teams client (ms-teams.exe) and classic Teams client (Teams.exe). You can combine these commands into a PowerShell script and distribute to your desired endpoints. 

**Set QoS for audio**

```powershell
new-NetQosPolicy -Name "Teams Audio" -AppPathNameMatchCondition "ms-teams.exe" -IPProtocolMatchCondition Both -IPSrcPortStartMatchCondition 50000 -IPSrcPortEndMatchCondition 50019 -DSCPAction 46 -NetworkProfile All
new-NetQosPolicy -Name "Classic Teams Audio" -AppPathNameMatchCondition "Teams.exe" -IPProtocolMatchCondition Both -IPSrcPortStartMatchCondition 50000 -IPSrcPortEndMatchCondition 50019 -DSCPAction 46 -NetworkProfile All

```

**Set QoS for video**

```powershell
new-NetQosPolicy -Name "Teams Video" -AppPathNameMatchCondition "ms-teams.exe" -IPProtocolMatchCondition Both -IPSrcPortStartMatchCondition 50020 -IPSrcPortEndMatchCondition 50039 -DSCPAction 34 -NetworkProfile All
new-NetQosPolicy -Name "Classic Teams Video" -AppPathNameMatchCondition "Teams.exe" -IPProtocolMatchCondition Both -IPSrcPortStartMatchCondition 50020 -IPSrcPortEndMatchCondition 50039 -DSCPAction 34 -NetworkProfile All
```

**Set QoS for sharing**

```powershell
new-NetQosPolicy -Name "Teams Sharing" -AppPathNameMatchCondition "ms-teams.exe" -IPProtocolMatchCondition Both -IPSrcPortStartMatchCondition 50040 -IPSrcPortEndMatchCondition 50059 -DSCPAction 18 -NetworkProfile All
new-NetQosPolicy -Name "Classic Teams Sharing" -AppPathNameMatchCondition "Teams.exe" -IPProtocolMatchCondition Both -IPSrcPortStartMatchCondition 50040 -IPSrcPortEndMatchCondition 50059 -DSCPAction 18 -NetworkProfile All
```

**Set QoS for calling and meeting signaling**

```powershell
new-NetQosPolicy -Name "Teams Calling-Meeting Signaling" -AppPathNameMatchCondition "ms-teams.exe" -IPProtocolMatchCondition UDP -IPSrcPortStartMatchCondition 50070 -IPSrcPortEndMatchCondition 50089 -DSCPAction 46 -NetworkProfile All
new-NetQosPolicy -Name "Classic Teams Calling-Meeting Signaling" -AppPathNameMatchCondition "Teams.exe" -IPProtocolMatchCondition UDP -IPSrcPortStartMatchCondition 50070 -IPSrcPortEndMatchCondition 50089 -DSCPAction 46 -NetworkProfile All

```

## Configuring DSCP markings using Group Policy

You can create policy-based QoS settings within a Group Policy object (GPO). When creating the policies, you'll need to create a separate policy for audio, video, and application sharing.

To create a QoS audio policy for domain-joined Windows computers, first log on to a computer on which Group Policy Management has been installed. Open Group Policy Management (click Start, point to Administrative Tools, and then click Group Policy Management), and then complete the following steps:

1. In Group Policy Management, locate the container where the new policy should be created. For example, if all your client computers are located in an OU named **Clients**, create the new policy in the Clients OU.
2. Right-click the appropriate container, and then select **Create a GPO in this domain, and Link it here**.
3. In the **New GPO** dialog box, type a name for the new Group Policy object in the **Name** box, and then select **OK**.
4. Right-click the newly created policy, and then select **Edit**.
5. In the Group Policy Management Editor, expand **Computer Configuration**, expand **Windows Settings**, right-click **Policy-based QoS**, and then select **Create new policy**.
6. In the **Policy-based QoS** dialog box, on the opening page, type a name for the new policy in the **Name** box. Select **Specify DSCP Value**, and set the value to **46**. Leave **Specify Outbound Throttle Rate** unselected, and then select **Next**.
7. On the next page, select **Only applications with this executable name** and enter the following name:
   
   - For new Teams enter **ms-teams.exe**
   - For classic Teams enter **teams.exe**
  
8. Click **Next**. This setting instructs the policy to prioritize only matching traffic from the Teams client.
9. On the third page, make sure that both **Any source IP address** and **Any destination IP address** are selected, and then select **Next**. These two settings ensure that packets will be managed regardless of which computer (IP address) sent the packets and which computer (IP address) will receive the packets.
10. On page four, select **TCP and UDP** from the **Select the protocol this QoS policy applies to** drop-down list. TCP (Transmission Control Protocol) and UDP (User Datagram Protocol) are the two networking protocols most commonly used.
11. Under the heading **Specify the source port number**, select **From this source port or range**. In the accompanying text box, type the port range reserved for audio transmissions. For example, if you reserved ports 50000 through ports 50019 for audio traffic, enter the port range using this format: **50000:50019**. Select **Finish**.
12. Repeat steps 5-10 to create policies for Video, Application/Desktop Sharing and Calling and Meeting Signaling, substituting the appropriate values in steps 6 and 10.

The new policies you've created won't take effect until Group Policy has been refreshed on your client computers. Although Group Policy periodically refreshes on its own, you can force an immediate refresh by following these steps:

1. On each computer for which you want to refresh Group Policy, open a Command Prompt as administrator (*Run as administrator*).

2. At the command prompt, enter

   ```console
   gpupdate /force
   ```

## Verify DSCP markings in the Group Policy object

To verify that the values from the Group Policy object are set, perform the following steps:

1. Open a Command Prompt as administrator (*Run as administrator*).

2. At the command prompt, enter

   ```console
   gpresult /R > gp.txt
   ```

   This will generate a report of applied GPOs and send it to a text file named *gp.txt*.

   For a more readable HTML report named *gp.html*, enter the following command:

   ```console
   gpresult /H gp.html
   ```

3. In the generated file, look for the heading **Applied Group Policy Objects**, and verify that the names of the Group Policy objects created earlier are in the list of applied policies.

4. Open the Registry Editor, and go to

   HKEY\_LOCAL\_MACHINE\\Software\\Policies\\Microsoft\\Windows\\QoS

   Verify the values for the registry entries listed in Table 2.

   *Table 2. Values for Windows registry entries for QoS*

   |          Name          |  Type  |    Data     |
   |         :---:          | :---:  |    :---:    |
   |    Application Name    | REG_SZ |  ms-teams.exe  |
   |       DSCP Value       | REG_SZ |     46      |
   |        Local IP        | REG_SZ |     \*      |
   | Local IP Prefix Length | REG_SZ |     \*      |
   |       Local Port       | REG_SZ | 50000-50019 |
   |        Protocol        | REG_SZ |     \*      |
   |       Remote IP        | REG_SZ |     \*      |
   |    Remote IP Prefix    | REG_SZ |     \*      |
   |      Remote Port       | REG_SZ |     \*      |
   |     Throttle Rate      | REG_SZ |     -1      |

5. Verify that the value for the Application Name entry is correct for the client you're using, and verify that both the DSCP Value and Local Port entries reflect the settings in the Group Policy object.


## Related topics

[Implement Quality of Service (QoS) in Teams](QoS-in-Teams.md)
