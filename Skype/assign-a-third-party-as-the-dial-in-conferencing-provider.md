---
title: Assign a third-party as the dial-in conferencing provider
ms.prod: OFFICE365
ms.assetid: 77f68ca7-c1cf-40d9-9c23-87a6b2abe9de
---


# Assign a third-party as the dial-in conferencing provider

A dial-in conferencing provider supplies the  *conference bridge*  . The conference bridge provides the dial-in phone number, PINs, and conference IDs for meetings that are created. You only need to assign a dial-in conferencing provider to people who are going to schedule or lead Skype for Business meetings.
  
    
    

Dial-in conferencing providers are also called **audio-conferencing providers**.
## Steps to do BEFORE you can assign a third-party dial-in conferencing provider


1. Depending on your Office 365 plan, you might need to buy PSTN conferencing add-on licenses for the people in your organization who are going to schedule or lead meetings that use dial-in conferencing. To learn more, see  [Skype for Business add-on licensing](skype-for-business-add-on-licensing.md).
    
  
2. If you purchased PSTN conferencing add-on licenses, assign them to the people in your organization who are going to schedule or lead meetings that use dial-in conferencing. See  [Assign Skype for Business licenses](assign-skype-for-business-licenses.md).
    
    > [!NOTE]
      > If you assign a Skype for Business PSTN Conferencing license to someone AFTER you assign them a third-party dial-in conferencing provider, that person will automatically be set to use Microsoft as their dial-in conferencing provider instead! If this happens, you will need to first remove Microsoft as the dial-in conferencing provider before you can assign a third-party dial-in conferencing provider to them. 
3. Find a third-party dial-in conferencing provider at  [Microsoft PinPoint](https://go.microsoft.com/fwlink/?LinkId=797530). Contact them and find out how to get things set up with them.
    
    They will give you: 
    
  - **Dial-in numbers** and toll-free numbers if they are available.
    
  
  - **Conference IDs** that are used for each person who schedules meetings. Some ACPs call these conference passcodes.
    
    > [!TIP]
      > When you enable a person for dial-in conferencing, and add assign them an third-party dial-in conferencing provider, the dial-in numbers and conference IDs (passcodes) are automatically added to any **new** Skype for Business Online meetings that they create.

## How to assign a third-party dial-in conferencing provider to a user


1. In the **Skype for Business admin center**, choose **Users**. Select the user from the list and click **Edit** in the action pane.
    
  
2. On the user's properties page click ** Dial-in conferencing** and then put in this information:
    
  - **Provider name** select the third-party provider from the list.
    
  
  - **Toll number** this is required.
    
  
  - **Toll-free number** this isn't required.
    
  
  - **Conference ID** Put it in. This is provided by your audio conferencing provider.
    
  
3. Click **Save**.
    
  
4. Send each person the PIN you received from the dial-in conferencing provider. The PIN may be required to call in as the conference call organizer, or leader.
    
    > [!NOTE]
      > When you use a third-party dial-in conferencing provider, there isn't a way for you to see or set PINs on behalf of meeting organizers. 

## How to assign a third-party dial-in conferencing provider to many people at the same time


1. In the **Skype for Business admin center**, choose **Dial-in conferencing** > **Microsoft bridge**. At the bottom of the page, click **If you would like to configure a third-party audio conferencing provider instead, click here**.
    
    > [!NOTE]
      > If there is already a dial-in conferencing provider set up, at the bottom of the page click **Click here to configure a third-party audio conferencing provider**. 
2. On the **Configure a third-party audio conferencing provider page**, under **Import and export users**, click **Export wizard**, and then follow the steps in the **Export Users wizard**. When you finish, you'll have a file that lists the people you want to set up for dial-in conferencing. 
    
  
3. Send the file you created to your third-party dial-in conferencing provider. They will add dial-in conferencing information for the people listed in the file, and then return the file to you.
    
  
4. Double-check that the returned file has the right information in it. We've heard of instances where not everyone listed in the file got the right information. 
    
  
5. On the **Configure a third-party audio conferencing provider page**, under **Import and export users**, click **Import wizard**, and then follow the steps in the **Import Users wizard**
    
  
6. Send each person the PIN you received from the dial-in conferencing provider. The PIN may be required to call in as the conference call organizer, or leader.
    
    > [!NOTE]
      > When you use a third-party dial-in conferencing provider, there isn't a way for you to see or set PINs on behalf of meeting organizers. 

## When to use a third-party dial-in conferencing provider

If you are in a country where Microsoft dial-in conferencing isn't available, the service quality isn't great because of it's location, or you have an existing contract with a third-party dial-in conferencing provider, we recommend using a third-party dial-in conferencing provider. Otherwise, we recommend using Microsoft as your dial-in conferencing provider. 
  
    
    

## What else do I need to know?

A person in your organization can only use one dial-in conferencing provider. To change a person's dial-in conferencing provider to Microsoft, see  [Moving a user's dial-in conferencing provider to Microsoft](moving-a-user-s-dial-in-conferencing-provider-to-microsoft.md) or [Assign Microsoft as the dial-in conferencing provider](assign-microsoft-as-the-dial-in-conferencing-provider.md).
  
    
    

## Automate assigning the third-party audio conferencing provider by using Windows PowerShell


- To save time or automate this, you can use the  [Set-CsUserAcp](https://go.microsoft.com/fwlink/?LinkId=716851) cmdlet.
    
    > [!NOTE]
      > To change the dial-in provider from Microsoft to a third party audio conferencing provider, you must remove Microsoft as the dial-in conferencing provider. To do this, use the  [Disable-CsOnlineDialInConferencingUser](https://go.microsoft.com/fwlink/?LinkId=617692 ) cmdlet.
- For more information about using Windows PowerShell, see  [Using Windows PowerShell to do common Skype for Business Online management tasks](https://go.microsoft.com/fwlink/?LinkId=525038).
    
  

## See also


#### Other Resources


  
    
    
 [Set up dial-in or PSTN conferencing for Skype for Business](set-up-dial-in-or-pstn-conferencing-for-skype-for-business.md)
  
    
    
 [Set up Skype for Business Online](set-up-skype-for-business-online.md)
