---
title: Microsoft Teams external domain activity report
ms.author: jtremper
author: jacktremper
manager: pamgreen
audience: Admin
ms.topic: article
ms.service: msteams
ms.reviewer: izzychun
ms.date: 01/23/2024
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
description: Learn how to use the Teams external domain usage report in the Microsoft Teams admin center to get an overview of external domain activity in your organization.
appliesto: 
  - Microsoft Teams
---
# Microsoft Teams external domain activity report

The external domain activity report in the Microsoft Teams admin center shows you the number of users in your organization that have communicated with [trusted external organizations](/microsoftteams/trusted-organizations-external-meetings-chat?tabs=organization-settings#specify-trusted-microsoft-365-organizations) each day. This report includes information for 1:1 and group chats, but not meetings or calls.

Note that if you have an explicit allowed domains list, this report may include domains not on your allow list. It is possible for users from an allowed organization to start a group chat with users from your organization and users from other organizations allowed by them, but not allowed by you. These domains will show up in your external domain activity report.

## View the usage report

1. In the left navigation of the Microsoft Teams admin center, select **Analytics & reports** > **Usage reports**. On the **View reports** tab, under **Report**, select **External domain activity**.
1. Under **Date range**, select a predefined date range.
1. Select **Run report**.  

## Interpret the report

:::image type="content" alt-text="Screenshot of the Teams external domain activity report in the Teams admin center." source="../media/external-domain-report-small.png" lightbox="../media/external-domain-report-expand.png":::

|Item |Description  |
|--------|-------------|
|Domain name|The domain of the trusted organization.|
|People in my org|The number of users that have communicated with the organization through meetings or chat during the selected time range.|

## Related topics

[Teams analytics and reporting](teams-reporting-reference.md)
