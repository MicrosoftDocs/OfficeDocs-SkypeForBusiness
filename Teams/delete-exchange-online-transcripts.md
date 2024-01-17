---
title: Delete Exchange Online and OneDrive Transcripts
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
ms.reviewer: richardzhang
ms.date: 17/01/2024
search.appverid: MET150
ms.localizationpriority: medium
f1.keywords:
- NOCSH
description: Learn how to delete Exchange Online and OneDrive Transcript files.
appliesto: 
  - Microsoft Teams
---

# Delete Exchange Online and OneDrive Transcript files

**APPLIES TO:** ✔️Meetings ✔️Webinars ✔️Town halls

In Microsoft Teams, the current storage location of meeting transcript files is in Exchange Online Transcript (EXO Transcript) or substrate transcript. EXO Transcript will be deprecated in 2024. The new storage location will be OneDrive for Business (ODB).

This article describes how to delete the meeting transcript files in Exchange Online.

## Delete EXO transcript files using XML

You need to use EWS API to delete a transcript file that’s saved on EXO. For more information on the instructions of API, see [EWS operations in Exchange](/exchange/client-developer/web-service-reference/ews-operations-in-exchange).

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

2. Find MeetingIntelligenceApp "93c8660e-1330-4e40-8fda-fd27f9eafe10" folder ID, as shown in the following code sample:

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

## Delete specific transcript file using XML

1. Get the *MeetingTranscriptCollection folder ID* using the first three steps mentioned in the [above section](#delete-exo-transcript-files-using-xml).

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

You can also use the [EWSEditor open source tool](https://github.com/dseph/EwsEditor) to delete the meeting transcripts by following these steps:

1. Sign in with client app ID: "d3590ed6-52b3-4102-aeff-aad2292ab01c".

   Select **Validate Authority** to let tenant admin control the data of the user in the tenant:

   :::image type="content" source="media/delete-transcripts-ews-editor.png" alt-text="Image of the screenshot displaying the EWSEditor for deleting transcripts.":::

2. Select **Identify folder by well known name** and select **Root** as Folder name and provide SMTP address, as shown in the following image:

   :::image type="content" source="media/ews-editor-folder-ID.png" alt-text="Image displaying the screenshot of the EWSEditor requesting to select a FolderID.":::

3. Find the transcription folder and right-click to delete. 

    :::image type="content" source="media/ews-meeting-transcription-collection.png" alt-text="Image displaying the screenshot of the Meeting Transcription selection in EWSEditor." lightbox="media/EWS-Meeting-transcription-collection.png":::

    To view more details in a pane, double-click on the transcription folder.

    :::image type="content" source="media/ewseditorredetails.png" alt-text="Image displaying the screenshot of the View pane of EWSEditor." lightbox="media/ewseditorredetails.png":::

### Delete specific transcript using EWSEditor

To identify a particular meeting, users can check the DateTimeCreated. Additionally, they can check the threadId for the item by following these steps:

1. Select **View** and then **Configure Detail Property Set…** in the toolbar on top.

    :::image type="content" source="media/ews-editor-datetime-and-threadid.png" alt-text="Image displaying the screenshot of the DateTimeCreated selection in EWSEditor." lightbox="media/ews-editor-datetime-and-threadid.png":::

2. Select **Add Extended Property** in the Property Set Editor pane and select **OK**.

   :::image type="content" source="media/add-extended-property-ews-editor.png" alt-text="Image displaying the screenshot of Property Set Editor pane in EWSEditor.":::

   Provide the following details under Property Identifier in the Extended Property Definition pane and select **OK**:
   - Name or ID: RawJSON
   - Property Set: 2842957e-8ed9-439b-99b5-f681924bd972 
   - Property Type: String

   :::image type="content" source="media/EWSEditor-extendedproperty.png" alt-text="Image displaying the screenshot of Extended Property pane in EWSEditor.":::

3. Go back to EWSEditor and the new property will be displayed with its raw JSON string in the lower part of the pane.

    :::image type="content" source="media/Filtered-string-ews-editor.png" alt-text="Image displaying the screenshot of filtered string in EWSEditor." lightbox="media/Filtered-string-ews-editor.png":::

4. Double-click on the property to open it in a new window and check the threadId, as shown in this image: 

    :::image type="content" source="media/threadid-ews-editor.png" alt-text="Image that displays the Thread ID in EWSEditor." lightbox="media/threadid-ews-editor.png":::

## Deleting transcript copy in ODSP via Microsoft Purview

You can choose to delete Teams meeting recordings along with their accompanying transcripts by using an *auto-apply retention label policy* that identifies these files from OneDrive and SharePoint Transcript (ODSP) or ODB Transcript. For more information, see [Automatically apply a retention label to Microsoft 365 items](/purview/apply-retention-labels-automatically). 

Here are the most relevant sections to help you get started:

- [How to create an auto-apply retention label policy](/purview/apply-retention-labels-automatically#how-to-create-an-auto-apply-retention-label-policy)
- [Auto-apply labels to content with keywords or searchable properties](/purview/apply-retention-labels-automatically#auto-apply-labels-to-content-with-keywords-or-searchable-properties)
- [Identifying Teams meeting recordings and accompanying transcripts in ODSP](/purview/apply-retention-labels-automatically#microsoft-teams-meeting-recordings)
- [How long it takes for retention labels to take effect](/purview/apply-retention-labels-automatically#how-long-it-takes-for-retention-labels-to-take-effect)

>[!NOTE]
> When creating a retention label policy in Microsoft Purview, the minimum retention period is 1 day, which means the recordings and accompanying transcripts will only be deleted after 1 day.  
