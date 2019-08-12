---
title: How user photos are displayed in Lync
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: How user photos are displayed in Lync
ms:assetid: b44a364d-a1d2-4d45-b27a-b5f77775e233
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn783119(v=OCS.15)
ms:contentKeyID: 62835297
ms.date: 08/27/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# How user photos are displayed in Lync

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-08-25_

**Summary:** User photos displayed in Lync client can be different depending on which Lync feature you are using, such as when in a conference or an IM chat.

Lync 2010 introduced the ability to include a photo with your Lync profile that is displayed to other Lync users. You can also choose whether or not to display photos for your contacts in Lync client. In Lync 2013, support for high-resolution photos for users. This topic describes how Lync client gets and displays user photos, where the images are stored, the limitations for each image source, and how user photos are used by different Lync services.

<div>

## Planning considerations

You should consider the following when planning to implement support for user photos.

  - High-definition user photo support requires that the user’s mailbox be located on Exchange 2013 and the Lync user account to be in Lync 2013 pool.

  - High-definition user photos are supported only in an environment where both Lync Server 2013 and Exchange 2013 are used.

  - Users with Mailboxes on Exchange 2010 will always use the **thumbnailPhoto** attribute from AD DS as the source for their user photo.

  - A user photo stored as the **thumbnailPhoto** attribute from AD DS will not be displayed to external / federated contacts.

  - If the photos for user contacts are stored in AD DS, the image file used is limited to 96×96 pixels and no more than 100 KB file size.

  - If connectivity between Lync Server and Exchange Server is lost, the user’s low resolution **thumbnailPhoto** from AD DS will be displayed, and to internal users only.

  - High-resolution user photos are displayed in Lync 2013 meetings when an active speaker does not have video enabled. Also, moving the mouse over thumbnail photo in the gallery will display the high-resolution photo.

</div>

<div>

## User Photos in Lync 2010

In the Lync 2010 client, you can choose from two options to display a photo for your profile, **Default corporate picture** and **Show picture from a web address**.

<div>

## Default corporate picture

When you choose the **Default corporate picture** option, Lync gets the photo displayed for you from Active Directory Domain Services. The image used is the image defined as the value for the **thumbnailPhoto** attribute in Active Directory Domain Services. This is the same file that is used by Exchange to display images in Outlook.

Considerations for using images from Active Directory Domain Services include the following:

  - Only images with dimensions up to 96 pixels by 96 pixels are supported. The file size for the image is limited to 100 KB.

  - By default, users are able to change the image used for the **thumbnailPhoto** attribute, though not directly through Lync client. You can disable this through Active Directory Domain Services.

  - Images stored in Active Directory Domain Services are not displayed to contacts external to your organization, even if they are federated contacts.

  - In large organizations, storing and retrieving the images for large numbers of users may impact the Active Directory Domain Services database size and performance.

  - The limited image dimensions and file size mean that only low resolution images can be used.

<div>

## How users manage their user photos in Active Directory Domain Services

User cannot change the image used in their Active Directory Domain Services profile directly through Lync 2010 client. They can use one of the following options to do so, if available:

  - **SharePoint Server**   Users can upload a photo to ‘My Site’ on a SharePoint Server and then [configure profile synchronization in SharePoint](http://go.microsoft.com/fwlink/p/?linkid=507466) to synchronize the photo to the **thumbnailPhoto** attribute in Active Directory Domain Services.

  - **Photo stored on publicly accessible URL**   Users can configure their user photo specifying a publicly accessible URL for the image that they want to use. The image must be publicly accessible without a password. The image stored at the specified web address is transferred to other users through the contact card category in the presence information. When Lync client needs to display a user photo, it retrieves the image from the specified web address.

  - **Exchange 2010 cmdlets for Windows PowerShell**   Administrators can run the [Import-RecipientDataProperty](http://go.microsoft.com/fwlink/p/?linkid=507468) cmdlet in the Exchange 2010 Management Shell in to manage the **thumbnailPhoto** attribute. When images are imported with Exchange 2010 cmdlets, the file size is limited to 10 KB.

  - **Third Party tools**   Users can upload only their own photo to for the **thumbnailPhoto** attribute.

</div>

</div>

<div>

## Show a picture from a web address

When you choose the **Show a picture from a web address** option, Lync gets the image at the address you enter and displays it for your user photo in Lync.

Considerations for using images from a web address include the following:

  - File size limits are determined by the **MaxPhotoSizeKB** attribute in the client policy, defined with the [New-CsClientPolicy](http://go.microsoft.com/fwlink/p/?linkid=507463) cmdlet. The default size limit is 30 KB. The maximum value is 100 KB. There is no restriction on the resolution of the image, but if you try to use an image file that exceeds the size limit it will not be downloaded to Lync clients. You can set the value to 0 to disable all user photos from being used in Lync.

  - User photos from a web address can be seen by external federated contacts.

</div>

<div>

## Managing user’s photo with Client Policy cmdlets

In Lync Server 2010, client policy settings are configured with the CsClientPolicy cmdlets. The configured policy settings are sent to clients through in-band provisioning. The two parameters of the CsClientPolicy cmdlets that determine the user photo experience are **DisplayPhoto** and **MaxPhotoSizeKB**. The corresponding in-band provisioning parameter for **DisplayPhoto** and **MaxPhotoSizeKB** is named **PhotoUsage**. Values for the **PhotoUsage** parameter are send to clients through the **endpointConfiguration** **provisionGroup**. See [Overview of Client Policies and Settings](http://go.microsoft.com/fwlink/?linkid=507470) for more information.

The **DisplayPhoto** parameter value determines the source of the user's photo image. The supported values are included in the following table.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>DisplayPhoto parameter value</th>
<th>Image source</th>
<th>Lync 2010 client settings</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>NoPhoto</p></td>
<td><p>none</p></td>
<td><p><strong>Do not show my picture</strong></p></td>
</tr>
<tr class="even">
<td><p>PhotoFromADOnly</p></td>
<td><p>Active Directory</p></td>
<td><p><strong>Default corporate picture</strong></p></td>
</tr>
<tr class="odd">
<td><p>AllPhotos</p></td>
<td><p>Web address</p></td>
<td><p><strong>Show a picture from a web address</strong></p></td>
</tr>
</tbody>
</table>


</div>

<div>

## How Lync 2010 client gets photos

In Lync 2010, user photos are managed on the server by the Address Book Service. Lync client gets user photos by first querying the Address Book Web Query (ABWQ) service on the server, which is exposed through the Distribution List Expansion web service. The client receives the image file and then copies it to the user's cache to avoid downloading the image each time it needs to be displayed. The attribute values returned from the query are also stored in the cached Address Book Service entry for the user. The Address Book Service deletes all cached images every 24 hours, which means that it can take up to 24 hours for new user images to be updated in the cache on the server. You can force an update to the cache by using the [Update-CsAddressBook](https://docs.microsoft.com/powershell/module/skype/Update-CsAddressBook) cmdlet.

User photos included in Presence status also have an associated hash value that Lync client uses to determine whether there is a newer image available. The client is automatically notified of changes to the image file used in Presence status.

<div class=" ">


> [!NOTE]  
> Because photos are not stored in the GalContacts.db database, downloading user photos is not dependent on the <STRONG>AddressBookAvailability</STRONG> setting in the client policy (<A href="http://go.microsoft.com/fwlink/p/?linkid=507508">Set-CsClientPolicy</A>).



</div>

The query to the ABWQ service includes the following attributes:

  - **PhotoHash**   The hash value of the binary photo data, and is used to determine whether the current photo has changed.

  - **PhotoRelPath**   The relative path to the image file stored on the server.

  - **PhotoSize**   The size of the image file, in bytes.

  - **TimeStamp**   The date and time at which the image file was last downloaded from the server and copied to the client cache.

Next, after retrieving the image file, Lync 2010 client compares the attribute values returned from the query against the attribute values received by the client from in-band provisioning to see if they are different. If the values are different, the client retrieves the image file of the signed-in user with an HTTP GET request.

Additionally, the client checks with the server every 24 hours from the time at which the cached version of the image file was created to compare the value of the **PhotoHash** attribute on the server with the value on the client. If the values are different, the client knows that the image file has changed. To obtain the updated image file, the client again queries the ABWQ service to update the image file in the client cache with the image file on the server, which also resets the **TimeStamp** on the file in the client cache.

The following is an example response to a query to the ABWQ service:

    <Attribute>
              <Name>PhotoRelPath</Name>
              <Value>efa6096aed2746cb9ab2037f7dbdde9d.f2eeeb5946db54a7aa607ecd3ae09d
              95.photo</Value>
              <Values xmlns:d6p1="http://schemas.microsoft.com/2003/10/Serialization/Arrays" i:nil="true" />
    </Attribute>
    <Attribute>
              <Name>PhotoHash</Name>
              <Value>f2eeeb5946db54a7aa607ecd3ae09d95</Value>
              <Values xmlns:d6p1="http://schemas.microsoft.com/2003/10/Serialization/Arrays" i:nil="true" />
    </Attribute>
    <Attribute>
         <Name>PhotoSize</Name>
         <Value>4620</Value>
         <Valuesxmlns:d6p1="http://schemas.microsoft.com/2003/10/Serialization/Arrays"
    i:nil="true" />
    </Attribute>

</div>

</div>

<div>

## User photos in Lync 2013

Lync 2013 introduced support for high-resolution images for user photos. Lync 2013 also includes support for storing user photos in the user's mailbox on Exchange 2013, which removes the image resolution and size limitations present in Lync 2010. User photos in Lync 2013 can be up to 648 pixels by 648 pixels with a file size of up to 20 MB. High-resolution photos in Lync 2013 must be located in the user's mailbox on Exchange 2013, and are supported only with Lync 2013 client. This integration with Exchange takes advantage of the new authorization framework included in the 2013 versions of Lync, Exchange, and SharePoint called Oauth.

If Exchange 2013 is not used in your deployment, support for user photos is the same as with Lync 2010. However, the user options to choose the photo to use are different in Lync 2013 client. In Lync 2013 client, users can select either **Hide my picture** or **Show my picture**. The option **Show a picture from a website** is not available by default, but can be enabled by assigning a client policy.

<div>

## Hide my picture

Settings for user photos are on the **Options** dialog in Lync 2013. When you choose **Hide my picture**, no user photo is displayed for you in Lync client, but your photo is still displayed on your contact card and outside of Lync.

</div>

<div>

## Show my picture

When you choose the **Show my picture** option, your user photo is displayed in your Lync client and to other users in Lync conversations. The image used is the one stored in AD DS.

</div>

<div>

## Show a picture from a website

The **Show picture from a website** option becomes available in Lync 2013 after a client policy is set to enable it. The client version must be newer than 15.0.4535.1002, which is installed with the [Lync Cumulative Updates: November 2013](http://go.microsoft.com/fwlink/p/?linkid=509908). Users may need to log out and then back in again to see the changes in the client.

You can set the client policy to enable to **Show picture from a website** setting by running the [Set-CsClientPolicy](https://docs.microsoft.com/powershell/module/skype/Set-CsClientPolicy) policy in the Lync Server Management Shell. The following example cmdlets demonstrate how to set the policy globally for all users in your deployment:

   ```
    $pe=New-CsClientPolicyEntry -Name EnablePresencePhotoOptions -Value True
   ```

   ```
    $po=Get-CsClientPolicy -Identity Global
   ```

   ```
    $po.PolicyEntry.Add($pe)
   ```

   ```
    Set-CsClientPolicy -Instance $po
   ```


When an image is uploaded to the user’s mailbox, Exchange automatically creates a lower resolution version of the image which can be used in client applications. The user photo is also updated in AD DS.

<div class=" ">


> [!NOTE]  
> When an image file is updated in AD DS, a 48 x 48 pixel image is created and used for the thumbnailPhoto in AD DS. Any existing image is replaced. So if you added a 96 x 96 image to AD DS, it will be overwritten with the new 48 x 48 image. This is only important is you have users in your environment using Lync 2010 clients, as those clients will obtain user photos from AD DS. You can import 96 x 96 pixel images to replace the ones created by AD DS if you have Lync 2010 clients in your organization.



</div>

</div>

<div>

## User photo support in Lync 2013

In Lync 2013, three image resolutions are supported for user photos as described in the following table. The image that is used is determined by the client policy setting assigned to Lync users. See “Managing user’s photo with Client Policy cmdlets” in this topic for more information.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Image resolution (pixels)</th>
<th>Application</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>48 x 48</p></td>
<td><p>Used if no higher resolution image is selected</p></td>
</tr>
<tr class="even">
<td><p>96 x 96</p></td>
<td><p>Used in Outlook Web App and Outlook 2013</p></td>
</tr>
<tr class="odd">
<td><p>648 x 648</p></td>
<td><p>Used in Lync 2013 desktop client and Lync 2013 Web App</p></td>
</tr>
</tbody>
</table>


Any user with a mailbox enabled in Exchange 2013 can upload a different image, including high-resolution photos, through Outlook Web Access or Lync 2013 client options. The recommended settings for images used include:

  - **Image Resolution**   648 by 648 pixels

  - **Color Depth**   24-bit

  - **Image file size**   up to 20 MB

  - **File format**   JPEG

A typical 24-bit JPEG image that is 648 pixels by 648 pixels has a file size of about 240 KB, so 1 MB of storage space is needed for every 4 user photos.

</div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

