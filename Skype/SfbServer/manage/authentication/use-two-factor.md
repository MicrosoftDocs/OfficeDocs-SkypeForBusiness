---
title: "Use two-factor authentication with Skype for Business client and Skype for Business Server"
ms.reviewer: 
ms.author: heidip
author: microsoftheidi
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: d4136e61-c3ab-4b26-85c8-c1b2c24f5ee3
description: "Summary: Use two-factor authentication with Skype for Business Server and Skype for Business."
---

# Use two-factor authentication with Skype for Business client and Skype for Business Server
 
**Summary:** Use two-factor authentication with Skype for Business Server and Skype for Business.
  
## Sign in to Skype for Business for the first time

Your sign-in information is usually configured automatically when Skype for Business is installed. But the first time you use Skype for Business, you might have to manually start the client.
  
### To sign in for the first time

1. Log on to your organization's network.
    
2. Select **Start** > **All Programs** > **Skype for Business**.
    
    You should see the sign-in screen.
    
    - If the sign-in address box is already filled in, confirm that the address shown is correct.
    
    - If it's not correct, or if the box is empty, enter your sign-in address (this is usually the same as your email address).
    
    - If an empty password box is displayed, add your password.
    
3. Select **Sign-in**.
    
## Sign out of Skype for Business

When you're finished using Skype for Business, you can close the display, sign out of your session, or exit from the program, all from the File menu. The following table explains the differences in the options.
  
|**Option**|**What it does**|**How to perform it**|
|:-----|:-----|:-----|
|Close  <br/> |Closes your display but lets the Skype for Business session identified with your user ID continue to run. This is so you can continue to get notifications and interact with others. <br/> <br/> You can get the display back at any time by clicking the Skype for Business icon on the taskbar or the notification area at the bottom of your screen.  <br/> | On the Skype for Business main window, do one of the following: <br/> 1. Select the **Options** button, then select **File** > **Close**.  <br/> 2. Click the **Close** button (X) in the upper-right corner of the window. <br/> |
|Sign out  <br/> |Ends the session associated with your user ID, but Skype for Business continues to run in the background. When you sign out, the sign-in window will appear.  <br/> **Tip:** Select **Delete my sign-in information** when you sign out to remove the record of your logon ID and password from the computer. Doing this might make it easier for support people to troubleshoot sign-in issues. It can also help ensure your sign-in information is more secure by making it difficult for unauthorized users to log on with your credentials. <br/> |On the Skype for Business main window, select the **Options** button, then select **File** > **Sign Out**.  <br/> |
|Exit  <br/> |Ends your Skype for Business session and shuts down Skype for Business on your computer. After exiting, if you want to restart, select **Start** > **All Programs** > Skype for Business. <br/> |On the Skype for Business main window, select the **Options** button, then select **File** > **Exit**.  <br/> |
   
## Sign in to Skype for Business with a Smart Card

Some organizations now use a multi-step sign-in process, called two-factor authentication, to increase security for their users. If you're expected to use this option, you'll need a "smart card" to sign in to Skype for Business. Smart cards can be either physical or virtual:
  
- **Physical** About the size of a credit card. You insert it into a smart card reader when you log in.
    
- **Virtual** Not a physical object, but an electronic identifier that gets written to a special chip on your computer, which in essence builds the smart card into your computer. Available only for use with Windows 8 computers that contain the TPM (Trusted Platform Module) chip.
    
### Enroll your smart card

Before you can sign in with a smart card, the card must be "enrolled"—that is, your user credentials have to be identified with the card. This is the case whether the card is physical or virtual. This process may already been carried out by your Skype for Business Server administrator. Check with them if you're not sure whether that has been done.
  
> [!NOTE]
> Since each virtual smart card is associated only with the device it's installed on, a separate card will need to be enrolled for each Windows 8 computer you use. 
  
### To manually enroll your smart card

1. Log on to the computer you'll be running Skype for Business on.
    
2. Using Internet Explorer, browse to your organization's Certificate Authority Web Enrollment page. 
    
    Ask your Skype for Business Server administrator for the web address of this resource if you don't already have it. The URL will look something like this: https://MyCA.[yourcompanyname].com/certsrv.
    
    > [!NOTE]
    > If you're using Internet Explorer 10, you may need to view this website in Compatibility Mode. 
  
3. When you're prompted to log on to the certification page, log on using your domain account (rather than as administrator of your computer).
    
4. On the website Welcome Page, select **Request a certificate**.
    
5. Select **Advanced Request**.
    
6. Select **Create and submit a request to this CA**, then click **Next**.
    
7. Now you'll see a page called Smart Card Enrollment Station. Approve the request to install the ActiveX control, and then complete the Advanced Certificate Request form as follows:
    
    a. Select **Smartcard user** from the **Certificate Template** dropdown list.
    
    b. Select **Create new key set**.
    
    c. Find the manufacturer information on the label of your smart card and select that manufacturer from the **CSP** dropdown list.
    
    d. Select **CSP** as the Request Format, if it's not already selected.
    
    e. Select **sha1** from the Hash Algorithm dropdown list, if it's not already selected.
    
    f. Give your certificate a name you'll recognize, and click **Submit**.
    
8. Now insert your blank smart card into the card reader attached to the enrollment station and click **Enroll**.
    
9. When prompted, enter your personal identification number (PIN), and then click **OK**.
    
    > [!NOTE]
    > If your technical support person has not given you a special PIN to use to enroll your smart card, use the default smart card PIN value, which is 12345678. 
  
10. Select the option to force the user (you) to change the PIN the first time the smart card is used.
    
11. Now insert your blank smart card into the card reader attached to the enrollment station and click **Enroll**.
    
12. When prompted, enter your personal identification number (PIN), and then click **OK**.
    
    > [!NOTE]
    > If your technical support person has not given you a special PIN to use to enroll your smart card, use the default smart card PIN value, which is 12345678. 
  
13. Select the option to force the user (you) to change the PIN the first time the smart card is used.
    
14. Click **OK** to confirm that the certificate displayed has your information on it.
    
15. Once you see the notice that the certificate has been issued, click **Install this certificate** to complete the enrollment process.
    
### Sign in to Skype for Business with your smart card credentials

Before you use your smart card for the first time, it's recommended that you click **Delete my sign-in info** on the Skype for Business sign-in page. Doing this clears any sign-in credentials stored on your computer, and eliminates a possible source of error.
  
### To sign in to Skype for Business with your smart card credentials

1. Start the Skype for Business client.
    
2. On the Sign in screen, type your sign in user account name in the **Sign-in address** box, and then click **Sign In**.
    
3. If you are using a virtual smart card, skip this step.
    
    If you are using a physical smart card, insert the smart card into your smart card reader and prompted to do so, and then click **OK** when the card is detected.
    
4. Type in the PIN number you for your smart card and then click **OK**.
    
    > [!NOTE]
    > If you were not assigned a smart card PIN number by your support person, use the default value, which is 12345678. 
  
## See also

[Manage two-factor authentication in Skype for Business Server](two-factor-authentication.md)
  
[Configure two-factor authentication in Skype for Business Server](configure-two-factor.md)
