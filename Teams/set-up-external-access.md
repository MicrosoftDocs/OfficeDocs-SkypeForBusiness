---
title: "Allow users to contact external Teams users"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.audience: Admin
appliesto:
- Microsoft Teams
localization_priority: Normal

description: "See how to configure Teams to let users talk to users in another organization, or let outside contacts talk to them. "
---

# Allow users to contact external Skype for Business users

<<I don't know if this applies to Teams.>>
> [!NOTE]
> Skype for Business federation isn't available to Office 365 operated by 21Vianet and Office 365 Germany organizations. 
  
Use the steps in this article when:
  
- You have users on different domains in your business. For example, Rob@ContosoEast.com and Ann@ContosoWest.com.
    
- You want the people in your organization to use Teams to contact people in specific businesses outside of your organization.
    
- You want anyone else in the world who uses Teams to be able to find and contact you, using your email address. If you and they use the default settings, this will work automatically. If they don't, then they need to make sure their configuration isn't blocking your domain.
    
## Enable business-to-business communications for your users
<a name="bk_preview"> </a>

You must have [admin permissions](https://support.office.com/en-us/article/da585eea-f576-4f55-a1e0-87090b6aaa9d) in Office 365 in both organizations to do this.

1. In the left navigation, go to **Org-wide settings** > **External access**. 

2. At the top of the **External access** page, turn on **External access**. 

3. Click **Save**. 

4. Make sure the admin in the other organization follows the same steps and enters the domain for your business as an allowed domain.
 
5. **WAIT UP TO 24 HOURS TO TEST**. Any time you change the external communications settings, it can take up to 24 hours for the changes to populate across all the data centers.

  
## Test and troubleshoot
<a name="bk_preview"> </a>

 **The most common issue people encounter when setting up business-to-business communication is getting their [Office 365 URLs and IP address ranges](https://docs.microsoft.com/en-us/microsoftteams/office-365-urls-ip-address-ranges) right.**
  
To test your setup, you need a contact on Teams who's not behind your company firewall.
  
1. After you change your external communications settings, **WAIT UP TO 24 HOURS TO TEST**.
    
2. Search for your contact in Skype for Business, and send a request to chat.
    
    If you get a message that it couldn't be sent due to company policy, you need to double-check your [Office 365 URLs and IP address ranges](https://docs.microsoft.com/en-us/microsoftteams/office-365-urls-ip-address-ranges).
    
3. Ask your contact to send you a request to chat. If you don't receive their request, the problem is your firewall settings (assuming they've already confirmed their firewall settings are correct).
    
4. Another way to test whether the problem is your firewall is to go to a wifi location not behind your firewall such as a coffee shop, and use Teams to send a request to your contact to chat. If the message goes through there, but not when you're at work, then you know the problem is your firewall.
    
## How to find others, and be found, when connecting with another business
<a name="bk_preview"> </a>

<<I don't know if the federated part applies to Teams.>>

After you enable external communication with other Teams users, your users can find federated Teams users by searching for their sign-in name: for example, Rob@contoso.com. Then they will need to add the person to their list of contacts.
  
  
## Tips on setting up communications with federated businesses
<a name="bk_preview"> </a>

<<Not sure if this section applies.>>

- To configure federation between Skype for Business 2015 and Skype for Business Online, see this TechNet article: [Configure federation with Skype for Business Online](https://technet.microsoft.com/en-us/library/jj205126.aspx).
    
- To configure federation between Lync and Skype for Business Online, see this TechNet article: [Configuring Federation Support for a Lync Online Customer](https://technet.microsoft.com/en-us/library/hh202193.aspx).
    
- When two Skype for Business users in Office 365 are communicating with each other on separate domains, they can only use Skype for Business features (for example, video conversations or desktop sharing) that are turned on in both organizations.
    
- If a Skype for Business user in your organization is put on an In-Place or Litigation Hold, any IM conversations between that user and other Skype for Business or Skype users will be saved in **Recoverable Items** in their mailbox. These conversations aren't saved in the **Conversations History** folder in their mailbox.
    
## Turn off external communication for specific individuals
<a name="bk_preview"> </a>

<<Does this procedure stay the same? >>

After you enable external communication for your entire business, you can turn it off for only specific individuals.
  
1. Sign in with your Office 365 admin account.
    
2. In the Office 365 admin center, go to **Users** > **Active users**.
    
3. In the list of users, choose the user, and then, under **More Settings**, click **Edit Skype for Business properties**.
    
    ![Choose Skype for Business](../skype/sfbonline/images/2b0f9a7b-3fee-4f4b-968a-68c429eeb395.png)
  
4. In the **Skype for Business admin center**, choose **External communications**.
    
    On the **Options** page, all of the choices will be selected. Clear the communications you want to disable. The following image shows that Jakob will be able to communicate with people in other trusted businesses, but not with other Skype users.
    
    ![Choose External contacts](../skype/SfbOnline/images/4e546321-a065-48ed-8ac7-1e112a780eab.png)
  
5. Choose **Save**.
    
> [!NOTE]
> You may have to wait up to 24 hours for your changes to take effect. 
  
  
   
## Related topics
<a name="bk_preview"> </a>

[Set up Skype for Business Online](../skype/sfbonline/set-up-skype-for-business-online/set-up-skype-for-business-online.md)
  
[Let Skype for Business users add Skype contacts](../skype/sfbonline/set-up-skype-for-business-online/let-skype-for-business-users-add-skype-contacts.md)
  
  
 
