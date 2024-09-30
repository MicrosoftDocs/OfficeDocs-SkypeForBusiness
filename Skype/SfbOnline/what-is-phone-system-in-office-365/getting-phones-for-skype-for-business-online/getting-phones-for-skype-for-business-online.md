---
ms.date: 11/28/2017
title: "Getting phones for Skype for Business Online"
ms.author: serdars
author: pamgreen
manager: serdars
ms.reviewer: wasseemh
ms.topic: article
ms.assetid: 91f2d947-45fc-4fab-bd8b-2e313531c477
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
search.appverid: MET150
ms.collection: 
- Adm_Skype4B_Online
- Strat_SB_PSTN
audience: Admin
appliesto:
- Skype for Business 
- Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.custom:
- Phone System
description: "Learn which phones work with Skype for Business from Polycom, HP, and Mitel, and the required licenses. "
---

# Getting phones for Skype for Business Online

[!INCLUDE [sfbo-retirement](../../../Hub/includes/sfbo-retirement.md)]

Skype for Business Online qualifies and supports desktop phones for users who want to have a traditional phone experience, rather than use the Skype for Business app. This article covers the phones and firmware versions that are supported for use in Skype for Business Online and other information that can help you when you're setting up phones in your organization.

> [!NOTE]
> Skype for Business will slowly be replaced by Microsoft Teams as the primary communication method in Microsoft 365 and Office 365.  See [A new vision for intelligent communications in Office 365](https://www.microsoft.com/microsoft-365/blog/2017/09/25/a-new-vision-for-intelligent-communications-in-office-365/) for more information.
>
>To get the latest updates and most up-to-date information on supported devices, see the [Microsoft Teams devices for intelligent communications](https://products.office.com/microsoft-teams/across-devices?ms.url=officecomteamsdevices&rtc=1).
  
## Supported phones
  
Microsoft is partnering and working closely with Polycom, Yealink, and AudioCodes to develop and certify a wide variety of devices through the Partner IP Phone Program (PIP) for the Phone System.
  
When ordering new phones for Skype for Business, it's important to buy phones with the *right product ID*. These product IDs will ensure that the phones you receive have the Skype for Business Online qualified version already installed.
  
|Phone Partner  |Skype for Business specific product ID  |
|:-----|:-----|
|Polycom   |Product ID -019   |
|Yealink   |SIP-TXXG Skype for Business Edition   |
|AudioCodes   |UCXXXHDEG (SfB)   |
   
For more information on Polycom phones, see [Poly Documentation Library](https://documents.polycom.com/category/voice).
  
For more information on Yealink phones, see [Skype for Business IP Phones](http://www.yealink.com/products_list_10.html#filter2).
  
For more information on AudioCodes phones, see [Skype for Business IP Phones](https://www.audiocodes.com/solutions-products/products/products-for-microsoft-365/ip-phones-room-solutions).
  
> [!NOTE]
> Lync Phone Edition is supported with Skype for Business Online, but not with Microsoft Teams. Mainstream support for the LPE platform ended by April/10/2014, with extended support until April/11/2023 to align with the product support lifecycle of Lync Server 2013. See [Microsoft Product Lifecycle](https://support.microsoft.com/lifecycle/search?qid=&amp;alpha=Lync%20Phone%20Edition&amp;Filter=FilterNO) for details on the LPE lifecycle. LPE CAP models aren't supported with Skype for Business Online.
>
> Later this year, Office 365 will not support any version of TLS older than 1.2. Since the underlying operating system of LPE does not support TLS 1.2, LPE will not be supported to connect to Office 365 anymore. See [Preparing for the mandatory use of TLS 1.2 in Office 365](https://support.microsoft.com/en-gb/help/4057306/preparing-for-tls-1-2-in-office-365) for more information.
  
## Supported firmware

This is the minimum software release required for supported phones to work with Phone System:
  

|Phone type |Minimum firmware |Release date |
|:-----|:-----|:-----|
|Optimized (Lync Phone Edition)   |4.0.7577.4463   |May 2015   |
|Certified Polycom VVX Series   |5.4.0A   |December 2015   |
|Yealink   |X.8.1.52   |February 2017   |
|AudioCodes   |3.0.0.459.1   |December 2016   |

For more information on current certified firmware versions, see [Microsoft Teams certified Android devices](/microsoftteams/devices/teams-ip-phones).

> [!NOTE]
> Lync Phone Edition (LPE) phones you have set up for your on-premises deployment must be updated to the minimum or later required firmware prior to moving those users over to Skype for Business Online. If you move your users from on-premises to Skype for Business Online before you update the firmware on the phones, those phones won't be able to connect to Skype for Business Online. 
  
## Required licenses

Skype for Business Online doesn't require any extra Microsoft license other than the user licenses. To learn more about the required user licenses, see [Skype for Business and Microsoft Teams add-on licensing](../../skype-for-business-and-microsoft-teams-add-on-licensing/skype-for-business-and-microsoft-teams-add-on-licensing.md).
  
Manufacturer licensing models might vary between open SIP and Skype for Business Certified firmware. If you're repurposing a certified model with an Open SIP firmware, you'll need to verify firmware license requirements with the manufacturer.
  
## Skype for Business Online connected phones feature set

For full device features and capabilities, check the manufacturer user guides.
  

|Feature  |Polycom 3PIP  |Yealink 3PIP |AudioCodes 3PIP |LPE |
|:-----|:-----|:-----|:-----|:-----|
|Sign in with user credentials   |Yes  |Yes   |Yes   |No   |
|Sign in via PC (Pairing), Windows Only   |Yes   |Yes   |Yes   |Yes   |
|Sign in using (Web Sign-in)  <br/>  <br/> **Note:** Check the supportability matrix in deployment guide.  |Yes   |Yes   |Yes   |No   |
|Single-click join meeting   |Yes   |Yes   |Yes   |Yes   |
|Click to dial (Pairing)   |Yes   |Yes   |Yes   |Yes  > |
|Meeting Controls   |Yes   |Yes   |Yes   |Yes   |
|Visual Voicemail   |Yes   |Yes   |Yes   |Yes   |
|Phone Lock   |Yes   |Yes   |Yes   |Yes   |
|Device Update   |Yes   |Yes   |Yes   |Yes   |
|In-band Provisioning   |Yes   |Yes   |Yes   |Yes   |
|QoE   |Yes   |Yes   |Yes   |No  |
|Log Upload  <br/> <br/> **Note:** Currently, all logs are uploaded to the Microsoft Support team only; customer access to phone logs aren't yet available.           |Yes   |Yes   |Yes   |Yes   |
|Modern Authentication   |Yes   |Yes   |Yes   |No   |
|Multiple Emergency Numbers   |Yes   |No   |No   |Yes   |
|Exchange Calendar Integration*   |Yes   |Yes   |Yes   |Yes  <br/> <br/> **Note:** Requires PC tethering           |
|Presence Integration   |Yes   |Yes   |Yes   |Yes   |
|Corporate Directory   |Yes   |Yes   |Yes   |Yes   |
|Delegation   |Yes   |Yes   |Yes   |No   |
|Contact Picture Integration   |No   |Yes  |No   |Yes   |


     
> [!NOTE]
> CX 600 or any other Aries phones don't support multifactor authentication (MFA). If you force MFA, these devices will fail to sign-in. These devices must use only Org ID for authetication.
 
## What else should you know?
For step-by-step setup instructions, see [Deploying Skype for Business Online phones](deploying-skype-for-business-online-phones.md).

## Related articles
[Getting service phone numbers for Skype for Business and Microsoft Teams](/microsoftteams/getting-service-phone-numbers)

[Here's what you get with Phone System](/MicrosoftTeams/here-s-what-you-get-with-phone-system)

[Country and region availability for Audio Conferencing and Calling Plans](/microsoftteams/country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans)

  

