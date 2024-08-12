---
title: Delete Exchange Online and OneDrive transcripts
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
  - Tier3
ms.reviewer: richardzhang
ms.date: 06/18/2024
search.appverid: MET150
ms.localizationpriority: medium
f1.keywords:
- NOCSH
description: Learn how to delete Exchange Online and OneDrive transcript files.
appliesto: 
  - Microsoft Teams
---

# Delete Exchange Online and OneDrive transcript files

**APPLIES TO:** ✔️Meetings ✔️Webinars ✔️Town halls

In Microsoft Teams, the current storage location of meeting transcript files is known as Exchange Online transcript or substrate transcript. Exchange Online transcript is scheduled for deprecation in 2024. The new storage location is OneDrive.

This article describes how to delete the meeting transcript files in Exchange Online and OneDrive.

## Delete Exchange Online transcript files using XML

You need to use EWS API to delete a transcript file saved on Exchange Online. For more information on the instructions of API, see [EWS operations in Exchange](/exchange/client-developer/web-service-reference/ews-operations-in-exchange).

The structure of the transcription file will be: `Root\ApplicationDataRoot\93c8660e-1330-4e40-8fda-fd27f9eafe10\MeetingTranscriptCollection\`

1. Find ParentFolderId (ApplicationDataRoot) using the following code sample:

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

2. Find MeetingIntelligenceApp folder ID: "93c8660e-1330-4e40-8fda-fd27f9eafe10", as shown in the following code sample:

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

3. Find MeetingTranscriptCollection folder ID using the following code sample:

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

4. Delete all transcription files of a user by deleting MeetingTranscriptCollection folder, as shown in the following code sample:

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

### Delete specific transcript file using XML

1. Get the *MeetingTranscriptCollection folder ID* by following the first three steps mentioned in the [above section](#delete-exchange-online-transcript-files-using-xml).

2. Now, find a transcript based on threadId + DateTimeCreated using the following code sample:

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

3. Delete the transcript using the following sample code:

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

## Delete transcripts using EWSEditor

> [!WARNING]
> EWS Editor has no protection against data deletion or corruption. Only users with extensive Exchange AND EWS Editor knowledge should proceed (with caution). EWS Editor can cause extensive damage to an installation (including, but not limited to, folder deletion, account deletion, Teams data corruption, calendar corruption, mail corruption).

You can also use the [EWSEditor open source tool](https://github.com/dseph/EwsEditor) to delete the meeting transcripts by following these steps:

1. Sign in with client app ID: "d3590ed6-52b3-4102-aeff-aad2292ab01c".

   Select **Validate Authority** to let tenant admin control the data of the user in the tenant.

2. Select **Identify folder by well known name** and select **Root** as Folder name and provide SMTP address.

3. Find the transcription folder and right-click to delete. To view more details in a pane, double-click on the transcription folder.

### Delete specific transcript using EWSEditor

To identify a particular meeting, users can check the DateTimeCreated. Additionally, they can check the threadId for the item by following these steps:

1. Select **View** and then **Configure Detail Property Set…** in the toolbar on top.

2. Select **Add Extended Property** in the Property Set Editor pane and select **OK**.

   Provide the following details under Property Identifier in the Extended Property Definition pane and select **OK**:
   - Name or ID: RawJSON
   - Property Set: 2842957e-8ed9-439b-99b5-f681924bd972
   - Property Type: String

3. Go back to EWSEditor and the new property will be displayed with its raw JSON string in the lower part of the pane.

4. Double-click on the property to open it in a new window and check the threadId.

## Delete transcript copy in OneDrive and SharePoint via Microsoft Purview

You can choose to delete Teams meeting recordings along with their accompanying transcripts by using an *auto-apply retention label policy* that identifies these files from OneDrive and SharePoint transcript or OneDrive transcript. For more information, see [Automatically apply a retention label to Microsoft 365 items](/purview/apply-retention-labels-automatically).

Here are the most relevant sections to help you get started:

- [How to create an auto-apply retention label policy](/purview/apply-retention-labels-automatically#how-to-create-an-auto-apply-retention-label-policy)
- [Auto-apply labels to content with keywords or searchable properties](/purview/apply-retention-labels-automatically#auto-apply-labels-to-content-with-keywords-or-searchable-properties)
- [Identifying Teams meeting recordings and accompanying transcripts in OneDrive and SharePoint](/purview/apply-retention-labels-automatically#microsoft-teams-meeting-recordings)
- [How long it takes for retention labels to take effect](/purview/apply-retention-labels-automatically#how-long-it-takes-for-retention-labels-to-take-effect)

>[!NOTE]
> When creating a retention label policy in Microsoft Purview, the minimum retention period is 1 day, which means the recordings and accompanying transcripts will only be deleted after 1 day.

## Related articles

- [Teams meeting recording](meeting-recording.md)
- [Configure transcription and captions for Teams meetings](meeting-transcription-captions.md)
- [Teams policies reference - Meetings](settings-policies-reference.md#meetings)
