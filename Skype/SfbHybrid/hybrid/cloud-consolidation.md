---
ms.date: 11/05/2018
title: "Cloud Consolidation for Teams and Skype for Business"
author: MicrosoftHeidi
ms.author: heidip
manager: jtremper
ms.reviewer: bjwhalen
ms.topic: article
ms.service: skype-for-business-server
search.appverid: MET150
ms.collection: 
- Hybrid 
- M365-voice
- m365initiative-voice
- M365-collaboration
- Teams_ITAdmin_Help
- Adm_Skype4B_Online
audience: ITPro
f1.keywords:
- NOCSH
appliesto:
- Skype for Business 
- Microsoft Teams
ms.localizationpriority: medium
description: "This article is for organizations with an on-premises deployment of Skype for Business (or Lync) who are looking to move their UC workload to Teams."
---

# Cloud consolidation for Teams and Skype for Business

[!INCLUDE [sfbo-retirement](../../Hub/includes/sfbo-retirement.md)]

Many large enterprises have more than one on-premises AD forest. In some cases, customers have more than one Exchange and/or Skype for Business Server (or Lync Server) deployment. Organizations with only one on-premises forest might be in a similar situation because of a business merger or acquisition. As these customers move to the cloud, they want to consolidate multiple instances of a given on-premises workload into a single online Microsoft 365 organization. This article is for organizations with multiple on-premises deployments of Skype for Business (or Lync) who want to move their organization entirely to Microsoft Teams (all users are Teams Only).

Historically, the guidance for customers is to consolidate deployments on-premises first and then move to the cloud. While this guidance is still an option, this article describes a solution that enables organizations with multiple Skype for Business deployments to migrate one deployment at a time into a single Microsoft 365 organization, without doing on-premises consolidation. Microsoft Teams doesn't support multiple Skype for Business or Lync Server forests in hybrid mode with a single Microsoft 365 organization.

> [!IMPORTANT]
> Before using this guide for configuration, be sure to review and understand the [Limitations](#limitations), as they may affect your organization.

## Overview of cloud consolidation

You can consolidate all on-premises users from multiple Skype for Business deployments into a single online Microsoft 365 organization, if the following key requirements are met:

- There must be at most one Microsoft 365 organization involved. Consolidation in scenarios with more than one organization isn't supported.

- At any given time, only one on-premises Skype for Business forest can be in hybrid mode (Shared SIP Address Space). All other on-premises Skype for Business forests must remain on-premises (and presumably federated with each other). These on-premises organizations *can* sync to Microsoft Entra ID if desired if you [disable online SIP domains](/powershell/module/skype/disable-csonlinesipdomain).

Customers with deployments of Skype for Business in multiple forests must fully migrate all users of a single hybrid Skype for Business forest individually into the Microsoft 365 organization using Shared SIP Address Space functionality. You must then disable hybrid with that on-premises deployment, before moving on to migrate the next on-premises Skype for Business deployment. Prior to being migrated to the cloud, on-premises users remain in a federated state with any users that aren't represented in the same user’s on-premises directory.  

## Canonical example of cloud consolidation

Consider an organization with two separate federated on-premises deployments of Skype for Business that wants to consolidate them online in Microsoft Teams.

|Original state details |Desired state details |
|---------|---------|
|<ul><li>Two independent Skype for Business on-premises deployments in separate AD forests<li>At most, one  forest is in hybrid with Teams <li> Orgs are federated with each other <li>Users aren't synced across these forests<li> The org might have a Microsoft 365 organization and may be syncing their directory into Microsoft Entra ID</ul>|<ul> <li>One Microsoft 365 organization<li>No more on-premises deployments, so no hybrid remaining<li>All users from on premises are to Teams Only mode <li>No on-premises footprint of Skype for Business Server anywhere <li>Users still have on-premises authentication</ul> |

![Consolidating two separate federated on-premises deployments.](../media/cloudconsolidationfig1.png)  

The basic steps to get from the original state to the desired end state are below. Some organizations might find that their starting point is somewhere in the middle of these steps. See [Other starting points](#other-starting-points), later in this article. Finally, in some cases the order can be adjusted, depending on need. [Key constraints and limitations](#limitations) are described later.

1. Get a Microsoft 365 organization if one doesn't yet exist.
2. Make sure all relevant SIP domains across both on-premises deployments are verified Microsoft 365 domains.
3. Pick one Skype for Business deployment that is hybrid with Microsoft 365. In this example, use OriginalCompany.<span>com.
4. [Enable Microsoft Entra Connect for the forest](configure-azure-ad-connect.md) that will first become hybrid (OriginalCompany.<span>com).
5. Set the tenant-wide policy for [TeamsUpgradePolicy](/powershell/module/skype/grant-csteamsupgradepolicy) to SfBWithTeamsCollab or one of the other Skype for Business modes (SfBOnly or SfBWithTeamsCollabAndMeetings). This step is critical to ensure routing of calls and chats from users who move to Teams Only to users who remain on premises.
6. It's recommended at this point (but not yet required until step 11) to [enable Microsoft Entra Connect for the other forest](cloud-consolidation-aad-connect.md) (AcquiredCompany.<span>com). Assuming Microsoft Entra Connect is enabled in both forests, the org looks like **[Figure A](#figure-a)**, which may be a common starting point for some orgs.
7. For any SIP domains hosted by other on-premises deployments (in this case, AcquiredCompany.<span>com), [disable these online SIP domains in your Microsoft 365 organization](/powershell/module/skype/disable-csonlinesipdomain) using `Disable-CsOnlineSipDomain` in the Teams PowerShell Module. 
8. [Configure Skype for Business hybrid](configure-federation-with-skype-for-business-online.md) for OriginalCompany.<span>com (the one deployment that still has enabled online SIP domains).
9. In the hybrid deployment (OriginalCompany.<span>com), start [moving users from Skype for Business on premises to the cloud](move-users-between-on-premises-and-cloud.md) (whether Teams Only or not) so that user is Teams Only. Now the organization looks like **[Figure B](#figure-b)**. The key changes from Figure A are:
    - Users from both on-premises directories are now in Microsoft Entra ID.
    - AcquiredCompany.<span>com is a disabled online SIP domain.
    - Some users have been moved online to Teams Only. (See purple user A.)
10. Once all users are moved to the cloud, [disable hybrid with the Skype for Business on-premises deployment](cloud-consolidation-disabling-hybrid.md) for OriginalCompany.<span>com from Microsoft 365:  
    - Disable split domain in the Microsoft 365 organization.
    - Disable the ability to communicate with Microsoft 365 in OriginalCompany.<span>com on-premises.
    - Update DNS records for OriginalCompany.<span>com to point to Microsoft 365.
11. If not done already, [enable Microsoft Entra Connect for the next forest](cloud-consolidation-aad-connect.md) that will go hybrid (AcquiredCompany.<span>com). At this point, the organization looks like **[Figure C](#figure-c)**. This configuration may be another common starting point for some organizations. 
12. In Teams PowerShell, [enable the SIP domains for the next on-premises deployment](/powershell/module/skype/enable-csonlinesipdomain) that will go hybrid, AcquiredCompany.<span>com. This is done using `Enable-CsOnlineSipDomain`, which is new functionality available as of December 2018.
13. If you're using closed federation, you must add any SIP domains (excluding \*.microsoftonline.com)  of the pure online tenant as Allowed Domains in **same** Microsoft 365. It can take some time before the change takes effect and there's no harm in doing this early, so we suggest doing this well in advance of moving to step 14.
14. Update the on-premises environment to accept any SIP domains from the online tenant, so they match.
    - [Update the SAN in all edge certificates](cloud-consolidation-edge-certificates.md) to be the same value as before, plus values for any existing online SIP domains (except *.microsoftonline.com), in this case, Sip.OriginalCompany.<span>com.
    - Make sure OriginalCompany.<span>com is an [allowed domain](/powershell/module/skype/new-csalloweddomain) in the on-premises deployment, AcquiredCompany. Add allowed domains.
15. [Enable Skype for Business hybrid](configure-federation-with-skype-for-business-online.md) between on-premises AcquiredCompany.<span>com and the cloud.
16. As desired, [migrate users from on-premises to the cloud](move-users-between-on-premises-and-cloud.md) to become [TeamsOnly users](/microsoftteams/teams-and-skypeforbusiness-coexistence-and-interoperability). During this state, the organization looks like **[Figure D](#figure-d)**.
17. Once all users are migrated, [disable hybrid with the on-premises environment](cloud-consolidation-disabling-hybrid.md) to *make the organization pure cloud*!

The diagrams below show the configuration at various key points during this process.

##### Figure A

- Both organizations sync via Microsoft Entra Connect, so Microsoft Entra ID now has all users from both on-premises deployments.
- All users homed on-premises.  
- Skype for Business Hybrid isn't* yet configured.
- If users in either deployment use Teams, they won’t be able to federate with each other (or any organization), nor will they have interoperability with any Skype for Business users. While in this stage, Microsoft recommends using Teams for Channels only.<br><br>
    ![Figure A diagram.](../media/cloudconsolidationfiga.png)

##### Figure B

- AcquiredCompany.<span>com is a [disabled](/powershell/module/skype/disable-csonlinesipdomain) online SIP domain. All users are on-premises. If they use Teams, they don't have federation or interoperability. While in this stage, Microsoft recommends using Teams for Channels only.
- Skype for Business Hybrid has been enabled for one of the on-premises organizations.
- Some users in the hybrid organization have been moved to the cloud and are Teams Only(user A as indicated by purple shading). These users Teams Only users have full interoperability and federation support with any other Skype for Business users.

    ![Figure B diagram.](../media/cloudconsolidationfigb.png)

##### Figure C

- All users from OriginalCompany.<span>com are now Teams Only mode in the cloud.
- Skype for Business hybrid configuration with the OriginalCompany.<span>com deployment has been disabled. The on-premises deployment is gone.
- If AcquiredCompany.<span>com wasn’t previously syncing to Microsoft Entra ID, to continue from here it needs to be synced now. But it's not yet hybrid (shared SIP address space). Until the organization is ready to move to hybrid, the online SIP domain for the pure on-premises organization (AcquiredCompany.com) should remain disabled, so that online Teams users can communicate with on-premises users.

    ![Figure C diagram.](../media/cloudconsolidationfigc.png)

##### Figure D

- AcquiredCompany.<span>com is now enabled as an online SIP domain.
- On-premises is updated to accept OriginalCompany.<span>com. (Both allowed domain, and edge certificates are updated).
- Shared SIP Address Space is enabled between AcquiredCompany.<span>com and Microsoft 365 organization.
- Some users in the hybrid organization may have been moved to the cloud, such as User D below (indicated by purple shading).

    ![Figure D diagram.](../media/cloudconsolidationfigd.png)

## Other starting points

The steps in the canonical example above assume that the organization starts with two federated on-premises deployments with no Microsoft 365 presence. However, some organizations may have an existing Microsoft 365 footprint, and there can be different entry points into the sequence above. There are four typical configurations:

- Multiple federated on-premises organizations with no Microsoft 365 organization. In this case, start at step 1.
- Multiple federated on-premises organizations that are already syncing multiple Skype for Business forest into a single Microsoft Entra tenant. Such an organization resembles the hypothetical organization in Figure A, which has completed steps 1-6 and should start at step 7.
- A hybrid organization that federates with one or more other pure on-premises organizations, none of which sync to Microsoft Entra ID. Such an organization would resemble the hypothetical organization in **Figure E**, shown below.
  - This organization is similar to Figure B, which has completed steps 1-9, except:
        - Its nonhybrid Skype for Business deployments are *NOT* yet syncing to Microsoft Entra ID.
        -  Online SIP domains aren't yet disabled.
  - These organizations should either:
        - Complete migration of the existing hybrid organization and enter the above sequence at step 10.  OR,
        - If you want to sync any other Skype for Business forests into Microsoft Entra prior to completing migration of the hybrid organization, then you must perform step 7 to disable all online SIP domains in any other on-premises Skype for Business deployment that will sync into Microsoft Entra ID. Then you must enable Microsoft Entra Connect, and only then continue with step 10 (decommission the original hybrid deployment).

##### Figure E

![Figure E diagram.](../media/cloudconsolidationfige.png)

- A pure Teams Only organization that federates with a separate on-premises Skype for Business organization. Once this organization disables the online SIP domain for the on-premises organization and enables Microsoft Entra Connect for the on-premises Skype for Business organization, it resembles the hypothetical organization shown in **[Figure C](#figure-c)** that has completed steps 1-11.

## Limitations

- There must be at most one Microsoft 365 organization involved. Consolidation in scenarios with more than one organization isn't supported.
- Only one on-premises Skype for Business forest can be in hybrid mode (shared SIP address space) at a time. All other on-premises Skype for Business forests must remain purely on-premises and should be federated with each other and the Microsoft 365 organization.
- Prior to being migrated to the cloud, there's an asymmetric experience for users in this deployment, because not all users in online are represented on-premises.
  - The experience can be summed up as follows:
    - Any user homed online will interact with on-premises users in the hybrid environment as if the user is hybrid.
    - On-premises users in the hybrid deployment will interact with online users who are represented in their on-premises directory as if they were hybrid.
    - On-premises users in the hybrid deployment will interact with online users who aren't represented in on-premises AD as federated.
    - In **[Figure D](#figure-d)** above, user E is on-premises in AcquiredCompany.<span>com.  User E will interact with User D (homed online) using the standard hybrid experience,  but user E will have a federated experience with users A, B, and C because they aren't represented in the on-premises directory. However, users A, B, and C will interact with user E as if the user were in hybrid.
    - Implications of interaction being hybrid vs. federation:
      - Presence isn't automatically subscribed to for federated users unless the user is marked as a contact.
      - Call forwarding doesn't work between federated domains.
      - Call transfer scenarios are more limited.
      - Throttling may be applied to federated traffic.
- Given this experience, support for calling functionality in cross-premises scenarios between an on-premises user and a cloud user that isn't in the on-premises directory is limited to peer only.
  - Call forwarding, transfer, call queues, etc. between these users isn't supported.
  - These nonsupported calling scenarios will still appear enabled, but in many cases they'll fail in unpredictable ways.
  - In **[Figure D](#figure-d)** above, user E is on-premises, and calls with users A, B, or C will be supported only as peer to peer. (Calls with user D wouldn't have support limitations.)  However, after the on-premises user E is moved to the cloud, this restriction no longer applies.
- If you have more than one deployment of Skype for Business Server 2019 in your environment, only one of those deployments can be configured to use Organizational Auto Attendant, since that feature requires Skype for Business Server hybrid configuration.
- The order of some of the previous steps can be adjusted. The key requirement is that if all of these are true:
  - More than one on-premises Skype for Business forest syncing to a single Microsoft 365 tenant in Microsoft Entra ID.
  - Split domain is enabled with one on-premises forest.
  - At least one user in the hybrid organization has been migrated to the cloud. Then, you *must* disable all other online SIP domains from any other on-premises Skype for Business forest. Otherwise, federation between online users in the hybrid organization and on-premises users in other organizations will break in one direction.

## Implications

- Because there are limitations in support for advanced calling functionality as described above, **organizations should treat these asymmetric states as transitory as part of migration, and not pursue them as steady state**.  
- Organizations with multiple on-premises Skype for Business deployments should generally start with a deployment that can be fully migrated to the cloud, so that consolidation can continue. It's understood that in some cases there will be holdouts of certain user groups for whom it’s not yet viable to move to Teams. When this is a consideration in scenarios involving multiple Skype for Business forests, start migrating with another forest that doesn't have these limitations, if at all possible.
- When moving from on-premises to the cloud, users that have delegation relationships and/or are typically are involved in call forwarding scenarios should be moved together as a unit.

## Considerations for moving to TeamsOnly mode

When you move users from on premises to the cloud in a hybrid environment, these users become Teams Only users.

- When you assign TeamsOnly mode to a user, all chats and calls from any other user will land in that user’s Teams client.
- If users with Skype for Business on-premises primarily use Skype for Business client and not Teams, consider setting TeamsUpgradePolicy so that routing to those on-premises users always lands in Skype for Business instead of Teams. To ensure proper routing of chats and calls between users who are TeamsOnly and users who are still using Skype for Business on premises, on-premises users must have an effective value of TeamsUpgradePolicy with one of the Skype for Business modes, rather than Islands (which is the default).
  - *You must first set your tenant’s global instance of TeamsUpgradePolicy to one of these values*:
        - SfBWithTeamsCollab (recommended)
        - SfBWithTeamsCollabAndMeetings
        - SfBOnly
  - You can grant tenant-wide policy by using this command:<br>`Grant-CsTeamsUpgradePolicy -PolicyName SfBWithTeamsCollab -Global`
  - Note: You must do this step at a tenant-wide level because policy can't be assigned to individual users who don't have a SIP address in the online directory. While you have disabled online SIP domains for your pure on-premises deployment(s), users in those domains won’t have SIP addresses in the online directory by design. Hence, the only way to apply policy to those on-premises users is by assigning at the tenant level. In the hybrid deployment, users will have a SIP address in the online directory so they can be explicitly assigned a policy if it’s desired that they have a different value than the tenant global policy.

## See also

[Update the edge certificate](cloud-consolidation-edge-certificates.md)

[Update Microsoft Entra Connect to include more than one forest](cloud-consolidation-aad-connect.md)

[Disable hybrid to complete migration to the cloud](cloud-consolidation-disabling-hybrid.md)
