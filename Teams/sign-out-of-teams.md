---
title: Sign out of Microsoft Teams
author: cichur
ms.author: c-cichur
manager: serdars
audience: Admin
ms.topic: article
ms.service: msteams
search.appverid: MET150
ms.reviewer: sbhatta
description: Learn how to sign out of Microsoft Teams.
ms.custom: seo-marvel-apr2020
localization_priority: Priority
ms.collection: 
  - M365-collaboration
f1.keywords:
- NOCSH
appliesto: 
  - Microsoft Teams
---

# Sign out of Microsoft Teams

We recommend for users to remain signed in to the Microsoft Teams app to continue receiving chats, incoming calls, and other activities. We understand that users might want to sign out of the Teams application at the end of the day to use another account on a shared device or for another reason.

To sign out of Teams desktop client or from the browser, users can select their profile picture at the top of the app, and then select **Sign out**.

<img src="c:\Users\v-cichur\GitHub\OfficeDocs-SkypeForBusiness-pr\Teams/media/image1.png" style="width:2.15329in;height:2.8426in" alt="Teams sign out screen" />

For the desktop app, right-click the app icon in the taskbar, and then select **Log out**.

| **Windows Taskbar**                                                                                                                   | **Windows Systray**                                                                                                                   | **Mac Dock**                                                                                                                                                                                                                |
|---------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <img src="c:\Users\v-cichur\GitHub\OfficeDocs-SkypeForBusiness-pr\Teams/media/image2.png" style="width:1.59028in;height:1.99921in" /> | <img src="c:\Users\v-cichur\GitHub\OfficeDocs-SkypeForBusiness-pr\Teams/media/image3.png" style="width:1.76398in;height:1.74315in" /> | <img src="c:\Users\v-cichur\GitHub\OfficeDocs-SkypeForBusiness-pr\Teams/media/image4.png" style="width:2.57989in;height:1.86111in" alt="Graphical user interface, text, application Description automatically generated" /> |

On mobile devices, Tap **More** <img src="c:\Users\v-cichur\GitHub\OfficeDocs-SkypeForBusiness-pr\Teams/media/image5.png" style="width:0.175in;height:0.14583in" alt="More button" /> &gt; **Settings** &gt; **Sign out**.

| **iOS**                                                                                                                                                                                                              | **Android**    |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|
| <img src="c:\Users\v-cichur\GitHub\OfficeDocs-SkypeForBusiness-pr\Teams/media/image7.png" style="width:1.7804in;height:3.85401in" alt="Graphical user interface, application Description automatically generated" /> | TBA by Content |

If you have multiple accounts added, you'll need to sign out of your individual accounts. Once you've signed out of the accounts in Teams, you'll need to enter their credentials again on the next launch of the app to access your account.

### Account residency

Modern Operating Systems allow sharing of accounts between different apps on a device. This Single Sign On design allow users to use multiple apps on their device without requiring them to sign in to every single app. Teams does not control this behavior, but it does take advantage of the convenience this design provides for the end-user experience.

This has an important impact on sign-out. When users sign out of Teams, the data associated with their account is removed from the Teams app, but other apps on the device continue to have access to their account. It also means that users may not be prompted to re-enter their credentials if they choose to sign back in to Teams with the same account.

To remove an account from the device, users will need to take some additional steps. Here’s an overview of steps required; please read OS specific documentation on how best to do this.

> [!NOTE]
> These actions might have consequences to your experience on the device or with other apps or services. Please use your judgement and use these only if you must.</td>

**Windows 10**

<table>
<tbody>
<tr class="odd">
<td><strong>For personal accounts</strong><br />
Go to Settings &gt; Accounts &gt; Email &amp; accounts &gt; Select the account you want to remove from the device &gt; Click the ‘Remove’ button and follow the instructions.<br />
<br />
<strong>For work or school accounts<br />
</strong>Go to Settings &gt; Accounts &gt; Access work or school &gt; Select the account you want to remove from the device &gt; Click the ‘Disconnect’ button and follow the instructions.</td>
</tr>
</tbody>
</table>

**Mac**

|                                                                                                                                         |
|-----------------------------------------------------------------------------------------------------------------------------------------|
| Open Keychain Access &gt; Select ‘login’ &gt; Right click on the account you want to remove &gt; Click on ‘Delete &lt;account name&gt;’ |

**iOS and Android**

<table>
<tbody>
<tr class="odd">
<td><p>For users using Microsoft Authenticator app:</p>
<ul>
<li><p>Open the app &gt; Select the account you want to remove from the device &gt; Click on the gear ️ icon &gt; Click ‘Remove account’</p></li>
</ul>
<p>For users not using Microsoft Authenticator app, please consult OS documentation.</p>
<p>For users on shared devices, please refer to the ‘Global sign out’ section below.</p></td>
</tr>
</tbody>
</table>

**Browsers**

<table>
<tbody>
<tr class="odd">
<td><p>If the user is signed in with multiple accounts, the account provider will ask to choose the account they want to sign out of. The user needs to choose the correct account.</p>
<p>It is always a good idea to close all open browser windows to fully complete the sign out process.</p></td>
</tr>
</tbody>
</table>

**Other OSs**

|                                             |
|---------------------------------------------|
| Please check the OS specific documentation. |

### Global sign in and sign out for Frontline workers

The Teams Android app now supports Global sign-in and sign-out, to provide a hassle free sign-in and sign-out experience for Frontline Workers. Employees can pick a device from the shared device pool and do a single sign in to "make it theirs" for the duration of their shift. At the end of their shift, they should be able to perform sign out to globally sign out on the device. This will remove all of their personal and company information from the device so they can return the device to the device pool. To get this capability, the device must be in shared mode. To learn how to set up a shared device, see [How to use a shared device mode in Android](https://docs.microsoft.com/en-us/azure/active-directory/develop/tutorial-v2-shared-device-mode#set-up-an-android-device-in-shared-mode).

The sign-in experience looks similar to our standard Teams sign experience, while sign out will look like the following two images:

<img src="c:\Users\v-cichur\GitHub\OfficeDocs-SkypeForBusiness-pr\Teams/media/image8.png" style="width:4.68611in;height:3.88333in" alt="A picture containing text, electronics, screenshot Description automatically generated" />

**Manual Cleanup**

While rare, it is possible that Teams might not be able to clean up after itself fully on sign out. Based on user reports, the common causes include files being locked by a service running on the system but there could be other reasons dependent on an individual’s device configurations or policies and user permissions applied to the device.

One common manifestation of this problem is that Teams will try to automatically select an existing account to sign the user in. In situations like this, the user might want to manually clean up Teams’ local cache.

Before you follow these steps, make sure that you don’t have Teams running (Quit from the systray on Windows and from the dock on Mac). It is also advised that the user reboots the machine in case the auto cleanup failed because one or more files were locked.

**Windows**

|                                                                                            |
|--------------------------------------------------------------------------------------------|
| Go to %appdata%\\Microsoft\\Teams &gt; Delete all the contents of the folder if it exists. |

**Mac**

<table>
<tbody>
<tr class="odd">
<td><p>Go to ~/Library/Application Support/Microsoft &gt; Delete all the contents of the folder if it exists.</p>
<p>Open Keychain Access &gt; Select ‘login’ &gt; Delete all entries for ‘Microsoft Teams Identities Cache’</p></td>
</tr>
</tbody>
</table>

APPENDIX – PLEASE IGNORE ANYTHING BELOW HERE

**Signing out from another device**

If a user has lost physical access to a device, either temporarily or permanently, they can use another device in their possession to sign out of the Teams client.

**Work or school account**

|     |
|-----|
|     |

**Personal account**

|     |
|-----|
|     |

**IT admin managed re-authentications**

Microsoft Identity also provides IT admins a set of tools that they can use to manage user sessions, including setting an expiry or revoking a token, which will require the end user to re-authenticate to the Teams client. Here’s a list of the most common tools:

-   Configurable token lifetime?

> IT admins can configure the lifetime (validity) of an access, ID or SAML token issued by Microsoft Identity platform for work or school accounts.  
> [Learn more about configurable token lifetimes](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-configurable-token-lifetimes).

-   Token Revocation V2?

-   Continuous Access Evaluation (CAE)?

**Signing out from embedded apps**

-   LMS

-   OWA

-   ??
