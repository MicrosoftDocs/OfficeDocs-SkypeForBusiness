---
title: 'Lync Server 2013: Create or modify a new client version policy rule'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Create or modify a new client version policy rule
ms:assetid: 6f879d99-8401-41e0-a562-195c890d63ea
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ898478(v=OCS.15)
ms:contentKeyID: 50873758
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Create or modify a new client version policy rule in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-01-21_

Client version policy rules define the actions that should be taken when users attempt to log on with specific clients and client versions. You can create or modify individual rules for a client version policy from Lync Server 2013 Control Panel.

<div>


> [!IMPORTANT]  
> Rules are listed in order of precedence. For example, if you have a rule that allows clients running version 1.5 to connect, followed by a rule that blocks clients running a version earlier than 2.0, the first rule takes precedence, and clients running version 1.5 are allowed to connect.



</div>

<div>

## To create or modify client version policy rules with Lync Server Control Panel

1.  [Create or modify a new client version policy in Lync Server 2013](lync-server-2013-create-or-modify-a-new-client-version-policy.md) with Lync Server Control Panel.

2.  On the **Edit Client Version Policy** page, do one of the following:
    
      - Click **New** to create a new client version rule.
    
      - Click one of the defined client types in the list, and then click **Show details**.
    
    <div>
    

    > [!NOTE]  
    > You can use wildcards to indicate the client type.

    
    </div>

3.  In **User agent**, select a client type.

4.  Under **Version number**, do the following:
    
      - In **Major version**, type the number that corresponds to the major release of the client.
    
      - In **Minor version**, type the number that corresponds to the minor release of the client.
    
      - In **Build**, type the number that corresponds to the major and minor release of the client.
    
      - In **Update**, type the number that corresponds to the updated release of the client.
    
    <div>
    

    > [!NOTE]  
    > You can use wildcards to indicate the client version number.

    
    </div>

5.  To specify the matching operation for the client version you specified in the preceding steps, in **Comparison operation**, click one of the following:
    
      - **Same as**
    
      - **Is not**
    
      - **Newer than**
    
      - **Newer than or same as**
    
      - **Older than**
    
      - **Older than or same as**

6.  To specify the action to perform when the criteria in the preceding steps are met, click one of the following in **Action**:
    
      - To allow the client to log on, click **Allow**.
    
      - To allow the client to log on and receive updates from Windows Server Update Service or Microsoft Update, click **Allow and Upgrade**. This action is available only when user agent **OC** is selected.
        
        <div>
        

        > [!NOTE]  
        > Selecting this action causes a notification to appear the next time users sign in to Lync 2013. The notification states that an update is available, even if updates have not yet been released to Windows Server Update Service or Microsoft Update. To avoid confusion, you should choose this action only after updates become available.

        
        </div>
    
      - To allow the client to log on and display a message about where to download another client version, click **Allow with URL**. You specify the URL later in this procedure.
    
      - To prevent the client from logging on, click **Block**.
    
      - To prevent the client from logging on and allow the client to receive updates from Windows Server Update Service or Microsoft Update, click **Block and Upgrade**. This action is available only when user agent **OC** is selected.
    
      - To prevent the client from logging on and display a message about where to download another client version, click **Block with URL**. You specify the URL later in this procedure.

7.  (Optional) If you clicked **Allow with URL** or **Block with URL** in the previous step, type the client download URL to include in the message in **URL**.

8.  Click **OK**, and then click **Commit**.

</div>

</div>

<span> </span>

</div>

</div>

</div>

