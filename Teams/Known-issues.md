---
title: Known issues for Microsoft Teams
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.topic: troubleshooting
ms.service: msteams
ms.collection: 
  - Teams_ITAdmin_GuestAccess
  - M365-collaboration
ms.reviewer: marcl
audience: admin
localization_priority: Priority
search.appverid: MET150
f1.keywords:
- NOCSH
description: Current list of known issues for the Microsoft Teams client app and admin experience.
appliesto: 
  - Microsoft Teams
---

# Known issues for Microsoft Teams

This article lists the known issues for Microsoft Teams, by feature area.

## Common issues and resolutions

> [!NOTE]
> If you need help deploying Teams to support Remote Workers (WFH) due to COVID-19, please review [Support remote workers using Teams](support-remote-work-with-teams.md). Also, you may be eligible for deployment assistance from the Microsoft 365 FastTrack Program - please visit the [FastTrack Center](https://www.microsoft.com/fasttrack) to submit a request.

### For all Teams customers

| |  |
|---------|---------|
|**New to Teams?**    |Check out [Get Started with Microsoft Teams](get-started-with-teams-quick-start.md).         |
|**Enable Teams guest access**     |Review the [Teams guest access checklist](guest-access-checklist.md) and make sure all steps are completed. See the following additional resources:<ul><li>[Understanding Guest Access in Microsoft Teams](guest-access.md)</li>[How a guest joins a Team](guest-joins.md) <li>[Setup – Microsoft Teams Guest Access Checklist](guest-access-checklist.md)</li></ul>|
|**Teams meetings and dial-in**    |Need help turning on or setting up Audio Conferencing in Teams? Has this user been recently created? If so, you'll need to wait 2 – 24 hrs **for the settings to take effect**.<br>To verify that the user is licensed for Audio Conferencing and has a default toll number:<br><ol><li>In the Microsoft 365 admin center, go to **Active users**, and then select the user in question.</li><li> Depending on the admin center version, choose either **Licenses and Apps** or click **Edit** on **Product licenses**.</li><li> Confirm that the user has licenses selected for Audio Conferencing, Microsoft Teams, and Skype for Business Online (Plan 2).</li><li>Under **Admin centers**, click **Show all**, and then click **Teams**.</li><li>In the Microsoft Teams admin center, click **Legacy portal**.</li><li>In the Skype for Business admin center, click **audio conferencing**, and then click **users**.</li><li>Select the user in question and verify the user has a default toll number.</li> </ol> For more information, see [Calling Plans for Office 365](calling-plans-for-office-365.md) or call the Microsoft Commerce Billing team for help with a licensing related questions. <br><br>Additional resources:<ul><li>[Meetings and conferencing in Microsoft Teams](deploy-meetings-microsoft-teams-landing-page.md)</li><li>[Audio Conferencing in Office 365](audio-conferencing-in-office-365.md)</li></ul>       |
|**Teams Exploratory License**     |The Microsoft Teams Exploratory experience lets users in your organization who have Azure Active Directory (AAD) and are not licensed for Teams initiate an exploratory experience of Teams. Admins can switch this feature on or off for users in their organization. The earlier [Microsoft Commercial Cloud Trial](iw-trial-teams.md) is now replaced by The Teams Exploratory experience. <br><br>Additional resources:<ul><li>[How users sign up for the Teams Exploratory experience](teams-exploratory.md#how-users-sign-up-for-the-teams-exploratory-experience)</li><li>[Manage the Teams Exploratory experience](teams-exploratory.md#manage-the-teams-exploratory-experience)</li></ul>|
|**Private channels**    |Private channels in Microsoft Teams create focused spaces for collaboration within your teams. Only the users on the team who are owners or members of the private channel can access the channel. Anyone, including guests, can be added as a member of a private channel as long as they are already members of the team.<br><br>You might want to use a private channel if you want to limit collaboration to those who have a need to know or if you want to facilitate communication between a group of people assigned to a specific project, without having to create an additional team to manage.<br><br>Additional resources:<ul><li>[How users sign up for the Teams Exploratory experience](teams-exploratory.md#how-users-sign-up-for-the-teams-exploratory-experience)</li><li>[Manage the Teams Exploratory experience](teams-exploratory.md#manage-the-teams-exploratory-experience)</li><ul>        |
|**Meeting policies**|[Meeting policies](meeting-policies-in-teams.md) are used to control the features that are available to meeting participants for meetings that are scheduled by users in your organization. After you create a policy and make your changes, you can then assign users to the policy.         |
||**Change or create a meeting policy**<br><br>To change or create a meeting policy, go to the Microsoft Teams admin center > **Meetings** > **Meeting policies**. Select a policy from the list or select **Add**. If you're creating a new policy, add a name and description. The name can't contain special characters or be longer than 64 characters. Choose your settings, and then click **Save**. For example, say you have a bunch of users and you want to limit the amount of bandwidth that their meeting would require. You would create a new custom policy named "Limited bandwidth" and disable the following settings:<br><br>Under **Audio & video**:<ul><li>Turn off Allow cloud recording.</li><li>Turn off Allow IP video.</li></ul>Under **Content sharing**:<ul><li>Disable screen sharing mode.</li><li>Turn off Allow whiteboard.</li><li>Turn off Allow shared notes.</li></ul>Then assign the policy to the users.         |
| |**Assign a meeting policy to users**<br><br><ol><li>In the left navigation of the Microsoft Teams admin center, go to **Users**, and then click the user.</li><li>Select the user by clicking to the left of the user name, and then click **Edit settings**.</li><li>Under **Meeting policy**, select the policy you want to assign, and then click **Apply**.</li></ol>To assign a policy to multiple users at a time, see [Edit Teams user settings in bulk](edit-user-settings-in-bulk.md). Or you can do the following:<ol><li>In the left navigation of the Microsoft Teams admin center, go to **Meetings > Meeting policies**.</li><li>Select the policy by clicking to the left of the policy name.</li><li>Select **Manage users**.</li><li>In the **Manage users** pane, search for the user by display name or by user name, select the name, and then click **Add**. Repeat this step for each user that you want to add.</li><li>After you finish adding users, click **Save**.</li>         |
|**Troubleshoot a missing dial pad**     |Do the following: <ul><li>Make sure the user has been assigned a [Teams license](assign-teams-licenses.md).</li><li>Make sure the user has a [Calling Plan](calling-plan-landing-page.md) assigned.</li><li>Enable the user for [Enterprise Voice](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/enable-users-for-enterprise-voice-online-and-phone-system-voicemail#to-enable-your-users-for-phone-system-in-office-365-voice-and-voicemail).</li></ul>      |
|**Troubleshoot Teams sign-in**   |First, make sure the [Microsoft Teams service is healthy](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/servicehealth). Then check for any common error codes and review [Why am I having trouble signing in to Microsoft Teams?](https://support.office.com/article/a02f683b-61a3-4008-9447-ee60c5593b0f)  You may also need to review [Identity models and authentication in Microsoft Teams](identify-models-authentication.md).         |

### For Education customers

|||
|---------|---------|
|Your users are seeing a "You're missing out!" message.   |Be sure to [Enable Microsoft Teams for your school](https://docs.microsoft.com/microsoft-365/education/intune-edu-trial/enable-microsoft-teams). In EDU tenants, Teams isn't enabled by default; you'll have to turn it on first. <br><br>Next, review [Remote teaching and learning in Office 365 Education](https://support.office.com/article/remote-teaching-and-learning-in-office-365-education-f651ccae-7b65-478b-8366-51bb884025c4) to learn the most up-to-date guidance on setting up your school, lesson planning, meeting virtually, and sharing content with students.<br><br>Finally, be sure to check out Microsoft Teams IT admin training videos, decks, and a lot more at [Admin training for Teams](itadmin-readiness.md).        |

## Administration

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|EAF policy in the Enhanced Mitigation Experience Toolkit (EMET) can incorrectly identify Chromium sandbox optimizations as threats. <br/> |There is an issue with Chromium sandbox in which the Export Address Table Access Filtering (EAF) policy in the Enhanced Mitigation Experience Toolkit (EMET) and in Windows Defender Advanced Threat Protection (ATP) can incorrectly identify Chromium sandbox optimizations as threats. This causes Teams to not work properly.  <br/> | To work around this issue turn off EAF for Teams. You can read more about the issue [EMET mitigations guidelines](https://support.microsoft.com/help/2909257/emet-mitigations-guidelines) For more information about Windows Defender ATP and EAF policy, see [Enable exploit protection](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/enable-exploit-protection) <br/> |10/11/18 <br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Unable to add members to teams when UsersPermissionToReadOtherUsersEnabled is set to false  <br/> |When this value is set to false in AAD, users are unable to add external/internal members in Microsoft Teams, and the following error message is displayed: "We couldn't add member. We ran into an issue. Please try again later." However, members can be added directly to Office 365 groups.    <br/> |Change this setting to true in AAD.  <br/> |4/10/18  <br/> |

## Apps

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Chrome version 80 users are unable to sign in to some apps on the Teams platform.<br/>|After users have properly entered their password credentials to an app's sign-in page, a continuous cycle is initiated where the user is not recognized by the app and redirected back to the app's sign-in page. <br/>|Direct users to use the Teams desktop client. |11/15/19<br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|[Conditional Access](https://docs.microsoft.com/azure/active-directory/conditional-access/overview) may not work when using the "Website" or "Azure DevOps" tab in the desktop app.<br/> |If a website, such as an intranet portal, has conditional access policies (such as browser, IP address restrictions, or Device Compliance) then that website may not render as a tab inside of Teams in the desktop app. <br/> |Use Teams in a browser instead of using the desktop app.  <br/> |7/1/18  <br/> |

## Audio Conferencing

|**Issue**|**Behavior/Symptoms**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|PSTN callers with the same "From" number are shown as the same user in meeting roster.  <br/> |When multiple PSTN callers join a meeting, and their caller IDs are masked as a single number, they will show up as a single caller in the meeting roster.  <br/> |No workaround.  <br/> |9/25/2017  <br/> |
|Meeting Info panel is not showing up intermittently.  <br/> |Meeting Info panel may not show in Teams client when users are trying to look up for conference bridge phone numbers or conference ID.  <br/> |Look at meeting details or Outlook calendar to view conference bridge phone numbers or conference ID.  <br/> |9/25/2017  <br/> |
|Meeting invites from Outlook Add-in show garbage characters in PSTN coordinates for non-US locales.  <br/> |When scheduling private meetings using Outlook Add-in for Microsoft Teams on a computer with non-US locales, PSTN coordinates may contain garbage characters.  <br/> |No workaround.  <br/> |9/25/2017  <br/> |
|Dial out needs to use 5 digits or more.  <br/> |Users trying to dial out from a meeting need to type in 5 or more digits, even though dial plan normalization rule is available to normalize short digit dialing to E.164.  <br/> |Dial out by typing the full DID number or local number format instead of internal extension number.  <br/> |9/25/2017  <br/> |
|Dial out control is not showing up intermittently.  <br/> |Dial out control may not be visible from the Meeting Info panel.  <br/> |No workaround.  <br/> |9/25/2017  <br/> |
|Static conference ID not supported for Microsoft Teams meetings.  <br/> |If the admin overrides the default setting from dynamic conference ID to static conference ID, this setting doesn't take effect for Microsoft Teams meetings. See [Using Audio Conferencing dynamic IDs in your organization](/skypeforbusiness/audio-conferencing-in-office-365/using-audio-conferencing-dynamic-ids-in-your-organization.md).  <br/> |No workaround.  <br/> |9/25/2017  <br/> |
|PSTN meeting coordinates are not available for Skype for Business on-premises users  <br/> |If the user is a Skype for Business on-premises user, assigned with Skype for Business Online, Audio Conferencing, and Teams licenses, all meetings scheduled using Teams will not include PSTN meeting coordinates. <br/> |No workaround.  <br/> |2/1/2018  <br/> |
|Cloud Video Interop information in Meet Now  <br/> |If you create a Meet Now instance of a meeting in Microsoft Teams with an existing CVI license, it will not populate the CVI information. <br/> |The recommendation is to schedule the meeting to populate this information.  <br/> |6/11/2019  <br/> |

## Authentication

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Teams requires access to Google Gstatic <br/> |Teams presently requires access (TCP port 443) to the Google ssl.gstatic.com service for all users; this is true even if you're not using Gstatic. Teams will remove this requirement soon (early 2020). <br/> | No workaround. <br/> |1/30/20  <br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|After changing password of the user account there is Error message - Either your password changed or the server needs your sign-in info again. This continues even using new password. <br/> | Teams will address this issue soon in a fix being rolled out. <br/> | Logout and relogin in incorrect credentials. After failure, enter in your correct credentials. <br/> |01/09/20  <br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|When you try to join Teams from Internet Explorer or Edge, the program consistently loops or crashes and doesn't sign in.   <br/> | Your organization utilizes Trusted Sites in Internet Explorer and the Teams web-based application does not correctly log in because trusted sites for Teams are not allowed. <br/>|Make the following changes to IE settings or from the Control Panel, either with Administrator rights or a Group Policy Object:<br/><ol><li>Under **Internet Options** &gt; **Privacy** &gt; **Advanced**, accept First-Party and Third-Party cookies, and check the box for **Always allow session cookies**.</li><li>Click **Internet Options** &gt; **Security** &gt; **Trusted Sites** &gt; **Sites**, and add all of the following:<ul><li>https://login.microsoftonline.com</li><li>https://\*.teams.microsoft.com</li></ul></li></ol><br/><b>NOTE</b>: Always validate and allow all trusted URLs for Teams and the requirements from the following document: [Office 365 URLs and IP address ranges](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges).   <br/> |11/1/17  <br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Microsoft Teams will always log into the Domain-joined PC account.   <br/> |If a user has two different Teams accounts and has a machine with domain-joined enabled, Teams will use the domain-joined profile on the machine to automatically log the user into Teams. To switch to the other Teams account, the user must manually log out of the app and enter credentials to the second account to log in. If the user logs out of Teams and restarts the machine, upon restart, Teams will automatically log in using the domain-joined profile. <br/> | If users are signed in to a domain-joined computer and you don't want their user name pre-populated on the Teams sign-in screen, admins can set the following Windows registry to turn off pre-population of the user name (UPN) Computer\HKEY_CURRENT_USER\Software\Microsoft\Office\Teams SkipUpnPrefill(REG_DWORD) 0x00000001 (1). Note Skipping user name pre-fill for user names that end in ".local" or ".corp" is on by default, so you don't need to set a registry key to turn these off. Reference https://docs.microsoft.com/microsoftteams/sign-in-teams. <br/> |8/2/17  <br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Modern authentication failure - Forms auth not enabled  <br/> |When there is an initial failure with multi-factor authentication, use the web app for authentication.  <br/> For more information, see [Active Directory Federation Services prompt=login parameter support](https://docs.microsoft.com/windows-server/identity/ad-fs/operations/ad-fs-prompt-login).  <br/> |Check this setting: `Set -MsolDomainFederationSettings -DomainName yourdomainhere -PreferredAuthenticationProtocol WsFed -SupportsMfa $False -PromptLoginBehavior Disabled`.  <br/> |6/19/17  <br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Planner on single sign-on (SSO) build <br/> |SSO does not apply to Planner. You will have to sign in again the first time you use Planner on each client.  <br/> |No workaround. Further authentication enhancements are being worked on.  <br/> |2/28/17  <br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Can't save profile picture  <br/> |Users can't save their profile picture when the Exchange Mailbox is hosted (homed) on-premises on Exchange 2016 CU2 or lower.  <br/> |No workaround.  <br/> |2/28/17  <br/> |

## Browser

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Green artifacts in Chrome video rendering  <br/> |Green artifacts appear while viewing video or sharing the screen in a call or meetup in Chrome.  <br/> |Disable the hardware acceleration setting in Chrome.  <br/> |8/3/17  <br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Safari web client support  <br/> | Teams is now available in preview on Safari 11.1+ on macOS. While in preview, users may run into issues related to Safari's Intelligent Tracking Prevention [Known Safari Issues](https://go.microsoft.com/fwlink/?linkid=2062082).  <br/> | While Safari browser support is in preview, go to **Preferences > Privacy**  and uncheck the **Prevent cross-site tracking**  setting. Then, close your browser and navigate back to teams.microsoft.com in Safari. <br/> |11/2/16  <br/> |


## Channels

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|When a user leaves the company, it appears in Microsoft Teams as "Unknown user"<br/> |When a user leaves the company, it appears in Microsoft Teams as "Unknown user." Also, the conversation tab displays: "Unknown user has been added to the team." <br/> |No workaround.  <br/> |9/12/17  <br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Users can't recreate a pre-existing channel name  <br/> |Once a channel name has been created, even if it's deleted, it cannot be recreated. Our system maintains this data for information protection scenarios.  <br/> |No workaround.  <br/> |3/13/17  <br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Renaming a channel in Microsoft Teams does not rename the corresponding folder in SharePoint Online  <br/> |If a channel is renamed in Microsoft Teams, the folder in the SharePoint Online document library corresponding to the team does not change to match. The correct SharePoint Online folder name is displayed at the top of the renamed channel Files tab.  <br/> |No workaround.  <br/> |3/13/17  <br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|URL preview may not show for all URL's  <br/> |Some URL's may not show a preview.  This is reliant on the original URL having the capability to show a preview. <br/> |No workaround. <br/> |9/1/18 <br/> |

## Chat

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|@ Mentions for deleted message send notification with channel link  <br/> |There's a known notification limitation when you are at-mentioned in a message that is deleted; the notification in the feed will navigate to the channel but not to a specific message. <br/> | By design <br/> | 3/28/17  <br/>|


## Client

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Can't start Teams for Surface Hub from Microsoft Store |Microsoft Teams for Surface Hub won't start when you click **Launch** in the Microsoft Store. | Launching the Teams for Surface Hub app from the Microsoft Store listing isn't supported by Windows on Surface Hub. <br> <br/> Please restart your Surface Hub after installing Teams. | 2/27/18 |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Teams does not automatically update   <br/> | When Microsoft Teams is installed to Program Files using installation scripts rather than to the default location, the client doesn't auto-update when new versions are available.    <br/> | By design. Be sure to install the application in the default location: `user\Appdata`.  <br/> | 9/7/17  <br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Symlink or mapping a drive to C:\users causes app to launch to white screen  <br/> | When Microsoft Teams is installed to Program Files using installation scripts rather than to the default location, the client doesn't auto-update when new versions are available.   <br/> | By design. Be sure to install the application in the default location: `user\Appdata`. If the mapping must exist, you should use the web version of Microsoft Teams.  <br/> | 9/7/17  <br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Symlink or mapping a drive to c:\users will cause app to launch to white screen  <br/> |When the default location of `C:\users\<user>\appData` is changed by moving the `C:\users` folder or using symlink, the app will launch with a white screen.   <br/> |There is no known work around. If the mapping must exist, you should use the web version of Microsoft Teams.   <br/> |3/13/17  <br/> |

## Environment

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Group mailboxes are not enabled for archival (extra storage) purposes  <br/> |In the Office 365 Security and Compliance Center, Global Admins cannot enable archival on Group mailboxes. They can do this on user mailboxes only.  <br/> |If the Group mailbox capacity is nearly full, please contact Microsoft Office Support to extend mailbox size.  <br/> |2/1/17  <br/> |

## Guest Access

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|EU and APAC customers receive an error when they add a guest user from another tenant    <br/> | Customers in EU and APAC experience a replication delay between Microsoft Teams and Azure Active Directory. When a user from an EU or APAC tenant tries to add a guest user from any other tenant, they receive an error message asking them to try again.   <br/> |Click the retry button again to execute the addition of the guest user.  <br/> |11/8/17  <br/> |

## Linux

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|AutoStart on Linux is not working. <br/> |AutoStart on Linux does not start the Teams application. <br/> | <br/> |12/05/19  <br/>|

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|White screen when resuming from sleep/suspend. <br/> |When your computer resumes / wakes from sleep or suspend mode there can be a network change (especially when the computer is connected to VPN before put to sleep/suspended) and that takes some time for the computer to reobtain the connection. The combination of these things can lead to a Teams white screen. <br/> |Restarting Teams client will help.  <br/> |12/05/19  <br/>|

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Cursor missing when screen sharing. <br/> |While sharing screen, the other party does not see the cursor of the person sharing the screen. <br/> | <br/> |12/05/19  <br/>|

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Issue running in parallel with VMWare workstation. <br/> |The Teams application experiences issues when running in parallel with VMWare workstation. <br/> | <br/> |12/05/19  <br/>|

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|KDE notifications create new taskbar.<br/> |Notification on KDE creates new window in taskbar. <br/> | <br/> |12/05/19  <br/>|

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Package managers not showing change list. <br/> |Package manager does not show change list. <br/> | <br/> |12/05/19  <br/>|

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Cannot launch Teams client in offline mode. <br/> |Unable to launch Teams Offline in Linux client. <br/> | <br/> |12/05/19  <br/>|

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Device settings while in meeting. <br/> |When in a meeting and changing device settings, the Microphone indicator isn't registering anything being picked up. <br/> | <br/> |12/05/19  <br/>|

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Can't close Teams application using keyboard. <br/> |Can't close the Teams application using the default `$mod + shift + q` or by clicking the close button in the app. <br/> | <br/> |12/05/19  <br/>|

## Meetings

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Users can't access Meetings/Connectors but have Exchange Online mailboxes. <br/> |Customer actively blocks EWS from services within Exchange Online but needs to have MS Teams compliant within EWS policies. <br/> |To make MS Teams compliant, you must add the following User Agent Strings for MS Teams within the EWSAllowList: `SkypeSpaces/*` and `MicrosoftNinja/*`, including asterisks. The following command can be used: `Set-organizationconfig -EwsAllowList @{Add="MicrosoftNinja/*","SkypeSpaces/*"}`<br/> For more info: https://docs.microsoft.com/powershell/module/exchange/organization/Set-OrganizationConfig?view=exchange-ps <br/> |5/30/17  <br/>|

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Skype for Business required for some meetings  <br/> |Your calendar of appointments is conveniently displayed within Microsoft Teams. To enter a meeting, click the **Join** button. <br/> While we are continuing development in this area, if this meeting was scheduled with Skype for Business and you click **Join**, Microsoft Teams will launch your Skype for Business client to complete your entrance into the meeting. Meetings scheduled within Microsoft Teams will initiate directly within the product.  <br/> In the future, we will streamline this experience.  <br/> |Click **Join**. Microsoft Teams will intelligently decide whether Skype for Business is required for a user to join the meeting based on the URL included in the meeting description.  <br/> |3/13/17  <br/> |


|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Attendee maximum for meetings  <br/> |Each Microsoft Teams meeting can have up to 250 attendees.  <br/> |Create live events in teams which can host 10000 users.  <br/> |3/13/17  <br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Meetings not available  <br/> |Meeting functionality is not available when Exchange Mailbox is hosted (homed) on-premises in version less than Exchange 2016 CU3.  <br/> |Upgrade to Exchange 2016 CU3 or later for the on-premises deployment.  <br/> |2/28/17  <br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|No audio while sharing content during a broadcast meeting  <br/> |When sharing content during a broadcast meeting, audio from the shared content (YouTube link or a saved video file) cannot be hear by participants.  <br/> |None as this is by design.  Teams does not currently support audio from content sharing  <br/> |10/9/18  <br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Unable to start meeting as Organizer from Outlook as you may get stuck in the Virtual Lobby  <br/> |You may run into this issue if your Outlook client is logged into a different account than your Teams client. <br/> |When you join the meeting, make sure your Outlook client and Teams client are logged into the same account that the meeting was scheduled from.  <br/> |11/5/18  <br/> |

## Mobile

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Unable to see auto-favorited channels  <br/> |Some members aren't able to see auto-favorited channels on the mobile app.  <br/> |Members must sign in to the desktop or web app first to see auto-favorited channels on their mobile app.  <br/> |4/30/18  <br/>|

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Users might not be able to switch accounts on Intune-managed mobile devices  <br/> |Users might not be able to switch accounts on Intune-managed mobile devices.  <br/> |No workaround.  <br/> |9/20/17  <br/>|

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Issues you may encounter if using iOS 13 Beta  <br/> |1. Teams notifications are not being fired.  This includes chats, mentions, and calls.  2. File preview is not working with the beta build.  <br/> |At this time there is no workaround.  We are working with Apple developers to find fixes for these issues.  <br/> | 6/25/19  <br/>|


## People

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|User Profile Photos  <br/> | Currently Teams does not have a mechanism to prevent users from changing photos. The BTS team has met with the development team who has filed the following for consideration: Feature 108874: IT Policy to disable Profile Photo uploading   <br/> | If you have customers who would like the ability to prevent Profile Photo uploading in Teams, please have them add their vote and business case to comments here: https://microsoftteams.uservoice.com/forums/555103-public/suggestions/18600505-disable-user-ability-to-change-profile-photos <br/> |3/1/17 <br/> |



## Phone System

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Resource account misconfigured Department <br/> | On-premises resource accounts associated with an auto attendant or call queue created before January 2019 might not have the Department parameter set properly, which might cause a phone number assignment to fail. A fix is underway to resolve this issue. <br/><br/> Resource Accounts configured using New-CsHybridApplicationEndpoint with Skype for Business Server may not have the Department parameter set properly which will cause the resource account creation in the Teams admin center to fail. In this case, you need to configure the department name in Active Directory on-premises before synchronizing to online.|To mitigate this issue, you can run the following Cmdlet to set the Department parameter: Set-AdUser -Identity <objectId> -Department “Microsoft Communication Application Instance” <br/> Also see the [Auto Attendant and Call Queues Service Update](https://techcommunity.microsoft.com/t5/Microsoft-Teams-Blog/Auto-Attendant-and-Call-Queues-Service-Update/ba-p/564521). |5/8/19 <br/> |


|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Resource accounts sync delay|Can't assign a phone number to the resource account, or you get the error "The following application instance is not present in BVD."|Allow 24 hours for syncing. If it has already been 24 hours, remove the phone number assignment, delete the resource account, and create a new one with a different name.|5/18/2019|

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Can't assign a toll service number from the Teams admin center|When you try to assign a toll service number in the Teams admin center, you get the error "You need a phone system license."|Use PowerShell cmdlets to assign a toll service number instead.|5/18/2019|


|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Resource account corrupted|Resource account not working|Removing or replacing the license of a resource account, or creating a new resource account with the same SIP URI as a previously deleted one will result in a corrupt resource account.|5/18/2019|


|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Phone number blocked|Phone number blocked: Deleting the resource account before removing the phone number will block the phone number.|Contact Microsoft support to release the telephone number.|5/18/2019|

## Presence
|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Presence in Outlook and other Office applications not showing after a user is moved to **Teams Only** mode. <br/> |If you uninstall the Skype for Business client after you move a user to **Teams Only** mode, presence stops working in Outlook and other Office apps. Presence works fine in Teams.  <br/> |To see presence in Outlook (and other Office apps), Skype for Business must be installed, even if you're running Teams in **Teams Only** mode. Microsoft is aware of this problem and is working on a fix.  <br/> |9/2019  <br/> |



## Provisioning

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Incorrect SharePoint user created for Microsoft Teams SharePoint site  <br/> |The SharePoint creator for a Microsoft Teams Group appears to be a SharePoint Admin, not the correct user.  <br/> When auditing from the SharePoint administration console, the creator for the site collection page associated with the Office 365 Group created against the team in Microsoft Teams is the SharePoint admin.  <br/> |No workaround.  <br/> |7/21/17  <br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Users can't create a team  <br/> |Your company may have set a policy restricting who can create Office 365 groups or teams.  <br/> |Check with your IT admin to understand your company's policy for creating groups and teams.  <br/> |3/13/17  <br/> |

## Skype for Business to Teams Upgrade

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|

## Tabs

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Website tab leading to customer confusion  <br/> |Website tabs are not equivalent to your browser. A number of sites, especially those requiring authentication or using popups, will not work when pinned as a website tab.  <br/> |We are working on improving the UI to make it clearer for customers.  <br/> |5/2/18  <br/>|

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Tabs not working since Conditional Access was enabled <br/> |Some tabs may not load anymore in the Desktop Client since Conditional Access was enabled on the tenant. The tabs load when using the Web Client. Some tabs that might be affected are: PowerBI, Forms, VSTS, PowerApps, and SharePoint List.  <br/> |To see affected tabs you must use Teams in Edge, IE, or Chrome with the Windows 10 Accounts extension installed. Some tabs still depend on web authentication, which doesn't work in the Desktop Client when CA is enabled. We are working with partners to enable these scenarios; so far we have enabled Planner, OneNote, and Stream. <br/> |4/5/18  <br/>|

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|List of workspaces is not alphabetized  <br/> |Users switching workspaces when adding a PowerBI tab will encounter an unalphabetized list of workspaces to switch between.  <br/> |No workaround.  <br/> |3/13/17  <br/>|

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Scroll bar disappears when selecting reports  <br/> |Users adding PowerBI reports can't scroll through a list longer than one screen of reports without losing their scroll bar.  <br/> |Use Up and Down arrows to scroll through the list.  <br/> |3/13/17  <br/>|

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Teams Planner integration with Planner online <br/> |Tasks buckets in Planner do not show up in Planner online experience.  <br/> |No workaround. <br/> |2/28/17  <br/>|


|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Teams Planner integration with Planner online <br/> |Owners are unable to create a plan for a team created from an existing Office 365 group.  <br/> |Give the member permissions to the group owner. <br/> |1/14/20  <br/>|




|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Legacy OneNote Tab  <br/> |Legacy OneNote tabs created during the public preview of Microsoft Teams cannot be renamed or deleted.  <br/> |No workaround. <br/> |11/8/2017  <br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Search function in SharePoint list tab  <br/> |Attempting to open a file from the search function of the SharePoint list tab will trigger a "You'll need a new app to open this about" prompt and the file will not be opened. <br/> |Open directly from list instead of search bar. <br/> |2/11/2019  <br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|File download failure <br/> |Attempting to download a file when the file path contains an apostrophe will trigger a "The file didn't download" failure when using the Microsoft Teams desktop client. <br/> |Download the file from the web client or SharePoint Online <br/> |5/10/2019  <br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Unable to upload or download OneNote file <br/> |Attempting to upload or download a OneNote file or notebook will fail using Microsoft Teams. <br/> |Download or upload the file directly in SharePoint Online <br/> |5/7/2019  <br/> |

## Teams

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Teams voicemail emails will arrive with spf fail if it is a sip call, if it is a pstn call to a user they will arrive with the from attribute with out the correct value, if the customer has a rule where he analyzes the spf voice mails will have the action where the etr decides. <br/> | <br/> | 29/08/2019 workaround will be adding a exception in the etr if the message is a voice mail.


|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Photo upload to Teams is not blocked on OWA/Outlook as policy requires   <br/> | Teams allows users to upload photos directly to Office 365, in spite of policy settings in place preventing photo upload for OWA.   <br/> |<br/>  |10/16/17  <br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Public team list does not display all teams  <br/> |The list of public teams is based on the Microsoft Graph.  <br/> |If you don't see a team, try searching for it in the top right search box. Also, the team owners should communicate team names to colleagues since many teams could show up in the search results. <br/> | 7/21/17  <br/>|

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Team names that contain special characters can create errors for meeting creation  <br/> |User will receive **error has occurred** message in red when trying to create a meeting for a Team that has special characters in the name.   <br/> |Rename or recreate team with a name that does not contain a "/".  <br/> |7/13/17  <br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Team member maximum of 5000  <br/> |Each Microsoft Team can have a maximum of 5000 members per team.  <br/> |No workaround.  <br/> |2/6/2019  <br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Deleting a team will also delete the group associated with it  <br/> |Users may not realize that the underlying Office 365 Group is deleted when the team is deleted. Additionally, if the underlying Office 365 Group is deleted, the team is deleted as well.  <br/> |Additional language in Microsoft Teams provides this information to the user. This information is not present in the Office 365 Groups interface. Your help desk can recover a deleted Group/Team.  <br/> |3/13/17  <br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Teams desktop app showing white screen  <br/> | <br/> |Try deleting or reinstalling the graphics drivers on the computer, or start Teams from a command line with a disable GPU flag:<ul><li>For Windows: Open the command prompt and enter the following: `cd %localappdata%\microsoft\teams\current run Teams.exe --disable-gpu`</li><li>For Mac: Start Terminal and enter the following: `cd \Applications folder Microsoft\ Teams.app/Contents/MacOS/Teams --disable-gpu`</li></ul> <br/> |<br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|User not receiving welcome email when added administratively  <br/> |When adding a member to a team using PowerShell or the Teams admin center, they are not receiving a welcome email from Microsoft Teams  <br/> |Adding a member from the Teams UI directly will send an email. Currently, there is no workaround doing so administratively.  <br/> |2/12/19  <br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Interoperability issue between Symantec DLP and Teams <br/> |Symantec DLP Endpoint agents can interfere with Teams process, which can then lead to a launch or exit failure.  <br/> |Exclude (whitelist) Teams.exe from the Symantec DLP's Endpoint agents as described in this <a href="https://support.symantec.com/us/en/article.TECH220322.html">Symantec support article</a>. <br/> |07/15/19  <br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Dell Encryption can prevent Teams from launching <br/> |Dell Encryption (formerly Dell Data Protection Encryption) can corrupt Teams installation during the update process, leading to a permanent failure to launch the application. <br/> |Exclude the Teams folder at %LocalAppData%\Microsoft\Teams from the encryption policy. <br/> |11/21/19  <br/> |
