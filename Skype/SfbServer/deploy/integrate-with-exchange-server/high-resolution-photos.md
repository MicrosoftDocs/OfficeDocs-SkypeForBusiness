---
title: "Configure the use of high-resolution photos in Skype for Business Server"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 12/20/2018
audience: ITPro
ms.topic: quickstart
ms.service: skype-for-business-server
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.collection: IT_Skype16
ms.assetid: 995da78a-dc44-45a3-908d-16fe36cfa0d9
description: "Summary: Configure the use of high-resolution photos in Exchange Server 2019, Exchange Server 2016, Exchange Server 2013, or Exchange Online and Skype for Business Server."
---

# Configure the use of high-resolution photos in Skype for Business Server

**Summary:** Configure the use of high-resolution photos in Exchange Server 2019, Exchange Server 2016, Exchange Server 2013, or Exchange Online and Skype for Business Server.
  
In Skype for Business Server, photos can be stored in a user's mailbox in Exchange Server 2019, Exchange Server 2016, Exchange Server 2013, or Exchange Online. Storing the photo in the mailbox allows for photo sizes up to 648 pixels by 648 pixels. In addition, Exchange Server can automatically resize these photos for use in different products as needed. Typically, there are three different photo sizes and resolutions:
  
- **64 pixels by 64 pixels**: Used for the Active Directory thumbnailPhoto attribute. If you upload a photo to Exchange Server, Exchange will automatically create a 64 pixel by 64 pixel version of that photo and update the user's thumbnailPhoto attribute. The reverse isn't true. If you manually update the thumbnailPhoto attribute in Active Directory, the photo in the user's Exchange mailbox isn't automatically updated.

- **96 pixels by 96 pixels**: Used in Outlook on the web (also known as Outlook Web App or OWA), Microsoft Outlook 2013 or later, Skype for Business Web App, and Skype for Business.

- **648 pixels by 648 pixels**: Used in Skype for Business and Skype for Business Web App.

> [!NOTE]
> If you have the resources, we recommended that you upload 648 x 648 photos. This size provides the maximum resolution and optimal picture quality in any Office applications. Each JPEG photo with a size of 648 x 648 and a depth of 24 bits results in a file size of approximately 240 kilobytes. In other words, you'll need approximately 1 megabyte of disk space for every 4 user photos.
  
High-resolution photos, which are accessed by using Exchange Web Services, can be uploaded by users who are running Outlook on the web. Users are allowed to update their own photo. Administrators, can update the photo for any user by using the following commands in the [Exchange Management Shell](/powershell/exchange/open-the-exchange-management-shell):
  
```powershell
$photo = [System.IO.File]::ReadAllBytes('C:\Photos\KenMyer.jpg')

Set-UserPhoto -Identity "Ken Myer" -PictureData $photo -Preview -Confirm:$False

Set-UserPhoto -Identity "Ken Myer" -Save -Confirm:$False
```

The first command reads the contents of the .jpg file and stores that binary data in a variable named $photo. The second command uses the `Set-UserPhoto` cmdlet to upload the photo and attach that photo to Ken Myer's user account.
  
> [!NOTE]
> You can use other identifiers for the Identity parameter value (for example, their email address or user principal name (UPN)). For more information, see [Set-UserPhoto](/powershell/module/exchange/set-userphoto).
  
Uploading the photo (the first two commands in the example) does not equate to assigning that photo to Ken Myer's user account. Uploading the photo simply results in a preview of that photo being displayed on the Options page in Outlook on the web. To actually assign that photo to the user account, the user must click **Save** on the Options page or the administrator must run the third command in the example.

To verify that the new photo has been assigned to the user account, Ken Myer can log on to Skype for Business, select **Options**, and then select **My Picture**. The newly uploaded photo should be displayed as Ken's personal photo. Alternatively, administrators can verify the photo for any user by opening a web browsers to the following URL: `https://atl-mail-001.litwareinc.com/ews/Exchange.asmx/s/GetUserPhoto?email=kenmyer@litwareinc.com&size=HR648x648`.

If the administrator can view the photo in a web browser but the user can't view their own photo in Skype for Business, there might be a connectivity problem with Exchange Web Services or with the Exchange Autodiscover service.
  
No other configuration is required to make this photo available in Skype for Business. Instead, the photo will be instantly available after it has been uploaded and the `Set-UserPhoto` cmdlet has been run.
