---
title: 'Create or modify a normalization rule by using Build a Normalization Rule'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Create or modify a normalization rule by using Build a Normalization Rule
ms:assetid: e8547d7b-f74d-4a73-9a7d-df20d7a87fcd
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg399036(v=OCS.15)
ms:contentKeyID: 48185889
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Create or modify a normalization rule by using Build a Normalization Rule in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-11-01_

Complete the following steps if you want to create or modify a normalization rule in Lync Server Control Panel. Alternatively, if you want to create or modify a normalization rule manually, see [Create or modify a normalization rule manually in Lync Server 2013](lync-server-2013-create-or-modify-a-normalization-rule-manually.md).

<div>

## To define a rule by using Build a Normalization Rule

1.  Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator role. For details, see [Delegate setup permissions in Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  (Optional) Follow the steps in [Create a dial plan in Lync Server 2013](lync-server-2013-create-a-dial-plan.md) through step 11 or [Modify a dial plan in Lync Server 2013](lync-server-2013-modify-a-dial-plan.md) through step 10.

4.  In **New Normalization Rule** or **Edit Normalization Rule**, type a name that describes the number pattern being normalized in **Name** (for example, **5DigitExtension**).

5.  (Optional) In **Description**, type a description of the normalization rule (for example, "Translates 5-digit extensions").

6.  In **Build a Normalization Rule**, enter values in the following fields:
    
      - **Starting digits**   (Optional) Specify the leading digits of dialed numbers you want the pattern to match. For example, type **425** if you want the pattern to match dialed numbers beginning with 425.
    
      - **Length**   Specify the number of digits in the matching pattern and select whether you want the pattern to match this length exactly, match dialed numbers that are at least this length, or match dialed numbers of any length.
    
      - **Digits to remove**   (Optional) Specify the number of starting digits to be removed from dialed numbers you want the pattern to match.
    
      - **Digits to add**   (Optional) Specify digits to be added to dialed numbers you want the pattern to match.
    
    The values you enter in these fields are reflected in **Pattern to match** and **Translation rule**. For example, if you leave **Starting digits** empty, type **7** into the **Length** field and select **Exactly**, and specify **0** in **Digits to remove**, the resulting regular expression in the **Pattern to match** is:
    
    **^(\\d{7})$**

7.  In **Translation rule**, specify a pattern for the format of translated E.164 phone numbers as follows:
    
      - A value that represents the number of digits specified in the matching pattern. For example, if the matching pattern is **^(\\d{7})$** then **$1** in the translation rule represents 7-digit dialed numbers.
    
      - (Optional) Type a value into the **Digits to add** field to specify digits to be prepended to the translated number (for example, **+1425**).
    
    For example, if **Pattern to match** contains **^(\\d{7})$** as the pattern for dialed numbers and **Translation rule** contains **+1425$1** as the pattern for E.164 phone numbers, the rule normalizes 5550100 to +14255550100.

8.  (Optional) If the normalization rule results in a phone number that is internal to your organization, select **Internal extension**.

9.  (Optional) Enter a number to test the normalization rule, and then click **Go**. The test results are displayed under **Enter a number to test**.
    
    <div>
    

    > [!NOTE]
    > You can save a normalization rule that does not yet pass the test and then reconfigure it later. For details, see <A href="lync-server-2013-test-voice-routing.md">Test voice routing in Lync Server 2013</A>.

    
    </div>

10. Click **OK** to save the normalization rule.

11. Click **OK** to save the dial plan.

12. On the **Dial Plan** page, click **Commit**, and then click **Commit all**.
    
    <div>
    

    > [!NOTE]
    > Whenever you create or change a normalization rule, you must run the <STRONG>Commit all</STRONG> command to publish the configuration change. For details, see <A href="lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md">Publish pending changes to the voice routing configuration in Lync Server 2013</A> in the Operations documentation.

    
    </div>

</div>

<div>

## See Also


[Create or modify a normalization rule manually in Lync Server 2013](lync-server-2013-create-or-modify-a-normalization-rule-manually.md)  
[Create a dial plan in Lync Server 2013](lync-server-2013-create-a-dial-plan.md)  
[Modify a dial plan in Lync Server 2013](lync-server-2013-modify-a-dial-plan.md)  
[Publish pending changes to the voice routing configuration in Lync Server 2013](lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md)  


[Test voice routing in Lync Server 2013](lync-server-2013-test-voice-routing.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

