---
title: 'Lync Server 2013: Assign a per-user location policy'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Assign a per-user location policy
ms:assetid: 343f2de3-a0ae-4403-8456-6e520b579d32
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg520974(v=OCS.15)
ms:contentKeyID: 48183794
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

# Assign a per-user location policy in Lync Server 2013

 


The location policy is one of the individual settings of a user account that you can configure in the Lync Server Control Panel.

Deploying one or more per-user location policies is optional. You can also deploy only a global-level location policy or subnet-level location policy. If you do deploy per-user policies, you must explicitly assign them to users, groups, or contact object. Enhanced 9-1-1 (E9-1-1) settings automatically default to those defined in the global-level location policy when no specific subnet-level or per-user policy is assigned.

After creating at least one per-user location policy, use the procedures in this topic to assign to the policy that specifies the settings that you want the server to apply for emergency calls placed by a particular user.

For a list of all available location policy settings, see [Defining the location policy for Lync Server 2013](lync-server-2013-defining-the-location-policy.md).

For details about creating location policies, see [Create location policies in Lync Server 2013](lync-server-2013-create-location-policies.md).

## To assign a per-user location policy with the Lync Server Control Panel

1.  From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Users**.

4.  Use one of the following methods to locate a user:
    
      - In the **Search users** box, type all or the first portion of the display name, first name, last name, Security Accounts Manager (SAM) account name, SIP address, or line Uniform Resource Identifier (URI) of the user account, and then click **Find**.
    
      - If you have a saved query, click the **Open query** icon, use the **Open** dialog box to retrieve the query (a .usf file), and then click **Find**.

5.  (Optional) Specify additional search criteria to narrow the results:
    
    1.  Click **Add Filter**.
    
    2.  Enter the user property by typing it or by clicking the arrow in the drop-down list to select the property.
    
    3.  In the **Equal to** drop-down list, click the operator (for example, **Equal to** or **Not equal to**).
    
    4.  Depending on the user property you selected, enter the criteria you want to use to filter the search results by typing it or by clicking the arrow in the drop-down list.
        

        > [!TIP]  
        > To add additional search clauses to your query, click <STRONG>Add Filter</STRONG>.

    
    5.  Click **Find**.

6.  Click a user in the search results, click **Action**, and then click **Assign policies**.
    

    > [!TIP]  
    > If you want the same per-user location policy to apply to multiple users, select multiple users in the search results, then click <STRONG>Actions</STRONG>, and then click <STRONG>Assign policies</STRONG>.



7.  In **Assign Policies**, under **Location policy**, do one of the following:
    

    > [!NOTE]  
    > Because there are multiple policies that you can configure by using the <STRONG>Assign Policies</STRONG> dialog box, <STRONG>&lt;Keep as is&gt;</STRONG> is selected by default for every policy in the dialog box. Continue using the policy previously assigned to the user by making no changes to this setting.

    
      - Allow Lync Server 2013 to automatically choose either the global-level policy or, if defined, the subnet-level policy.
    
      - Click the name of a per-user location policy you previously defined by running the **New-CsLocationPolicy** cmdlet.
        

        > [!TIP]  
        > To help you decide the policy that you want to assign, after you click a policy name, click <STRONG>View</STRONG> to view the user rights and permissions defined in the policy.



8.  When you are finished, click **OK**.

## Assigning a Per-User Location Policy by Using Lync Server Management Shell Cmdlets

You can assign per-user location policies by using the Grant-CsLocationPolicy cmdlet. You can run this cmdlet either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

## To assign a per-user location policy to a single user

  - The following command assigns the per-user location policy RedmondLocationPolicy to the user Ken Myer.
    
        Grant-CsLocationPolicy -Identity "Ken Myer" -PolicyName "RedmondLocationPolicy"

## To assign a per-user location policy to multiple users

  - This command assigns the per-user location policy AccountingDepartmentLocationPolicy to all the users who work for the Accounting department. For more information on the LdapFilter parameter used in this command, see the documentation for the [Get-CsUser](https://technet.microsoft.com/en-us/library/gg398125\(v=ocs.15\)) cmdlet.
    
        Get-CsUser -LdapFilter "Department=Accounting" | Grant-CsLocationPolicy -PolicyName "AccountingDepartmentLocationPolicy"

## To unassign a per-user location policy

  - The following command unassigns any per-user location policy previously assigned to Ken Myer. After the per-user policy is unassigned, Ken Myer will automatically be managed by using the global policy or, if one exists, his local site policy. A site policy takes precedence over the global policy.
    
        Grant-CsLocationPolicy -Identity "Ken Myer" -PolicyName $Null

For more information, see the help topic for the [Grant-CsLocationPolicy](https://technet.microsoft.com/en-us/library/gg413049\(v=ocs.15\)) cmdlet.

