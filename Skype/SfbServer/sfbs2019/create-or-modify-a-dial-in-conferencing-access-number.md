---
title: "Create or modify a dial-in conferencing access number in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 06f55c28-57f8-4d4e-8313-9740846796d9
description: "Follow these steps if you want to create or modify a dial-in conferencing access number."
---

# Create or modify a dial-in conferencing access number in Lync Server 2013
[]
Follow these steps if you want to create or modify a dial-in conferencing access number.
  
> [!IMPORTANT]
> Before you create a new dial-in access number, you must set a dial-in conferencing region in the dial plan that is associated with the new dial-in access number. Multiple dial plans can use the same region. 
  
### To create or modify a dial-in access number

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Conferencing** and then click **Dial-in Access Number**.
    
4. On the **Dial-in Access Number** page, do one of the following: 
    
  - Click **New** to open **New Dial-in Access Number**.
    
  - Click one of the dial-in access numbers in the list, click **Edit**, and then click **Show details**.
    
    > [!NOTE]
    > Using the search field to search for the contents of a column in the list of dial-in access numbers may not yield the results you expect. Instead, sort the list by the column of interest to identify the dial-in access number you want to view or change. 
  
5. In **Display number**, type the phone number that public switched telephone network (PSTN) phone users dial to join a conference. 
    
    > [!NOTE]
    > This number is displayed in meeting invitations and on the Dial-in Conferencing Settings webpage. 
  
6. In **Display name**, type a description for the dial-in access number. This is the name that is associated with the dial-in access number in Lync search results.
    
    > [!NOTE]
    > This name is displayed in the client when a user calls the access number. 
  
7. In **Line URI**, type the E.164 number of the dial-in access number in TEL URI format, including the + symbol before the number and excluding spaces. For example, tel:+14255550200.
    
    > [!NOTE]
    > The same Line URI cannot be reused by another dial-in conferencing access number. 
  
8. In **SIP URI**, do the following:
    
  - In the text box, type a unique SIP URI for this dial-in conferencing access number. This SIP URI is displayed in various locations including, but not limited to, call notification messages and previous versions of Communicator clients.
    
    > [!NOTE]
    > The same SIP URI cannot be reused by another dial-in conferencing access number. The SIP URI cannot be modified after the access number is created. The only way to change the SIP URI is to delete and recreate the access number. 
  
  - In the drop-down list box, click the domain of the Conferencing Attendant application that supports this dial-in access number.
    
9. In **Pool**, click the pool that is running the instance of Conferencing Attendant that supports this dial-in access number.
    
    > [!NOTE]
    > If you need to change the pool after you create the access number, you must use the **Move-CsApplicationEndpoint** cmdlet or delete and recreate the access number. 
  
10. In **Primary language**, click the language in which prompts are played for this dial-in access number. 
    
    > [!NOTE]
    > The primary language is the language that the Conferencing Attendant uses to answer the call. Supported languages are displayed alongside each access phone number on the Dial-in Conferencing Settings webpage. 
  
11. (Optional) In **Secondary languages (maximum of four)**, click **Add**, select one or more additional languages that you want to support for callers to this dial-in access number, and then click **OK**. 
    
    > [!NOTE]
    > You can choose up to four secondary languages for each dial-in access number. Users can select a secondary language before entering the conference ID when they dial in to a conference. 
  
12. To add a region for the dial-in access number, under **Associated regions**, click ** Add **, click one or more regions that are associated with the dial plans for this dial-in access number, and then click **OK**.
    
13. To delete a region from the dial-in access number, under **Associated regions**, click the region you want to delete, and then click **Remove**.
    
14. Click **Commit**.
    

