---
title: 'Lync Server 2013: Creating or modifying a location policy'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Creating or modifying a location policy
ms:assetid: 10338418-4da4-42df-b231-f52098c08dae
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ687971(v=OCS.15)
ms:contentKeyID: 49733557
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Creating or modifying a location policy in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-11-01_

In Lync Server 2013, you can use the location policy to apply settings that relate to Enhanced 9-1-1 (E9-1-1) functionality and to location settings for users or contacts. The location policy determines whether a user is enabled for E9-1-1, and if so what the behavior is of an emergency call. For example, you can use the location policy to define what number constitutes an emergency call (for example, 911 in the United States), whether corporate security should be automatically notified, and how the call should be routed.

You can configure location policies from the **Network Configuration** group in Lync Server 2013 Control Panel. From Lync Server Control Panel you can view, create, modify, or delete location policies. Use the procedures in this section to create or modify a location policy. For details on deleting location policies, see [Deleting a location policy in Lync Server 2013](lync-server-2013-deleting-a-location-policy.md).

In Lync Server 2013, you can override the default amount of time between client requests for a location update from the Location Information service. The default value is 4 hours. Use the **Set-CsLocationPolicy** cmdlet with the LocationRefreshInterval parameter to override the default value.

<div>

## To create a new location policy in Lync Server Control Panel

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Network Configuration** and then click **Location Policy**.

4.  On the **Location Policy** page, click **New** and then select the type of policy you want to create:
    
      - To create a site policy, click **Site policy**. In **Select a Site**, choose the site to which you want the policy applied and click **OK**. On the **New Location Policy** page, the **Scope** field contains the value **Site**, and the **Name** field contains the name of the site you chose. You cannot modify either of these fields. A site policy is automatically applied to all users on the specified site and overrides the global policy for those users.
    
      - To create a **User policy**, click **User policy**. In the **New Location Policy**, the **Scope** field contains the value **User**. You cannot modify this value. In the **Name** field, type the name you want to give this policy. A user policy does not automatically apply to any users. After creating the user policy, you must manually grant the policy to the users or network sites to which you want to policy to apply.

5.  Fill in the remaining fields as follows:
    
      - **Enable enhanced emergency services**   Select this check box to enable the users associated with this policy for E9-1-1. When emergency services are enabled, Lync Server clients will retrieve location information on registration and include that information when an emergency call is made.
    
      - **Location**   Specify one of the following values:
        
          - **Required**   The user will be prompted to input location information when the client registers at a new location. The user can dismiss the prompt without entering any information. If information is entered, an emergency call will first be answered by the emergency services provider to verify the location before being routed to the Public Safety Answering Point (PSAP) operator (that is, the 911 operator).
        
          - **Not Required**   The user will not be prompted for a location. When a call is made with no location information, the emergency services provider will answer the call and ask for a location.
        
          - **Disclaimer**   This option is the same as **Required** except that the user cannot dismiss the prompt without entering location information. The user can still complete an emergency call, but no other calls can be completed without entering the information. In addition, disclaimer text will be displayed to the user that can alert them to the consequences of declining to enter location information. To set the disclaimer text, you must use Lync Server Management Shell to run the **Set-CsLocationPolicy** cmdlet or the **New-CsLocationPolicy** cmdlet with the EnhancedEmergencyServiceDisclaimer parameter. For details, see [Set-CsLocationPolicy](https://docs.microsoft.com/powershell/module/skype/Set-CsLocationPolicy) or [New-CsLocationPolicy](https://docs.microsoft.com/powershell/module/skype/New-CsLocationPolicy) in the Lync Server Management Shell documentation.
            
            <div>
            

            > [!NOTE]  
            > In Lync Server 2013, you can use location policy to set different disclaimers for different locales or different sets of users, unlike in Lync Server 2010 where you could specify only a global disclaimer for the entire organization.

            
            </div>
    
      - **Use location for emergency services only**   Lync can use location information for various reasons (for example, to notify teammates of your current location). Select this check box to ensure location information is available only for use with an emergency call.
    
      - **PSTN usage**   The public switched telephone network (PSTN) usage that will be used to determine which voice route will be used to route emergency calls from clients using this profile. The route associated with this usage should point to a SIP trunk dedicated to emergency calls or to an Emergency Location Identification Number (ELIN) gateway that routes emergency calls to the nearest Public Safety Answering Point (PSAP).
    
      - **Emergency dial number**   The number that is dialed to reach emergency services. In the United States this value is 911. The string must be made of the digits 0 through 9 and can be from 1 to 10 digits in length.
    
      - **Emergency dial mask**   A number that you want to translate into the value of the emergency dial number value when it is dialed. For example, if you enter a value of 212 in this field and the emergency dial number field has a value of 911, if a user dials 212 the call will be made to 911. This allows for alternate emergency numbers to be dialed and still have the call reach emergency services (for example, if someone from a country or region with a different emergency number attempts to dial that country or region’s number rather than the number for the country or region they are currently in). You can define multiple emergency dial masks by separating the values with semicolons. For example, 212;414. Maximum length of the string is 100 characters. Each character must be a digit 0 through 9.
        
        <div>
        

        > [!IMPORTANT]  
        > Ensure that the specified dial mask value is not the same as a number in a call park orbit range. Call park routing will take precedence over emergency dial string conversion. To see the existing call park orbit ranges, click <STRONG>Voice Features</STRONG> in the left navigation bar and then click <STRONG>Call Park</STRONG>. For details, see <A href="lync-server-2013-configure-phone-number-extensions-for-parking-calls.md">Configure phone number extensions for parking calls in Lync Server 2013</A>.

        
        </div>
    
      - **Notification URI**   One or more SIP Uniform Resource Identifiers (URIs) to be notified when an emergency call is made. For example, the company security office could be notified through an instant message whenever an emergency call is made. If the caller’s location is available that location will be included in the notification. Multiple SIP URIs can be included as a comma-separated list. For example, "sip:security@litwareinc.com","sip:kmyer@litwareinc.com". Distribution lists are supported. The string must be from 1 to 256 characters in length and must begin with the prefix "sip:". Before you click in the Notification URI field an example is displayed.
    
      - **Conference URI**   The SIP URI, in this case the telephone number, of a third party that will be conferenced in to any emergency calls that are made. For example, the company security office could receive a call when an emergency call is made and listen in or participate in that call (depending on the value supplied in the **Conference mode** field). The string must be from 1 to 256 characters in length and must begin with the prefix sip:. An example is displayed until you click inside this field.
    
      - **Conference mode**   If you specify a value in the **Conference URI** field, the **Conference mode** determines whether a third party can participate in the call or can only listen in. Specify one of the following options:
        
          - **One-way**   A third party can only listen to the conversation between the caller and the PSAP operator.
        
          - **Two-way**   A third party can listen in and participate in the call between the caller and the PSAP operator.

6.  Click **Commit**.
    
    <div>
    

    > [!IMPORTANT]  
    > When you create a user policy, initially that policy does not apply to any users or network sites. To apply the policy to a user, click <STRONG>Users</STRONG> in the left navigation bar. Find the user to which you want to apply the policy. On the <STRONG>Edit</STRONG> menu, click <STRONG>Show details</STRONG>. On the <STRONG>Edit Lync Server User</STRONG> page, select the new location policy from the <STRONG>Location policy</STRONG> drop-down list and then click <STRONG>Commit</STRONG>.<BR>To apply the policy to a network site, click <STRONG>Network Configuration</STRONG> in the left navigation bar and then click <STRONG>Site</STRONG>. Find the network site to which you want to apply the policy. On the <STRONG>Edit</STRONG> menu, click <STRONG>Show details</STRONG>. In <STRONG>Edit Site</STRONG>, select the new location policy from the <STRONG>Location policy</STRONG> drop-down list and then click <STRONG>Commit</STRONG>.

    
    </div>

</div>

<div>

## To modify a location policy in Lync Server Control Panel

1.  From a user account that is a member of the RTCUniversalServerAdmins group (or has equivalent user rights), or is assigned to the CsAdministrator role, log on to any computer in your internal deployment.

2.  Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](lync-server-2013-open-lync-server-administrative-tools.md).

3.  In the left navigation bar, click **Network Configuration** and then click **Location Policy**.

4.  On the **Location Policy** page, select the location policy that you want to modify.

5.  On the **Edit** menu, click **Show details**.

6.  On the **Edit Location Policy** page, modify the fields as necessary (for details, see Step 5 in the "To create a new location policy" procedures earlier in this topic).

7.  Click **Commit**.

</div>

<div>

## See Also


[Deleting a location policy in Lync Server 2013](lync-server-2013-deleting-a-location-policy.md)  


[Defining the location policy for Lync Server 2013](lync-server-2013-defining-the-location-policy.md)  


[Configure phone number extensions for parking calls in Lync Server 2013](lync-server-2013-configure-phone-number-extensions-for-parking-calls.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

