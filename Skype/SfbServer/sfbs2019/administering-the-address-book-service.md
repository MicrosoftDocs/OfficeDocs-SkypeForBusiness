---
title: "Administering the Address Book Service in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 801e4243-9670-4477-aa2f-88b61ecf5351
description: "In this articleAddress Book Server Phone Number NormalizationUser Replicator and Address Book ServerFiltering the Address Book"
---

# Administering the Address Book Service in Lync Server 2013
[]
 **In this article**
  
[Address Book Server Phone Number Normalization](#sectionSection0)
  
[User Replicator and Address Book Server](#sectionSection1)
  
[Filtering the Address Book](#sectionSection2)
  
As a part of the deployment of Lync Server, Enterprise Edition or Standard Edition server, the Address Book Service is installed by default. The database used by the Address Book Service - RTCab - is created on the SQL Server (for Enterprise Edition, this is the back-end SQL Server; for Standard Edition server, the collocated SQL Server).
  
> [!NOTE]
> For information about using **ADSI Edit** to edit Active Directory Domain Services object attributes, see [ADSI Edit](https://go.microsoft.com/fwlink/?LinkId=330427). For information about a tool in the Resource Kit specifically for the Address Book service, see [Microsoft Lync Server 2013 Resource Kit Tools](https://go.microsoft.com/fwlink/?LinkId=330429). 
  
## Address Book Server Phone Number Normalization
<a name="sectionSection0"> </a>

Lync Server requires standardized RFC 3966/E.164 phone numbers. To use phone numbers that are unstructured or inconsistently formatted, Lync Server relies on the Address Book Server to preprocess phone numbers before they are handed off to the normalization rules. When a phone number is used from the address book and the normalization rule is applied, clients, such as Lync Phone Edition and Lync Mobile, can use these normalized numbers.
  
The normalization rules that were used in previous versions may not work properly without some adjustments. Because the white space and non-mandatory characters are removed prior to the normalization rules, if your regex expression is specifically looking for a dash or other character that was removed, your normalization rule might fail. You should review your normalization rules to ensure that either they are not looking for these non-mandatory characters, or that the rule can fail gracefully and continue in the event that the character is not present where the rule anticipates it will be.
  
## User Replicator and Address Book Server
<a name="sectionSection1"> </a>

The Address Book Server uses data provided by User Replicator to update the information that it initially obtains from the global address list (GAL). User Replicator writes the Active Directory Domain Services attributes for each user, contact, and group into the AbUserEntry table in the database and the Address Book Server syncs the user data from the database into files in the Address Book Server file store and into the Address Book database RTCab. The schema for the AbUserEntry table uses two columns, **UserGuid** and **UserData**. **UserGuid** is the index column and contains the 16-byte GUID of the Active Directory object. **UserData** is an image column which contains all of the previously mentioned Active Directory Domain Services attributes for that contact. 
  
User Replicator determines which Active Directory attributes to write by reading a configuration table located in the same SQL Server-based instance as the AbUserEntry table. The AbAttribute table contains three columns, **ID**, **Name**, **Flags**, and **Enable**. The table is created during database setup. If the AbAttribute table is empty, User Replicator skips its AbUserEntry table processing logic. Address Book Server attributes are dynamic and are retrieved from the AbAttribute table, which is initially written by the Address Book Server when the Address Book Server is activated.
  
Address Book Server activation populates the AbAttribute table with the values shown in the following table.
  
|**ID**|**Name**|**Flags**|
|:-----|:-----|:-----|
|1  <br/> |givenName  <br/> |0x01400000  <br/> |
|2  <br/> |Sn  <br/> |0x02400000  <br/> |
|3  <br/> |displayName  <br/> |0x03420000  <br/> |
|4  <br/> |Title  <br/> |0x04000000  <br/> |
|5  <br/> |mailNickname  <br/> |0x05400000  <br/> |
|6  <br/> |Company  <br/> |0x06000000  <br/> |
|7  <br/> |physicalDeliveryOfficeName  <br/> |0x07000000  <br/> |
|8  <br/> |msRTCSIP-PrimaryUserAddress  <br/> |0x08520C00  <br/> |
|9  <br/> |telephoneNumber  <br/> |0x09022800  <br/> |
|10  <br/> |homePhone  <br/> |0x0A302800  <br/> |
|11  <br/> |Mobile  <br/> |0x0B622800  <br/> |
|12  <br/> |otherTelephone  <br/> |0x0C302000  <br/> |
|13  <br/> |ipPhone  <br/> |0x0D302000  <br/> |
|14  <br/> |Mail  <br/> |0x0E500000  <br/> |
|15  <br/> |groupType  <br/> |0x0F010800  <br/> |
|16  <br/> |Department  <br/> |0x10000000  <br/> |
|17  <br/> |Description  <br/> |0x11000100  <br/> |
|18  <br/> |Manager  <br/> |0x12040001  <br/> |
|19  <br/> |proxyAddress  <br/> |0x00500105  <br/> |
|20  <br/> |msExchHideFromAddressLists  <br/> |0xFF000003  <br/> |
|99  <br/> |entryID  <br/> |0x99000000  <br/> |
   
The numbers in the **ID** column must be unique and should never be reused. Also, keeping the ID values under 256 saves space in the output files written by the Address Book Server. However, the maximum ID value is 65535. The **Name** column corresponds to the Active Directory attribute name that User Replicator should put in the AbUserEntry table for each contact. The value in the **Flags** column is used to define the type of attribute. The following types of Address Book Server attributes are recognized by User Replicator, indicated by the low byte of the value in the **Flags** column. 
  
|**Attribute**|**Description**|
|:-----|:-----|
|0x0  <br/> |A string attribute. User Replicator converts this type to UTF-8 before storing it in the AbUserEntry table.  <br/> |
|0x1  <br/> |A binary attribute. User Replicator stores this in the blob without any conversion.  <br/> |
|0x2  <br/> |A string attribute, but is included only if the attribute value begins with "tel:". This is primarily for multi-valued string attributes, specifically **proxyAddresses**. In this case, Address Book Server is interested only in **proxyAddresses** entries that begin with "tel:". Therefore, in the interest of saving space, User Replicator stores only the entries that begin with "tel:".  <br/> |
|0x3  <br/> |A Boolean string attribute, which if TRUE causes User Replicator to not include this contact in the AbUserEntry table. If FALSE, it causes User Replicator to include the attributes for this contact in the AbUserEntry table, but not the particular attribute with this flag. This is another special case type that is primarily for the **msExchHideFromAddressLists** attribute.  <br/> |
|0x4  <br/> |A string attribute, but is included only if the attribute value begins with "smtp:" and includes the "@" symbol.  <br/> |
|0x5  <br/> |A string attribute, but is included only if the attribute value begins with either "tel:" or "smtp:" and includes the "@" symbol.  <br/> |
|0x100  <br/> |If set, this is a multi-valued attribute that can appear more than once for each contact.  <br/> |
|0x400  <br/> |If set, this identifies the email user account name attribute for a contact. Address Book Server uses this flag to identify which attribute value to show in the phone normalization event log entry.  <br/> |
|0x800  <br/> |If set, this identifies a required attribute for a contact. Address Book Server includes a user in the AbUserEntry table only if there is a value for this attribute in Active Directory. If there is more than one required attribute, only one of them is required to have a value to include the user in the AbUserEntry table.  <br/> |
|0x1000  <br/> |If set, Address Book Server always normalizes the value of this attribute.  <br/> |
|0x2000  <br/> |If set, Address Book Server uses the normalized number from **proxyAddresses**, if the **UseNormalizationRules** CMS setting is FALSE; otherwise it behaves the same as when the flag bit is 0x1000.  <br/> |
|0x4000  <br/> |If set, Address Book Server does not include objects in the AbUserEntry table that have this value for the specified attribute. For example, if the **msRTCSIP-PrimaryUserAddress** attribute has this flag bit set, then contacts that have this attribute are not written to the database.  <br/> |
|0x8000  <br/> |If set, Address Book Server does not include objects in the AbUserEntry table that do not have this value for the specified attribute. If both the 0x4000 and 0x8000 flag bits are set on an object, the attribute with the flag bit value set to 0x4000 takes precedence, and the object is excluded from the AbUserEntry table.  <br/> |
|0x10000  <br/> |If set, this represents a group object. User Replicator uses this flag bit to include contacts with the **groupType** attribute whose presence indicates a group (for example, a distribution list or security group).  <br/> |
|0x20000  <br/> |If set, User Replicator uses this flag bit to include this attribute in device-specific Address Book Server files (that is, files with a .dabs extension).  <br/> |
   
In previous versions of Lync Server, when applying a change to Active Directory, the administrator would be required to run **Update -CSUserDatabase** and **Update -CSAddressBook** Windows PowerShell cmdlets to persist the change to the Lync Server user database and RTCab database immediately. In Lync Server 2013, Lync Server User Replicator will pick up the changes from Active Directory and update the Lync Server user database based on a configured interval. Lync Server User Replicator will also propagate the changes to the RTCab database quickly without the administrator having to run Update-CSAddressBook. If Address Book Web query is enabled, then the changes will be reflected in search results by Lync clients. Administrators will only need to run Update -CSAddressBook if the Address Book file download is enabled. 
  
> [!NOTE]
> By default Lync Server User Replicator runs automatically every 5 minutes. You can configure this interval by using Set -CSUserReplicatorConfiguration -ReplicationCycleInterval \<\>. 
  
## Filtering the Address Book
<a name="sectionSection2"> </a>

The users populated in the Address Book Server files can be controlled based on certain Active Directory Domain Services attributes listed in the AbAttribute table. One such attribute used for filtering is the **msExchangeHideFromAddressBook** attribute. This is a user attribute added by the Exchange schema. If the value of this attribute is TRUE, Exchange Server uses this attribute to hide the contact from the Outlook Global Address List (GAL). Similarly, if the value of this attribute is TRUE, User Replicator does not include that user in the AbUserEntry table and this user will not be in the Address Book Server files. 
  
You can use some flag bits to define a filter to use on Address Book Server attributes. For example, the presence of certain flag bits can identify an attribute as an include attribute or an exclude attribute. User Replicator filters out contacts that contain an exclude attribute and filters out contains that do not contain an include attribute.
  
> [!CAUTION]
> For more information about filtering the Address Book, see [Address Book Server cmdlets in Lync Server 2013](address-book-server-cmdlets.md), and [Filter Lync 2013 address book](https://go.microsoft.com/fwlink/?LinkId=330430)
  
Currently, there are three different filters. The following table lists these filters.
  
|**Attribute**|**Description**|
|:-----|:-----|
|0x800  <br/> |If set, this identifies a required attribute for a contact. User Replicator uses this flag bit to filter out contacts that do not contain at least one required attribute. The OuPathId is a required attribute, which is always set. So at least one of other required attributes should be set. Otherwise, contact (that is, with value of required attribute OuPathId) will still not be written to database. For example, if **telephoneNumber** and **homePhone** are defined as required attributes, only the contacts that have at least one of these attributes are written to the database.  <br/> |
|0x4000  <br/> |If set, this identifies an exclude attribute. User Replicator uses this flag bit to filter out contacts that contain this attribute. For example, if **msRTCSIP-PrimaryUserAddress** is defined as an exclude attribute, contacts that have this attribute are not written to the database.  <br/> |
|0x8000  <br/> |If set, this identifies an include attribute. User Replicator uses this flag bit to filter out contacts that do not contain this attribute. For example, if **msRTCSIP-PrimaryUserAddress** is defined as an include attribute, only the contacts that have this attribute are written to the database.  <br/> |
   
> [!NOTE]
> If both the 0x4000 (exclude attribute) and 0x8000 (include attribute) flag bits are set, the 0x4000 bit overrides the 0x8000 bit and the contact is excluded. 
  
Although you can filter the Address Book to include only certain users, limiting entries does not limit other users' ability to contact the filtered users or to see their presence status. Users can always find, manually send instant messages, or manually initiate calls to users not in the Address Book by entering a user's complete sign-in name. Also, contact information for a user could also be found in Outlook.
  
While having full contact records in the Address Book files enables you to use Lync Server to initiate email, telephone, or Enterprise Voice calls (that is, if Enterprise Voice is enabled on the server) with users that are not configured for Session Initiation Protocol (SIP), some organizations prefer to include only SIP-enabled users in their Address Book Server entries. You can filter the Address Book to include only SIP-enabled users by clearing the 0x800 bit in the **Flags** column of the following required attributes: **mailNickname**, **telephoneNumber**, **homePhone**, and **mobile**. You can also filter the Address Book to include only SIP-enabled users by setting the 0x8000 (include attribute) in the **Flags** column of the **msRTCSIP-PrimaryUserAddress** attribute. This also helps to exclude service accounts from the Address Book files. 
  
After you modify the AbAttribute table, you can refresh the data in the AbUserEntry table by running the cmdlet **Update-CsUserDatabase** command. After UR replication completes, you can update the file in the Address Book Server file store by manually running the cmdlet **UpdateCsAddressBook** command. 
  
> [!NOTE]
> The Front End Server that the Address Book Server is placed is not administratively configurable. One is chosen during deployment—typically, the first Front End Server deployed. In the event of failure, the Address Book Service will move to another Front End Server, and requires no administrative attention. 
  
> [!IMPORTANT]
> If you have consolidated or otherwise modified your infrastructure from a multi-forest deployment or a parent/child deployment (such as consolidating your infrastructure before moving to Lync Server), you may find that the Address Book service download and the Address Book Web Query fails for some users. When in a deployment that had multiple domains or forests, the attribute **MsRTCSIP-OriginatorSid** is populated on the user objects that are exhibiting the issue. The **MsRTCSIP-OriginatorSid** attribute must be set to NULL on these objects to resolve the issue. 
  

