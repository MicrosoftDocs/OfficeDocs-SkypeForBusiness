---
title: "Deploy clients for Skype for Business Server"
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.reviewer: PhillipGarding
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 3d10abf2-d484-4fa0-8f10-4a5f9dfba4f5
description: "Summary: Overview of enterprise client installation methods for Skype for Business."
---

# Deploy clients for Skype for Business Server
 
**Summary:** Overview of enterprise client installation methods for Skype for Business.
  
How you deploy Skype for Business to your users depends on whether you purchased Skype for Business as part of an Office 365 plan or you purchased a volume licensed version of Skype for Business. 
  
- **Office 365** If you have an Office 365 plan that includes Skype for Business, the installation technology that's used is called Click-to-Run. With Office 365, you can let your users install Skype for Business for themselves from the Office 365 portal. Or, you can deploy Skype for Business to your users by downloading the software to your local network and then using your existing software deployment tools, such as with Microsoft System Center Configuration Manager. For installation information about Skype for Business that comes with Office 365, see [Deploy the Skype for Business client in Office 365](https://support.office.com/article/8c563b81-22c9-4024-9efe-9fe28c7bbc96).
    
- **Volume licensed** If you have a volume licensed version of the Skype for Business 2015 or 2016 client, the installation technology that's used is Windows Installer (MSI). A Windows Installer-based installation package consists of multiple MSI files. A language-neutral core MSI package is combined with one or more language-specific packages to make a complete product. Setup assembles the individual packages and performs customization and maintenance tasks during and after installation of Office on users' computers. The Skype for Business 2019 client uses Click-to-Run installers.
    
The topics in this section describe how to use and customize the Windows Installer to deploy the Skype for Business client to your users through your normal procedures.
  
> [!NOTE]
> The Skype Meeting Add-in for Microsoft Office, which supports meeting management from within the Outlook messaging and collaboration client, installs automatically with Skype for Business clients. 
  
> [!NOTE]
> The Office 365 setup program does not uninstall previous versions of Lync. The Skype for Business client installs side-by-side with other Lync clients. 
  
## Installing Windows clients

- [Customize Windows client installation in Skype for Business Server](customize-windows-client-installation.md)
    
- [Configure the client experience with Skype for Business](configure-the-client-experience.md)
    
- [Configure Smart contacts list in Skype for Business Server](configure-smart-contacts-list.md)
    
## Installing device clients

- [Install and test Skype for Business for Windows Phone](windows-phone.md)
    
- [Install and test Skype for Business for iOS](ios.md)
    
    
- [Deploy the Lync VDI plug-in with Skype for Business Server](deploy-the-lync-vdi-plug-in.md)
    
- [Deploy Web downloadable clients in Skype for Business Server](deploy-web-downloadable-clients.md)
    
- [Customize the Mac client experience in Skype for Business](customize-the-mac-client-experience.md)
    
## See also

[Deploy the Skype for Business client in Office 365](../../../SfbOnline/set-up-skype-for-business-online/deploy-the-skype-for-business-client-in-office-365.md)
