---
title: Plan for Operator Connect Conferencing
author: DaniEASmith
ms.author: danismith
manager: serdars
ms.date: 10/28/2021
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-voice
  - m365initiative-voice
ms.reviewer: crowe
search.appverid: MET150
f1.keywords:
- NOCSH
- ms.teamsadmincenter.directrouting.overview
description: Learn more about Operator Connect Conferencing, such as requirements and planning for deployment.
ms.custom: 
 - seo-marvel-apr2020
 - seo-marvel-jun2020
appliesto: 
  - Microsoft Teams
---

# Plan for Operator Connect Conferencing

Microsoft Audio Conferencing provides the ability to dial into a conference and dial out from a conference using Public Switched Telephone Network (PSTN) phone numbers.  Participants join Microsoft Teams meetings using an audio-only conferencing bridge.

With Operator Connect Conferencing capabilities, organizations can use phone numbers from a third-party operator to join Microsoft Teams meetings. If your current operator is part of the Microsoft Operator Connect program, you can add phone numbers from your operator to your Audio Conferencing bridge and use them to join meetings.

Without Operator Connect Conferencing capabilities, organizations can only use phone numbers provided by Microsoft for their audio conferencing bridge.

>[!NOTE]
>A telephone number provider that is part of the Microsoft Operator Connect program is referenced in this article as an "operator."
>
>To see if your operator participates in the Microsoft Operator Connect program, see the [Microsoft 365 Operator Connect directory](https://cloudpartners.transform.microsoft.com/practices/microsoft-365-for-operators/directory).

This article describes Operator Connect Conferencing:

- [Benefits](#benefits)
- [Licensing requirements and billing](#licensing-requirements-and-billing)
- [Additional information on Microsoft Audio Conferencing](#additional-information-on-microsoft-audio-conferencing)

For information about configuring Operator Connect Conferencing, see [Configure Operator Connect Conferencing](operator-connect-conferencing-configure.md).

If some of your organization's users need to make external calls to PSTN phone numbers, you still need a calling plan. To learn about using a third-party operator for external PSTN connectivity, see [Plan for Operator Connect](operator-connect-plan.md).

## Benefits

Operator Connect Conferencing provides the following benefits:

- **Flexible allocation of phone numbers between your operator and Microsoft.** Use phone numbers from both Microsoft and your operator (with a Microsoft Audio Conferencing Standard subscription only), or only use phone numbers from your operator (with an Operator Connect Conferencing license only).

- **Operator-managed infrastructure.** Your operator manages the Session Border Controllers (SBCs) and the interconnectivity with Microsoft, saving you from extra hardware purchases and management.

- **Faster, easier deployment.** Quickly connect to your operator and assign phone numbers to your Audio Conferencing bridge from the Teams admin center.

- **Enhanced support and reliability.** Operators provide technical support and shared service level agreements to improve service support, and direct peering powered by Azure creates a one-to-one network connection for enhanced reliability.

Operator Connect Conferencing might be the right solution for your organization if:

- You want to **keep your contracts** with your existing telephone number provider

- You want to **expand the global coverage** of your existing Microsoft Audio Conferencing bridge

- You want to **source phone numbers for Audio Conferencing** from a new telephone number provider

- **Microsoft Audio Conferencing isn't available in your geographic location**

- You want to **leverage an operator for Audio Conferencing services with a pay-per-minute model**, such as use toll-free numbers and make outbound calls from Teams meetings to phone numbers in countries not included in your subscription

## Licensing requirements and billing

Users who need Operator Connect Conferencing numbers to join the meetings they organize must have either a Microsoft Audio Conferencing Standard subscription or a Microsoft Operator Connect Conferencing license assigned to them.

### Audio Conferencing Standard subscription

A Microsoft Audio Conferencing Standard subscription can be purchased as an add-on to a Microsoft Teams license and is also included in Microsoft 365 E5 and Office 365 E5 subscriptions.

The Audio Conferencing Standard subscription allows subscribers to use phone numbers from Microsoft and expand their audio conferencing bridges with numbers from an operator. Subscribers can also decide which outbound calls from Teams meetings to route via Microsoft and which calls to route via an operator.

For more information, see [**Configure Operator Connect Conferencing**](operator-connect-conferencing-configure.md).

### Operator Connect Conferencing license

A Microsoft Operator Connect Conferencing license can be acquired as an add-on to a Microsoft Teams license.

The Operator Connect Conferencing license allows subscribers to use phone numbers from an operator, but it doesn't include phone numbers from Microsoft. All outbound calls from Teams meetings must be routed via an operator.

For more information, see [**Configure Operator Connect Conferencing**](operator-connect-conferencing-configure.md).

>[!Note]
>Meeting participants don't require an Audio Conferencing Standard Subscription license or an Operator Connect Conferencing license to join a meeting organized by a user with Operator Connect Conferencing capabilities.

With Operator Connect Conferencing, Microsoft bills your organization according to the type of Audio Conferencing license used by your organization, Microsoft Audio Conferencing or Operator Connect Conferencing, and the use of any phone numbers provided by Microsoft.

Your operator bills your organization for the use of Operator Connect Conferencing numbers they provide.

## Additional information on Microsoft Audio Conferencing

Microsoft Audio Conferencing allows participants to join Microsoft Teams meetings by dialing in with a PSTN phone number or by dialing out to a PSTN phone number. For more information on Microsoft Audio Conferencing capabilities available to your organization, see [Audio Conferencing in Microsoft 365](audio-conferencing-in-office-365.md).
