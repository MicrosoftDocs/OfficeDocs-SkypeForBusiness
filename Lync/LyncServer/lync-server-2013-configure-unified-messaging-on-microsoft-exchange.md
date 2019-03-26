---
title: 'Lync Server 2013: Configure Unified Messaging on Microsoft Exchange'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configure Unified Messaging on Microsoft Exchange
ms:assetid: 07547968-c59b-4dde-ace4-9fd286933759
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398129(v=OCS.15)
ms:contentKeyID: 48183311
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configure Unified Messaging on Microsoft Exchange for Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-24_

This topic describes how to configure Exchange Unified Messaging (UM) on a Microsoft Exchange Server for use with Enterprise Voice.

<div>


> [!NOTE]  
> The cmdlet examples in this topic provide syntax for the Exchange 2007 version of Exchange Management Shell. If you are running Exchange 2010 or Exchange 2013, see the appropriate documentation as referenced.



</div>

<div>

## To configure a server running Exchange Server UM

1.  Create a UM Session Initiation Protocol (SIP) Uniform Resource Identifier (URI) dial plan for each of your Enterprise Voice location profiles. If you choose to use the Exchange Management Console, create a new dial plan with the security setting **Secured (preferred)**.
    
    <div>
    

    > [!WARNING]  
    > If you set your security setting value to <STRONG>SIP Secured</STRONG> to require encryption for SIP traffic only, as previously recommended, note that this security setting on a dial plan is insufficient if the Front End pool is configured to require encryption, which means the pool requires encryption for both SIP and RTP traffic. When the dial plan and pool security settings are not compatible, all calls to Exchange UM from the Front End pool will fail, resulting in an error indicating that you have an "Incompatible security setting."

    
    </div>
    
    If you use the Exchange Management Shell, type:
    
        New-UMDialPlan -Name <dial plan name> -UriType "SipName" -VoipSecurity <SIPSecured|Unsecured|Secured> -NumberOfDigitsInExtension <number of digits> -AccessTelephoneNumbers <access number in E.164 format>
    
    For details, see:
    
      - For Office Communications Server 2007, see "How to Create a Unified Messaging SIP URI Dial Plan" at [http://go.microsoft.com/fwlink/p/?LinkId=268632](http://go.microsoft.com/fwlink/p/?linkid=268632) and "New-UMDialplan: Exchange 2007 Help" at [http://go.microsoft.com/fwlink/p/?LinkId=268666](http://go.microsoft.com/fwlink/p/?linkid=268666).
    
      - For Exchange 2010, see "Create a UM Dial Plan" at [http://go.microsoft.com/fwlink/p/?LinkId=268674](http://go.microsoft.com/fwlink/p/?linkid=268674) and "New-UMDialplan: Exchange 2010 Help" at [http://go.microsoft.com/fwlink/p/?LinkId=268680](http://go.microsoft.com/fwlink/p/?linkid=268680).
    
      - For Exchange 2013, see "Unified Messaging" at [http://go.microsoft.com/fwlink/p/?LinkID=266579](http://go.microsoft.com/fwlink/p/?linkid=266579).
    
    <div>
    

    > [!NOTE]  
    > Whether you select a security level of <STRONG>SIPSecured</STRONG> or <STRONG>Secured</STRONG> depends on whether secure real-time transport protocol (SRTP) is activated or deactivated for media encryption. For the Lync Server 2010 integration with Exchange UM, this should correspond to the encryption level in the Lync Server media configuration. The Lync Server media configuration can be viewed by running the <STRONG>Get-CsMediaConfiguration</STRONG> cmdlet. For details, see Get-CsMediaConfiguration in the Lync Server Management Shell documentation.<BR>For details about selecting the appropriate VoIP Security setting, see <A href="lync-server-2013-deployment-process-for-integrating-on-premises-unified-messaging.md">Deployment process for integrating on-premises Unified Messaging and Lync Server 2013</A>.

    
    </div>

2.  Run the following cmdlet to obtain the fully qualified domain name (FQDN) for each UM dial plan:
    
    ``` 
    (Get-UMDialPlan <dialplanname>).PhoneContext  
    ```
    
    For details, see:
    
      - For Exchange 2007, see "Get-UMDialplan: Exchange 2007 Help" at [http://go.microsoft.com/fwlink/p/?LinkId=268678](http://go.microsoft.com/fwlink/p/?linkid=268678).
    
      - For Exchange 2010, see "Get-UMDialplan: Exchange 2010 Help" at [http://go.microsoft.com/fwlink/p/?LinkId=268679](http://go.microsoft.com/fwlink/p/?linkid=268679).
    
      - For Exchange 2013, see "Unified Messaging" at [http://go.microsoft.com/fwlink/p/?LinkID=266579](http://go.microsoft.com/fwlink/p/?linkid=266579).

3.  Record the dial plan name of each UM dial plan. Depending on your version of Exchange Server, you may need to use the FQDN of each dial plan name later as the name of each UM dial plan’s corresponding Lync Server dial plan so that the dial plan names match.
    
    <div>
    

    > [!NOTE]  
    > Lync Server dial plan names must match UM dial plan names only if the UM dial plan is running on a version of Exchange <EM>earlier</EM> than Exchange 2010 SP1.

    
    </div>

4.  Add the dial plan to the server running Exchange UM as follows:
    
      - If you choose to use the Exchange Management Console, you can add the dial plan from the property sheet for the server. For specific instructions, see the Exchange Server product documentation.
        
        For Exchange 2007, see "How to Add Unified Messaging Server to a Dial Plan" at [http://go.microsoft.com/fwlink/p/?LinkId=268681](http://go.microsoft.com/fwlink/p/?linkid=268681).
        
        For Exchange 2010, see "View or Configure the Properties of a UM Server" at [http://go.microsoft.com/fwlink/p/?LinkId=268682](http://go.microsoft.com/fwlink/p/?linkid=268682).
        
        For Exchange 2013, see "Unified Messaging" at [http://go.microsoft.com/fwlink/p/?LinkID=266579](http://go.microsoft.com/fwlink/p/?linkid=266579).
    
      - If you use the Exchange Management Shell, run the following for each of your Exchange UM servers:
        
            $ums=get-umserver; 
            $dp=get-umdialplan -id <name of dial-plan created in step 1>; 
            $ums[0].DialPlans +=$dp.Identity; 
            set-umservice -instance $ums[0]
    
    <div>
    

    > [!NOTE]  
    > Before you perform the following step, make sure that all Enterprise Voice users have been configured with an Exchange Server mailbox.<BR>For Exchange 2007, see the Exchange Server 2007 TechNet Library at <A href="http://go.microsoft.com/fwlink/p/?linkid=268685">http://go.microsoft.com/fwlink/p/?LinkId=268685</A>.<BR>For Exchange 2010, see the Exchange Server 2010 TechNet Library at <A href="http://go.microsoft.com/fwlink/p/?linkid=268686">http://go.microsoft.com/fwlink/p/?LinkId=268686</A>.<BR>When specifying a mailbox policy for each dial plan that you created in step 1, select either the default policy or one that you have created.

    
    </div>

5.  Navigate to \<Exchange installation directory\>\\Scripts, and then if Exchange is deployed in a single forest, type:
    
        exchucutil.ps1
    
    Or, if Exchange is deployed in multiple forests, type:
    
        exchucutil.ps1 -Forest:"<forest FQDN>"
    
    where forest FQDN specifies the forest in which Lync Server is deployed.
    
    If you have one or more UM dial plans that are associated with multiple IP gateways, continue to step 6. If your dial plans are each associated with only a single IP gateway, skip step 6.
    
    <div>
    

    > [!IMPORTANT]  
    > Be sure to restart the <STRONG>Lync Server Front-End</STRONG> service (rtcsrv.exe) <EM>after</EM> you run exchucutil.ps1. Otherwise, Lync Server will not detect Unified Messaging in the topology.

    
    </div>

6.  Using either the Exchange Management Shell or Exchange Management Console, disable outbound calling for all but one of the IP gateways associated with each of your dial plans.
    
    <div>
    

    > [!NOTE]  
    > This step is necessary to make sure that outbound calls by the server running Exchange Server Unified Messaging to external users (for example, as is the case with play-on-phone scenarios) reliably traverse the corporate firewall.

    
    </div>
    
    <div>
    

    > [!IMPORTANT]  
    > When selecting the UM IP gateway through which to allow outgoing calls, choose the one that is likely to handle the most traffic. Do not allow outgoing traffic through an IP gateway that connects to a pool of Lync Server Directors. Also avoid pools in another central site or a branch site. You can use either of the following methods to block outgoing calls from passing through an IP gateway:

    
    </div>
    
      - If you use the Exchange Management Shell, disable each IP gateway by running the following command:
        
            Set-UMIPGateway <gatewayname> -OutcallsAllowed $false
        
        For Exchange 2007, see "Set-UMIPGateway: Exchange 2007 Help" at [http://go.microsoft.com/fwlink/p/?LinkId=268687](http://go.microsoft.com/fwlink/p/?linkid=268687).
        
        For Exchange 2010, see "Set-UMIPGateway: Exchange 2010 Help" at [http://go.microsoft.com/fwlink/p/?LinkId=268688](http://go.microsoft.com/fwlink/p/?linkid=268688).
    
      - If you use the Exchange Management Console, clear the **Allow outgoing calls through this IP gateway** check box.
    
    <div>
    

    > [!IMPORTANT]  
    > If your UM SIP URI dial plan is associated with only a single IP gateway, do not disallow outgoing calls through this gateway.

    
    </div>

7.  Create a UM auto-attendant for each Lync Server dial plan.
    
    <div>
    

    > [!IMPORTANT]  
    > Do not include any spaces in the name of the auto attendant.

    
    </div>
    
        New-umautoattendant -name <auto attendant name> -umdialplan < name of dial plan created in step 1> -PilotIdentifierList <auto attendant phone number in E.164 format> -SpeechEnabled $true -Status Enabled
    
    For details, see:
    
      - For Exchange 2007, see "New-UMAutoAttendant: Exchange 2007 Help" at [http://go.microsoft.com/fwlink/p/?LinkId=268689](http://go.microsoft.com/fwlink/p/?linkid=268689).
    
      - For Exchange 2010, see "New-UMAutoAttendant: Exchange 2010 Help" at [http://go.microsoft.com/fwlink/p/?LinkId=268690](http://go.microsoft.com/fwlink/p/?linkid=268690).
    
    The following step should be performed for each user after you have enabled Lync Server users for Enterprise Voice and know their SIP URIs.

8.  Associate Exchange UM users (each of whom should be configured with an Exchange mail box) with the UM dial plan and create a SIP URI for each user.
    
    <div>
    

    > [!NOTE]  
    > The <STRONG>SIPResourceIdentifier</STRONG> in the following sample must be the SIP address of the Lync Server user.

    
    </div>
    
        enable-ummailbox -id <user name> -ummailboxpolicy <name of the mailbox policy for the dial plan created in step 1> -Extensions <extension> -SIPResourceIdentifier "<user name>@<full domain name>" -PIN <user pin>
    
    For details, see:
    
      - For Exchange 2007, see "Enable-UMMailbox: Exchange 2007 Help" at [http://go.microsoft.com/fwlink/p/?LinkId=268691](http://go.microsoft.com/fwlink/p/?linkid=268691).
    
      - For Exchange 2010, see "Enable-UMMailbox: Exchange 2010 Help" at [http://go.microsoft.com/fwlink/p/?LinkId=268692](http://go.microsoft.com/fwlink/p/?linkid=268692).

</div>

</div>

<span> </span>

</div>

</div>

</div>

