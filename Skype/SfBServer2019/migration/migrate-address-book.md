---
title: "Migrate Address Book"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
description: "In general, the Address Book is migrated along with the rest of your topology. However, you might need to perform some post-migration steps if you customized the following in your legacy environment:"
---

# Migrate Address Book

In general, the Address Book is migrated along with the rest of your topology. However, you might need to perform some post-migration steps if you customized the following in your legacy environment: 

- Customized the Address Book normalization rules.

- Changed the default value for the **UseNormalizationRules** parameter to False. 


 **Address Book Normalization Rules**

If you customized Address Book normalization rules in your legacy environment, you must migrate the customized rules to your pilot pool. If you did not customize Address Book normalization rules, you have nothing to migrate for Address Book service. The default normalization rules for Skype for Business Server 2019 are the same as the default rules for the legacy install. Follow the procedure later in this section to migrate customized normalization rules.

> [!NOTE]
> If your organization uses remote call control and you customized Address Book normalization rules, you must perform the procedure in this topic before you can use remote call control. The procedure requires membership in the RTCUniversalServerAdmins group or equivalent rights. 

 **UseNormalizationRules Set to False**

If you set the value for **UseNormalizationRules** to False so that users can use phone numbers as they are defined in Active Directory Domain Services without having Skype for Business Server 2019 apply normalization rules, you need to set the **UseNormalizationRules** and **IgnoreGenericRules** parameters to True. Follow the procedure later in this section to set these parameters to True. 

## To migrate Address Book customized normalization rules

1. Find the Company_Phone_Number_Normalization_Rules.txt file in the root of the Address Book shared folder, and copy it to the root of the Address Book shared folder in your Skype for Business Server 2019 pilot pool.

    > [!NOTE]
    > The sample Address Book normalization rules have been installed in your ABS Web component file directory. The path is **$installedDriveLetter:\Program Files\Microsoft Skype for Business Server 2019\Web Components\Address Book Files\Files\ Sample_Company_Phone_Number_Normalization_Rules.txt**. This file can be copied and renamed as **Company_Phone_Number_Normalization_Rules.txt** to the address book shared folder's root directory. For example, the address book shared in **$serverX**, the path will be similar to: **\\$serverX \SkypeForBusiness-FileShare\2-WebServices-1\ABFiles**. 

2. Use a text editor, such as Notepad, to open the Company_Phone_Number_Normalization_Rules.txt file.

3. Certain types of entries will not work correctly in Skype for Business Server 2019. Look through the file for the types of entries described in this step, edit them as necessary, and save the changes to the Address Book shared folder in your pilot pool.

    Strings that include required whitespace or punctuation cause normalization rules to fail because these characters are stripped out of the string that is input to the normalization rules. If you have strings that include required whitespace or punctuation, you need to modify the strings. For example, the following string would cause the normalization rule to fail:

   ```
   \s*\(\s*\d\d\d\s*\)\s*\-\s*\d\d\d\s*\-\s*\d\d\d\d
   ```

    The following string would not cause the normalization rule to fail:

   ```
   \s*\(?\s*\d\d\d\s*\)?\s*\-?\s*\d\d\d\s*\-?\s*\d\d\d\d
   ```

## To set UseNormalizationRules and IgnoreGenericRules to true

1. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Skype for Business Server 2019**, and then click **Skype for Business Server Management Shell**.

2. Do one of the following:

   - If your deployment includes only Skype for Business Server 2019, run the following cmdlet at the global level to change the values for **UseNormalizationRules** and **IgnoreGenericRules** to True: 

   ```
   Set-CsAddressBookConfiguration -identity <XdsIdentity> -UseNormalizationRules=$true -IgnoreGenericRules=$true
   ```

   - If your deployment includes a combination of Skype for Business Server 2019 and a legacy install, run the following cmdlet and assign it to each Skype for Business Server 2019 pool in the topology:

   ```
   New-CsAddressBookConfiguration -identity <XdsIdentity> -UseNormalizationRules=$true -IgnoreGenericRules=$true
   ```

3. Wait for Central Management store replication to occur on all pools.

4. Modify the phone normalization rules file, "Company_Phone_Number_Normalization_Rules.txt", for your deployment to clear the content. The file is on the file share of each Skype for Business Server 2019 pool. If the file is not present, then create an empty file named "Company_Phone_Number_Normalization_Rules.txt".

5. Wait several minutes for all Front End pools to read the new files.

6. Run the following cmdlet on each Skype for Business Server 2019 pool in your deployment:

   ```
   Update-CsAddressBook
   ```


