---
title: Turn on or off Offline Messages for admins
ms.assetid: 8967a77f-caa2-4680-aa22-8faa32c716e4
---


# Turn on or off Offline Messages for admins

You can now send Skype for Business IMs to your contacts even if they aren't signed in. This feature lets your contacts know that you have been trying to reach them. You don't have to wait until someone is online before sending them a message. And you'll no longer receive those "Tony can't receive IMs right now. Status is unavailable or offline."
  
    
    

For Offline messages, it's important to know:
- Offline messages won't be archived in the user's mailbox.
    
  
- Offline messages will be sent to the users mailbox and the user will be notified when they log in to Skype for Business and they come online.
    
  
- If the message recipient's status is set to **Do Not Disturb** or **Presenting** they will receive a missed message that is sent from the recipient's Skype for Business client.
    
  
You can learn more about it by looking at how to  [Use offline messaging in Skype for Business](http://technet.microsoft.com/library/ffdc6a43-71a1-40ee-bfcc-640d21324a3d%28Office.14%29.aspx).
> [!NOTE]
> Don't see this feature in your Skype for Business client yet? Stay tuned. It will be rolling out to you in an upcoming Office 365 update. 
  
    
    


## To get you started


### 

 **Check that you are running Windows PowerShell version 3.0 or higher**
  
    
    

1. To verify that you are running version 3.0 or higher: **Start Menu** > **Windows PowerShell**.
    
  
2. Check the version by typing  _Get-Host_ in the **Windows PowerShell** window.
    
  
3. If you don't have version 3.0 or higher, you need to download and install updates to Windows PowerShell. See  [Windows Management Framework 4.0 ](https://go.microsoft.com/fwlink/?LinkId=716845) to download and update Windows PowerShell to version 4.0. Restart your computer when you are prompted.
    
  
4. You will also need to install the Windows PowerShell module for Skype for Business Online that enables you to create a remote Windows PowerShell session that connects to Skype for Business Online. This module, which is supported only on 64-bit computers, can be downloaded from the Microsoft Download Center at  [Windows PowerShell Module for Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=294688). Restart your computer if you are prompted.
    
  
If you need to know more, see  [Connect to all Office 365 services in a single Windows PowerShell window](https://technet.microsoft.com/EN-US/library/dn568015.aspx).
  
    
    

### 

 **Start a Windows PowerShell session**
  
    
    

1. From the **Start Menu** > **Windows PowerShell**.
    
  
2. In the **Windows PowerShell** window, connect to your Office 365 organization by running:
    
    > [!NOTE]
      > You only have to run the **Import-Module** command the first time you use the Skype for Business Online Windows PowerShell module.


  
    
    
> 
  ```
  
Import-Module "C:\\Program Files\\Common Files\\Skype for Business Online\\Modules\\SkypeOnlineConnector\\SkypeOnlineConnector.psd1"
  ```


  
    
    
> 
  ```
  $credential = Get-Credential
  ```


  
    
    
> 
  ```
  $session = New-CsOnlineSession -Credential $credential
  ```


  
    
    
> 
  ```
  Import-PSSession $session
  ```

If you want more information about starting Windows PowerShell, see  [Connect to all Office 365 services in a single Windows PowerShell window](https://technet.microsoft.com/EN-US/library/dn568015.aspx) or [Connecting to Skype for Business Online by using Windows PowerShell](https://technet.microsoft.com/en-us/library/dn362795%28v=ocs.15%29.aspx).
  
    
    

## Turning on or off Offline IM


> [!NOTE]
> Offline Messages are **only** available in the latest version of the Click-to-Run Skype for Business client and aren't available when an older Click-to-Run Skype for Business is used or a *.msi file was used to install the Skype for Business client.
  
    
    

To enable or disable Offline Messages send Offline Messages for users in your organization set  _EnableIMAutoArchiving_ to `True` or `False`. By default, this is set to  `True`.
  
    
    
To turn it off, use the **Set-CsClientPolicy** cmdlet and run:
  
    
    



```
Set-CsClientPolicy -Identity Global -EnableIMAutoArchiving $False
```

To enable or disable Offline Messages send Offline Messages for a user set  _EnableIMAutoArchiving_ to `True` or `False`. By default, this is set to  `True`. You can use an existing policy or create on like the example below.
  
    
    


  
    
    
> 
  ```
  New-CsClientPolicy -Identity OfflineIM
  ```


  
    
    
> 
  ```
  Set-CsClientPolicy -Identity OfflineIM -EnableIMAutoArchiving $False
  ```


  
    
    
> 
  ```
  Grant -CsClientPolicy -Identity "Tony Smith" - PolicyName OfflineIM
  ```


## Want to know more about Windows PowerShell?


- When it comes to Windows PowerShell is all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Office 365 and Skype for Business Online using a single point of administration that can simplify your daily work, when you have multiple tasks to do. To get started with Windows PowerShell, see these topics:
    
  -  [An introduction to Windows PowerShell and Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525039)
    
  
  -  [Six Reasons Why You Might Want to Use Windows PowerShell to Manage Office 365 ](https://go.microsoft.com/fwlink/?LinkId=525041)
    
  
- Windows PowerShell has many advantages in speed, simplicity, and productivity over only using the Office 365 admin center such as when you are making setting changes for many users at one time. Learn about these advantages in the following topics:
    
  -  [Best ways to manage Office 365 with Windows PowerShell](https://go.microsoft.com/fwlink/?LinkId=525142)
    
  
  -  [Using Windows PowerShell to manage Skype for Business Online](https://go.microsoft.com/fwlink/?LinkId=525453)
    
  
  -  [Using Windows PowerShell to do common Skype for Business Online management tasks](https://go.microsoft.com/fwlink/?LinkId=525038)
    
  

