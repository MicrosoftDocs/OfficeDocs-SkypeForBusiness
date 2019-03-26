---
title: Migrate Address Book
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Migrate Address Book
ms:assetid: b6e000ce-8b2e-460c-8a8b-000254b9d778
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205198(v=OCS.15)
ms:contentKeyID: 48185218
ms.date: 07/23/2014
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

_**Topic Last Modified:** 2012-10-02_

**To migrate Address Book customized normalization rules**

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

<span> </span>

</div>

</div>

</div>

