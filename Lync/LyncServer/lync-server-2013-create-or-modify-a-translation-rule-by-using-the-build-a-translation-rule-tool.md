---
title: 'Create or modify a translation rule by using the Build a Translation Rule tool'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Create or modify a translation rule by using the Build a Translation Rule tool
ms:assetid: ba112df8-3bb4-48e4-a353-4bf9110ccd71
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412909(v=OCS.15)
ms:contentKeyID: 48185224
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Create or modify a translation rule by using the Build a Translation Rule tool in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-05_

Follow these steps if you want to define a translation rule by entering a set of values in the **Build a Translation Rule** tool and enabling Lync Server Control Panel to generate the corresponding matching pattern and translation rule for you. Alternatively, you can a write regular expression manually to define the matching pattern and translation rule. For details, see [Create or modify a translation rule manually in Lync Server 2013](lync-server-2013-create-or-modify-a-translation-rule-manually.md).

<div>

## To define a rule by using the Build a Translation Rule tool

1.  Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator role. For details, see [Delegate setup permissions in Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  To begin defining a translation rule, follow the steps in [Configure a trunk with media bypass in Lync Server 2013](lync-server-2013-configure-a-trunk-with-media-bypass.md) through step 10 or [Configure a trunk without media bypass in Lync Server 2013](lync-server-2013-configure-a-trunk-without-media-bypass.md) through step 9.

4.  Under **Name** on the **New Translation Rule** or **Edit Translation Rule** page, type a name that describes the number pattern being translated.

5.  (Optional) Under **Description**, type a description of the translation rule, for example **US International long-distance dialing**.

6.  In the **Build a Translation Rule** section of the dialog box, enter values in the following fields:
    
      - **Starting digits**: (Optional) Specify the leading digits of numbers you want the pattern to match. For example, enter **+** in this field to match numbers in E.164 format (which begin with +).
    
      - **Length**: Specify the number of digits in the matching pattern and select whether you want the pattern to match numbers that are this length exactly, at least this length, or any length. For example, enter **11** and select **At least** in the drop-down list to match numbers that are at least 11 digits in length.
    
      - **Digits to remove**: (Optional) Specify the number of starting digits to be removed. For example, enter **1** to strip out the **+** from the beginning of the number.
    
      - **Digits to add**: (Optional) Specify digits to be prepended to the translated numbers. For example, enter **011** if you want 011 to be prepended to the translated numbers when the rule is applied.
    
    The values you enter in these fields are reflected in the **Pattern to match** and **Translation rule** fields. For example, if you specify the preceding example values, the resulting regular expression in the **Pattern to match** field is:
    
    **^\\+(\\d{9}\\d+)$**
    
    The **Translation rule** field specifies a pattern for the format of translated numbers. This pattern has two parts:
    
      - A value (for example, **$1**) that represents the number of digits in the matching pattern
    
      - (Optional) A value that you can prepend by entering it in the **Digits to add** field
    
    Using the preceding example values, **011$1** appears in the **Translation rule** field.
    
    When this translation rule is applied, +441235551010 becomes 011441235551010.

7.  Click **OK** to save the translation rule.

8.  Click **OK** to save the trunk configuration.

9.  On the **Trunk Configuration** page, click **Commit**, and then click **Commit all**.
    
    <div>
    

    > [!NOTE]
    > Whenever you create or modify a translation rule, you must run the <STRONG>Commit all</STRONG> command to publish the configuration change. For details, see <A href="lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md">Publish pending changes to the voice routing configuration in Lync Server 2013</A> in the Operations documentation.

    
    </div>

</div>

<div>

## See Also


[Create or modify a translation rule manually in Lync Server 2013](lync-server-2013-create-or-modify-a-translation-rule-manually.md)  
[Configure a trunk with media bypass in Lync Server 2013](lync-server-2013-configure-a-trunk-with-media-bypass.md)  
[Configure a trunk without media bypass in Lync Server 2013](lync-server-2013-configure-a-trunk-without-media-bypass.md)  
[Publish pending changes to the voice routing configuration in Lync Server 2013](lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md)  


[Global media bypass options in Lync Server 2013](lync-server-2013-global-media-bypass-options.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

