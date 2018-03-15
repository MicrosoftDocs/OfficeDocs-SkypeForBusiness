---
title: Overview of security and compliance in Microsoft Teams
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 09/25/2017
ms.topic: article
ms.service: msteams
ms.reviewer: anach
description: An overview of security and compliance features of Microsoft Teams including auditing and reporting, compliance content search, eDiscovery, and more.
MS.collection: Strat_MT_TeamsAdmin
appliesto: 
- Microsoft Teams
---

Overview of security and compliance in Microsoft Teams
======================================================

Microsoft Teams is built on the Office 365 hyper-scale, enterprise-grade cloud, delivering the advanced security and compliance capabilities our customers expect.

Teams is Tier C-compliant at launch. This includes the following standards: ISO 27001, ISO 27018, SSAE16 SOC 1 and SOC 2, HIPAA, and EU Model Clauses (EUMC). Within the Microsoft compliance framework, Microsoft classifies Office 365 applications and services into four categories. Each category is defined by specific compliance commitments that must be met for an Office 365 service, or a related Microsoft service, to be listed in that category.

Services in compliance categories C and D that have industry-leading compliance commitments are enabled by default. Services in categories A and B come with controls to turn on or turn off these services for an entire organization. Details can be found in the [Compliance Framework for Industry Standards and Regulations](https://go.microsoft.com/fwlink/?linkid=855777). Teams also supports Cloud Security Alliance compliance.

Teams also enforces team-wide and organization-wide two-factor authentication, single sign-on through Active Directory, and encryption of data in transit and at rest. Files are stored in SharePoint and are backed by SharePoint encryption. Notes are stored in OneNote and are backed by OneNote encryption.

We also added support for audit log search, eDiscovery and legal hold for channels, chats and files as well as mobile application management with Microsoft Intune.

These tools reside in the Office 365 Security and Compliance Portal and provide the following features:

-   Auditing and Reporting

    -   Audit log search plugs right into the Office 365 Security and Compliance Center and exposes abilities to set alerts and/or report on Audit event by making available, export of workload specific or generic event sets for admin use and investigation, across an unlimited auditing timeline. All Audit Log data is available for setting up of alerts within the Office 365 Security and Compliance Center, as well as for filtering and export for further analysis.

-   Compliance Content Search

    -   Content Search can be used to search Teams through rich filtering capabilities and exported to a specific container for compliance and litigation support. This can be done with or without an eDiscovery case.

-   eDiscovery

    -   Electronic discovery is the electronic aspect of identifying, collecting and producing electronically stored information (ESI) in response to a request for production in a law suit or investigation.

    -   Capabilities include case management, preservation, search, analysis and export of Teams data. This includes chat, messaging and file data.

    -   Customers can leverage in-place eDiscovery or [Advanced eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)

    -   The following table outlines the differences between the two:


| |In-place eDiscovery  |Advanced eDiscovery  |
|---------|---------|---------|
|Case Management     |X        |X         |
|Access Control  |X         |X         |
|Content Searches     |X         | X        |
|Hold(s)   |X         | X        |
|Export     |X         |X         |
|Duplication Detection     |-         |X         |
|Relevance Searches with Machine Learning    |-         |X         |
|Unstructured Data Analysis      |-         |X         |


-   Legal Hold

    -   When any team within Teams is put on In-Place Hold or Litigation Hold, the hold is placed on the groups mailbox.

    -   Legal Holds are generally applied within the context of an eDiscovery case.

The figure below indicates the workflow of Teams data to both Exchange and SharePoint.

![Diagram of the workflow of Teams data to Exchange and SharePoint.](media/Overview_of_security_and_compliance_in_Microsoft_Teams_image1.png)


> [!IMPORTANT]
> There can be up to a 24-hr delay to discover Teams content.

Additionally, Microsoft is considering providing the following security features for Teams. Once available, guidance will be provided on how customers can leverage the features:

-   Tenant-specific retention Policy

-   Data loss prevention (DLP)

-   Customer Lockbox

-   Rights Management


| | | |
|---------|---------|---------|
|![Decison Point icon.](media/Overview_of_security_and_compliance_in_Microsoft_Teams_image3.png)     |Decision point         |What security and compliance features does your organization require? Does your organization have the required licenses to meet Security and Compliance business requirements?         |
|![Next Steps icon.](media/Overview_of_security_and_compliance_in_Microsoft_Teams_image4.png)     |Next steps         |Document the required security and compliance features in the table below.         |

Licensing
---------------

When it comes to the information protection capabilities, Office 365 subscriptions and the associated standalone licenses will determine the available feature set.

|Information Protection Capability   |Office 365 Business Essentials   |Office 365 Business Premium   |Office 365 Enterprise E1   |Office 365 Enterprise E3/E4   |Office 365 Enterprise E5   |
|---|---|---|---|---|---|
|Archive|-  |-   |-   |Yes   |Yes   |
|In-Place eDiscovery|-   |-   |-   |Yes   |Yes   |
|Advanced eDiscovery|-   |-   |-   |-   |Yes   |
|Legal Hold|-   |-   |-   |Yes   |Yes   |
|Compliance Content Search|- |- |- |Yes |Yes |
|Auditing and Reporting|Yes |Yes |Yes |Yes |Yes |
|Conditional Access* |Yes |Yes |Yes |Yes |Yes |
\*Conditional Access requires additional licenses


| |  |  |
|---------|---------|---------|
|![Decision Point icon.](media/Overview_of_security_and_compliance_in_Microsoft_Teams_image3.png)     |Decision point         |Does your organization have the required licenses to meet Compliance and Security business requirements?         |
|![Next Steps icon.](media/Overview_of_security_and_compliance_in_Microsoft_Teams_image4.png)    |Next steps         |Review your organizations current licensing and confirm it meets all business requirements for compliance and security.         |

Before enabling any of these features, ensure you have access to the Security & Compliance Center in the Office 365 Admin center. By default, tenant admins have access.

Content Search and eDiscovery do not require enablement within the Security & Compliance Center.

Location of data in Teams
-------------------------

Data in Teams resides in the geographic region associated with your Office 365 tenant. Currently, Teams supports the Americas, EMEA, and APAC regions. 

> [!IMPORTANT]
> Teams currently offers data residency in the United Kingdom and India for new tenants only. 
> A new tenant is defined as any tenant that hasn’t had a single user from the tenant sign in to Teams. Existing tenants from the UK and India will continue to remain in the EMEA and APAC regions respectively, until a migration plan is announced (anticipated in 2018).

To learn more about the launch of India and UK data residency for Teams, read Ansuman Acharya's blog post, [Microsoft Teams launches India Data Residency, other geos coming soon](https://go.microsoft.com/fwlink/?linkid=867773).

To see which region houses data for your tenant, go to the [Office 365 Admin center](https://portal.office.com/adminportal/home) > **Settings** > **Organization profile**. Scroll down to **Data location**. 

![Screenshot of the Data location table, including Teams, in the Office 365 Admin center.](media/Overview_of_security_and_compliance_in_Microsoft_Teams_image5.png)

Privacy in Teams
--------------------------

As a customer of Office 365, you own and control your data. Microsoft does not use your data for anything other than providing you with the service that you have subscribed to. As a service provider, we do not scan your email, documents, or teams for advertising or for purposes that are not service-related. Microsoft doesn’t have access to uploaded content. Like OneDrive for Business and SharePoint Online, customer data stays within the tenant.

Check out more about our trust and security related information at the [*Office 365 Trust Center*](https://go.microsoft.com/fwlink/?linkid=855779). Teams follows the same guidance and principles as the Office 365 Trust Center.
