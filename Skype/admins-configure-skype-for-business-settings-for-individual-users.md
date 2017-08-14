---
title: Admins Configure Skype for Business settings for individual users
ms.assetid: 77b26eac-8228-4161-ba9f-733b187bd836
---


# Admins: Configure Skype for Business settings for individual users

This article explains how admins configure Skype for Business for a small number of users. To do these steps in bulk, we've included links to the PowerShell cmdlets you can use. 
  
    
    

To allow (or block) everyone in your business to communicate with external people, see:
-  [Allow users to contact external Skype for Business users](allow-users-to-contact-external-skype-for-business-users.md) : You can let your organization use advanced Skype for Business features (share desktops, look for who's online) to communicate with people in a specific trusted (federated) business. Also explains how to block communication with specific domains.
    
  
-  [Let Skype for Business users add Skype contacts](let-skype-for-business-users-add-skype-contacts.md) . You can let your organization use Skype for Business to search for and IM people who use Skype, the free app.
    
  

## Configure general settings for one user
<a name="__toc325019204"> </a>

You must have  [About Office 365 admin roles](http://technet.microsoft.com/library/da585eea-f576-4f55-a1e0-87090b6aaa9d%28Office.14%29.aspx) to perform these steps.
  
    
    

1. Sign in to Office 365 with your work or school account. 
    
  
2. Choose **Admin centers** > **Skype for Business**. 
    
  
3. Choose **Users**.
    
    ![In the Skype for Business admin center, choose Users.](images/7c80eeb3-6555-4fc8-91f4-61b493581e9e.png)
  
    
    

    
  
4. Choose which users you want to edit. 
    
  
5. In the right panel, choose **Edit**.
    
    ![Choose the edit icon.](images/5dd7c5bc-b8fa-4201-b6a6-1436ad8f88fb.png)
  
    
    

    
  
6. On the **General** options page, select or clear the check box next to the features you want to change, and then choose **Save**.
    

|**Option**|**Details**|
|:-----|:-----|
|Audio and HD video  <br/> |Allow this person to record audio meetings, audio and video meetings, or don't allow them to schedule any meeetings (none).  <br/> |
|Record conversations and meetings  <br/> |Choose what this person is allowed to record.  <br/> This option is not available with Skype for Business Basic  <br/> |
|For compliance, turn off non-archived features  <br/> | Choose this option if you're legally required to preserve electronically stored information. <br/>  Selecting this option turns off features that aren't captured when you have an [In-place hold](https://technet.microsoft.com/en-us/library/ff637980%28v=exchg.150%29.aspx) set up in in the Exchange admin center. It turns off the following features: <br/>  File transfer using instant messaging <br/>  Shared OneNote pages <br/>  PowerPoint annotations <br/> |
   
 **To configure these settings in bulk, use PowerShell. See  [Managing policies in Skype for Business Online](https://technet.microsoft.com/en-us/library/dn362826%28v=ocs.15%29.aspx)**.
  
    
    

## Block external communications
<a name="__toc325019206"> </a>

After you  [Let Skype for Business users add Skype contacts](let-skype-for-business-users-add-skype-contacts.md) for everyone in your company, you can selectively block external communications for specific individuals using these steps.
  
    
    

1. Choose **Users**, select the users whose settings you want to disable, and then choose **Edit**![Edit](images/2f8948c1-e4f3-4022-b9cd-37fed066056e.png). 
    
  
2. Choose **External communications**, and then clear the options as appropriate:
    
  - **External Skype for Business users**: Clear this box if you don't want the user to be able to communicate with Skype for Business users in federated domains.
    
  
  - **External Skype users**: Clear this box if you don't want the user to be able to communicate with people who are using the freeSkype app.
    
  
3. Click **Save**.
    
  
 **To configure these settings in bulk, use PowerShell. See  [Managing communications in Skype for Business Online with outside users and organizations](https://technet.microsoft.com/en-us/library/dn362813%28v=ocs.15%29.aspx)**.
  
    
    

## Edit dial-in conferencing settings for one user
<a name="__toc314837483"> </a>


1. Click **Users** > *UserName >* **Edit**![Edit](images/2f8948c1-e4f3-4022-b9cd-37fed066056e.png). 
    
  
2. Select your audio conferencing provider, type or change the requested information, and then click **Save**.
    

|**Dial-in conferencing setting**|**Description**|
|:-----|:-----|
|Provider  <br/> |Choose your audio conferencing provider from the list.  <br/> |
|**Toll number** (required) <br/> **Toll-free number** <br/> |The phone numbers you received from the audio conferencing provider. Format the numbers as you want them to appear in Skype for Business Meeting requests.  <br/> |
|**Passcode**(required)  <br/> |The participant passcode, or conference code, used to join meetings that are scheduled by this user.  <br/> |
   
 **To configure these settings in bulk, use PowerShell. See  [Set the dial-in phone numbers for meeting organizers that are included on invites](set-the-dial-in-phone-numbers-for-meeting-organizers-that-are-included-on-invite.md)**.
  
    
    

## See also
<a name="__toc314837483"> </a>


#### Other Resources


  
    
    
 [Set up Skype for Business Online](set-up-skype-for-business-online.md)
  
    
    
 [Skype for Business add-on licensing](skype-for-business-add-on-licensing.md)
