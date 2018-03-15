---
title: "Migrate Address Book [OCS 2007 R2 to W15]"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b6e000ce-8b2e-460c-8a8b-000254b9d778
description: ""
---

# Migrate Address Book [OCS 2007 R2 to W15]
[]
### To migrate Address Book customized normalization rules

1. Find the Company_Phone_Number_Normalization_Rules.txt file in the root of the Address Book shared folder, and copy it to the root of the Address Book shared folder in your Lync Server 2013 pilot pool.
    
    > [!NOTE]
    > The sample Address Book normalization rules have been installed in your ABS Web component file directory. The path is **$installedDriveLetter:\Program Files\Microsoft Lync Server 2013\Web Components\Address Book Files\Files\ Sample_Company_Phone_Number_Normalization_Rules.txt,**. This file can be copied and renamed as **Company_Phone_Number_Normalization_Rules.txt** to the address book shared folder's root directory. For example, the address book shared in **$serverX**, the path will be similar to: **\\$serverX \LyncFileShare\2-WebServices-1\ABFiles**. 
  
2. Use a text editor, such as Notepad, to open the Company_Phone_Number_Normalization_Rules.txt file.
    
3. Certain types of entries will not work correctly in Lync Server 2013. Look through the file for the types of entries described in this step, edit them as necessary, and save the changes to the Address Book shared folder in your pilot pool.
    
    Strings that include required whitespace or punctuation cause normalization rules to fail because these characters are stripped out of the string that is input to the normalization rules. If you have strings that include required whitespace or punctuation, you need to modify the strings. For example, the following string would cause the normalization rule to fail:
    
  ```
  \s*\(\s*\d\d\d\s*\)\s*\-\s*\d\d\d\s*\-\s*\d\d\d\d
  ```

    The following string would not cause the normalization rule to fail:
    
  ```
  \s*\(?\s*\d\d\d\s*\)?\s*\-?\s*\d\d\d\s*\-?\s*\d\d\d\d
  ```


