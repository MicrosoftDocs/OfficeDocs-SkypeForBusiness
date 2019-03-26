---
title: "Customize user account properties for Skype for Business Server"
ms.reviewer: 
ms.author: jambirk
author: jambirk
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 505d9619-adab-4cc4-b054-89286e18a19b
description: "You can use the procedures in this section to modify individual user account properties."
---

# Customize user account properties for Skype for Business Server
 
You can use the procedures in this section to modify individual user account properties.
  
There are two basic operations that can be done at the individual user level:
  
- [Configure telephony options for a specific user account](customize-properties.md#Tel_Op)
    
- [Move users to another pool ](customize-properties.md#Move_Users)
    
## Configure telephony options for a specific user account
<a name="Tel_Op"> </a>

You can customize the telephony settings for a specific user (so long as the individual user has been enabled for Skype for Business Server and the organization supports telephony).
  
Skype for Business Server user telephony options include the following:
  
- **Audio/video disabled** The user cannot make calls with audio and video.
    
- **PC-to-PC only** The user can make only PC-to-PC audio or video calls.
    
- **Enterprise Voice** The user can use the Skype for Business Server infrastructure to route all incoming and outgoing calls. The user can also make PC-to-PC calls.
    
- **Remote call control** The user can use Skype for Business Server to control the desktop phone, and can also make PC-to-PC calls.
    
For details about configuring telephony for an organization, see [Enable users for Enterprise Voice in Skype for Business Server](../../deploy/deploy-enterprise-voice/enable-users-for-enterprise-voice.md) and [Deploy Enterprise Voice in Skype for Business Server](../../deploy/deploy-enterprise-voice/deploy-enterprise-voice.md) in the Deployment documentation.
  
1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 
    
3. In the left navigation bar, click **Users**.
    
4. In the **Search users** box, type all or the first portion of the display name, first name, last name, Security Accounts Manager (SAM) account name, SIP address, or line Uniform Resource Identifier (URI) of the user account that you want, and then click **Find**.
    
5. In the table, click the user account that you want to modify.
    
6. On the **Edit** menu, click **Modify**.
    
7. In **Telephony**, do the following:
    
   - To disable audio and video calls for the user, click **Audio/video disabled**.
    
   - To enable PC-to-PC audio communications for the user, but not remote call control or Enterprise Voice, click **PC-to-PC only**. Specify a value for **Line URI** for the telephone that the user uses for PC-to-PC audio communications.
    
   - To route the user's phone calls by using the Skype for Business infrastructure in accordance with the class of service policy, including PC-to-PC audio communication, click **Enterprise Voice**. In **Line URI**, specify the telephone number for Enterprise Voice. In **Dial plan policy** and **Voice policy**, specify the appropriate policies for the user. To specify the normalization rules for translating phone numbers dialed by the user to the E.164 format, select the appropriate location profile in **Location policy**.
    
   - To enable remote call control, which enables users to control their desktop phone line from Skype for Business Server to make PC-to-PC calls and PC-to-phone calls, click **Remote call control**. In **Line URI**, specify the telephone number for remote call control. The user must have a desktop phone and private branch exchange (PBX) connection for call routing.
    
## Move users to another pool
<a name="Move_Users"> </a>

You can use Skype for Business Server Control Panel to assign users to a specific server or pool.
  
> [!TIP]
> Moving all existing users from a source pool that is running Lync Server 2010 or earlier to a Skype for Business Server destination pool in a complex Active Directory environment might result in slower Active Directory replication. To avoid this, you can use search filters to move users from pools that are running Lync Server 2010 or earlier separately, or you can use Skype for Business Server Management Shell to move users with cmdlets. Also, the filter functionality works with Skype for Business Server users. 
  
### To move selected users to a different server or pool

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel.  
    
3. In the left navigation bar, click **Users**.
    
4. In the **Search users** box, type all or the first portion of the display name, first name, last name, Security Accounts Manager (SAM) account name, SIP address, or line Uniform Resource Identifier (URI) of the user account that you want, and then click **Find**. 
    
5. In the table, select a specific user or users in the list. 
    
6. On the **Action** menu, click **Move selected users to pool**.
    
7. In **Move Users**, select the pool that you want to move the users to in **Destination registrar pool**.
    
8. (Optional) If the destination server or pool is unavailable, select the **Force** check box.
    
    > [!CAUTION]
    > If you select **Force**, the user account is moved, but any associated user data is deleted (for example, conferences that the user has scheduled). If you do not select it, both the account and the associated data are moved. 
  
### To move all users from one server or pool to a different server or pool

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel.  
    
3. In the left navigation bar, click **Users**.
    
4. On the **Action** menu, click **Move all users to pool**.
    
5. In **Move Users**, select the pool that contains the user accounts that you want to move in **Source registrar pool**.
    
6. In **Destination registrar pool**, select the pool that you want to move the users to.
    
7. (Optional) If the destination server or pool is unavailable, select the **Force** check box.
    
    > [!CAUTION]
    > If you select **Force**, the user account is moved, but any associated user data is deleted (for example, conferences that the user has scheduled). If you do not select it, both the account and the associated data are moved. 
  
### To move users from one pool to a different pool by using a filter

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Skype for Business Server Control Panel. 
    
3. In the left navigation bar, click **Users**.
    
4. In **User Search**, click **Search**, and then click **Add Filter**.
    
5. In the Search criteria, select **Registrar Pool**, select **Equal to**, select **Current Pool FQDN**, and then click **Find**.
    
6. On the **Action** menu, click **Move all users to pool**.
    
    > [!NOTE]
    > When a filter is applied to an existing set of users, the option **Move all users to pool** is in the context of the filtered subset of users, not **all** possible users.
  
7. In **Move Users**, select the pool that contains the user accounts that you want to move in **Source registrar pool**.
    
8. In **Destination registrar pool**, select the pool where you want to move the users.
    
9. (Optional) If the destination server or pool is unavailable, select the **Force** check box.
    
    > [!CAUTION]
    > If you select **Force**, the user account is moved, but any associated user data is deleted (for example, conferences that the user has scheduled and contacts). If you do not select it, both the account and the associated data are moved. 
  
### To move users from one pool to another using Windows Powershell cmdlets

1. Depending on how you run Windows PowerShell commands (that is, locally or remotely), you need to log on as a member of the correct Skype for Business Server administrative roles as follows:
    
   a. If you are running the commands on the local machine (for example, you log on directly to a Front End Server): Log on to the computer where Skype for Business Server Management Shell is installed as a member of the RTCUniversalServerAdmins group or with the necessary user rights as described in **Delegate Setup Permissions**.
    
   b. If you are running the commands remotely on another computer (for example, you log on to your computer and run the commands remotely on a Standard Edition Front End Server): From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business**, and then click **Skype for Business Server Management Shell**.
    
3. To move single users, use the Move-CsUser cmdlet as follows:
    
    ```
    Move-CsUser -Identity "Pilar Ackerman" -Target "pool01.contoso.net"
    ```

    Where the user to move is the user Pilar Ackerman, and the user will be moved from their currently assigned home pool to the pool pool01.contoso.net
    
4. To move a large number of users, use filters with the **Get-CsUser** cmdlet and pass the resulting set of users to **Move-CsUser**:
    
    ```
    Get-CsUser -Filter {RegistrarPool -eq "CurrentPoolFqdn"} | Move-CsUser -Target "TargetPoolFQDN"
    ```

    The combined commands of the **Get-CsUser** and **Move-CsUser** might result in this:
    
    ```
    Get-CsUser -Filter {RegistrarPool -eq "pool02.contoso.net"} | Move-CsUser -Target "pool01.contoso.net"
    ```


