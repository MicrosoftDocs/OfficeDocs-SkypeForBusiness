---
title: 'Lync Server 2013: Create a voice routing test case'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Create a voice routing test case
ms:assetid: 43a07a5b-2f20-462a-81e5-d628c18391e0
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425935(v=OCS.15)
ms:contentKeyID: 48183979
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Create a voice routing test case in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-02-07_

<div>

## To create a test case

1.  Log on to the computer as a member of the RTCUniversalServerAdmins group, or as a member of the CsVoiceAdministrator, CsServerAdministrator, or CsAdministrator role. For details, see [Delegate setup permissions in Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Voice Routing** and then click **Test Voice Routing**.

4.  On the **Test Voice Routing** page, click **New** to create a new test case.

5.  In **Name**, type in a unique name for the test case.
    
    The name must be unique among all voice routing test cases in your Enterprise Voice deployment. It can be up to 32 characters in length and may contain any alphanumeric characters, in addition to the backslash (\\), period (.), or underscore (\_).

6.  In **Dialed number to test**, type in the dialed number that you want to use to test the routing configuration that you specify for this test case. Based on the dial plan, route, and voice policy, this number will be normalized and displayed as output.

7.  In the **Dial Plan** list, select the dial plan to use when running the test. Default is the Global dial plan.

8.  In the **Voice Policy** list, select the voice policy to use when running the test. Default is the Global voice policy.

9.  In **Expected translation**, type in the phone number in the format you expect to see it after translation. This is the value of the phone number that you are testing after it has been translated by the first normalization rule that matches in the selected dial plan. When you run the test case, if the number you are testing does not result in the value in **Expected translation**, the test fails.

10. (Optional) In the **Expected PSTN usage** list, you can select the public switched telephone network (PSTN) usage record that you expect to be used when you run the test case, based on the specified dial plan and voice policy. If a different PSTN usage record is used, the test fails.

11. (Optional) In the **Expected route** list, you can select the voice route that you expect to be used when you run the test case, based on the specified dial plan and voice policy. If a different voice route is used, the test fails.

12. (Optional) Click **Run** to run the test case. The results are shown in the right panel of the page.

13. Click **OK**.

14. Click **Commit**, and then click **Commit all**.
    
    <div>
    

    > [!NOTE]  
    > Whenever you create a voice routing test case, you must run the <STRONG>Commit all</STRONG> command to publish the configuration change. For details, see <A href="lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md">Publish pending changes to the voice routing configuration in Lync Server 2013</A> in the Operations documentation.

    
    </div>
    
    If the dial plan being employed in the test normalizes phone numbers that begin with a plus sign (for example, +12065551219), that plan might cause the voice routing test to fail. (The dial plan and the voice route will work; in fact, Test-CsDialPlan will succeed. However, the voice routing test might fail.) This is something to keep in mind when testing voice routes.

</div>

<div>

## See Also


[Export voice routing test cases in Lync Server 2013](lync-server-2013-export-voice-routing-test-cases.md)  
[Import voice routing test cases in Lync Server 2013](lync-server-2013-import-voice-routing-test-cases.md)  


[Configuring dial plans in Lync Server 2013](lync-server-2013-configuring-dial-plans.md)  
[Configuring voice policies, PSTN usage records, and voice routes in Lync Server 2013](lync-server-2013-configuring-voice-policies-pstn-usage-records-and-voice-routes.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

