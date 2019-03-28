---
title: "Getting phones for Skype for Business Online"
ms.author: tonysmit
author: tonysmit
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
ms.audience: Admin
appliesto:
- Skype for Business 
- Microsoft Teams
localization_priority: Normal
f1keywords: None
ms.custom:
- Phone System
description: "Learn which phones work with Skype for Business from Polycom, HP, and Mitel, and the required licenses. "
---

# Getting phones for Skype for Business Online

Skype for Business Online qualifies and supports desktop phones for users who want to have a traditional phone experience, rather than use the Skype for Business app. This topic covers the phones and firmware versions that are supported for use in Skype for Business Online and other information that can help you when you are setting up phones in your organization.
  
To get the latest updates and most up-to-date information on supported devices, see the [Skype for Business Device Catalog](http://partnersolutions.skypeforbusiness.com/solutionscatalog).
  
## Supported phones

For Skype for Business Online users, you can choose from several models within the *Certified for Skype for Business Phones*  and phones running Lync Phone Edition (LPE) listed under the Skype for Business Online category in the [Skype for Business Device Catalog](http://partnersolutions.skypeforbusiness.com/solutionscatalog).
  
Microsoft is partnering and working closely with Polycom, Yealink, and AudioCodes to develop and certify a wide variety of devices through the Partner IP Phone Program (PIP) for the Phone System in Office 365 and Skype for Business Server.
  
When ordering new phones for Skype for Business, it is important to buy phones with the *right product ID*. These product IDs will ensure that the phones you receive have the Skype for Business Online qualified version already installed.
  
|||
|:-----|:-----|
|**Phone Partner** <br/> |**Skype for Business specific product ID** <br/> |
|Polycom  <br/> |Product ID -019  <br/> |
|Yealink  <br/> |SIP-TXXG Skype for Business Edition  <br/> |
|AudioCodes  <br/> |UCXXXHDEG (SfB)  <br/> |
   
For more details on Polycom phones, see [Voice Solutions for Microsoft](http://www.polycom.com/voice-conferencing-solutions/desktop-ip-phones.html).
  
For more details on Yealink phones, see [Skype for Business IP Phones](http://www.yealink.com/products_list_10.html#filter2).
  
For more details on AudioCodes phones, see [Skype for Business IP Phones](https://www.audiocodes.com/solutions-products/products/products-for-microsoft-365/ip-phones-room-solutions).
  
> [!NOTE]
> Lync Phone Edition is supported with Skype for Business Online, but not with Microsoft Teams. Mainstream support for the LPE platform ended by April/10/2014, with extended support until April/11/2023 to align with the product support lifecycle of Lync Server 2013. See [Microsoft Product Lifecycle](https://support.microsoft.com/lifecycle/search?qid=&amp;alpha=Lync%20Phone%20Edition&amp;Filter=FilterNO) for details on the LPE lifecycle. LPE CAP models aren't supported with Skype for Business Online.
>
> Later this year, Office 365 will not support any version of TLS older than 1.2. Since the underlying operating system of LPE does not support TLS 1.2, LPE will not be supported to connect to Office 365 anymore. See [Preparing for the mandatory use of TLS 1.2 in Office 365](https://support.microsoft.com/en-gb/help/4057306/preparing-for-tls-1-2-in-office-365) for more information.
  
## Supported firmware

This is the minimum software release required for supported phones to work with Phone System in Office 365:
  
||||
|:-----|:-----|:-----|
|**Phone type** <br/> |**Minimum firmware** <br/> |**Release date** <br/> |
|Optimized (Lync Phone Edition)  <br/> |4.0.7577.4463  <br/> |May 2015  <br/> |
|Certified Polycom VVX Series  <br/> |5.4.0A  <br/> |December 2015  <br/> |
|Yealink  <br/> |X.8.1.52  <br/> |February 2017  <br/> |
|AudioCodes  <br/> |3.0.0.459.1  <br/> |December 2016  <br/> |

For more details on current certified firmware versions, see [Skype for Business IP Phones](https://docs.microsoft.com/skypeforbusiness/certification/devices-ip-phones#conference-phones).

> [!NOTE]
> Lync Phone Edition (LPE) phones you have set up for your on-premises deployment must be updated to the minimum or later required firmware prior to moving those users over to Skype for Business Online. If you move your users from on-premises to Skype for Business Online before you update the firmware on the phones, those phones won't be able to connect to Skype for Business Online. 
  
## Required licenses

Skype for Business Online doesn't require any additional Microsoft license other than the user licenses. To learn more about the required user licenses, see [Skype for Business and Microsoft Teams add-on licensing](../../skype-for-business-and-microsoft-teams-add-on-licensing/skype-for-business-and-microsoft-teams-add-on-licensing.md).
  
Manufacturer licensing models might vary between open SIP and Skype for Business Certified firmware. If you are repurposing a certified model with an Open SIP firmware, you will need to verify firmware license requirements with the manufacturer.
  
## Skype for Business Online connected phones feature set

For full device features and capabilities, check the manufacturer user guides.
  
||||||
|:-----|:-----|:-----|:-----|:-----|
|**Feature** <br/> |**Polycom 3PIP** <br/> |**Yealink 3PIP** <br/> |**AudioCodes 3PIP** <br/> |**LPE** <br/> |
|Sign in with user credentials  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |No  <br/> |
|Sign in via PC (Pairing), Windows Only  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|Sign in using (Web Sign-in)  <br/>  <br/> **Note:** Check the supportability matrix in deployment guide.           |Yes  <br/> |Yes  <br/> |Yes  <br/> |No  <br/> |
|Single-click join meeting  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|Click to dial (Pairing)  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|Meeting Controls  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|Visual Voicemail  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|Phone Lock  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|Device Update  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|In-band Provisioning  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|QoE  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |No  <br/> |
|Log Upload  <br/> <br/> **Note:** Currently, all logs are uploaded to the Microsoft Support team only; customer access to phone logs aren't yet available.           |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|Modern Authentication  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |No  <br/> |
|Multiple Emergency Number  <br/> |Yes  <br/> |No  <br/> |No  <br/> |Yes  <br/> |
|Exchange Calendar Integration*  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> <br/> **Note:** Requires PC tethering           |
|Presence Integration  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|Corporate Directory  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |
|Delegation  <br/> |Yes  <br/> |Yes  <br/> |Yes  <br/> |No  <br/> |
|Contact Picture Integration  <br/> |No  <br/> |Yes  <br/> |No  <br/> |Yes  <br/> |
||||||

     
> [!NOTE]
> CX 600 or any other Aries phones don't support multifactor authentication (MFA). If you force MFA, these devices will fail to sign-in. These devices must use only Org ID for authetication.
 
## What else should you know?
For step-by-step setup instructions, see [Deploying Skype for Business Online phones](deploying-skype-for-business-online-phones.md).

## Related topics
[Getting service phone numbers for Skype for Business and Microsoft Teams](../getting-service-phone-numbers.md)

[Here's what you get with Phone System in Office 365](/MicrosoftTeams/here-s-what-you-get-with-phone-system)

[Country and region availability for Audio Conferencing and Calling Plans](/microsoftteams/country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans)

  
 
