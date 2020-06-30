---
title: Communication compliance for Microsoft Teams
author: MicrosoftHeidi
ms.author: heidip
manager: serdars
ms.topic: reference
ms.service: msteams
audience: admin
ms.reviewer: anwara
description: Learning about communication compliance, part of the insider risk solution set, from the Microsoft Teams perspective (this is part of the M365 communication compliance functionality).
localization_priority: Normal
search.appverid: MET150
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
---

# Communication compliance for Microsoft Teams

Communication compliance is part of the new insider risk solution set in Microsoft 365 that helps minimize communication risks by helping you detect, capture, and take remediation actions for inappropriate messages in your organization. It helps in identifying Offensive language and anti-harassment in Team Channels or 1:1 and Group chats. You can also set policies to see if any Sensitive information is being shared as part of Team channels or 1:1 and Group chats. For more information on different types of policies and how to set up refer to the [M365 article](https://docs.microsoft.com/microsoft-365/compliance/communication-compliance).

## How to use communication compliance in Teams

### Identify inappropriate messages

If you want to identify any messages that are sent in Microsoft Teams (1:1, Group Chats or Channel conversations) contain Offensive Language or anti-harassment, you can enable policies to identify this and the reviewer can look into the messages and take necessary steps like sending training material or escalate to the right authorities.

### Identify sensitive or Regulatory information

If you want to scan messages sent in Microsoft Teams (1:1, Group Chats or Channel conversations) for sensitive information or regulatory types, you can choose policies that support predefined sensitive or regulatory types.

> [!NOTE]
> Private channels are not supported by communication compliance.

### Custom Policy

Use this template to configure specific communication channels, individual detection conditions, and the amount of content to monitor and review in your organization.

### Custom Trainable classifier

Use trainable classifiers when one of the out of the box classifiers won't meet your needs. A Microsoft 365 classifier is a tool you can train to recognize various types of content by giving it samples to look at. Training the classifier involves first giving it samples that are human picked and positively match the category. Then, after it has processed those samples, you test the predictions by giving it a mix of positive and negative samples. To Lean more about this refer to the [M365 article](https://docs.microsoft.com/microsoft-365/compliance/classifier-creating-a-trainable-classifier) for more on this topic.

> [!NOTE]
> Communication compliance does not support Exchange hybrid deployments.

Communication compliance supports conversation history for any messages that match the polices. This provides context to the investigating admin.

:::image type="content" source="media/communication-compliance-1.png" alt-text="A screen for communication compliance in Microsoft Teams.":::

## Where communication policies can be applied in Teams

Communication compliance policies can be setup for messages sent in Teams at the following levels:

- User level : An admin can set up policies at an individual user level or apply it to all the users on the tenant. This will only covers messages that a user sent in 1:1 or Group chats.
- Team Level: An admin can also set up policies on a team. This covers all the messages sent in the channel in that team (Private channel messages are not supported).

## What do you need to do to enable communication compliance in Teams

Before you get started with communication compliance, you should confirm your [Microsoft 365 subscription](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) and any add-ons. To access and use communication compliance, your organization must have one of the following subscriptions or add-ons:



UNFINISHED DO NOT PUBLISH ???
