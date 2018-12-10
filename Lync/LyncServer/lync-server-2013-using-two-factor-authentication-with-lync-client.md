﻿---
title: 'Lync Server 2013: Using two-factor authentication with Lync client'
TOCTitle: Using two-factor authentication with Lync client
ms:assetid: d4136e61-c3ab-4b26-85c8-c1b2c24f5ee3
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn338071(v=OCS.15)
ms:contentKeyID: 55115593
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Using two-factor authentication with Lync client and Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-11_

This topic described how to take advantage of two-factor authentication with Lync 2013 client.

<div>

## Sign in to Lync 2013 for the first time

Your Lync sign-in information is usually configured automatically when Lync 2013 is installed. But the first time you use Lync, you might have to manually start the client.

**To sign in to Lync for the first time**

1.  Log on to your organization’s network.

2.  Select **Start** \> **All Programs** \> **Microsoft Lync \> Lync 2013**.
    
    You should see the Lync sign-in screen.
    
      - If the sign-in address box is already filled in, confirm that the address shown is correct.
    
      - If it’s not correct, or if the box is empty, enter your Lync sign-in address (this is usually the same as your email address).
    
      - If an empty password box is displayed, add your password.

3.  Select **Sign-in**.

</div>

<div>

## Sign out of Lync

When you’re finished using Lync, you can close the display, sign out of your session, or exit from the program, all from the File menu. The following table explains the differences in the options.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Option</th>
<th>What it does</th>
<th>How to perform it</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Close</p></td>
<td><p>Closes your Lync display but lets the Lync session identified with your user ID continue to run. This is so you can continue to get notifications and interact with others.</p>
<p>You can get the display back at any time by clicking the Lync icon on the taskbar or the notification area at the bottom of your screen.</p></td>
<td><p>On the Lync main window, do one of the following:</p>
<ol>
<li><p>Select the <strong>Options</strong> button, then select <strong>File</strong> &gt; <strong>Close</strong>.</p></li>
<li><p>Click the <strong>Close</strong> button (X) in the upper-right corner of the window.</p></li>
</ol></td>
</tr>
<tr class="even">
<td><p>Sign out</p></td>
<td><p>Ends the Lync session associated with your user ID, but Lync continues to run in the background. When you sign out, the sign-in window will appear.</p>
<div>

> [!TIP]  
> Select <STRONG>Delete my sign-in information</STRONG> when you sign out to remove the record of your logon ID and password from the computer. Doing this might make it easier for support people to troubleshoot sign-in issues. It can also help ensure your sign-in information is more secure by making it difficult for unauthorized users to log on with your credentials.


</div></td>
<td><p>On the Lync main window, select the <strong>Options</strong> button, then select <strong>File</strong> &gt; <strong>Sign Out</strong>.</p></td>
</tr>
<tr class="odd">
<td><p>Exit</p></td>
<td><p>Ends your Lync session and shuts down Lync on your computer. After exiting, if you want to restart Lync, select <strong>Start</strong> &gt; <strong>All Programs</strong> &gt; <strong>Microsoft Lync</strong> &gt; <strong>Lync 2013</strong>.</p></td>
<td><p>On the Lync main window, select the <strong>Options</strong> button, then select <strong>File</strong> &gt; <strong>Exit</strong>.</p></td>
</tr>
</tbody>
</table>


</div>

<div>

## Sign in to Lync with a Smart Card

Some organizations now use a multi-step sign-in process, called two-factor authentication, to increase security for their Lync 2013 users. If you’re expected to use this option, you’ll need a “smart card” to sign in to Lync. Smart cards come in two varieties, physical and virtual:

  - **Physical**   About the size of a credit card. You insert it into a smart card reader when you log in.

  - **Virtual**   Not a physical object, but an electronic identifier that gets written to a special chip on your computer, which in essence builds the smart card into your computer. Available only for use with Windows 8 computers that contain the TPM (Trusted Platform Module) chip.

<div>

## Enroll your smart card

Before you can sign in with a smart card, the card must be “enrolled”—that is, your user credentials have to be identified with the card. This is the case whether the card is physical or virtual. This process may already been carried out by your Lync Server administrator. Check with them if you’re not sure whether that has been done.

<div>


> [!NOTE]  
> Since each virtual smart card is associated only with the device it’s installed on, a separate card will need to be enrolled for each Windows 8 computer you use.



</div>

**To manually enroll your smart card**

1.  Log on to the computer you’ll be running Lync on.

2.  Using Internet Explorer, browse to your organization’s Certificate Authority Web Enrollment page.
    
    Ask your Lync Server administrator for the web address of this resource if you don’t already have it. The URL will look something like this: https://MyCA.\[yourcompanyname\].com/certsrv.
    
    <div>
    

    > [!NOTE]  
    > If you’re using Internet Explorer 10, you may need to view this website in Compatibility Mode.

    
    </div>

3.  When you’re prompted to log on to the certification page, log on using your domain account (rather than as administrator of your computer).

4.  On the website Welcome Page, select **Request a certificate**.

5.  Select **Advanced Request**.

6.  Select **Create and submit a request to this CA**, then click **Next**.

7.  Now you’ll see a page called Smart Card Enrollment Station. Approve the request to install the ActiveX control, and then complete the Advanced Certificate Request form as follows:
    
    1.  Select **Smartcard user** from the **Certificate Template** dropdown list.
    
    2.  Select **Create new key set**.
    
    3.  Find the manufacturer information on the label of your smart card and select that manufacturer from the **CSP** dropdown list.
    
    4.  Select **CSP** as the Request Format, if it’s not already selected.
    
    5.  Select **sha1** from the Hash Algorithm dropdown list, if it’s not already selected.
    
    6.  Give your certificate a name you’ll recognize, and click **Submit**.

8.  Now insert your blank smart card into the card reader attached to the enrollment station and click **Enroll**.

9.  When prompted, enter your personal identification number (PIN), and then click **OK**.
    
    <div>
    

    > [!NOTE]  
    > If your technical support person has not given you a special PIN to use to enroll your smart card, use the default smart card PIN value, which is 12345678.

    
    </div>

10. Select the option to force the user (you) to change the PIN the first time the smart card is used.

11. Now insert your blank smart card into the card reader attached to the enrollment station and click **Enroll**.

12. When prompted, enter your personal identification number (PIN), and then click **OK**.
    
    <div>
    

    > [!NOTE]  
    > If your technical support person has not given you a special PIN to use to enroll your smart card, use the default smart card PIN value, which is 12345678.

    
    </div>

13. Select the option to force the user (you) to change the PIN the first time the smart card is used.

14. Click **OK** to confirm that the certificate displayed has your information on it.

15. Once you see the notice that the certificate has been issued, click **Install this certificate** to complete the enrollment process.

</div>

<div>

## Sign in to Lync with your smart card credentials

Before you use your smart card for the first time, it’s recommended that you click **Delete my sign-in info** on the Lync sign-in page. Doing this clears any sign-in credentials stored on your computer, and eliminates a possible source of error.

**To sign in to Lync with your smart card credentials**

1.  Start the Lync client.

2.  On the Sign in screen, type your sign in user account name in the **Sign-in address** box, and then click **Sign In**.

3.  If you are using a virtual smart card, skip this step.
    
    If you are using a physical smart card, insert the smart card into your smart card reader and prompted to do so, and then click **OK** when the card is detected.

4.  Type in the PIN number you for your smart card and then click **OK**.
    
    <div>
    

    > [!NOTE]  
    > If you were not assigned a smart card PIN number by your support person, use the default value, which is 12345678.

    
    </div>

</div>

</div>

</div>

<span> </span>

</div>

</div>

</div>

