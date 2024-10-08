---
title: Microsoft Teams external domain activity report
ms.author: heidip
author: MicrosoftHeidi
manager: jtremper
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: izzychun
ms.date: 09/09/2024
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
description: Learn how to use the Teams external domain usage report in the Microsoft Teams admin center to get an overview of external domain activity in your organization.
appliesto: 
  - Microsoft Teams
---
# Microsoft Teams external domain activity report

The external domain activity report in the Microsoft Teams admin center shows you how you communicate with [trusted external organizations](/microsoftteams/trusted-organizations-external-meetings-chat?tabs=organization-settings#specify-trusted-microsoft-365-organizations) over chat. This report includes information for 1:1 chats, group chats, and meeting chats, but not for calls or meetings themselves. This report includes both a base and Teams Premium version, where the base version tells you which domains you communicate with and the premium version exposes more detailed information about your communication with each domain.

> [!NOTE]
> If you have an explicit allowed domains list, this report may include domains not on your allow list. It's possible for users from an allowed organization to start a group chat with users from your organization and users from other organizations allowed by them, but not allowed by you. These domains will show up in your external domain activity report.

## View the usage report

1. In the left navigation of the Microsoft Teams admin center, select **Analytics & reports** > **Usage reports**. On the **View reports** tab, under **Report**, select **External domain activity**.
1. Under **Date range**, select a predefined date range.
1. Select **Run report**.  

## Interpret the report

:::image type="content" alt-text="Screenshot of the Teams external domain activity report in the Teams admin center." source="../media/external-domain-report-small.png" lightbox="../media/external-domain-report-expand.png":::

|Item                           |Description |
|-------------------------------|------------|
|Domain name                    |The domain of the trusted organization. **Premium:** Each domain can be clicked on to see domain-specific insights. |
|People in my org               |The number of users that have communicated with the organization through chat during the selected time range. |
|**Premium:** Total messages    | The number of messages that have been exchanged between your organization and the external domain during the selected time range. |
|**Premium:** Messages sent     | The number of messages that have been sent to your organization by the external domain during the selected time range. |
|**Premium:** Messages received | The number of messages that have been sent by your organization to the external domain during the selected time range. |

> [!NOTE]
>
> It's possible to have 0 **people in my org**. If an external domain reaches out to your organization and receives no response, we will display 0 **people in my org**.

## Interpret the domain-specific report

|Item |Description  |
|--------|-------------|
|**Premium:** Username|The UPN of the user in your org who communicates with the external domain. |
|**Premium:** Messages sent| The number of messages that have been sent to each user by the external domain during the selected time range.|

> [!NOTE]
>
> It's not possible at this time to expose the messages received at a per-user basis due to privacy concerns.

## Related topics

[Teams analytics and reporting](teams-reporting-reference.md)
