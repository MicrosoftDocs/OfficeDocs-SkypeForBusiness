---
title: Migrate Address Book
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Migrate Address Book
ms:assetid: ac7f0f39-4c6d-4702-8e25-93a73e3d800f
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205160(v=OCS.15)
ms:contentKeyID: 48185064
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Migrate Address Book

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-09_

In general, the Lync Server 2010 Address Book is migrated along with the rest of your topology. However, you might need to perform some post-migration steps if you customized the following in your Lync Server 2010 environment:

  - Set the **PartitionbyOU** WMI property to group Address Book entries by organizational unit (OU).

  - Customized the Address Book normalization rules.

  - Changed the default value for the **UseNormalizationRules** parameter to False.

**Grouped Address Book Entries**

If you set the **PartitionbyOU** WMI property to True to create address books for each OU, you need to set the **msRTCSIP-GroupingId** Active Directory attribute on users and contacts if you want to continue grouping address book entries. You might want to group address book entries to limit the scope of Address Book searches. To use the **msRTCSIP-GroupingId** attribute, write a script to populate the attribute, assigning the same value for all of the users that you want to group together. For example, assign a single value for all the users in an OU.

**Address Book Normalization Rules**

If you customized Address Book normalization rules in your Lync Server 2010 environment, you must migrate the customized rules to your pilot pool. If you did not customize Address Book normalization rules, you have nothing to migrate for Address Book service. The default normalization rules for Lync Server 2013 are the same as the default rules for Lync Server 2010. Follow the procedure later in this section to migrate customized normalization rules.

<div>


> [!NOTE]  
> If your organization uses remote call control and you customized Address Book normalization rules, you must perform the procedure in this topic before you can use remote call control. The procedure requires membership in the RTCUniversalServerAdmins group or equivalent rights.



</div>

**UseNormalizationRules Set to False**

If you set the value for **UseNormalizationRules** to False so that users can use phone numbers as they are defined in Active Directory Domain Services without having Lync Server 2013 apply normalization rules, you need to set the **UseNormalizationRules** and **IgnoreGenericRules** parameters to True. Follow the procedure later in this section to set these parameters to True.

<div>

## To migrate Address Book customized normalization rules

1.  Find the Company\_Phone\_Number\_Normalization\_Rules.txt file in the root of the Address Book shared folder, and copy it to the root of the Address Book shared folder in your Lync Server 2013 pilot pool.
    
    <div>
    

    > [!NOTE]  
    > The sample Address Book normalization rules have been installed in your ABS Web component file directory. The path is <STRONG>$installedDriveLetter:\Program Files\Microsoft Lync Server 2013\Web Components\Address Book Files\Files\ Sample_Company_Phone_Number_Normalization_Rules.txt,</STRONG>. This file can be copied and renamed as &nbsp;<STRONG>Company_Phone_Number_Normalization_Rules.txt</STRONG> &nbsp;to the address book shared folder’s root directory. For example, the address book shared in <STRONG>$serverX</STRONG>,&nbsp;the path will be similar to: <STRONG>\\$serverX \LyncFileShare\2-WebServices-1\ABFiles</STRONG>.

    
    </div>

2.  Use a text editor, such as Notepad, to open the Company\_Phone\_Number\_Normalization\_Rules.txt file.

3.  Certain types of entries will not work correctly in Lync Server 2013. Look through the file for the types of entries described in this step, edit them as necessary, and save the changes to the Address Book shared folder in your pilot pool.
    
    Strings that include required whitespace or punctuation cause normalization rules to fail because these characters are stripped out of the string that is input to the normalization rules. If you have strings that include required whitespace or punctuation, you need to modify the strings. For example, the following string would cause the normalization rule to fail:
    
        \s*\(\s*\d\d\d\s*\)\s*\-\s*\d\d\d\s*\-\s*\d\d\d\d
    
    The following string would not cause the normalization rule to fail:
    
        \s*\(?\s*\d\d\d\s*\)?\s*\-?\s*\d\d\d\s*\-?\s*\d\d\d\d

</div>

<div>

## To set UseNormalizationRules and IgnoreGenericRules to true

1.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

2.  Do one of the following:
    
      - If your deployment includes only Lync Server 2013, run the following cmdlet at the global level to change the values for **UseNormalizationRules** and **IgnoreGenericRules** to True:
        
            Set-CsAddressBookConfiguration -identity <XdsIdentity> -UseNormalizationRules=$true -IgnoreGenericRules=$true
    
      - If your deployment includes a combination of Lync Server 2013 and Lync Server 2010 or Office Communications Server 2007 R2, run the following cmdlet and assign it to each Lync Server 2013 pool in the topology:
        
            New-CsAddressBookConfiguration -identity <XdsIdentity> -UseNormalizationRules=$true -IgnoreGenericRules=$true

3.  Wait for Central Management store replication to occur on all pools.

4.  Modify the phone normalization rules file, "Company\_Phone\_Number\_Normalization\_Rules.txt", for your deployment to clear the content. The file is on the file share of each Lync Server 2013 pool. If the file is not present, then create an empty file named "Company\_Phone\_Number\_Normalization\_Rules.txt".

5.  Wait several minutes for all Front End pools to read the new files.

6.  Run the following cmdlet on each Lync Server 2013 pool in your deployment:
    
        Update-CsAddressBook

</div>

</div>

<span> </span>

</div>

</div>

</div>

