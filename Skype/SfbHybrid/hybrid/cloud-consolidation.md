---
title: "Cloud Consolidation for Teams and Skype for Business"
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.reviewer: bjwhalen
ms.topic: article
ms.prod: skype-for-business-itpro
search.appverid: MET150
ms.collection: 
- Hybrid 
- M365-voice
- M365-collaboration
- Teams_ITAdmin_Help
- Adm_Skype4B_Online
audience: ITPro
appliesto:
- Skype for Business 
- Microsoft Teams
localization_priority: Normal
description: "This article describes how to achieve that consolidation for organizations with on-premises deployment(s) of Skype for Business (or Lync) who are looking to move to move their UC workload to Teams and/or Skype for Business Online."
---

# Cloud consolidation for Teams and Skype for Business

> [!Note]
> This is a preview or early release feature. 

Many large enterprises have more than one on-premises AD forest, and in some cases, customers have more than one Exchange and/or Skype for Business Server (or Lync Server) deployment. In addition, even organizations with only one on-premises forest could find themselves in a similar situation via a business merger or acquisition. As these customers move to the cloud, they want to consolidate the multiple instances of a given on-premises workload into the cloud into a single Office 365 tenant. This article describes how to achieve that consolidation for organizations with multiple on-premises deployments of Skype for Business (or Lync) who want to move their UC workload to the Microsoft cloud, e.g., Microsoft Teams and/or Skype for Business Online.

Historically, the guidance has been for customers in this situation to consolidate deployments on-premises first and then move to the cloud. While this is still an option, this article describes a solution based on new functionality that enables organizations with multiple Skype for Business deployments to migrate one deployment at a time into a single Office 365 tenant, without doing on-premises consolidation. Note that even with this new functionality, Skype for Business Online and Microsoft Teams do not support multiple Skype for Business/Lync forests in hybrid mode with a single Office 365 tenant. 

> [!Important]
> Before using this guide for configuration, be sure to review and understand the [Limitations](#limitations), as they may affect your organization.

## Overview of cloud consolidation

Consolidation of all users from on-premises into the cloud in a single Office 365 tenant can be achieved for any organization with multiple Skype for Business deployments, provided that the following key requirements are met:

- There must be at most one Office 365 tenant involved. Consolidation in scenarios with more than one Office 365 tenant is not supported.
- At any given time, only one on-premises Skype for Business forest can be in hybrid mode (Shared SIP Address Space). All other on-premises Skype for Business forests must remain on-premises (and presumably federated with each other). Note that these other on-premises organizations *can* sync to AAD if desired with [new functionality to disable online SIP domains](https://docs.microsoft.com/en-us/powershell/module/skype/disable-csonlinesipdomain?view=skype-ps) available as of December 2018.

Customers with deployments of Skype for Business in multiple forests must fully migrate all users of a single hybrid Skype for Business forest individually into the Office 365 tenant using Shared SIP Address Space functionality, and then disable hybrid with that on-premises deployment, before moving on to migrate the next on-premises Skype for Business deployment. Prior to being migrated to the cloud, on-premises users remain in a federated state with any users that are not represented in the same user’s on-premises directory.  

## Canonical example of cloud consolidation

Consider an organization with two separate federated on-premises deployments of Skype for Business that wants to consolidate them online in Microsoft Teams or Skype for Business Online.


|Original state details |Desired state details |
|---------|---------|
|<ul><li>2 independent Skype for Business on-premises deployments in separate AD forests<li>At most 1 forest is in hybrid with Skype for Business Online <li> Orgs are federated with each other <li>Users are not synced across these forests<li> The org may have an Office 365 tenant and may be syncing their directory into Azure AD</ul>|<ul> <li>1 Office 365 tenant<li>No more on-premises deployments, so no hybrid remaining<li>All users from on premises are homed in Skype for Business Online and optionally may be Teams-only users <li>No on-premises footprint of Skype for Business anywhere <li>Users still have on-premises authentication</ul> |

![Consolidating two separate federated on-premises deployments](../media/cloudconsolidationfig1.png)  

The basic steps to get from the original state to the desired end state are below.  Note that some organizations may find that their starting point is somewhere in the middle of these steps. See [Other starting points](#other-starting-points), later in this article. Finally, in some cases the order can be adjusted, depending on need. [Key constraints and limitations](#limitations) are described later.

1.	Get an Office 365 tenant if one does not yet exist.
2.	Make sure all relevant SIP domains across both on-premises deployments are verified Office 365 domains.
3.	Pick one Skype for Business deployment that will be hybrid with Office 365. In this example, we’ll use OriginalCompany.<span>com.
4.	[Enable AAD Connect for the forest](configure-azure-ad-connect.md) that will first become hybrid (OriginalCompany.<span>com). 
5.	If you will be introducing Teams into your organization, set the tenant-wide policy for [TeamsUpgradePolicy](https://docs.microsoft.com/en-us/powershell/module/skype/grant-csteamsupgradepolicy) to SfBWithTeamsCollab or one of the other SfB modes (SfBOnly or SfBWithTeamsCollabAndMeetings). This is critical to ensure routing of calls and chats from users who move to Teams Only to users who remain on premises.
6.	It is recommended at this point (but not yet required until step 11) to [enable AAD Connect for the other forest](cloud-consolidation-aad-connect.md) (AcquiredCompany.<span>com). Assuming AAD Connect is enabled in both forests, the org looks like **[Figure A](#figure-a)**, which may be a common starting point for some orgs. 
7.	For any SIP domains hosted by other on-premises deployments (in this case, AcquiredCompany.<span>com), [disable these SIP domains in Skype for Business Online](https://docs.microsoft.com/en-us/powershell/module/skype/disable-csonlinesipdomain) using `Disable-CsOnlineSipDomain` in PowerShell. (This is new functionality as of December 2018.)
8.	[Configure Skype for Business hybrid](configure-federation-with-skype-for-business-online.md) for OriginalCompany.<span>com (the one deployment that still has enabled online SIP domains).
9.	In the hybrid deployment (OriginalCompany.<span>com), start [moving users from Skype for Business on premises to the cloud](move-users-between-on-premises-and-cloud.md) (whether Teams Only or not) so that account is homed in Skype for Business Online. Now the organization looks like **[Figure B](#figure-b)**. The key changes from Figure A are:
    - Users from both on-premises directories are now in AAD.
    - AcquiredCompany.<span>com is a disabled online SIP domain.
    - Some users have been moved online to either Skype for Business Online or Teams. (See purple user A.)
10.	Once all users are moved to the cloud, [disable hybrid with the Skype for Business on-premises deployment](cloud-consolidation-disabling-hybrid.md) for OriginalCompany.<span>com from Office 365:  
    - Disable split domain in the Office 365 tenant.
    - Disable the ability to communicate with Office 365 in OriginalCompany.<span>com on-premises.
    - Update DNS records for OriginalCompany.<span>com to point to Office 365.
11.	If not done already, [enable AAD Connect for the next forest](cloud-consolidation-aad-connect.md) that will go hybrid (AcquiredCompany.<span>com). At this point, the organization looks like **[Figure C](#figure-c)**. This may be another common starting point for some organizations. 
12.	In PowerShell, [enable the SIP domains for the next on-premises deployment](https://docs.microsoft.com/en-us/powershell/module/skype/enable-csonlinesipdomain?view=skype-ps) that will go hybrid, AcquiredCompany.<span>com. This is done using `Enable-CsOnlineSipDomain`, which is new functionality available as of December 2018.
13.	If you are using closed federation, you must add any SIP domains (excluding *.microsoftonline.com)  of the pure online tenant as Allowed Domains in **same** Office 365. Note that it can take some time before the change takes effect and there is no harm in doing this early, so we suggest doing this well in advance of moving to step 14.
14.	Update the on-premises environment to accept any SIP domains from the online tenant, so they match.
    - [Update the SAN in all edge certificates](cloud-consolidation-edge-certificates.md) to be the same value as before, plus values for any existing online SIP domains (except *.microsoftonline.com), in this case, Sip.OriginalCompany.<span>com.
    - Make sure OriginalCompany.<span>com is an [allowed domain](https://docs.microsoft.com/en-us/powershell/module/skype/new-csalloweddomain) in the on-premises deployment, AcquiredCompany. Add allowed domains.
15.	[Enable Skype for Business hybrid](configure-federation-with-skype-for-business-online.md) between on-premises AcquiredCompany.<span>com and the cloud.
16.	As desired, [migrate users from on-premises to the cloud](move-users-between-on-premises-and-cloud.md). You can migrate users either directly to [TeamsOnly](/microsoftteams/teams-and-skypeforbusiness-coexistence-and-interoperability) mode or you can migrate them first to Skype for Business Online. During this state, the organization looks like **[Figure D](#figure-d)**.
17.	Once all users are migrated, [disable hybrid with the on-premises environment](cloud-consolidation-disabling-hybrid.md) to *make the organization pure cloud*!

The diagrams below show the configuration at various key points during this process.

##### Figure A:

- Both organizations sync via AAD Connect, so AAD now has all users from both on-premises deployments.
- All users homed on-premises.  
- Skype for Business Hybrid is *not* yet configured.
- If users in either deployment use Teams, they won’t be able to federate with each other (or any organization), nor will they have interoperability with any Skype for Business users. While in this stage, Microsoft recommends using Teams for Channels only.<br><br>
    ![Figure A diagram](../media/cloudconsolidationfiga.png)

##### Figure B:

- AcquiredCompany.<span>com is a [disabled](https://docs.microsoft.com/en-us/powershell/module/skype/disable-csonlinesipdomain) online SIP domain. All users are on-premises. If they use Teams they do not have federation or interoperability. While in this stage, Microsoft recommends using Teams for Channels only.
- Skype for Business Hybrid has been enabled for one of the on-premises organizations.
- Some users in the hybrid organization have been moved to the cloud (user A as indicated by purple shading). These users can be either Skype for Business Online users or Teams Only users with full interoperability and federation support.<br><br>
    ![Figure B diagram](../media/cloudconsolidationfigb.png)

##### Figure C:

- All users from OriginalCompany.<span>com are now in the cloud (homed in Skype for Business Online). It’s recommended that they also be Teams Only.
- Skype for Business hybrid configuration with the OriginalCompany.<span>com deployment has been disabled. The on-premises deployment is gone.
- If AcquiredCompany.<span>com wasn’t previously syncing to AAD, to continue from here it needs to be synced now. But it is not yet hybrid (shared SIP address space), and until the organization is ready to move to hybrid, the online SIP domain for the pure on-premises organization (AcquiredCompany.com) should remain disabled, so that online Teams users can communicate with on-premises users.<br><br>
    ![Figure C diagram](../media/cloudconsolidationfigc.png)

##### Figure D:

- AcquiredCompany.<span>com is now enabled as an online SIP domain.
- On-premises is updated to accept OriginalCompany.<span>com. (Both allowed domain, and edge certificates are updated).
- Shared SIP Address Space is enabled between AcquiredCompany.<span>com and Office 365 tenant.
- Some users in the hybrid organization may have been moved to the cloud, such as User D below (indicated by purple shading).<br><br>
    ![Figure D diagram](../media/cloudconsolidationfigd.png)

## Other starting points

The steps in the canonical example above assume that the organization starts with two federated on-premises deployments with no Office 365 presence. However, some organizations may have an existing Office 365 footprint, and there can be different entry points into the sequence above. There are four typical configurations:

- Multiple federated on-premises organizations with no Office 365 tenant. In this case, start at step 1.
- Multiple federated on-premises organizations that are already syncing multiple Skype for Business forest into a single Azure AD tenant. Such an organization resembles the hypothetical organization in Figure A, which has completed steps 1-6 and should start at step 7.
- A hybrid organization that federates with 1 or more other pure on-premises organizations, none of which sync to AAD. Such an organization would resemble the hypothetical organization in **Figure E**, shown below.
    - This organization is similar to Figure B, which has completed steps 1-9, except:
        - Its non-hybrid Skype for Business deployments are *NOT* yet syncing to Azure AD.
        -  Online SIP domains are not yet disabled. 
    - These organizations should either:
        - Complete migration of the existing hybrid organization and enter the above sequence at step 10.  OR,
        - If it is desired to sync any other Skype for Business forests into AAD prior to completing migration of the hybrid organization, then the organization must perform step 7 (disable all online SIP domains in any other on-premises Skype for Business deployment that will sync into AAD) and then enable AAD Connect, and only then continue with step 10 (decommission the original hybrid deployment).       
                **Figure E**<br>
                ![Figure E diagram](../media/cloudconsolidationfige.png)
- A pure Skype for Business Online organization (which may or may not be using Teams) that federates with a separate on-premises Skype for Business organization. Once this organization disables the online SIP domain for the on-premises organization and enables AAD Connect for the on-premises Skype for Business organization, it resembles the hypothetical organization shown in **[Figure C](#figure-c)** that has completed steps 1-11.

## Limitations

- There must be at most one Office 365 tenant involved. Consolidation in scenarios with more than one Office 365 tenant is not supported.
- Only one on-premises Skype for Business forest can be in hybrid mode (shared SIP address space) at a time. All other on-premises Skype for Business forests must remain purely on-premises and should be federated with each other and the Office 365 tenant.
- Prior to being migrated to the cloud, there is an asymmetric experience for users in this deployment, because not all users in online are represented on-premises:
    - The experience can be summed up as follows:
        - Any user homed online will interact with on-premises users in the hybrid environment as if the user is hybrid.
        - On-premises users in the hybrid deployment will interact with online users who are represented in their on-premises directory as if they were hybrid. 
        - On-premises users in the hybrid deployment will interact with online users who are not represented in on-premises AD as federated.
    - In **[Figure D](#figure-d)** above, user E is on-premises in AcquiredCompany.<span>com.  User E will interact with User D (homed online) using the standard hybrid experience,  but user E will have a federated experience with users A, B, and C because they are not represented in the on-premises directory. However, users A, B, and C will interact with user E as if the user were in hybrid.
    - Implications of interaction being hybrid vs. federation:
        - Presence is not automatically subscribed to for federated users unless the user is marked as a contact.
        - Call forwarding does not work between federated domains.
        - Call transfer scenarios are more limited.
        - Throttling may be applied to federated traffic.
- Given this asymmetric experience, official support for calling functionality in cross-premises scenarios between an on-premises user and a cloud user that is not in the on-premises directory is limited to peer to peer only. 
    - Call forwarding, transfer, call queues, etc. between these users is not supported.
    - These non-supported calling scenarios will still appear enabled, but in many cases they will fail in unpredictable ways. 
    - In **[Figure D](#figure-d)** above, user E is on-premises, and calls with users A, B, or C will be supported only as peer to peer. (Calls with user D would not have support limitations.)  However, after the on-premises user E is moved to the cloud, this restriction no longer applies.
- If you have more than one deployment of Skype for Business Server 2019 in your environment, only 1 of those deployment can be configured to use Organizational Auto Attendant, since that feature requires Skype for Business Server hybrid configuration. 
- The order of some of the previous steps can be adjusted. The key requirement that must be met is that if all of these are true:
    - More than one on-premises Skype for Business forest syncing to a single AAD tenant
    - Split domain is enabled with one on-premises forest
    - At least one user in the hybrid organization has been migrated to the cloud<br>   Then, you *must* disable all other online SIP domains from any other on-premises Skype for Business forest. Otherwise, federation between online users in the hybrid organization and on-premises users in other organizations will break in one direction.

## Implications

- Because there are limitations in support for advanced calling functionality as described above, **organizations should treat these asymmetric states as transitory as part of migration, and not pursue them as steady state**.  
- Organizations with multiple on-premises Skype for Business deployments should generally start with a deployment that can be fully migrated to the cloud, so that consolidation can continue. It is understood that in some cases there will be holdouts of certain user groups for whom it’s not yet viable to move to Teams. When this is a consideration in scenarios involving multiple Skype for Business forests, start migrating with another forest that does not have these limitations, if at all possible.
- When moving from on-premises to the cloud, users that have delegation relationships and/or are typically are involved in call forwarding scenarios should be moved together as a unit.

## Considerations for moving to TeamsOnly mode

When you move users from on premises to the cloud in a hybrid environment, you can move them to either Skype for Business Only or TeamsOnly mode. *If you plan to move users to TeamsOnly mode, be sure to read this section first.*

- When you assign TeamsOnly mode to a user, all chats and calls from any other user will land in that user’s Teams client. 
- To ensure proper routing of chats and calls between users who are TeamsOnly and users who are still using Skype for Business on premises, you must ensure that on-premises users have TeamsUpgradePolicy with one of the SfB modes, rather than Islands (which is the default). 
    - To do this, *you must first set your tenant’s global instance of TeamsUpgradePolicy to one of these values*:
        - SfBWithTeamsCollab (recommended)
        - SfBWithTeamsCollabAndMeetings
        - SfBOnly
    - You can grant tenant-wide policy by using this command:<br>`Grant-CsTeamsUpgradePolicy -PolicyName SfBWithTeamsCollab -Global`
    - Note: Currently, you must do this at a tenant-wide level because policy cannot be assigned to individual users who do not have a SIP address in the online directory. While you have disabled online SIP domains for your pure on-premises deployment(s), users in those domains won’t have SIP addresses in the online directory by design. Hence, the only way to apply policy to those on-premises users is by assigning at the tenant level. In contrast, in the hybrid deployment users will have a SIP address in the online directory so they can be explicitly assigned a policy if it’s desired that they have a different value than the tenant global policy.
- The Teams client UX does not yet honor the SfB modes of TeamsUpgradePolicy. For example, when in these modes, call and chat initiation in Teams is currently possible, although in the future that won’t be the case. This can cause confusion among users because replies may sometimes land in Teams and sometimes Skype for Business, depending on the circumstances. It is recommended that you separately disable calling and chat via TeamsMessagingPolicy and TeamsCallingPolicy for users who are still on premises.

## See also

[Update the edge certificate](cloud-consolidation-edge-certificates.md)

[Update AAD Connect to include more than one forest](cloud-consolidation-aad-connect.md)

[Disable hybrid to complete migration to the cloud](cloud-consolidation-disabling-hybrid.md)
