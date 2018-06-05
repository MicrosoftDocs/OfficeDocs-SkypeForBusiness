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
localization_priority: Priority
MS.collection: Strat_MT_TeamsAdmin
appliesto: 
- Microsoft Teams
---

Overview of security and compliance in Microsoft Teams
======================================================

Microsoft Teams is built on the Office 365 hyper-scale, enterprise-grade cloud, delivering the advanced security and compliance capabilities our customers expect.

Teams is Tier C-compliant at launch. This includes the following standards: ISO 27001, ISO 27018, SSAE16 SOC 1 and SOC 2, HIPAA, and EU Model Clauses (EUMC). Within the Microsoft compliance framework, Microsoft classifies Office 365 applications and services into four categories. Each category is defined by specific compliance commitments that must be met for an Office 365 service, or a related Microsoft service, to be listed in that category.

Services in compliance categories C and D that have industry-leading compliance commitments are enabled by default. Services in categories A and B come with controls to turn on or turn off these services for an entire organization. Details can be found in the [Compliance Framework for Industry Standards and Regulations](https://go.microsoft.com/fwlink/?linkid=855777). Teams also supports Cloud Security Alliance compliance.

Teams also enforces team-wide and organization-wide two-factor authentication, single sign-on through Active Directory, and encryption of data in transit and at rest. Files are stored in SharePoint and are backed by SharePoint encryption. Notes are stored in OneNote and are backed by OneNote encryption. The OneNote data is stored in the team SharePoint site. The Wiki tab can also be used for note taking and it's content is also stored within the team SharePoint site.

We also added support for audit log search, eDiscovery and legal hold for channels, chats and files as well as mobile application management with Microsoft Intune. Go to the Office 365 Security & Compliance center to manage these settings. 

## Auditing and Reporting

Audit log search plugs right into the Office 365 Security and Compliance Center and exposes abilities to set alerts and/or report on Audit event by making available, export of workload specific or generic event sets for admin use and investigation, across an unlimited auditing timeline. All Audit Log data is available for setting up of alerts within the Office 365 Security and Compliance Center, as well as for filtering and export for further analysis.

## Compliance Content Search

Content Search can be used to search Teams through rich filtering capabilities and exported to a specific container for compliance and litigation support. This can be done with or without an eDiscovery case.

## eDiscovery

Electronic discovery is the electronic aspect of identifying, collecting and producing electronically stored information (ESI) in response to a request for production in a law suit or investigation.

Capabilities include case management, preservation, search, analysis, and export of Teams data. This includes chat, messaging and file data.

Customers can leverage in-place eDiscovery or [Advanced eDiscovery](https://support.office.com/article/Office-365-Advanced-eDiscovery-fd53438a-a760-45f6-9df4-861b50161ae4)

The following table outlines the differences between the two:


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


## Legal Hold

When any team within Teams is put on In-Place Hold or Litigation Hold, the hold is placed on the groups mailbox.

Legal Holds are generally applied within the context of an eDiscovery case.

The figure below indicates the workflow of Teams data to both Exchange and SharePoint.

![Diagram of the workflow of Teams data to Exchange and SharePoint.](media/Overview_of_security_and_compliance_in_Microsoft_Teams_image1.png)


> [!IMPORTANT]
> There can be up to a 24-hr delay to discover Teams content.


## Retention policies

Teams conversations are persistent and retained forever by default. With the introduction of Retention policies, admins can configure retention policies (both preservation and deletion) in the Security & Compliance center for Teams chat and channel messages. This helps organizations either retain data for compliance (namely, preservation policy) for a specific period or get rid of data (namely, deletion policy) if it is considered a liability after a specific period. Teams retention policies ensure that when you delete data, it is removed from all permanent data storage locations on the Teams service. 

To manage Teams Retention policies works use the settings and cmdlets in the Office 365 Security & compliance center under **Data Governance** > **Retention**.

Teams Retention Policies do support: 
    
- Preservation: Keep Teams data for a specified duration and then do nothing
- Preservation and then delete: Keep Teams data for a specified duration and then delete
- Deletion: Delete Teams data after a specified duration

Teams Retention Policies do not yet support:

- Advanced Retention policies don't apply to Teams chat and Teams channel message locations
- Duration of fewer than 30 days

Admins can set up separate retention policies for Teams private chats (1:1 or 1:Many chats) and Teams channel messages. In many cases, organizations consider private chat data as more of a liability than channel messages, which are usually more project-related conversations. Set up these policies in the Security & Compliance center, **Data governance** > **Retention**. Turn on **Teams channel messages** and **Teams chats** and then define retention policies for these locations (also shown in the diagram below). 

When you turn on **Teams channel messages**, you can specify Teams to which this policy will apply. For example, for teams X, Y, and Z, the admin can set the deletion policies for 1 year (by selecting those teams individually), and apply a 3-year deletion policy to the rest of the teams. 

You can do the same thing for **Teams chats** by selecting specific users and applying unique retention policies. 

![Diagram of the workflow of Teams data to Exchange and SharePoint.](media/Retention-Policies.png)


> [!IMPORTANT]
> The Teams Channel message locations and Teams chats locations only address the Teams conversations stored in Exchange Online mailboxes (user and group mailboxes). The messages are deleted from all relevant storage locations, namely the mailboxes, substrate, and chat service. 
> 
> To manage retention policies for Teams Files, which are stored in OneDrive for Business and SharePoint, use their retention policies.




By design, deletion policies for Teams files are configured through SharePoint Online and OneDrive for Business locations. As a result, it's possible that a policy could delete a file referenced in a Teams chat or channel message before those messages get deleted. In this case, the file will still show up in the Teams message, but if you click the file, you'll get a "File not found" error (this could also happen in the absence of a policy, if someone manually deletes a file from SharePoint Online or OneDrive for Business).


For detailed information about configuring retention policies for Office 365, read [Overview of retention policies](https://support.office.com/article/overview-of-retention-policies-5e377752-700d-4870-9b6d-12bfc12d2423).
 

## Retention policies FAQ

### What types of policies can I setup in Retention policies and how do they work?

In the Security & compliance center, when you set up a retention policy, for Teams or for any other workload, you can set up two main types of policies: 
- Preservation: These policies ensure that your data is preserved for a given period of time, no matter what happens in the end user tools. They ensure that data is preserved for compliance reasons and available in eDiscovery until this time expires. After the time expires, your policy can indicate whether to do nothing or delete the data. In Teams, if you create a preservation policy for 7 years, even if end users delete their Teams messages, these messages are still preserved for eDiscovery for 7 years.
- Deletion: These policies ensure that data is not a liability for your organization. After the specified duration, data is deleted from all relevant storage in Teams. 

### Can we include Teams in org-wide policies? 

No, not currently. You must create specific policies for Teams chat and channel messages using the Teams location row or these Teams cmdlets: [New-TeamsRetentionCompliancePolicy](https://docs.microsoft.com/en-us/powershell/module/exchange/policy-and-compliance-retention/new-teamsretentioncompliancepolicy?view=exchange-ps) & [New-TeamsComplianceRetentionRule](https://docs.microsoft.com/en-us/powershell/module/exchange/policy-and-compliance-retention/new-teamsretentioncompliancerule?view=exchange-ps). These cmdlets have get and set versions as well.

### Are these retention policies retroactive? 

Yes, they are. If you create a retention policy to delete data older than 60 days, it will delete Teams data created more than 60 days ago. 

### What is the default retention policy? 

By default, Teams chat, channel, and files data are retained forever. A user can delete something, but in the absence of retention policies, Teams data is always archived into Exchange online mailboxes (user and group) and stays there for eDiscovery. 

### Can I target sets of users or teams in a policy? 

Yes, you do. In the policy creation wizard, in the Locations step, you can include or exclude teams (**Teams channel messages**) or users (**Teams chat**) and create targeted policies for your organization. 

### What is the main difference between using the Group mailbox location row and Teams channel messages location row in retention policies? 

If you use the Group mailbox and User mailbox location rows for Exchange Online, Teams data will be deleted from the specified mailboxes. However, this only removes data from the mailbox. It doesn’t delete other Teams data, such as chats service. We recommend that you use Teams retention policies to properly manage all Teams data. A Teams retention policy removes teams data from all storage locations – Mailboxes, Chat service, Teams clients. 

### What happens to Skype for Business Online and Teams interop chats – are they affected by retention policies?

Yes, Skype for Business Online and Teams interop chats work the same way. Once the Skype for Business Online chat comes into Teams, it becomes a message in a Teams chat thread and gets ingested into the appropriate mailbox. So the same flow works – Teams deletion policies will delete these messages from the Teams thread. However, if conversation history is turned on for Skype for Business Online and from the Skype for Business Online client side those are being saved into a mailbox, this chat data is not handled by a Teams retention policy.

### Can I do these through Security & compliance center cmdlets? What should I use? 

Absolutely. You can create Teams retention policies using [Security & compliance center Powershell cmdlets]( https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps). Remember these are not Exchange Online cmdlets. 
Here are the cmdlets we created for Teams. They follow existing nomenclature and style from retention cmdlets available today in Security & compliance center.

|Policy|Rule|
|---|---|
|[New-TeamsRetentionCompliancePolicy](https://docs.microsoft.com/en-us/powershell/module/exchange/policy-and-compliance-retention/new-teamsretentioncompliancepolicy?view=exchange-ps)| [New-TeamsRetentionComplianceRule](https://docs.microsoft.com/en-us/powershell/module/exchange/policy-and-compliance-retention/new-teamsretentioncompliancerule?view=exchange-ps)|
|[Get-TeamsRetentionCompliancePolicy](https://docs.microsoft.com/en-us/powershell/module/exchange/policy-and-compliance-retention/get-teamsretentioncompliancepolicy?view=exchange-ps)| [Get-TeamsRetentionComplianceRule](https://docs.microsoft.com/en-us/powershell/module/exchange/policy-and-compliance-retention/get-teamsretentioncompliancerule?view=exchange-ps)|
|[Set-TeamsRetentionCompliancePolicy](https://docs.microsoft.com/en-us/powershell/module/exchange/policy-and-compliance-retention/set-teamsretentioncompliancepolicy?view=exchange-ps)| [Set-TeamsRetentionComplianceRule](https://docs.microsoft.com/en-us/powershell/module/exchange/policy-and-compliance-retention/set-teamsretentioncompliancerule?view=exchange-ps)|
|[Remove-TeamsRetentionCompliancePolicy](https://docs.microsoft.com/en-us/powershell/module/exchange/policy-and-compliance-retention/remove-teamsretentioncompliancepolicy?view=exchange-ps)| [Remove-TeamsRetentionComplianceRule](https://docs.microsoft.com/en-us/powershell/module/exchange/policy-and-compliance-retention/remove-teamsretentioncompliancerule?view=exchange-ps)|

### If there are multiple retention policies for Teams with varying durations, which one wins?

We follow [Principles of retention policies](https://support.office.com/article/overview-of-retention-policies-5e377752-700d-4870-9b6d-12bfc12d2423), and we recommend that you do too. The short answer is: 
-	Preservation always wins over deletion
-	Longest preservation period always wins
-	Explicit inclusion wins over implicit inclusion in terms of locations
-	Shortest deletion period wins



## Retention policies known issues

1. Under Choose Teams in the Teams Channel messages location row, you may see Office 365 Groups that are not also Teams. This will be addressed in the future.

1. Under Choose Users in the Teams Chat location row, you may see guests and non-mailbox users. Retention policies are not meant to be set for guests, and we are working to remove these from the list. 

1. Exchange Life Cycle assistant (ELC) runs daily, but it has an SLA of 7 days. As a result, it's possible that, if you have a Teams retention policy to delete items older than 60 days, these items could persist for up to 67 days. This isn't a new situation - it follows the Exchange model. Of course, in most cases, there is no delay.


| | | |
|---------|---------|---------|
|![Decison Point icon.](media/Overview_of_security_and_compliance_in_Microsoft_Teams_image3.png)     |Decision point         |What security and compliance features does your organization require? Does your organization have the required licenses to meet Security and Compliance business requirements?         |
|![Next Steps icon.](media/Overview_of_security_and_compliance_in_Microsoft_Teams_image4.png)     |Next steps         |Document your required security and compliance features.         |

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
> [!NOTE]
> \*Conditional Access requires additional licenses


| |  |  |
|---------|---------|---------|
|![Decision Point icon.](media/Overview_of_security_and_compliance_in_Microsoft_Teams_image3.png)     |Decision point         |Does your organization have the required licenses to meet Compliance and Security business requirements?         |
|![Next Steps icon.](media/Overview_of_security_and_compliance_in_Microsoft_Teams_image4.png)    |Next steps         |Review your organization's current licensing and confirm it meets all business requirements for compliance and security.         |

Before enabling any of these features, ensure you have access to the Security & Compliance Center in the Office 365 Admin center. By default, tenant admins have access.

Content Search and eDiscovery do not require enablement in the Security & Compliance Center.

Location of data in Teams
-------------------------

Data in Teams resides in the geographic region associated with your Office 365 tenant. Currently, Teams supports the Americas, EMEA, and APAC regions. 

> [!IMPORTANT]
> Teams currently offers data residency in the United Kingdom and India for new tenants only. 
> A new tenant is defined as any tenant that hasn’t had a single user from the tenant sign in to Teams. Existing tenants from the UK and India will continue to remain in the EMEA and APAC regions respectively, until a migration plan is announced (anticipated in 2018).

To learn more about the launch of India and UK data residency for Teams, read Ansuman Acharya's blog post, [Microsoft Teams launches India Data Residency, other geos coming soon](https://go.microsoft.com/fwlink/?linkid=867773).

To see which region houses data for your tenant, go to the [Office 365 Admin center](https://portal.office.com/adminportal/home) > **Settings** > **Organization profile**. Scroll down to **Data location**. 

![Screenshot of the Data location table, including Teams, in the Office 365 Admin center.](media/Overview_of_security_and_compliance_in_Microsoft_Teams_image5.png)

How do Conditional Access policies work for Teams?
-------------------------

Microsoft Teams relies heavily on Exchange Online, SharePoint Online and Skype for business online for core productivity scenarios, like meetings, calendars, interop chats & file sharing. Conditional access policies that are set for these cloud apps apply to Microsoft Teams when a user signs directly into Microsoft Teams - on any client. 

Microsoft Teams is supported separately as a cloud app in Azure Active Directory conditional access policies. Conditional access policies that are set for the Microsoft Teams cloud app apply to Microsoft Teams when a user signs in. However, without the correct policies on other apps like Exchange Online and SharePoint Online users may still be able to access those resources directly. For more informaton about setting up a conditional access policy in the azure portal, please go here: (https://docs.microsoft.com/en-us/azure/active-directory/active-directory-conditional-access-azure-portal-get-started) 

Microsoft Teams desktop clients for Windows and Mac support modern authentication. Modern authentication brings sign-in based on the Azure Active Directory Authentication Library (ADAL) to Microsoft Office client applications across platforms.

Privacy in Teams
--------------------------

As a customer of Office 365, you own and control your data. Microsoft does not use your data for anything other than providing you with the service that you have subscribed to. As a service provider, we do not scan your email, documents, or teams for advertising or for purposes that are not service-related. Microsoft doesn’t have access to uploaded content. Like OneDrive for Business and SharePoint Online, customer data stays within the tenant.

Check out more about our trust and security related information at the [Office 365 Trust Center](https://go.microsoft.com/fwlink/?linkid=855779). Teams follows the same guidance and principles as the Office 365 Trust Center.
