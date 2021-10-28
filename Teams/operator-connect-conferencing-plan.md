---
title: Operator Connect for Audio Conferencing
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
description: Learn more about Operator Connect for Audio Conferencing, such as requirements and planning for deployment.
ms.custom: 
 - seo-marvel-apr2020
 - seo-marvel-jun2020
appliesto: 
  - Microsoft Teams
---

# Plan for Operator Connect for Audio Conferencing

Operator Connect Conferencing enables customers to use phone numbers from their telephone number providers to join Microsoft Teams meetings. If your existing telephone number provider is part of the Microsoft Operator Connect Conferencing program, you can add phone numbers from your telephone number provider to your Audio Conferencing bridge and use them to join meetings.

>[!NOTE]
>A telephone number provider that is part of the Microsoft Operator Connect program is referenced in this article as an "operator."
>
>To see if your operator participates in the Microsoft Operator Connect program, see the [Microsoft 365 Operator Connect directory](https://cloudpartners.transform.microsoft.com/practices/microsoft-365-for-operators/directory).

This article describes the benefits, requirements, and licensing of Operator Connect Conferencing.

## Benefits

Operator Connect Conferencing provides the following benefits:

- **Keep your contracts with your existing telephone number provider.** You keep your preferred operator and contracts.

- **Flexible allocation of phone numbers between your operator and Microsoft.** You can use phone numbers from both Microsoft and your operator, or only use phone numbers from your operator.

- **Operator-managed infrastructure.** Your operator manages the Session Border Controllers (SBCs) and the interconnectivity with Microsoft, allowing you to save on hardware purchases and management.

- **Faster, easier deployment.** You can quickly connect to your operator and assign phone numbers to your Audio Conferencing bridge from the Teams admin center.

- **Enhanced support and reliability.** Operators provide technical support and shared service level agreements to improve service support, while direct peering powered by Azure creates a one-to-one network connection for enhanced reliability.

Operator Connect Conferencing might be the right solution for your organization if:

- You want to **keep your contracts** with your existing telephone number provider.

- You want to **source phone numbers for Audio Conferencing** from a new telephone number provider.

- **Microsoft Audio Conferencing isn't available in your geographic location**.

- You want to **expand the global coverage** of your existing Microsoft Audio Conferencing bridge.

- You want to **leverage an operator for Audio Conferencing services with a pay-per-minute model**, such as use toll-free numbers and outbound calls from Teams meetings to phone numbers in countries not included in your subscription.

## Requirements

The following is required to enable Operator Connect Conferencing for your organization:

- **Audio Conferencing or Operator Connect Conferencing license.** Users that need Operator Connect Conferencing numbers to join the meetings that they organize need to have a Microsoft Audio Conferencing Standard subscription or a Microsoft Operator Connect Conferencing license assigned to them.

    A Microsoft Audio Conferencing Standard subscription can be acquired as an add-on to a Microsoft Teams license and is also included in Office 365 E5 subscriptions. A Microsoft Operator Connect Conferencing license can be acquired as an add-on to a Microsoft Teams license.

## Licensing and billing

Microsoft offers two types of licenses that include Operator Connect Conferencing:

- **Audio Conferencing Standard Subscription license:** The Audio Conferencing Standard subscription enables customers to use phone numbers from Microsoft and from an operator. In addition to the phone numbers provided by Microsoft, customers can expand their Audio Conferencing bridge by adding phone numbers from an operator. Customers can also decide which outbound calls from Teams meetings to route via Microsoft and which calls to route via an operator. For additional information, see [**Configure Operator Connect Conferencing**](operator-connect-conferencing-configure.md).

    If your organization already has Audio Conferencing Standard Subscription licenses, your organization is automatically enabled for Operator Connect Conferencing. The Audio Conferencing Standard Subscription license is included in Microsoft 365 E5 and Office 365 E5. Additionally, it can be added as an add-on to a Microsoft Teams subscription.

- **Operator Connect Conferencing license:** The Operator Connect Conferencing license enables customers to only use phone numbers from an operator and it does not include phone numbers from Microsoft. All outbound calls from Teams meetings must be routed via an operator. For additional information, see [**Configure Operator Connect Conferencing**](operator-connect-conferencing-configure.md).

>[!Note]
>Meeting participants do not require an Audio Conferencing Standard Subscription license or an Operator Connect Conferencing license to join a meeting organized by a user with an Audio Conferencing Standard Subscription license or an Operator Connect Conferencing license.

With Operator Connect Conferencing, Microsoft bills your organization for Microsoft Audio Conferencing or Operator Connect Conferencing licenses and usage of any phone numbers provided by Microsoft and according to the type of Audio Conferencing license used by your organization.

Your operator bills your organization for usage of Operator Connect Conferencing numbers provided by them.
