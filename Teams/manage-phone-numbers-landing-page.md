---
title: "Manage phone numbers for your organization"
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: davlick, roykuntz, jenstr
ms.topic: conceptual
ms.assetid: 6b61cb3c-361c-48a8-a9ef-d81bddde27bb
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - highpri
audience: Admin
appliesto: 
  - Skype for Business
  - Microsoft Teams
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: 
  - ms.teamsadmincenter.voice.phonenumbers.overview
  - ms.teamsadmincenter.voice.searchandacquire.PSTNpartner
  - ms.lync.lac.NewNumberManualAcquisitionOpenSupportTicket
  - ms.lync.lac.VASAMissingGeoCodes
  - Calling Plans
  - seo-marvel-apr2020
description: Learn how to get and manage user (subscriber) and service (toll and toll-free) telephone numbers for Microsoft Teams for your organization.
---

# Manage telephone numbers for your organization

Currently, Microsoft supports two telephone number types: 

- [**User numbers**](#user-telephone-numbers), also called subscriber numbers, which can be assigned to users in your organization.

- [**Service numbers**](#service-telephone-numbers), which are assigned to services, such as [Audio Conferencing](deploy-audio-conferencing-teams-landing-page.md), [Auto Attendants](plan-auto-attendant-call-queue.md), or [Call Queues](plan-auto-attendant-call-queue.md).

Microsoft is working to simplify number types, but for now you will need to decide:

- Which user locations need new telephone numbers from Microsoft?
- Which type of telephone number (subscriber or service) do I need?
- How do I port existing telephone numbers to Teams?

How you acquire and manage telephone numbers differs depending on your Public Switched Telephone Network (PSTN) connectivity option.

- For information about managing telephone numbers for Microsoft Calling Plan, see [Manage telephone numbers for Calling Plans](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md).

- For information about managing telephone numbers for Operator Connect, see [Set up telephone numbers with Operator Connect](operator-connect-configure.md#set-up-phone-numbers).

- For information about managing telephone numbers for Teams Phone Mobile, see [Set up telephone numbers with Teams Phone Mobile](operator-connect-mobile-configure.md#set-up-phone-numbers).

- For information about managing telephone numbers for Direct Routing, see [Configure the telephone number and enable enterprise voice](direct-routing-enable-users.md#configure-the-phone-number-and-enable-enterprise-voice).




> [!NOTE]
> If you need additional or other number types other than those numbers seen in the Microsoft Teams admin center, you can submit a telephone number request to the [Phone Number Service Center](https://pstnsd.powerappsportals.com/).

## User telephone numbers

There are two types of user telephone numbers, which can be assigned to users in your organization:  
    
- **Geographic numbers** have a relationship to a geographic area and are the most common. For example, geographic telephone numbers in most cases can only be used within a certain address, city, state, or region of the country.
    
- **Non-geographic numbers** are known as national numbers or sometimes VoIP numbers. These numbers don't have a relationship to a geographic area within a country/region. For example, non-geographic numbers often have the same cost when calling the number from anywhere within the country/region. Also, some countries, such as Denmark, only have non-geographic numbers available.


## Service telephone numbers  

This section describes service numbers available from Microsoft that are included in your licensing. For information about service numbers provided by Operator Connect or Direct Routing, contact your provider. 

There are two types of service telephone numbers provided by Microsoft--toll and toll-free--which can be assigned to services such as Audio Conferencing, Auto Attendants, or Call Queues. Service numbers have a higher concurrent call capacity than user numbers. Service number availability varies by country/region and the type of number (whether it's a toll or toll-free number). Microsoft’s telephony licenses in each country/region dictate what the number can be used for.
    
 - **Toll service numbers** - There are two types of toll service numbers, which may incur a toll cost to the caller:
    
   - **Geographic numbers** Geographic numbers have a relationship to a geographic area. For example, geographic telephone numbers in most cases can only be used within a certain address, city, state, or region of the country.
        
   - **Non-geographic numbers** Non-geographic numbers are national numbers that don't have a relationship to a geographic area within a country/region. For example, non-geographic numbers often have the same cost when calling the number from anywhere within the country/region.
   
- **Toll-free service numbers** - These service numbers don't typically incur a toll cost to the caller. Teams provides national toll-free numbers in over 60 countries/regions.
    
    > [!CAUTION]
    > Some countries/regions and originating number types, such as calls originating from mobile phones, may in some cases incur a toll cost to the caller. 

## Where phone numbers are managed

Where and how numbers are managed depend on the PSTN connectivity option:

- Microsoft Calling Plan and Operator Connect phone numbers can be managed only in Microsoft 365.

- Direct Routing phone numbers can be managed in the on-premises Active Directory or in Microsoft 365 as described in the following sections.

### Direct Routing numbers managed in an on-premises Active Directory

If you have or had a Skype for Business Server hybrid deployment,
your on-premises Active Directory is most likely synchronizing with Microsoft 365. This means that directory attributes on user and resource accounts are managed in the on-premises Active Directory and synchronized into Microsoft 365.

If the Direct Routing phone number is managed on the user or resource account in the on-premises Active Directory, the msRTCSIP-Line parameter on the account contains a value. You can use a tool such as ADSI Edit to view the msRTCSIP-Line parameter for a user or resource account that has a Direct Routing phone number assigned in on-premises Active Directory.   

After this parameter is automatically synchronized to the user or resource account in Microsoft 365 through the directory synchronization process (Azure AD Connect), you can view the phone number by looking at the OnPremLineURi parameter in the output from the [Get-CsOnlineUser](/powershell/module/skype/get-csonlineuser) cmdlet.

| Where | Parameter | Value |
| :------------| :-------| :---------|
| On-premises AD | msRTCSIP-Line | tel:+14255551234 |
| Microsoft 365 | OnPremLineURi | tel:+14255551234 |

### Direct Routing numbers managed in Microsoft 365

If you're not managing Direct Routing phone numbers in the on-premises Active Directory, then they're managed in Microsoft 365. Because the phone numbers are not synching to Microsoft 365, they're not visible in the OnPremLineUri parameter in the output from the Get-CsOnlineUser cmdlet  run for the user or resource account.

### Direct Routing numbers managed in both an on-premises Active Directory and Microsoft 365

It's possible to manage Direct Routing phone numbers of some user and resource accounts in an on-premises Active Directory and Direct Routing phone numbers of other accounts in Microsoft 365. This capability depends on whether the attribute msRTCSIP-Line is set on the user or resource account in the on-premises Active Directory.    

### Change where Direct Routing phone numbers are managed

To change where a Direct Routing phone number is managed, you need to remove the phone number from the msRTCSIP-Line attribute on the user or resource account in the on-premises Active Directory.   

For more information, see [Clear Skype for Business attributes for all on-premises users in Active Directory](/skypeforbusiness/hybrid/cloud-consolidation-managing-attributes#method-2---clear-skype-for-business-attributes-for-all-on-premises-users-in-active-directory.md). Note that the phone number needs to be re-assigned to the user or resource account in Microsoft 365.

After the removal has been synchronized to Microsoft 365, the OnPremLineUri attribute in the output from Get-CsOnlineUser on the user or resource account will be empty. 

