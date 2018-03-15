---
title: "Configuring the use of high-resolution photos in Microsoft Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 995da78a-dc44-45a3-908d-16fe36cfa0d9
description: "Microsoft Lync Server 2010 provided the ability for users to view photos of their contacts (and to make their own photos available to others). Typically these photos were stored as part of the user's thumbnailPhoto attribute in Active Directory. That placed a serious limitation on the size and resolution of the photos: the thumbnailPhoto attribute can only hold a photograph with a maximum size of 48 pixels by 48 pixels."
---

# Configuring the use of high-resolution photos in Microsoft Lync Server 2013
[]
Microsoft Lync Server 2010 provided the ability for users to view photos of their contacts (and to make their own photos available to others). Typically these photos were stored as part of the user's thumbnailPhoto attribute in Active Directory. That placed a serious limitation on the size and resolution of the photos: the thumbnailPhoto attribute can only hold a photograph with a maximum size of 48 pixels by 48 pixels.
  
In Microsoft Lync Server 2013, however, photos can be stored in a user's Microsoft Exchange Server 2013 mailbox; that allows for photo sizes up to 648 pixels by 648 pixels. In addition to that, Exchange 2013 can automatically resize these photos for use in different products as needed. Typically that means three different photo sizes and resolutions:
  
- 48 pixels by 48 pixels, the size used for the Active Directory thumbnailPhoto attribute. If you upload a photo to Exchange 2013 Exchange will automatically create a 48 pixel by 48 pixel version of that photo and update the user's thumbnailPhoto attribute. Note, however, that the reverse is not true: if you manually update the thumbnailPhoto attribute in Active Directory the photo in the user's Exchange 2013 mailbox will not automatically be updated.
    
- 96 pixels by 96 pixels, for use in Microsoft Outlook 2013 Web App, Microsoft Outlook 2013, Microsoft Lync Web App, and Lync 2013.
    
- 648 pixels by 648 pixels for use in Lync 2013 and Microsoft Lync Web App.
    
> [!NOTE]
> If you have the resources, it is recommended that you upload 648x648 photos; that provides the maximum resolution and optimal picture quality in any of the Office 2013 applications. Each JPEG photo with a size of 648x648 and a depth of 24 bits results in a file size of approximately 240 kilobytes. That means you will need approximately 1 megabyte of disk space for every 4 user photos. 
  
High-resolution photos, which are accessed by using Exchange Web Services, can be uploaded by users who are running Outlook 2013 Web App; users are only allowed to update their own photo. Administrators, however, can update the photo for any user by using the Exchange Management Shell and a series of Windows PowerShell commands similar to the following:
  
```
$photo = ([Byte[]] $(Get-Content -Path "C:\Photos\Kenmyer.jpg" -Encoding Byte -ReadCount 0))
Set-UserPhoto -Identity "Ken Myer" -PictureData $photo -Confirm:$False
Set-UserPhoto -Identity "Ken Myer" -Save -Confirm:$False
```

The first command in the preceding example uses the Get-Content cmdlet to read the contents of the file C:\Photos\Kenmyer.jpg and store that data in a variable named $photo. In the second command, the Exchange cmdlet Set-UserPhoto is used to upload the photo and attach that photo to Ken Myer's user account.
  
> [!NOTE]
> In this example, Ken Myer's Active Directory display name is used as the user account Identity. You can also reference a user account by using other identifiers such as the user's SMTP address or his or her User Principal Name. See the documentation for the Set-UserPhoto cmdlet at [https://go.microsoft.com/fwlink/p/?LinkId=268536](https://go.microsoft.com/fwlink/p/?LinkId=268536) for more information 
  
Uploading the photo does not equate to assigning that photo to Ken Myer's user account. Instead, uploading the photo simply results in a preview of that photo to be displayed on the Outlook Web App Options page. To actually assign that photo to the user account the user must click **Save** on the Options page or the administrator must execute the third command in the example. That third command uses the Save parameter to assign the photo to Ken Myer's user account: 
  
```
Set-UserPhoto -Identity "Ken Myer" -Save -Confirm:$False
```

To verify that the new photo has been assigned to the user account, Ken Myer can log on to Lync 2013, select **Options**, and then select **My Picture**. The newly-uploaded photo should be displayed as Ken's personal photo. Alternatively, administrators can verify the photo for any user by starting Internet Explorer and navigating to a URL similar to this:
  
```
https://atl-mail-001.litwareinc.com/ews/Exchange.asmx/s/GetUserPhoto?email=kenmyer@litwareinc.com&amp;size=HR648x648
```

If the administrator can view the photo using Internet Explorer but the user cannot view his or her photo in Lync 2013, that typically indicates a connectivity problem with Exchange Web Services or with the Exchange autodiscover service.
  
Note, too that no additional configuration is required in order to make this photo available in Lync 2013. Instead, the photo will be instantly available after it has been uploaded and the Set-UserPhoto cmdlet has been run.
  

