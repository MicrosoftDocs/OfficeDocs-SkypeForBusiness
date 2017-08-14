---
title: Deploy clients for Skype for Business Server 2015
ms.prod: SKYPEFORBUSINESS
ms.assetid: 3d10abf2-d484-4fa0-8f10-4a5f9dfba4f5
---


# Deploy clients for Skype for Business Server 2015
[]Overview of enterprise client installation methods.
 To deploy Skype for Business to your users as part of Office 365, have them use Office 365 installation methods and customization tools. If your Enterprise is implementing Skype for Business but staying with earlier versions of Office, you can deploy Skype for Business.
  
    
    


- ** Click-to-Run** (Recommended) is an installation program that streams setup files to the user from the Microsoft Office 365 portal. It provides a faster installation, so users can be up and running Office in a matter of minutes. If you have ten minutes to spare, you can find out more about Click-to-Run in a video that is part of our Garage series. . [Watch the video "Who moved my MSI?"](https://blogs.technet.microsoft.com/office_resource_kit/2013/03/05/the-new-office-garage-series-who-moved-my-msi/). Administrators can customize installation by using the Office Deployment Tool for Click-to-Run. For example, you can set how often to update to new features of Skype for Business by selecting an update branch. You have the following options to select from:
    
    Administrators can customize installation by using the Office Deployment Tool for Click-to-Run. Because Click-to-Run is primarily used in the Office 365 environment, this installation method is described in  [Deploy the Skype for Business client for your organization](https://support.officeppe.com/en-us/article/Deploy-the-Skype-for-Business-client-for-your-organization-8c563b81-22c9-4024-9efe-9fe28c7bbc96?ui=en-US&amp;rs=en-US&amp;ad=US). Detailed information about using and customizing Click-to-Run installation is available in the Office 365 Resource Kit documentation. Administrators can also download the Office 365 Click-to-Run program and language source files to an on-premises location, which is useful when you want to minimize the demand on the network or prevent users from installing software from the Internet because of corporate security requirements.
    

|**Update branch**|**New Feature Updates**|
|:-----|:-----|
| [Current Branch](https://technet.microsoft.com/library/mt455210.aspx) (CB) <br/> | Monthly <br/>  The Current Branch (CB) gets access to monthly innovations, along with security and performance improvements as part of the Current Branch release cycle. <br/> |
|| Every four months <br/>  The Current Branch for Business (CBB) will get new features 3 times a year but will be behind FRCBB branch users by 4 months. Security and performance improvements will occur monthly. The majority of enterprise customers will be on this branch providing the most stable and dependable experience. <br/> |
|| Every four months <br/>  • (Prior to CBB) <br/>  The First Release Current Branch for Business (FRCBB) get access to first release innovations, along with security and performance improvements, before they're released broadly. <br/> |
   

    Review the  [Overview of update branches for Office 365 ProPlus](https://technet.microsoft.com/library/mt455210.aspx) for more details.
    
     Other benefits of using C2R technology includes having the ability to control bandwidth used to download updates by using Background Intelligence Transfer Services (BITS) when downloading updates. BITS uses idle network bandwidth to transfer files and can increase or decrease the rate at which files are transferred based on the amount of idle network bandwidth is available. As a global admin you also have the ability to deactivate an installation.
    
    Detailed information about using and customizing Click-to-Run installation is available in the Office 365 Resource Kit documentation (see the" [Overview of Click-to-Run customization](https://technet.microsoft.com/en-us/library/jj219428%28v=office.15%29)"). Administrators can also download the Office 365 Click-to-Run program and language source files to an on-premises location, which is useful when you want to minimize the demand on the network or prevent users from installing software from the Internet because of corporate security requirements.
    
  
- **MSI Windows Installer** is a Windows Installer-based installation package that consists of multiple MSI files. A language-neutral core MSI package is combined with one or more language-specific packages to make a complete product. Setup assembles the individual packages and performs customization and maintenance tasks during and after installation of Office on users' computers. The topics in this section describe how to use and customize the Windows Installer to deploy the Skype for Business client to your users through your normal procedures.
    
  

 You should use the Office documentation in conjunction with topics in this section, which point out deployment considerations that are specific to Skype for Business.
  
    
    


> [!NOTE]
>  The Online meeting Add-in for Skype for Business, which supports meeting management from within the Outlook messaging and collaboration client, installs automatically with Skype for Business.>  The Office 365 setup program does not uninstall previous versions of Lync or Office Communicator. The Skype for Business client installs side-by-side with other Lync or Office Communicator clients.
  
    
    


## Installing Windows Clients


-  [Customize Wondows client installation in Skype for Business Server 2015](customize-wondows-client-installation-in-skype-for-business-server-2015.md)
    
  
-  [Configure the client experience with Skype for Business](configure-the-client-experience-with-skype-for-business.md)
    
  

## Installing Device Clients


-  [Install and test Skype for Business for Windows Phone](install-and-test-skype-for-business-for-windows-phone.md)
    
  
-  [Install and test Skype for Business for iOS](install-and-test-skype-for-business-for-ios.md)
    
  

## See also


#### 


  
    
    
 [Deploy the Skype for Business client for your organization](https://support.officeppe.com/en-us/article/Deploy-the-Skype-for-Business-client-for-your-organization-8c563b81-22c9-4024-9efe-9fe28c7bbc96?ui=en-US&amp;rs=en-US&amp;ad=US)
