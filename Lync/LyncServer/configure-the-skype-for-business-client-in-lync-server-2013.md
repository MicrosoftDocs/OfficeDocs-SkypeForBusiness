---
title: Configure the Skype for Business client in Lync Server 2013
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configure the client experience
ms:assetid: 61e783f1-24f4-430b-ae52-c76a4d206dc7
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn954919(v=OCS.15)
ms:contentKeyID: 65227958
ms.date: 09/18/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure the client experience with Skype for Business

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2015-09-17_

**Summary:** This topic describes how to configure the client experience for Skype for Business client users in a Lync Server 2013 environment. You can configure the client experience only if you are running Lync Server 2013 with the December 2014 Cumulative Update (5.0.8308.857) or later installed. For information about updating Lync Server 2013, see [Updates for Lync Server 2013](http://go.microsoft.com/fwlink/p/?linkid=532651).

Skype for Business provides a new user experience that is based on the Skype consumer product experience. In addition to all the features of Lync, Skype for Business provides new features with simplified controls and familiar icons. For detailed information about the new client experience, see [Lync is now Skype for Business -- see what's new](http://go.microsoft.com/fwlink/?linkid=529022).

Lync Server 2013 supports the new Skype for Business client experience as well as the Lync client experience. As an administrator, you can choose the preferred client experience for your users. For example, you might want to deploy the Lync client experience until users in your organization are fully trained in the new Skype for Business experience. Or, if you have not yet upgraded all users to Skype for Business Server 2015, you might want all users to have the same client experience until all are upgraded to the new server.

<div>


> [!IMPORTANT]  
> If your organization has both Skype for Business Server 2015 and Lync Server 2013 deployed, the default client experience will differ depending on server versions and UI settings. When users launch Skype for Business for the first time, they will always see the Skype for Business user interface--even if you have selected the Lync user interface. After several minutes, users are asked to switch to Lync mode. For more information, see <STRONG>First launch client behavior</STRONG> later in this topic.



</div>

<div>


> [!NOTE]  
> The Lync 2013 client experience is not an option for Skype for Business 2016 client versions. Before you attempt to configure your client environment to use the Lync 2013 client, please check the client version to ensure it does not start with the number 16; for example: 16.x.x.x.



</div>

<div>

## Configure the client experience

You can specify the client experience the users in your organization will see by using the **Set-CSClientPolicy** cmdlet with the EnableSkypeUI parameter. The following command selects the Skype for Business client experience for all users in your organization affected by the Global policy (remember, site or user-specific policies override the Global policy):

    Set-CsClientPolicy -Identity Global -EnableSkypeUI $true

The next command selects the Lync client experience for all users in your organization affected by the Global policy:

    Set-CsClientPolicy -Identity Global -EnableSkypeUI $false

The next command selects the Skype for Business client experience for all users within the Redmond site:

    Set-CsClientPolicy -Identity site:Redmond -EnableSkypeUI $true

If you want to configure the client experience for specific users within your organization, you can create a new user policy by using the **New-CsClientPolicy** cmdlet, and then assign the policy to specific users by using the **Grant-CsClientPolicy** cmdlet.

For example, the following command creates a new client policy, SalesClientUI, that selects the Skype for Business client experience:

    New-CsClientPolicy -Identity SalesClientUI -EnableSkypeUI $true

The next command assigns the policy, SalesClientUI, to all members of the Sales department:

    Get-CsUser -LDAPFilter "Department=Sales" | Grant-CsClientPolicy -PolicyName SalesClientUI

</div>

<div>

## First launch client behaviors

By default, when users launch Skype for Business for the first time, they will always see the Skype for Business user interface--even if you have selected the Lync client experience by setting the value of the EnableSkypeUI parameter to $False as described previously. After several minutes, users will then be asked to switch to Lync mode.

If you want to display the Lync user interface when users launch the Skype for Business client for the first time, follow these steps before the client is started for the first time after being updated:

1.  Confirm that the value of `EnableSkypeUI` is set to $False in the policy you are using as described previously.

2.  Update the system registry on the user's computer. You should do this before the first time users launch the Skype for Business client, and you should do this only once. For information about how to create a Group Policy Object to update the registry on a domain joined computer, see the section later in the topic.
    
    In the **\[HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\Lync\]** key, create a new **Binary** value.
    
    The **Value name** must be **EnableSkypeUI**, and the **Value data** must be set to **00 00 00 00**.
    
    The key should look like the following:
    
        [HKEY_CURRENT_USER\Software\Microsoft\Office\Lync]
        "CanSharePptInCollab"=dword:00000001
        "CanShareOneNoteInCollab"=dword:00000001
        "CanAppShareInCollab"=dword:00000001
        "EnableSkypeUI"=hex:00,00,00,00

The Lync user interface will now be displayed when users launch the Skype for Business client for the first time.

<div>

## Control the display of the Welcome screen tutorial

When users open the Skype for Business client, the default behavior is to display a Welcome screen that includes *7 Quick tips most people ask for*. You can turn off the display of the Welcome screen but still allow users to access the tutorial by adding the following Registry value on the client computer:

In the **\[HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\15.0\\Lync\]** key, create a new **DWORD (32-bit) Value**. The **Value name** must be **IsBasicTutorialSeenByUser**, and the **Value data** must be set to **1**.

The key should look like the following:

    "IsBasicTutorialSeenByUser"=dword:00000001

</div>

<div>

## Turn off the client tutorial

If you do not want your users to be able to access the tutorial, you can turn off the client tutorial with the following Registry value:

In the **\[HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\15.0\\Lync\]** key, create a new **DWORD (32-bit) Value**. The **Value name** must be **TutorialFeatureEnabled**, and the **Value data** must be set to **0**.

    "TutorialFeatureEnabled"=dword:00000000

You can turn the tutorial back on by setting the **Value data** to **1**.

</div>

</div>

<div>

## Default client experiences

If your organization has both Skype for Business Server 2015 and Lync Server deployed, the client experience will differ depending on server versions and the Skype UI setting. The following table shows the initial client experience based on server version and the UI setting:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Server version</p></th>
<th><p>EnableSkypeUI setting</p></th>
<th><p>Client experience</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Skype for Business Server 2015</p></td>
<td><p>Default</p></td>
<td><p>Skype for Business</p></td>
</tr>
<tr class="even">
<td><p>Skype for Business Server 2015</p></td>
<td><p>True</p></td>
<td><p>Skype for Business</p></td>
</tr>
<tr class="odd">
<td><p>Skype for Business Server 2015</p></td>
<td><p>False</p></td>
<td><p>User asked to switch to Lync mode (user can switch to Skype for Business later if you change the UI setting to $true)</p></td>
</tr>
<tr class="even">
<td><p>Lync Server 2010 or Lync Server 2013 (with correct patches)</p></td>
<td><p>Default</p></td>
<td><p>User asked to switch to Lync mode (user can switch to Skype for Business later if you change the UI setting to $true)</p></td>
</tr>
<tr class="odd">
<td><p>Lync Server 2010 or Lync Server 2013 (with correct patches)</p></td>
<td><p>True</p></td>
<td><p>Skype for Business</p></td>
</tr>
<tr class="even">
<td><p>Lync Server 2010 or Lync Server 2013 (with correct patches)</p></td>
<td><p>False</p></td>
<td><p>User asked to switch to Lync mode (user can switch to Skype for Business later if you change the UI setting to $true)</p></td>
</tr>
<tr class="odd">
<td><p>Lync Server 2010 or Lync Server 2013 (without patches)</p></td>
<td><p>Default</p></td>
<td><p>User asked to switch to Lync client experience (user cannot switch to Skype for Business later)</p></td>
</tr>
</tbody>
</table>


The next table shows the client experience when the administrator changes the initial setting for the Skype UI experience:


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Server version</p></th>
<th><p>Skype UI setting</p></th>
<th><p>Client UI = Lync</p></th>
<th><p>Client UI = Skype for Business</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Skype for Business Server 2015</p></td>
<td><p>True</p></td>
<td><p>User asked to switch to Skype for Business</p></td>
<td><p>Skype for Business</p></td>
</tr>
<tr class="even">
<td><p>Skype for Business Server 2015</p></td>
<td><p>False</p></td>
<td><p>Lync UI</p></td>
<td><p>User asked to switch to Lync UI</p></td>
</tr>
<tr class="odd">
<td><p>Lync Server 2010 or Lync Server 2013 (with correct patches)</p></td>
<td><p>True</p></td>
<td><p>User asked to switch to Skype for Business</p></td>
<td><p>Skype for Business</p></td>
</tr>
<tr class="even">
<td><p>Lync Server 2010 or Lync Server 2013 (with correct patches)</p></td>
<td><p>False</p></td>
<td><p>Lync UI</p></td>
<td><p>User asked to switch to Lync UI</p></td>
</tr>
<tr class="odd">
<td><p>Lync Server 2010 or Lync Server 2013 (without patches)</p></td>
<td><p>Default</p></td>
<td><p>Lync mode (cannot switch to Skype for Business)</p></td>
<td><p>Lync UI (cannot switch to Skype for Business)</p></td>
</tr>
</tbody>
</table>


The patch versions required to manage the configuration of the Skype for Business client are:

  - Lync Server 2010 - February 2015 Cumulative Update (4.0.7577.710) for Lync Server 2010. For information, see [Updates for Lync Server 2010](http://go.microsoft.com/fwlink/p/?linkid=532771)

  - Lync Server 2013 - December 2014 Cumulative Update (5.0.8308.857) for Lync Server 2013. For information, see [Updates for Lync Server 2013](http://go.microsoft.com/fwlink/p/?linkid=532772).

</div>

<div>

## Create a Group Policy Object to modify the registry on a domain joined computer

The registry update to display the Lync client experience the first time a user launches the Skype for Business client should be done only once. If you use a Group Policy Object (GPO) to update the registry, you need to define the object to create a new value rather than update the Value data. When the GPO is applied, if the new value does not exist, the GPO will create it and set the Value data to 0.

The following procedure describes how to modify the registry so that the Lync client experience is displayed the first time a user launches the Skype for Business. You can also use this procedure to update the registry to disable the Welcome screen tutorial as described earlier.

**To create the GPO**

1.  Start the **Group Policy Management console**.
    
    For information about how to use the Group Policy Management Console, see [Group Policy Management Console](http://go.microsoft.com/fwlink/?linkid=532759).

2.  Right-click the **Group Policy Objects** node and select **New** on the menu.

3.  In the **New GPO** dialog, enter a name for the GPO, for example, **MakeLyncDefaultUI**, and then click **OK**.

4.  Right-click on the new GPO you just created and then select **Edit** from the menu.

5.  In the **Group Policy Management Editor**, expand **User Configuration**, expand **Preferences**, expand **Windows Settings**, and then select the **Registry** node.

6.  Right-click on the **Registry** node, and then select **New** \> **Registry Item**.

7.  On the **New Registry Properties** dialog, update the following:
    
    
    <table>
    <colgroup>
    <col style="width: 50%" />
    <col style="width: 50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Field</th>
    <th>Value to select or enter</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><strong>Action</strong></p></td>
    <td><p><strong>Create</strong></p></td>
    </tr>
    <tr class="even">
    <td><p><strong>Hive</strong></p></td>
    <td><p>HKEY_CURRENT_USER</p></td>
    </tr>
    <tr class="odd">
    <td><p><strong>Key Path</strong></p></td>
    <td><p>Software\Microsoft\Office\Lync</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>Value name</strong></p></td>
    <td><p>EnableSkypeUI</p></td>
    </tr>
    <tr class="odd">
    <td><p><strong>Value type</strong></p></td>
    <td><p>REG_BINARY</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>Value data</strong></p></td>
    <td><p>00000000</p></td>
    </tr>
    </tbody>
    </table>


8.  Click **OK** to save your changes, and then close the GPO.

Next, you'll need to link the GPO you created to the group of users that you want to assign the policy to, such as an OU.

**To use the GPO to assign the policy**

1.  In the Group Policy Management Console, right-click on the OU you want to assign the policy to, and then select **Link to an existing GPO**.

2.  On the **Select GPO** dialog, select the GPO you created, and then select **OK**.

3.  On the target user's computer, open a command prompt and type the following command:
    
    **gpupdate /target:user**
    
    The message "Updating policy..." is displayed while the GPO is applied. When it is completed, the message "User Policy update has completed successfully" is displayed.

4.  At the command prompt, type the following command:
    
    **gpresult /r**
    
    You should see "Assigned Group Policy Objects" with the name of the GPO you created displayed below.

You can also verify that the GPO has successfully updated the registry on a user's computer by examining the registry. Open Registry Editor and navigate to the **\[HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\Lync\]** key. If the GPO successfully updated the registry you will see a value named EnableSkypeUI with a value of 0.

</div>

</div>

<span> </span>

</div>

</div>

</div>

