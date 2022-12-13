---
title: "Contact the Telephone Number Services team"
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: mikedav, roykuntz, jastark
ms.topic: conceptual
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection:
  - M365-voice
audience: Admin
appliesto:
  - Skype for Business
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
  - ms.teamsadmincenter.voice.tnsservicedesk
  - ms.teamsadmincenter.voice.contacttnssupport
  - Calling Plans
ROBOTS: NOINDEX, NOFOLLOW
description: "When you get phone numbers or port (transfer) numbers for your organization, you might need to get help and support at the TNS service desk."
---

# Telephone Number Services (TNS) - Service Desk

> [!NOTE]
> As of July 22, 2021, the previous email system to reach out to the TNS service desk has been retired.

There is a new process to interact with the Telephone Number Services (TNS) service desk from our new **[Phone Number Service Center](https://pstnsd.powerappsportals.com)**. You can now open tickets, view tickets, and track communication in a single place that is integrated with the Teams Admin Center. These tasks are described in more detail in the following sections.


- **[Create a new case](#create-a-new-case)** – Submit a new request or general enquiry.

- **[View my existing cases](#view-and-manage-existing-cases)** – Track and monitor your existing case(s).

- **[View my company cases](#view-and-manage-existing-cases)** – Track and monitor your company's existing case(s). If your colleagues from your company have opened any cases, you can look those up in this view.

- **[Give feedback](#view-and-manage-existing-cases)**– Share your feedback with us.

## Create a new case

> [!NOTE]
> Only someone from the same tenant is allowed to create a case. For example, someone from @fabrikam.com can't create a case on behalf of @contoso.com.

To create a new case, follow these steps:

1. Select **Create a new case** from one of the following places:

   - From the **Phone Number Service Center** home page, at the top of the page or at the bottom tile.

   - From  the **View my existing cases**  page.

   - From  the **View my company cases** page.

2. Provide your case details as described in detail in the [next section](#provide-case-details).

3. After entering all values, select **Submit**. You'll see a new screen where you can see your case number.

### Provide case details

To understand case details, Microsoft needs the following information:

- [Case category](#case-category)
- [Country or region](#country-or-region)
- [Case type](#case-type)
- [Case title](#case-title)
- [Additional contacts for notifications](#additional-contacts-for-notifications)
- [Description](#description)
- [Additional supporting documents](#additional-supporting-documents)

#### Case category

A case can have one of two categories:

- **Submit a new request**- Choose this option if you want to submit a new request. For example, you want to submit a port request or you want to purchase phone numbers from Microsoft.

- **General enquiry** - Choose this option if you have questions that will help you determine your request. For example, you need to know if you can port your wireless numbers to Microsoft, or you need to know if Microsoft supports vanity toll-free numbers.

#### Country or region

Select the country/region for which you are submitting this case. If you have requests for multiple countries, you must open one case per country/region.

#### Case type

Case type can be one of the following:

- **Custom Calling Name (US Only)** - Set a custom calling name on your Microsoft phone numbers. This is applicable to United States phone numbers only.

  - **Custom calling name to set (15 chars only)** - The custom calling name that you want to set. Name has a maximum limit of 15 characters.

  - **List of phone numbers** - The list of phone numbers for which you want to set a custom calling name value. Upload a csv file with the list of phone numbers.

- **Inter tenant port** – Move phone numbers from one tenant to another. For example, you have two different tenants within Microsoft, and you want to move your phone numbers from one tenant to the other.

  - **Source tenant domain name** - The tenant from which you want to move phone numbers to a different tenant.

  - **Source tenant unique identifier** - The tenant ID for the source tenant. This is an optional field.

  - **Destination tenant domain name** - The tenant to which you want to move phone numbers to.

  - **Destination tenant unique identifier** - The tenant ID for the destination tenant. This is an optional field.

  - **Requested Date time*** -  The date and time on which you want your numbers moved from the source tenant to the destination tenant. See Date and time.

  - **List of phone numbers** - The list of phone numbers that you want to move from the source tenant to the destination tenant. Upload a csv file with the list of phone numbers.

- **Inventory Type Change** – Change the type of phone number(s). For example, you want to change your Microsoft subscriber numbers to service numbers. For more information about the types of phone numbers Microsoft supports, see [Types of phone numbers](../different-kinds-of-phone-numbers-used-for-calling-plans.md).

  - **Convert to** - Select to convert your numbers to user numbers or to service numbers.

  - **Preferred Datetime*** - The date and time on which you want the inventory type of your numbers to be changed. See Date and time for more information.

  - **Checkbox – I understand that to be able to update the inventory type, my phone numbers need to be unassigned** - Microsoft can't process phone number type change requests unless the phone numbers within your tenant are not assigned. If you are requesting this change for a future date, then you will need to ensure that the numbers are unassigned before your requested date and time.

  - **List of phone numbers** - The list of phone numbers whose type you want to change. Upload a csv file with the list of phone numbers.

- **New TN Acquisition** – Purchase new phone numbers from Microsoft.

  - **Number Type** - Select the type for your numbers. See [Types of phone numbers](../different-kinds-of-phone-numbers-used-for-calling-plans.md).

  - **Tried to get phone numbers from the Teams Admin Center Portal** - Have you tried purchasing these phone numbers from the Microsoft Teams Admin Center?

  - **Quantity of phone numbers required** - The count of phone numbers that you want to purchase.

  - **State/Province** - The state/province within your country/region for which you want phone numbers.

  - **City** - The city within the state/province for which you want phone numbers.

  - **Office address** - This is specific to certain countries only. This is the site address of your office.

  - **Directory listing** - This is specific to certain countries only. Do you want to publish your company information with the phone numbers?

- **Port in** – Port existing phone numbers from your current service provider to Microsoft.

  - **Name your port order** - Provide an easy-to-remember name for your port request.

  - **Requested porting date/time*** - The date and time on which you want the numbers to port to Microsoft. This is not a guaranteed porting date because the current number owner has to approve our port request first. See Date and time.

  - **List of porting numbers** - The list of phone numbers that you would like to port to Microsoft. Upload a csv file with the list of phone numbers.

  - **Letter of authorization (LOA)** - Attach a signed and filled out LOA here. Microsoft cannot process a port request without an LOA.

- **Address Update** – Update emergency calling address. Note that this field applies to select countries only.

  - **Location id** - The location ID for your emergency address.

  - **List of phone numbers** - The list of phone numbers for which you want to change the emergency address (enter your desired address in the Description field). Upload a csv file with the list of phone numbers.

**Date and Time.** If you select Country = France, date = 8/14/2021 and time = 10am, then the request will be executed on 8/14/2021 at 10 a.m. French time.

#### Case title

Enter a title that summarizes your ask.

#### Additional contacts for notifications

Enter the list of people who will receive automated status notifications from Microsoft.
For example, you want to place a port-in order and you want two other colleagues in addition to yourself to receive automated status notifications. Provide the email addresses of your colleagues in the **Notification emails** section. This information is optional.

#### Description

Describe what you are trying to achieve and list your questions for the Microsoft Telephone Number Services (TNS) Service desk.

#### Additional supporting documents

Upload any additional documents for your case.

## View and manage existing cases

You can view your cases by selecting **View my existing cases** and selecting the case number. Selecting a case number will redirect you to the case details. (You can also view company cases by selecting **View company cases**.)  You can also:

- **Filter your cases** by selecting **Open cases**,  **All cases**, or **Closed cases**.

- **Communicate with the TNS service desk** regarding your case by opening an existing case, scrolling down, and selecting **Add comment**. A new window will appear. Enter your message in the comment box. Attach any supporting documents (if available), and then select **Submit**.

  Responses from the **TNS service desk** will be displayed under the same timeline. When there is an update on your case, you will receive an automated email notification of the update.

- **Cancel a case** by navigating to an existing case, scrolling down, and selecting **Cancel case.** Select a reason for the cancellation from the drop-down list and then select **Cancel**.

- **Resolve a case** - If you believe your request has been completed, you can resolve a case by navigating to an existing case, scrolling down, and selecting **Resolve case**. Select **Close**; the case will now show as **Resolved – Problem solved**.

## Related topics and additional resources

- For assistance that's related to numbers setup and configuration, licenses, fees, or billing, see [Support Contact for Business Products - Admin Help](/microsoft-365/admin/contact-support-for-business-products?tabs=online).

- For information about the calling plans that are available in your country/region, see [Countries and region availability for Audio Conferencing and Calling Plans](../country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md).

- For information zbout the appropriate type(s) of phone numbers for your organization, see [Different kinds of phone numbers](../different-kinds-of-phone-numbers-used-for-calling-plans.md).

- For information about managing phone numbers for your organization, see [Manage phone numbers for your organization](manage-phone-numbers-for-your-organization.md).

- For information about emergency calling terms and conditions, see [Emergency calling terms and conditions](../emergency-calling-terms-and-conditions.md).
