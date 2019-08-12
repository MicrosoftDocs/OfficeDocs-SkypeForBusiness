---
title: "Microsoft telephony solutions"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 12/20/2018
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- Hybrid 
- M365-voice
- M365-collaboration
- Teams_ITAdmin_Help
- Adm_Skype4B_Online
description: "Describes Microsoft telephony solutions."
---


# Microsoft telephony solutions

Microsoft supports several options as you begin your journey to Teams in the Microsoft cloud. This article helps you decide which Microsoft telephony solution (Phone System in the cloud or Enterprise Voice on-premises) is right for users in your organization, and how your organization can connect to the Public Switched Telephone Network (PSTN). 

You should use this article along with the associated technical diagram, which provides a visual aid for making the right decision for your organization:

- [Microsoft telephony solutions - PDF](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/telephony-solutions/microsoft-telephony-solutions-12-18.pdf)

- [Microsoft telephony solutions - Visio](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/telephony-solutions/microsoft-telephony-solutions-12-18.vsdx)




## Private Branch Exchange (PBX) options

### Phone System (Office 365)
  
Phone System is Microsoft's technology for enabling call control and Private Branch Exchange (PBX) capabilities in the Office 365 cloud with Microsoft Teams and/or Skype for Business Online. 

Phone System works with Teams or Skype for Business Online clients and certified devices. Phone System allows you to replace your existing PBX system with a set of features directly delivered from Office 365 and tightly integrated into the company’s cloud productivity experience. To connect Phone System to the Public Switched Telephone Network (PSTN), you can choose Microsoft’s Calling Plan or your own telephony carrier.

For more information, see [What is Phone System in Office 365](https://docs.microsoft.com/en-us/MicrosoftTeams/what-is-phone-system-in-office-365).

### Enterprise Voice (Skype for Business Server)

Enterprise Voice is Microsoft's technology for enabling call control and Private Branch Exchange (PBX) capabilities in the on-premises Skype for Business Server. This option can only be connected to the Public Switched Telephone Network by using your own telephony carrier. 

For more information, see [Plan for Enterprise Voice in Skype for Business Server](https://docs.microsoft.com/en-us/SkypeForBusiness/plan-your-deployment/enterprise-voice-solution/enterprise-voice?toc=/SkypeForBusiness/toc.json&bc=/SkypeForBusiness/breadcrumb/toc.json).

## Connection to the Public Switched Telephone Network (PSTN) options

You can choose to connect to the Public Switched Telephone Network (PSTN) by:

- Using Microsoft Calling Plan in Office 365 
- Connecting your own telephony carrier

### Calling Plan (Office 365)

This option connects Microsoft’s Office 365 Phone System to the Public Switched Telephone Network (PSTN) to enable calls to landlines and mobile phones around the world. With Calling Plan, Microsoft is your PSTN carrier.

For more information, see [Calling Plans for Office 365](https://docs.microsoft.com/en-us/MicrosoftTeams/calling-plans-for-office-365).

### Connect your own telephony carrier (Office 365 and Skype for Business on-premises)

This option connects either Phone System in Office 365 or Enterprise Voice system in Skype for Business on-premises to your telephony network. This option requires a supported Session Border Controller (SBC). In some cases, this option might require additional Microsoft software deployed on-premises.

## Which solution is right for your organization?

You can choose an all-in-the-cloud solution, a connect-your-own-carrier solution, or a mix between all-in-the-cloud and third-party carriers:

- Phone System with Calling Plan (all in the cloud)

- Phone System with own carrier via Direct Routing

- Phone System with own carrier via Skype for Business Server OR Cloud Connector Edition

- Enterprise Voice in Skype for Business Server with own carrier

The solution you choose depends on your current and future needs, such as:

- Whether you want—-or are required—-to retain functionality provided by your on-premises deployment.
- Which client you want to deploy for your users.
- What your plan is for moving people to the cloud.
- Whether you need to interoperate with 3rd party PBXs and other telephony equipment.

Consider the following questions to determine the best solution for your organization:

- Do you have an existing Skype for Business Server deployment?
- Are your users homed in Skype for Business on premises, in the cloud on Skype for Business Online, or both? 
- Do you want to move on-premises users to the cloud?
- Is Microsoft’s PSTN Calling Plan available in your region?
- Do you want or need to keep your current telephony carrier?  For example, do you need to keep your current carrier because of an existing contract?
- Do you have an existing on-premises legacy PBX that you want or need to keep?
- Does your current legacy PBX offer unique features that are critical to your business?
- Do any or all of your users require features not currently offered in Phone System?

Note the following:

- All four options can co-exist with each other in case you need to design a solution for complex environment or managing multi-step migration.
- Phone System with own carrier via Skype for Business Server OR Cloud Connector Edition can only be deployed with either Skype for Business Server OR Cloud Connector. Co-existence of Skype for Business Server and Cloud Connector is not supported in a single company.

## Phone System with Calling Plan


Phone System with Calling Plan is an all-in-the-cloud option for Teams or Skype for Business Online users as shown in the following diagram:

![Phone System with Calling Plan](../../sfbserver2019/media/msft-telephony-solutions-1.png)


- Microsoft Phone System with added Domestic or International Calling Plans that enables calling to  phones around the world (depending on the level of service being licensed). 
- Because PSTN Calling Plan operates out of Office 365, this option does not require deployment or maintenance of any on-premises deployment.
- Customers can connect a supported SBC via Direct Routing for interoperability with 3rd party PBX, analog devices, and other 3rd party telephony equipment supported by the SBC.

| Infrastructure requirements                   | Required?|
| :----------------------------------------------------| ---------:|
| Requires uninterrupted connection to Office 365 | Yes |
| Available worldwide*                            | No  |
| Requires deploying and maintaining a supported Session Border Controller (SBC) | No |
| Requires contract with third-party carrier      | No   |
| Requires deploying and maintaining Skype for Business Server or Cloud Connector Edition | No |

\* For more information about the countries where Calling Plan is available, see [Country and region availability for Audio Conferencing and Calling Plans](https://docs.microsoft.com/en-us/MicrosoftTeams/country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans).


If you answer yes to the following questions, then this is the right solution for you:

- Calling Plan is available in your region.
- You do not need to retain your current PSTN carrier.
- You want to use Microsoft-managed access to the Public Switched Telephone Network( PSTN).
- You do not want to manage Session Border Controllers on your own.
- Teams and/or Skype for Business Online has all the features that your organization requires.

For more information, see [What is Phone System in Office 365](https://docs.microsoft.com/en-us/MicrosoftTeams/what-is-phone-system-in-office-365) and [Calling Plans for Office 365](https://docs.microsoft.com/en-us/MicrosoftTeams/calling-plans-for-office-365).

## Phone System with own carrier via Direct Routing

This option provides Microsoft Phone System in the cloud with virtually any telephony carrier for Teams users.

![Phone System with your carrier via Direct Routing](../../sfbserver2019/media/msft-telephony-solutions-2.png)

- Connect your own supported SBC to Microsoft Phone System directly without need of additional on-premises software.  
- Use virtually any telephony carrier with Microsoft Phone System.
- Can be configured and managed by customers or by your carrier or partner (ask if your carrier or partner provides this option).
- Configure interoperability between your telephony equipment—such as a third-party PBX and analog devices—and Microsoft Phone System.

| Infrastructure requirements                   | Required?|
| :----------------------------------------------------| ---------:|
| Requires uninterrupted connection to Office 365 | Yes |
| Available worldwide                            | Yes  |
| Requires deploying and maintaining a supported Session Border Controller (SBC) | Yes |
| Requires contract with third-party carrier*      | Yes   |
| Requires deploying and maintaining Skype for Business Server or Cloud Connector Edition | No |

\* Unless deployed as an option to provide connection to 3rd party PBX, analog devices, or other telephony equipment for users who are on Phone System with Calling Plans.

If you answer yes to the following questions, then this is the right solution for you:

- You want to use Teams with Phone System.
- You need to retain your current PSTN carrier.
- You want to mix routing, some calls are going via Calling Plans, some via your carrier
- You need to interoperate with 3rd party PBXs and/or equipment such us overhead pagers, analog devices
- Teams has all the features that your organization requires.

For more information, see [What is Phone System in Office 365](https://docs.microsoft.com/en-us/MicrosoftTeams/what-is-phone-system-in-office-365) and [Plan Direct Routing](https://docs.microsoft.com/en-us/MicrosoftTeams/direct-routing-plan).


## Phone System with own carrier via Skype for Business Server OR Cloud Connector Edition

This option provides Microsoft Phone System in the cloud with connectivity to an on-premises telephony network for Skype for Business Online users.

![Phone System with your carrier via Skype for Business Server OR Cloud Connector Edition](../../sfbserver2019/media/msft-telephony-solutions-3.png)

 - Connect your own supported SBC to Microsoft Phone System via Skype for Business Server or Skype for Business Cloud Connector Edition deployed on-premises. 
- Use virtually any telephony carrier with Microsoft Phone System. 
- If you already have Skype for Business Server on-premises you can leverage it;  if you do not, you can deploy a lighter version – Cloud Connector Edition.


| Infrastructure requirements                   | Required?|
| :----------------------------------------------------| ---------:|
| Requires uninterrupted connection to Office 365 | Yes |
| Available worldwide                            | Yes  |
| Requires deploying and maintaining a supported Session Border Controller (SBC) | Yes |
| Requires contract with third-party carrier      | Yes   |
| Requires deploying and maintaining Skype for Business Server or Cloud Connector Edition | Yes |



If you answer yes to the following questions, then this is the right solution for you:

- You want to use Skype for Business Online for your users.
- PSTN Calling Plan is not available in your region.
- You need to retain your current PSTN carrier.

For more information, see [What is Phone System in Office 365](https://docs.microsoft.com/en-us/MicrosoftTeams/what-is-phone-system-in-office-365), [Skype for Business Server 2019](https://docs.microsoft.com/en-us/SkypeForBusiness/skype-for-business-server-2019), and [Plan for Skype for Business Cloud Connector Edition](https://docs.microsoft.com/en-us/SkypeForBusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).

Recommendation:  When business conditions change--for example, you no longer need to retain your PSTN carrier--consider moving to Microsoft Teams using options 1 or 2 to:
- Minimize maintenance costs
- Have access to the latest features released by Microsoft

## Enterprise Voice in Skype for Business Server with own carrier

This option provides Enterprise Voice on-premises with connectivity to an on-premises telephony network for Skype for Business on-premises users.

![Enterprise Voice in Skype for Business Server with own carrier](../../sfbserver2019/media/msft-telephony-solutions-4.png)

- Connect your own supported SBC to Enterprise Voice System in Skype for Business on-premises Server.
- Use if you need local survivability.
- Use virtually any telephony carrier with Microsoft Phone System. 
- Most complex option to deploy and maintain.

| Infrastructure requirements                   | Required?|
| :----------------------------------------------------| ---------:|
| Requires uninterrupted connection to Office 365 | No |
| Available worldwide                            | Yes  |
| Requires deploying and maintaining a supported Session Border Controller (SBC) | Yes |
| Requires contract with third-party carrier      | Yes   |
| Requires deploying and maintaining Skype for Business Server | Yes |

For more information, see [Plan for Enterprise Voice in Skype for Business Server](https://docs.microsoft.com/en-us/SkypeForBusiness/plan-your-deployment/enterprise-voice-solution/enterprise-voice?toc=/SkypeForBusiness/toc.json&bc=/SkypeForBusiness/breadcrumb/toc.json).

Recommendation:  When business conditions change--for example, you no longer need to retain your PSTN carrier--consider moving to Microsoft Teams using options 1 or 2 to:
- Minimize maintenance costs
- Have access to the latest features released by Microsoft











  
