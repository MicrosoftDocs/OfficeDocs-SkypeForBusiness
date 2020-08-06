---
title: Overview of security and compliance
author: MicrosoftHeidi
ms.author: heidip
manager: serdars
ms.topic: conceptual
ms.service: msteams
ms.reviewer: anach
audience: admin
description: An overview of Microsoft Teams security and compliance features including privacy and encryption, auditing and reporting, and more.
localization_priority: Normal
search.appverid: MET150
ms.collection: 
  - M365-collaboration
  - remotework
f1.keywords:
  - CSH
ms.custom: 
  - ms.teamsadmincenter.dashboard.helparticle.securityandcompliance
  - seo-marvel-apr2020
  - seo-marvel-jun2020
appliesto: 
  - Microsoft Teams
---

# Security and compliance in Microsoft Teams

> [!IMPORTANT]
> To learn how to best ensure **security while everyone's working from home during the COVID-19 outbreak**, read these articles:
>  - [Top 12 tasks for security teams to support working from home](https://docs.microsoft.com/microsoft-365/security/top-security-tasks-for-remote-work)
>  - [Optimize Office 365 connectivity for remote users using VPN split tunnelling](https://docs.microsoft.com/Office365/Enterprise/office-365-vpn-split-tunnel)
>  - Updated April 2, 2020: [Teams security guide](teams-security-guide.md)


Microsoft Teams is built on the Office 365 hyper-scale, enterprise-grade cloud, delivering the advanced security and compliance capabilities our customers expect. For more information on planning for security in Office 365, please review our Office 365 content. [The Office 365 security roadmap](https://docs.microsoft.com/microsoft-365/security/office-365-security/security-roadmap) is a good place to start. For more information on planning for compliance in Office 365, you can start with [the plan for security and compliance](https://docs.microsoft.com/microsoft-365/compliance/plan-for-security-and-compliance) article.


This article will provide further information about Teams-specific security and compliance. Don't miss these Microsoft Mechanics videos about security and compliance:

- [Microsoft Teams Essentials for IT: Security and Compliance](https://youtu.be/91lHNKVVvQ4) (12:42 min)
- [Microsoft Teams Controls for Security and Compliance](https://www.youtube.com/watch?v=Km4T4hMM__k) (10:54 min)

> [!IMPORTANT]
> As a customer of Office 365, you own and control your data. Microsoft does not use your data for anything other than providing you with the service that you have subscribed to. As a service provider, we do not scan your email, documents, or teams for advertising or for purposes that are not service-related. Microsoft doesn't have access to uploaded content. Like OneDrive for Business and SharePoint Online, customer data stays within the tenant. You can check out more about our trust and security related information at the [Microsoft Trust Center](https://microsoft.com/trustcenter). Teams follows the same guidance and principles as the Microsoft Trust Center.

## Security

Teams enforces team-wide and organization-wide two-factor authentication, single sign-on through Active Directory, and encryption of data in transit and at rest. Files are stored in SharePoint and are backed by SharePoint encryption. Notes are stored in OneNote and are backed by OneNote encryption. The OneNote data is stored in the team SharePoint site. The Wiki tab can also be used for note taking and its content is also stored within the team SharePoint site.

Read [Identity models and authentication](identify-models-authentication.md) for more insight into authentication and Teams, and [How modern authentication works](sign-in-teams.md) will help with modern authentication in particular.

Because Teams works in partnership with SharePoint, OneNote, Exchange, and more, you should be comfortable managing security in Office 365 all-up. To learn more about Office 365 security, read [Configure your Office 365 organization for increased security](https://docs.microsoft.com/office365/securitycompliance/tenant-wide-setup-for-increased-security).

> [!NOTE]
> Currently, [private channels](private-channels.md) supports limited security and compliance features. Support for the full set of security and compliance features in private channels is coming soon.

### Advance Threat Protection (ATP)

Advance Threat protection (ATP) is available for Microsoft Teams, along with SharePoint and OneDrive for Business, applications that integrate with Teams for content management. ATP allows you to determine if content in these applications is malicious in nature, and block this content from user access.

How the affected content is managed after detection is up to the settings you've selected in Office 365. We strongly recommend you consider all applications when it comes to configuring ATP, and for further reading, the [Office 365 ATP for SharePoint, OneDrive, and Microsoft Teams](https://docs.microsoft.com/microsoft-365/security/office-365-security/atp-for-spo-odb-and-teams) article will have detailed information on how to get started.

### Safe Links

While, at this time, Advanced Threat Protection (ATP) safe links are not available in Microsoft Teams, they are now in [public preview](https://docs.microsoft.com/microsoft-365/security/office-365-security/atp-safe-links-for-teams?view=o365-worldwide) through our Technology Adoption Program (TAP), and while a release date for general availability isn't set, we'll update this article when that time arrives. Meanwhile, for information on Office 365 Safe Links, please review [Office 365 ATP Safe Links](https://docs.microsoft.com/office365/securitycompliance/atp-safe-links#how-to-get-atp-safe-links-protection). ATP Safe links is available in both [ATP Plan 1 and ATP Plan 2](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp?view=o365-worldwide).

### Safe Attachments

Safe attachments is a feature designed to enhance user security by checking for, and detecting, malicious attachments. Global- or Security Administrators create [policies](https://docs.microsoft.com/microsoft-365/security/office-365-security/set-up-atp-safe-attachments-policies?view=o365-worldwide) for handling these suspected malicious attachments to prevent them from being sent to users, clicked, and acted upon. Safe attachment protection is available to SharePoint Online, OneDrive for Business, and Microsoft Teams, and both Office 365 [Advanced Threat Protection Plan 1 and 2](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp?view=o365-worldwide) have this capability. Read more about Safe Attachments and how they can help protect your organization [here](https://docs.microsoft.com/microsoft-365/security/office-365-security/atp-safe-attachments?view=o365-worldwide).

### How Conditional Access policies work for Teams

Microsoft Teams relies heavily on Exchange Online, SharePoint Online, and Skype for Business Online for core productivity scenarios, like meetings, calendars, interop chats, and file sharing. Conditional access policies that are set for these cloud apps apply to Microsoft Teams when a user directly signs in to Microsoft Teams - on any client.

Microsoft Teams is supported separately as a cloud app in Azure Active Directory conditional access policies. Conditional access policies that are set for the Microsoft Teams cloud app apply to Microsoft Teams when a user signs in. However, without the correct policies on other apps like Exchange Online and SharePoint Online, users may still be able to access those resources directly. For more information about setting up a conditional access policy in the azure portal, go to: [Azure Active Directory Quickstart](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started).

Microsoft Teams desktop clients for Windows and Mac support modern authentication. Modern authentication brings sign-in based on the Azure Active Directory Authentication Library (ADAL) to Microsoft Office client applications across platforms.

Microsoft Teams desktop application supports AppLocker.  For more information about AppLocker prerequisites, please see: Requirements to use [AppLocker](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/applocker/requirements-to-use-applocker).

## Compliance

Teams has a wide range of information to help you with compliance areas, including communication compliance for channels, chats, and attachments, retention policies, Data Loss Protection (DLP), eDiscovery and legal hold for channels, chats and files, audit log search, as well as mobile application management with Microsoft Intune. We've provided some information on all these topics below, and you can go to the [Microsoft 365 Compliance Center](https://compliance.microsoft.com) to manage these settings.

### Information Barriers

Information barriers are policies put in-place by Teams administrators to do things like keep people or groups from communicating with one another (when there is no business need for them to do so, or a regulatory reason to block them from doing so), and it also allows you to set policies relating to things like lookups and eDiscovery (covered below). These policies can impact users in 1:1 chats, group chats, or at a team-level.

For further reading on this topic, go to [Information barriers in Microsoft Teams](information-barriers-in-teams.md).

### Communication compliance

Communication compliance in Microsoft 365 allows you to add users to in-scope policies that can be configured to examine Microsoft Teams communications for offensive language, sensitive information, and information related to internal and regulatory standards. Chat communications and associated attachments in both public and private Teams channels, individual chats, and attachments can be scanned to help minimize communication risks in your organization. For more information on how you can configure policies to help you detect, capture, and take action for inappropriate Teams communications, see [Communication compliance in Microsoft 365](https://docs.microsoft.com/microsoft-365/compliance/communication-compliance).

### Retention Policies

Retention policies in Microsoft Teams allows you to both retain data that's important for your organization to keep, for regulatory, legal, business, or other reasons, and also to remove content and communications that are not relevant to be retained. You can also use retention policies to keep data for a period of time and then delete it. For further information, review the [Retention policies in Microsoft Teams](retention-policies.md) article.

### Data Loss Prevention (DLP)

Data Loss Prevention (DLP) in Microsoft Teams, as well as the larger DLP story for Office 365, revolves around business readiness when it comes to protecting sensitive documents and data in Office 365. Whether you have concerns around sensitive information in messages or documents, DLP policies will be able to help ensure your users don't share this sensitive data with the wrong people.

For information on Data Loss Prevention in Teams, please review [DLP for Microsoft Teams](https://docs.microsoft.com/microsoft-365/compliance/dlp-microsoft-teams). A good article for O36 DLP concerns is [Overview of data loss prevention](https://docs.microsoft.com/microsoft-365/compliance/data-loss-prevention-policies).

### eDiscovery

Electronic discovery, or eDiscovery, is the electronic aspect of identifying, collecting and producing electronically stored information (ESI) in response to a request for production in a law suit or investigation. Capabilities include case management, preservation, search, analysis, and export of Teams data. This includes chat, messaging and files, meeting and call summaries. For Teams meetings and Calls, a summary of the events that happened in the meeting and call are created and made available in eDiscovery.

For more details about how to do Office 365 eDiscovery in Security & Compliance Center and run compliance content search for Teams content, please go to the links below:

[eDiscovery](https://docs.microsoft.com/microsoft-365/compliance/manage-legal-investigations)

[Content Search](https://docs.microsoft.com/microsoft-365/compliance/search-for-content)

We have a Teams-specific article for more information, [eDiscovery of guest-to-guest chats](eDiscovery-investigation.md).

Customers can leverage eDiscovery or [Advanced eDiscovery](https://docs.microsoft.com/microsoft-365/compliance/office-365-advanced-ediscovery) per their requirements. The following table outlines the differences between the two:

| |eDiscovery  |Advanced eDiscovery  |
|---------|---------|---------|
|Case Management     |X        |X         |
|Access Control  |X         |X         |
|Content Searches     |X         | X        |
|Hold(s)   |X         | X        |
|Export     |X         |X         |
|Duplication Detection     |-         |X         |
|Relevance Searches with Machine Learning    |-         |X         |
|Unstructured Data Analysis      |-         |X         |

### Legal Hold

During litigation, you may need all data associated with a user (custodian) or a Team to be preserved as immutable, so that it can be used as evidence for the case. You can do this by placing either a user (user mailbox) or a Team on legal hold. For a team legal hold, the team's mailbox can be put on the following holds:

- In-Place Hold (a subset of the mailbox or site collection through targeted queries or filtered content is put on hold), or
- Litigation Hold (the entire mailbox or site collection is placed on hold).

In either case, once the hold is set it ensures that, even if end users delete or edit channel messages that are in the group mailbox, immutable copies of that content are maintained and available through eDiscovery search. Legal holds are generally applied within the context of an eDiscovery case.

Please see the [Overview of retention policies](https://docs.microsoft.com/microsoft-365/compliance/retention-policies) article to understand more about preservation and holds in the Microsoft 365 Compliance Center. For more Teams-specific information on legal hold, we also have our [Place a Microsoft Teams user or team on legal hold](legal-hold.md) article for you to learn more.

### Compliance Content Search

Content search can be used to search for all Teams data through rich filtering capabilities. The resulting data can be exported to a specific container for compliance and litigation support. This can be done with or without an eDiscovery case. This enables compliance admins to gather Teams data across all users, review and export it for further processing. Please refer to this [Content Search in Office 365](https://docs.microsoft.com/microsoft-365/compliance/content-search) article to learn more about how to conduct a compliance content search for Microsoft Teams and other Microsoft 365 or Office 365 content in the Microsoft 365 Compliance Center.

> [!TIP]
> Using content search, you can filter down to Microsoft Teams only content, such as Chat and Channel Messages, Meetings, and Calls, if necessary.

If you'd like further Teams-specific information on configuring content search, review the [Content search in Microsoft Teams](content-search.md) article.

### Auditing and Reporting

Audit log search plugs right into the Microsoft 365 Compliance Center and gives you the ability to set alerts, as well as report on audit events, by allowing the export of workload specific or generic event sets for admin use and investigation across an unlimited auditing timeline. You can set up alerts for all audit Log data within the Microsoft 365 Compliance Center, and filter and export this data for further analysis. Please refer to the [Search the audit log](https://docs.microsoft.com/microsoft-365/compliance/search-the-audit-log-in-security-and-compliance) article to learn more about how to conduct an Audit log for Office 365. To learn more about searching for Microsoft Teams events in the Microsoft 365 Compliance Center, we also have the [Turn on auditing in Teams](audit-log-events.md) article for you to review.

## Privacy

At Microsoft, protecting your data is our highest priority. To learn about our privacy practices, read:  

- [Privacy at Microsoft](https://www.microsoft.com/trust-center/privacy)
- [Our commitment to privacy and security in Microsoft Teams](https://www.microsoft.com/en-us/microsoft-365/blog/2020/04/06/microsofts-commitment-privacy-security-microsoft-teams/)
- [For IT professionals: Privacy and security in Microsoft Teams](https://www.microsoft.com/en-us/microsoft-365/blog/2020/04/06/it-professionals-privacy-security-microsoft-teams/#:~:text=We%20safeguard%20your%20privacy%20by,and%20distribution%20of%20your%20data.)

## Information Protection Architecture

The following figure indicates the ingestion flow of Teams data to both Exchange and SharePoint for Teams Files and Messages.

![Diagram of the workflow of Teams data to Exchange and SharePoint](media/Overview_of_security_and_compliance_in_Microsoft_Teams_image1.png)

The following figure indicates the ingestion flow of Teams Meetings and calling data to Exchange.

![Diagram of the workflow of Teams Meetings and calling data to Exchange](media/Overview_of_security_and_compliance_in_Microsoft_Teams_image1a.png)

> [!IMPORTANT]
> There can be up to a 24-hour delay to discover Teams content.

## Licensing

When it comes to information protection capabilities, Microsoft 365 subscriptions, Office 365 subscriptions, and the associated standalone licenses will determine the available feature set.

For information on determining the licensing needs to implement features for security and compliance, please review [Licensing for Office 365 or Microsoft 365](https://download.microsoft.com/download/8/7/7/877B1713-671E-43AA-BB79-AF8478C64AFF/Licensing-Microsoft-365.pdf).

> [!NOTE]
> Content Search and eDiscovery do not need to be enabled in the Security & Compliance Center to work.

## Location of data in Teams

Data in Teams resides in the geographic region associated with your Office 365 organization. To see what regions are supported currently, please review [Location of data in Microsoft Teams](location-of-data-in-teams.md).

If you need to see which region houses data for your tenant, go to the [Microsoft 365 admin center](https://portal.office.com/adminportal/home) > **Settings** > **Organization profile**. Scroll down to **Data location**.

![Screenshot of Data location table including Teams in the admin center](media/Overview_of_security_and_compliance_in_Microsoft_Teams_image5.png)

## Compliance standards

Teams uses the following standards: [ISO 27001](https://docs.microsoft.com/microsoft-365/compliance/offering-iso-27001), [ISO 27018](https://docs.microsoft.com/microsoft-365/compliance/offering-iso-27018), [SSAE16 SOC 1 and SOC 2](https://docs.microsoft.com/microsoft-365/compliance/offering-soc), and [EU Model Clauses (EUMC)](https://docs.microsoft.com/microsoft-365/compliance/offering-eu-model-clauses). Microsoft Teams is also fully compliant with [HIPAA](https://docs.microsoft.com/microsoft-365/compliance/offering-hipaa-hitech) standards. Within the Microsoft compliance framework, Microsoft classifies Office 365 applications and services into four categories. Each category is defined by specific compliance commitments that must be met for an Office 365 service, or a related Microsoft service, to be listed in that category.

Details can be found in the [Data Protection Resources](https://servicetrust.microsoft.com/ViewPage/TrustDocumentsV3?command=Download&downloadType=Document&downloadId=b7d05b86-c69b-41ba-8245-21161b9febf9&tab=7f51cb60-3d6c-11e9-b2af-7bb9f5d2d913&docTab=7f51cb60-3d6c-11e9-b2af-7bb9f5d2d913_Compliance_Guides). Teams also supports Cloud Security Alliance compliance.

## Related topics

[Microsoft 365 Security](https://docs.microsoft.com/microsoft-365/security/)
[Microsoft 365 Compliance](https://docs.microsoft.com/microsoft-365/compliance/)
[Microsoft compliance offerings](https://docs.microsoft.com/microsoft-365/compliance/offering-home)
