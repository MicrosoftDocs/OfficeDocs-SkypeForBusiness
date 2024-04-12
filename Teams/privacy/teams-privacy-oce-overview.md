---
title: Teams Optional Connected Experiences 
ms.author: danbrown
author: DHB-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: msteams
ms.collection: 
  - M365-collaboration
  - privacy-teams
ms.reviewer: 
ms.date: 10/04/2023
ms.localizationpriority: high
search.appverid: MET150
description: This article outlines the optional connected experiences you'll see in Microsoft Teams.
appliesto: 
  - Microsoft Teams
---

# Overview of optional connected experiences in Microsoft Teams

If you have a work or school account, your organization's admin may have provided you with the ability to use one or more cloud-backed services (also referred to as **optional connected experiences**) while using Microsoft Teams, like GIPHY and/or URL Preview service. These cloud-backed services are optional. Whether you use them is up to you. They're offered to you under  terms that differ from the [Microsoft Online Service Terms](https://www.microsoft.com/licensing/product-licensing/products), as described separately for each optional service. This article lists our Teams cloud-backed services.

If your admin has given you the ability to use optional connected experiences in Teams, you can go to **Settings** > **Privacy** in Teams and choose whether you want to use optional connected experiences.

> [!NOTE]
> If you're an admin, you can give or restrict your users' ability to use optional connected experiences. You can do this by using the [Office cloud policy service](/deployoffice/overview-office-cloud-policy-service) and configuring the *Allow the use of additional optional connected experiences in Office* policy setting. This is the same policy setting that controls whether optional connected experiences are available to your users in the Office apps (such as Word, Excel, and PowerPoint) that come with Microsoft 365 Apps for enterprise.

## GIPHY

GIPHY is a cloud-backed service that lets you use GIFs in your Teams chats. If you're in **Teams** > **GIF** > **Search**, the search terms are sent to GIPHY. These experiences, if allowed by your admin and after you choose to use them, are subject to the [GIPHY Privacy Policy](https://support.giphy.com/hc/articles/360032872931-GIPHY-Privacy-Policy) and [Terms of Service](https://support.giphy.com/hc/articles/360020027752-GIPHY-User-Terms-of-Service).

## Ratings and reviews for Teams apps

Ratings and reviews allow Teams users to provide feedback about their experience with using a Teams app. Reviews are anonymous unless the user chooses otherwise. All Teams users can view these ratings and reviews on the details page for the app. Users are only allowed to provide ratings and reviews for apps they’ve installed and only for apps that are publicly available from Microsoft or other companies. The ratings are powered by Microsoft AppSource and are shown on the app’s page on the [AppSource website](https://appsource.microsoft.com/). AppSource is provided under the [Microsoft Privacy Statement](https://privacy.microsoft.com/privacystatement) and the [Microsoft Commercial Marketplace Terms of Use](/legal/marketplace/marketplace-terms).

## Search Coach Tab App

The Search Coach Teams tab app available in Microsoft EDU Class Teams makes search requests to Bing search through the Bing API when a user sends a query, returning ad-free SafeSearch results. Experiences that rely on Bing are licensed to you under the terms of the [Microsoft Services Agreement](https://www.microsoft.com/servicesagreement) and covered by the [privacy statement](https://privacy.microsoft.com/privacystatement).

## Teams apps link previews

The Teams app link previews service generates a preview snippet of the app's adaptive card and attaches it under the URL when a user sends a URL string that maps to the app in the Teams store. If the URLP setting is turned on, this service will make a request to the service URL as the user is typing the message to unfurl a card preview. Tenant admin and user settings for apps would be honored.

## Teams device store checkout  

Teams device store is available in the Teams admin center and Teams App. It enables discovery and purchase of Teams certified devices. To enable checkout, the Teams device store shares basic user and company information, including user email address, user GUIDs, and tenant GUIDs, with UnifiedCommunications.com. This experience, if allowed by the **Allow the use of additional optional connected experiences in Office** policy setting, is subject to the terms of service and privacy statement of UnifiedCommunications.com.

To learn more about Teams device store, see [Purchase devices in the Teams device store](../devices/device-store.md).

## URL Preview service

The URL Preview service automatically generates a preview snippet and attaches under the snippet the URL when a user sends a URL string. This service will make a request to the service URL as the user is typing the message. If the service URL doesn't have any schema.org data, it will send a request to Bing search to get the data it needs to generate the preview snippet. Experiences that rely on Bing are licensed to you under the terms of the [Microsoft Services Agreement](https://www.microsoft.com/servicesagreement) and covered by the [privacy statement](https://privacy.microsoft.com/privacystatement). Any URLs you provide to Microsoft Teams while using these services can be sent to Microsoft Bing, including Bing Content Validation Service for evaluation of harmful content. They aren't linked to you by the Bing organization.

:::image type="content" source="../media/url-preview.png" alt-text="A screen showing a sample of a URL preview for the Microsoft home page in a text box.":::

## Related articles

- [Overview of policy controls for Teams](policy-control-overview.md)
- [Overview of optional connected experiences in Office](/deployoffice/privacy/optional-connected-experiences)
- [Required service data for Office](/deployoffice/privacy/required-service-data)
- [Account Privacy Settings](https://support.microsoft.com/office/3e7bc183-bf52-4fd0-8e6b-78978f7f121b)
