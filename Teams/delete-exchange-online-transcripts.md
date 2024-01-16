---
title: Delete Exchange Online and OneDrive transcripts
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
  - highpri
  - Tier1
ms.reviewer: nakulm
ms.date: 03/13/2023
search.appverid: MET150
ms.localizationpriority: medium
f1.keywords:
- NOCSH
description: Learn how to Delete Exchange Online and OneDrive transcript files.
appliesto: 
  - Microsoft Teams
---

# Delete Exchange Online and OneDrive transcripts

**APPLIES TO:** ✔️Meetings ✔️Webinars ✔️Town halls

The current storage location of meeting transcript files in Microsoft Teams, that is Exchange Online Transcript (EXO transcript) or substrate transcript will be deprecated in 2024. The new storage location will be OneDrive for Business (ODB) and is referred to as OneDrive and SharePoint Transcript (ODSP or ODB transcript).


You need to use EWS API to delete a transcript file that’s saved on EXO. For more information, see [EWS operations in Exchange](https://learn.microsoft.com/en-us/exchange/client-developer/web-service-reference/ews-operations-in-exchange).

`Root\ApplicationDataRoot\93c8660e-1330-4e40-8fda-fd27f9eafe10\MeetingTranscriptCollection\`

## Step 1: Find ParentFolderId (ApplicationDataRoot) 

To find the ParentFolderId, 

```xml
<?xml version="1.0" encoding="utf-8"?> 

<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:m="http://schemas.microsoft.com/exchange/services/2006/messages" xmlns:t="http://schemas.microsoft.com/exchange/services/2006/types" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"> 

  <soap:Header> 

    <t:RequestServerVersion Version="Exchange2010_SP2" /> 

  </soap:Header> 

  <soap:Body> 

    <m:FindFolder Traversal="Shallow"> 

      <m:FolderShape> 

        <t:BaseShape>IdOnly</t:BaseShape> 

        <t:AdditionalProperties> 

          <t:FieldURI FieldURI="folder:DisplayName" /> 

        </t:AdditionalProperties> 

      </m:FolderShape> 

      <m:IndexedPageFolderView MaxEntriesReturned="50" Offset="0" BasePoint="Beginning" /> 

      <m:Restriction> 

          <t:IsEqualTo> 

            <t:FieldURI FieldURI="folder:DisplayName" /> 

            <t:FieldURIOrConstant> 

              <t:Constant Value="ApplicationDataRoot"/> 

            </t:FieldURIOrConstant> 

          </t:IsEqualTo> 

      </m:Restriction> 

      <m:ParentFolderIds> 

        <t:DistinguishedFolderId Id="root" /> 

      </m:ParentFolderIds> 

    </m:FindFolder> 

  </soap:Body> 

</soap:Envelope> 
```

## Step 2: Find MeetingIntelligenceApp "93c8660e-1330-4e40-8fda-fd27f9eafe10" folder ID

```xml
<?xml version="1.0" encoding="utf-8"?> 

<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:m="http://schemas.microsoft.com/exchange/services/2006/messages" xmlns:t="http://schemas.microsoft.com/exchange/services/2006/types" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"> 

  <soap:Header> 

    <t:RequestServerVersion Version="Exchange2010_SP2" /> 

  </soap:Header> 

  <soap:Body> 

    <m:FindFolder Traversal="Shallow"> 

      <m:FolderShape> 

        <t:BaseShape>AllProperties</t:BaseShape> 

        <t:AdditionalProperties> 

          <t:FieldURI FieldURI="folder:DisplayName" /> 

        </t:AdditionalProperties> 

      </m:FolderShape> 

      <m:IndexedPageFolderView MaxEntriesReturned="50" Offset="0" BasePoint="Beginning" /> 

      <m:Restriction> 

          <t:IsEqualTo> 

            <t:FieldURI FieldURI="folder:DisplayName" /> 

            <t:FieldURIOrConstant> 

              <t:Constant Value="93c8660e-1330-4e40-8fda-fd27f9eafe10"/> 

            </t:FieldURIOrConstant> 

          </t:IsEqualTo> 

      </m:Restriction> 

      <m:ParentFolderIds> 

<t:FolderId Id="AQMkADRhOWIyODBmLTQzMDEtNDc5Yi1iNTY2AC0zYWM4YjNhMjhkNWMALgAAA784AonxS+lBuntvnROGrHMBACDUFKCn6g9ItmL6JTlNKDAAAAIBIgAAAA==" ChangeKey="AQAAAA==" /> 

      </m:ParentFolderIds> 

    </m:FindFolder> 

  </soap:Body> 

</soap:Envelope> 
```

## Step 3: Find MeetingTranscriptCollection folder ID

```xml
<?xml version="1.0" encoding="utf-8"?> 

<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:m="http://schemas.microsoft.com/exchange/services/2006/messages" xmlns:t="http://schemas.microsoft.com/exchange/services/2006/types" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"> 

  <soap:Header> 

    <t:RequestServerVersion Version="Exchange2010_SP2" /> 

  </soap:Header> 

  <soap:Body> 

    <m:FindFolder Traversal="Shallow"> 

      <m:FolderShape> 

        <t:BaseShape>AllProperties</t:BaseShape> 

        <t:AdditionalProperties> 

          <t:FieldURI FieldURI="folder:DisplayName" /> 

        </t:AdditionalProperties> 

      </m:FolderShape> 

      <m:IndexedPageFolderView MaxEntriesReturned="50" Offset="0" BasePoint="Beginning" /> 

      <m:Restriction> 

          <t:IsEqualTo> 

            <t:FieldURI FieldURI="folder:DisplayName" /> 

            <t:FieldURIOrConstant> 

              <t:Constant Value="MeetingTranscriptCollection"/> 

            </t:FieldURIOrConstant> 

          </t:IsEqualTo> 

      </m:Restriction> 

      <m:ParentFolderIds> 

<t:FolderId Id="AAMkADRhOWIyODBmLTQzMDEtNDc5Yi1iNTY2LTNhYzhiM2EyOGQ1YwAuAAAAAAC/OAKJ8UvpQbp7b50ThqxzAQAg1BSgp+oPSLZi+iU5TSgwAAF1f4tpAAA=" ChangeKey="AQAAABYAAAAg1BSgp+oPSLZi+iU5TSgwAATlHZy8"/> 

      </m:ParentFolderIds> 

    </m:FindFolder> 

  </soap:Body> 

</soap:Envelope> 
```

## Step 4: Delete all transcription files of a user by deleting MeetingTranscriptCollection folder 

```xml
<?xml version="1.0" encoding="utf-8"?> 

<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:m="http://schemas.microsoft.com/exchange/services/2006/messages" xmlns:t="http://schemas.microsoft.com/exchange/services/2006/types" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"> 

  <soap:Header> 

    <t:RequestServerVersion Version="Exchange2016" /> 

  </soap:Header> 

  <soap:Body> 

    <m:DeleteFolder DeleteType="HardDelete"> 

      <m:FolderIds> 

        <t:FolderId Id="AAMkAGUzNDY1MjY4LTRmNjItNGQ1Ni05YzE4LTE1NDlmYzFiZmFmYgAuAAAAAAC+Ct50+goBS4yeyX/xvq9QAQDhHjGubgXIQZeXAlxCHvQOAACwZS4iAAA=" ChangeKey="AQAAABYAAADhHjGubgXIQZeXAlxCHvQOAACwOP/U" /> 

      </m:FolderIds> 

    </m:DeleteFolder> 

  </soap:Body> 

</soap:Envelope> 
```

Steps to delete specific item: 

Find MeetingTranscriptCollection folder ID by following the first 3 steps mentioned above.

### Find Transcript based on threadId + DateTimeCreated

```xml
<?xml version="1.0" encoding="utf-8"?> 

<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:m="http://schemas.microsoft.com/exchange/services/2006/messages" xmlns:t="http://schemas.microsoft.com/exchange/services/2006/types" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"> 

  <soap:Header> 

    <t:RequestServerVersion Version="Exchange2010_SP2" /> 

  </soap:Header> 

  <soap:Body> 

    <m:FindItem Traversal="Shallow"> 

      <m:ItemShape> 

        <t:BaseShape>AllProperties</t:BaseShape> 

        <t:AdditionalProperties> 

          <t:ExtendedFieldURI PropertySetId="2842957e-8ed9-439b-99b5-f681924bd972" PropertyName="RawJSON" PropertyType="String" /> 

        </t:AdditionalProperties> 

      </m:ItemShape> 

      <m:Restriction> 

<t:And> 

         <t:Contains ContainmentMode="Substring" ContainmentComparison="IgnoreCase"> 

          <t:ExtendedFieldURI PropertySetId="2842957e-8ed9-439b-99b5-f681924bd972" PropertyName="RawJSON" PropertyType="String" /> 

           <t:Constant Value="19:meeting_ZWRmMGVkMDctNTI0NS00NmQ4LWJjMDgtMDA5MjVhMzE0ZjJl@thread.v2"/> 

         </t:Contains> 

        <t:GreaterThanOrEqual> 

          <t:FieldURI FieldURI="item:DateTimeReceived" /> 

          <t:FieldURIOrConstant> 

            <t:Constant Value="2022-12-28T00:00:00Z" /> 

          </t:FieldURIOrConstant> 

        </t:GreaterThanOrEqual> 

</t:And> 

      </m:Restriction> 

      <m:ParentFolderIds> 

                <t:FolderId Id="AAMkAGUzNDY1MjY4LTRmNjItNGQ1Ni05YzE4LTE1NDlmYzFiZmFmYgAuAAAAAAC+Ct50+goBS4yeyX/xvq9QAQDhHjGubgXIQZeXAlxCHvQOAAEP+YkQAAA=" /> 

      </m:ParentFolderIds> 

    </m:FindItem> 

  </soap:Body> 

</soap:Envelope> 
```

## Delete Transcript

```xml
<?xml version="1.0" encoding="utf-8"?> 

<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:m="http://schemas.microsoft.com/exchange/services/2006/messages" xmlns:t="http://schemas.microsoft.com/exchange/services/2006/types" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"> 

  <soap:Header> 

    <t:RequestServerVersion Version="Exchange2010_SP2" /> 

  </soap:Header> 

  <soap:Body> 

    <m:DeleteItem DeleteType="HardDelete"> 

      <m:ItemIds> 

        <t:ItemId Id="AAMkAGUzNDY1MjY4LTRmNjItNGQ1Ni05YzE4LTE1NDlmYzFiZmFmYgBGAAAAAAC+Ct50+goBS4yeyX/xvq9QBwDhHjGubgXIQZeXAlxCHvQOAACwZS4iAADhHjGubgXIQZeXAlxCHvQOAAEP+bwSAAA=" /> 

      </m:ItemIds> 

    </m:DeleteItem> 

  </soap:Body> 

</soap:Envelope> 
```

## Delete transcripts using EWS editor

You can also use the [Ews editor open source tool](https://github.com/dseph/EwsEditor) to delete the meeting transcripts. 

Logging in with client app ID: d3590ed6-52b3-4102-aeff-aad2292ab01c

Tenant admin to control the data of the user from the tenant: 

Find the transcription folder, right click to delete or double click to view the details: 

To identify a particular meeting, users can check the DateTimeCreated. Additionally, they can check the threadId for the item by following these steps: 

Click on View->Configure Detail Property Set… in the toolbar on top 

Click on "Add Extended Property" 
Name or ID: RawJSON 
property Set: 2842957e-8ed9-439b-99b5-f681924bd972 
Property Type: String 

Go back to EWS editor and it the new property should be there with the raw json string in the lower pane 

## Deleting transcript copy in ODSP via Microsoft Purview 

You can choose to delete Teams meeting recordings with their accompanying transcripts by using an auto-apply retention label policy that identifies these files from ODSP. You can find all the details in Automatically apply a retention label to Microsoft 365 items | Microsoft Learn, and here are the most relevant sections to help you get started: 

How to create an auto-apply retention label policy 

Auto-apply labels to content with keywords or searchable properties 

Identifying Teams meeting recordings and accompanying transcripts in ODSP 

How long it takes for retention lables to take effect 

>[!NOTE]
> When creating a retention label policy in Microsoft Purview, the minimum retention period is 1 day, meaning recordings and accompanying transcripts will only be deleted after 1 day.  
