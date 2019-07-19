---
title: Known issues for Microsoft Teams
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 6/25/2019
ms.topic: troubleshooting
ms.service: msteams
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
ms.reviewer: marcl
localization_priority: Priority
search.appverid: MET150
description: Current list of known issues for the Microsoft Teams client app and admin experience.
appliesto:
- Microsoft Teams
---

# Known issues for Microsoft Teams

This article lists the known issues for Microsoft Teams, by feature area.

## Administration



|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Audit logs may report an incorrect username as initiator when someone has been removed from a Team  <br/> |Teams team is a modern group in AAD. When you add/remove a member through the Teams user interface, the flow knows exactly which user initiated the change, and the Audit log reflects the correct info. However, if a user adds/removes a member through AAD, the change is synced to the Teams backend without telling Teams who initiated the action. Microsoft Teams picks the first owner of team as the initiator, which is eventually reflected in the Audit log as well.    <br/> |  <br/> |5/11/18  <br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|EAF policy in the Enhanced Mitigation Experience Toolkit (EMET) can incorrectly identify Chromium sandbox optimizations as threats. <br/> |There is an issue with Chromium sandbox in which the Export Address Table Access Filtering (EAF) policy in the Enhanced Mitigation Experience Toolkit (EMET) and in Windows Defender Advanced Threat Protection (ATP) can incorrectly identify Chromium sandbox optimizations as threats. This causes Teams to not work properly.  <br/> | To work around this issue turn off EAF for Teams. You can read more about the issue [EMET mitigations guidelines](https://support.microsoft.com/en-us/help/2909257/emet-mitigations-guidelines) For more information about Windows Defender ATP and EAF policy, see [Customize exploit protection](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/customize-exploit-protection) <br/> |10/11/18 <br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Unable to add members to teams when UsersPermissionToReadOtherUsersEnabled is set to false  <br/> |When this value is set to false in AAD, customer is unable to add external/internal members in Microsoft Teams, and the following error message is displayed: "We couldn't add member. We ran into an issue. Please try again later." However, members can be added directly to Office 365 groups.    <br/> |Change this setting to true in AAD.  <br/> |4/10/18  <br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Admin management of tenant-wide Connectors is no longer available  <br/> |When trying to add a connector in both client and online version we get the error: An unexpected error occurred. Please try again. Set-OrganizationConfig -ConnectorsEnabled=True   <br/> |Disable with Teams settings. See this support article: https://answers.microsoft.com/en-us/msoffice/forum/msoffice_o365admin-mso_teams-mso_o365b/how-to-enable-or-disable-connectors-in-office-365/33d4b2c1-00eb-420a-ad83-01a2b42ad098    <br/> |6/21/17  <br/> |

## Apps

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|[Conditional Access](https://docs.microsoft.com/en-us/azure/active-directory/conditional-access/overview) may not work when using the "Website" tab in the desktop app<br/> |If a website, such as an intranet portal, has conditional access policies (such as browser or IP address restrictions) then that website may not render as a tab inside of Teams in the desktop app <br/> |Use Teams in a browser instead of using the desktop app.  <br/> |7/1/18  <br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Connector options is missing for some teams  <br/> |When you right-click a channel, the Connectors option is not present for any member of the team.  <br/> |The creator of the team must have an online mailbox; otherwise, no Connector option will be available. This is expected behavior.  <br/> |6/26/17  <br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|"Assignments" app remains visble when disabled  <br/> |When the "Assignments" app is disabled in the admin center, it remains visible within the Teams client for EDU-licensed users. Selecting it when disabled will return an error indicating, "Doh! Something went wrong..."  <br/> |No workaround.  <br/> |12/29/17  <br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Unable to delete connectors as a team owner  <br/> |Attempting to delete a connector as an owner, that can otherwise add a conector, while "Allow members to create, update, and remove connectors" is disabled throws an error indicating the user does not have permission to do so. <br/> |Temporarily enabling "Allow members to create, update, and remove connectors" will allow the owner to delete the connector.  <br/> |7/27/18  <br/> |

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

## Authentication

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|When you try to join Teams from Internet Explorer or Edge, the program consistently loops or crashes and doesn't sign in.   <br/> | Your organization utilizes Trusted Sites in Internet Explorer and the Teams web-based application does not correctly log in because trusted sites for Teams are not allowed. <br/>|Make the following changes to IE settings or from the Control Panel, either with Administrator rights or a Group Policy Object:<br/><ol><li>Under **Internet Options** &gt; **Privacy** &gt; **Advanced**, accept First-Party and Third-Party cookies, and check the box for **Always allow session cookies**.</li><li>Click **Internet Options** &gt; **Security** &gt; **Trusted Sites** &gt; **Sites**, and add all of the following:<ul><li>https://login.microsoftonline.com</li><li>https://\*.teams.microsoft.com</li></ul></li></ol><br/><b>NOTE</b>: Always validate and allow all trusted URLs for Teams and the requirements from the following document: [Office 365 URLs and IP address ranges](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges).   <br/> |11/1/17  <br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Outlook add-in limitations  <br/> |To use the Outlook add-in, you must sign in to Teams using multi-factor authentication (MFA). If MFA fails halfway through the sign-in process, you'll still be able to sign into Teams, but you'll get an error message when you try to use the add-in.  <br/> The add-in is only available for Windows users for the time being.  <br/> The add-in won't work if you're using an authentication proxy.  <br/> | No workaround. <br/> |8/2/17  <br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Microsoft Teams will always log into the Domain-joined PC account.   <br/> |If a user has two different Teams accounts and has a machine with domain-joined enabled, Teams will use the domain-joined profile on the machine to automatically log the user into Teams. To switch to the other Teams account, the user must manually log out of the app and enter credentials to the second account to log in. If the user logs out of Teams and restarts the machine, upon restart, Teams will automatically log in using the domain-joined profile. <br/> | No workaround. <br/> |8/2/17  <br/> |

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
|Symlink or mappying a drive to C:\users causes app to launch to white screen  <br/> | When Microsoft Teams is installed to Program Files using installation scripts rather than to the default location, the client doesn't auto-update when new versions are available.   <br/> | By design. Be sure to install the application in the default location: `user\Appdata`. If the mapping must exist, you should use the web version of Microsoft Teams.  <br/> | 9/7/17  <br/> |

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

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Wiki not created for channels created by guests  <br/> |When a guest creates a new channel, the **Wiki** tab is not created. There isn't a way to manually attach a **Wiki** tab to the channel. <br/> |No workaround.  <br/> |9/20/17  <br/>|

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
|No audio while sharing content during a broadcast meeting  <br/> |When sharing content during a broadcast meeting, audio from the shared content (youtube link or a saved video file) cannot be hear by participants.  <br/> |None as this is by design.  Teams does not currently support audio from content sharing  <br/> |10/9/18  <br/> |

## Mobile

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Unable to see auto-favorited channels  <br/> |Some members aren't able to see auto-favorited channels on the mobile app.  <br/> |Members must sign in to the desktop or web app first to see auto-favorited channels on their mobile app.  <br/> |4/30/18  <br/>|

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Users might not be able to switch accounts on Intune-managed mobile devices  <br/> |Users might not be able to switch accounts on Intune-managed mobile devices.  <br/> |No workaround.  <br/> |9/20/17  <br/>|

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Mobile Client Teams Layout differences  <br/> |Teams are listed in alphabetical order and the channels can't be collapsed on the mobile client.  <br/> |No workaround.  <br/> |3/13/17  <br/>|

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
|Resource Account misconfigured Department <br/> |Resource Accounts associated with an auto attendant or call queue created before January 2019 might not have the Department parameter set properly, which might cause a phone number assignment to fail. A fix is undergoing to resolve this issue. <br/><br/> Resource Accounts configured using New-CsHybridApplicationEndpoint with Skype for Business Server will not have the Department parameter set properly which will cause the resource account creation in Skype for Business online to fail. In this case, you need to configure the department name in Active Directory before synchronizing to online.|To mitigate this issue, you can run the following Cmdlet to set the department parameter. Set-MsolUser -ObjectId <Resource Account Object ID> -Department "Microsoft Communication Application Instance" <br/> |5/8/19 <br/> |



|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Resource accounts sync delay|Can’t assign a phone number to the resource account, or you get the error “The following application instance is not present in BVD.”|Allow 24 hours for syncing. If it has already been 24 hours, remove the phone number assignment, delete the resource account, and create a new one with a different name.|5/18/2019|

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Can’t assign a toll service number from the Teams admin center|When you try to assign a toll service number in the Teams admin center, you get the error “You need a phone system license.”|Use PowerShell cmdlets to assign a toll service number instead.|5/18/2019|


|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Resource account corrupted|Resource account not working|Removing or replacing the license of a resource account, or creating a new resource account with the same SIP URI as a previously deleted one will result in a corrupt resource account.|5/18/2019|


|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Phone number blocked|Phone number blocked: Deleting the resource account before removing the phone number will block the phone number.|Contact Microsoft support to release the telephone number.|5/18/2019|


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
|Audit logs may report an incorrect username as initiator when someone has been removed from a Team  <br/> |Teams team is a modern group in AAD. When you add/remove a member through the Teams user interface, the flow knows exactly which user initiated the change, and the Audit log reflects the correct info. However, if a user adds/removes a member through AAD, the change is synced to the Teams backend without telling Teams who initiated the action. Microsoft Teams picks the first owner of team as the initiator, which is eventually reflected in the Audit log as well.    <br/> |  <br/> |5/11/18  <br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Photo upload to Teams is not blocked on OWA/Outlook as policy requires   <br/> | Teams allows users to upload photos directly to Office 365, in spite of policy settings in place preventing photo upload for OWA.   <br/> |<br/>  |10/16/17  <br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Public team list does not display all teams  <br/> |The list of public teams is based on the Microsoft Graph.  <br/> |If you don't see a team, try searching for it in the top right search box. Also, the team owners should communicate team names to colleagues since many teams could show up in the search results. <br/> | 7/21/17  <br/>|

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Team names that contain special characters can create errors for meeting creation  <br/> |User will receive **error has occured** message in red when trying to create a meeting for a Team that has special characters in the name.   <br/> |Rename or recreate team with a name that does not contain a "/".  <br/> |7/13/17  <br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|A team name with an &amp; symbol in it breaks connector functionality  <br/> |When a team name is created with the &amp; symbol, connectors within the Team/Group cannot be established.  <br/> |Don't use special characters in team names.  <br/> |6/21/17  <br/> |

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
|User not recieving welcome email when added administratively  <br/> |When adding a member to a team using PowerShell or the Teams admin center, they are not recieving a welcome email from Microsoft Teams  <br/> |Adding a member from the Teams UI directly will send an email. Currently, there is no workaround doing so administratively.  <br/> |2/12/19  <br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Unable to move, delete or rename files after editing  <br/> |After a file is edited in Teams it cannot be moved or renamed or deleted immediately <br/> |This is currently a known issue and the workaround is to wait for some time before making administrative changes.  <br/> |03/12/19  <br/> |

|**Issue title**|**Behavior / Symptom**|**Known workaround**|**Discovery date**|
|:-----|:-----|:-----|:-----|
|Interoperability issue between Symantec DLP and Teams <br/> |Symantec DLP Endpoint agents can interfere with Teams process, which can then lead to a launch or exit failure.  <br/> |Exclude (whitelist) Teams.exe from the Symantec DLP's Endpoint agents as described in this Symantec's <a href="https://support.symantec.com/us/en/article.TECH220322.html">article</a> . <br/> |07/15/19  <br/> |
