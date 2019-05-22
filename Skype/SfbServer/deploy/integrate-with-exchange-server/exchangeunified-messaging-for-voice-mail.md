---
title: "Configure Exchange Server Unified Messaging for Skype for Business Server voice mail"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 2/11/2019
audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: 1be9c4f4-fd8e-4d64-9798-f8737b12e2ab
description: "Summary: Configure Exchange Server Unified Messaging for Skype for Business Server voice mail."
---

# Configure Exchange Server Unified Messaging for Skype for Business Server voice mail
 
**Summary:** Configure Exchange Server Unified Messaging for Skype for Business Server voice mail.
  
Skype for Business Server enables you to have voicemail messages stored in Exchange Server 2016 or Exchange Server 2013; those voicemail messages will then appear as email messages in your users' Inboxes. 

> [!NOTE]
> Exchange Unified Messaging as previously known is no longer available in Exchange 2019, but you can still use Phone System to record voicemail messages and then leave the recording in a user's Exchange mailbox. See [Plan Cloud Voicemail service](../../../sfbhybrid/hybrid/plan-cloud-voicemail.md) for more information.
  
If you have already configured server-to-server authentication between Skype for Business Server and Exchange Server 2016 or Exchange Server 2013, then you are ready to setup unified messaging. To do so, you must first create and assign a new unified messaging dial plan on your Exchange Server. For example, these two commands (run from within the Exchange Management Shell) configure a new 3-digit dial plan for Exchange:
  
```
New-UMDialPlan -Name "RedmondDialPlan" -VoIPSecurity "Secured" -NumberOfDigitsInExtension 3 -URIType "SipName" -CountryOrRegionCode 1
Set-UMDialPlan "RedmondDialPlan" -ConfiguredInCountryOrRegionGroups "Anywhere,*,*,*" -AllowedInCountryOrRegionGroups "Anywhere"
```

In the first command in the example, the VoIPSecurity parameter, and the parameter value "Secured" indicates that the signaling channel is encrypted by using Transport Layer Security (TLS). The URIType "SipName" indicates that messages will be sent and received using the SIP protocol, and the CountryOrRegionCode of 1 indicates that the dial plan applies to the US.
  
In the second command, the parameter value passed to the ConfiguredInCountryOrRegionGroups parameter specifies the in-country groups that can be used with this dial plan. The parameter value "Anywhere,\*,\*,\*" sets the following:
  
- Group name ("Anywhere")
    
- AllowedNumberString (\*, a wildcard character indicating that any number string is allowed)
    
- DialNumberString (\*, a wildcard character indicating that any dialed number is allowed)
    
- TextComment (\*, a wildcard character indicating that any text command is allowed)
    
> [!NOTE]
> Creating a new dial plan will also create a Default Mailbox Policy. 
  
After creating and configuring the new dial plan you must add the new dial plan to your unified messaging server and then modify the startup mode of that server; in particular, you must set the startup mode to "Dual". You can perform both of these tasks from within the Exchange Management Shell:
  
```
Set-UmService -Identity "atl-exchangeum-001.litwareinc.com" -DialPlans "RedmondDialPlan" -UMStartupMode "Dual"
```

After the unified messaging server has been configured you should next run the Enable-ExchangeCertificate cmdlet to ensure that your Exchange certificate is applied to the unified messaging service:
  
```
Enable-ExchangeCertificate -Server "atl-umserver-001.litwareinc.com" -Thumbprint "EA5A332496CC05DA69B75B66111C0F78A110D22d" -Services "SMTP","IIS","UM"
```

After the certificate has been correctly assigned you must then stop and restart the MsExchangeUM service on the unified messaging server. This service must be stopped and restarted any time you change the startup mode.
  
After finishing configuration of the unified messaging server you can then configure the UM Call Router:
  
```
Set-UMCallRouterSettings -Server "atl-exchange-001.litwareinc.com" -UMStartupMode "Dual" -DialPlans "RedmondDialPlan" 
Enable-ExchangeCertificate -Server "atl-umserver-001.litwareinc.com" -Thumbprint "45BAA32496CC891169B75B9811320F78A1075DDA" -Services "IIS","UMCallRouter"
```

Because the startup mode has changed you must stop and restart the MsExchangeUMCR service on the computer hosting the UM Call Router.
  
To complete the unified messaging setup, you then need to create a UM mailbox policy and then use that policy to enable users for unified messaging. You can create a mailbox policy by using a command similar to this:
  
```
New-UMMailboxPolicy -Name "RedmondMailboxPolicy" -AllowedInCountryOrRegionGroups "Anywhere"
```

And you can enable a user for unified messaging by using a command similar to this:
  
```
Enable-UMMailbox -Extensions 100 -SIPResourceIdentifier "kenmyer@litwareinc.com" -Identity "litwareinc\kenmyer" -UMMailboxPolicy "RedmondMailboxPolicy"
```

In the preceding command, the Extensions parameter represents the telephone extension number for the user. In this example, the user has the extension number 100.
  
After you have enabled his mailbox, the user kenmyer@litwareinc.com should be able to use Exchange unified messaging. You can verify that the user can connect to Exchange UM by running the [Test-CsExUMConnectivity](https://docs.microsoft.com/powershell/module/skype/test-csexumconnectivity?view=skype-ps) cmdlet from within the Skype for Business Server Management Shell:
  
```
$credential = Get-Credential "litwareinc\kenmyer"
Test-CsExUMConnectivity -TargetFqdn "atl-cs-001.litwareinc.com" -UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $credential
```

If you have a second user who has been enabled for unified messaging you can use the [Test-CsExUMVoiceMail](https://docs.microsoft.com/powershell/module/skype/test-csexumvoicemail?view=skype-ps) cmdlet to verify that this second user can leave a voicemail message for the first user.
  
```
$credential = Get-Credential "litwareinc\pilar"
Test-CsExUMVoiceMail -TargetFqdn "atl-cs-001.litwareinc.com" -ReceiverSipAddress "sip:kenmyer@litwareinc.com" -SenderSipAddress "sip:pilar@litwareinc.com" -SenderCredential $credential
```



## Configuring Unified Messaging on Microsoft Exchange Server 
> [!IMPORTANT]
> If you want to use Exchange Unified Messaging (UM) to provide call answering, Outlook Voice Access, or auto-attendant services for Enterprise Voice users, read [Plan for Exchange Unified Messaging integration in Skype for Business](../../plan-your-deployment/integrate-with-exchange/unified-messaging.md), and then follow the instructions in this section. 

To configure Exchange Unified Messaging (UM) to work with Enterprise Voice, you’ll need to perform the following tasks:

- Configure certificates on the server running Exchange Unified Messaging (UM) services
  > [!NOTE]
  > Add all Client Access and Mailbox servers to all UM SIP URI dial plans. If not, outbound call routing won’t work as expected. 
- Create one or more UM SIP URI dial plans, along with the subscriber access phone numbers, as needed, and then create corresponding L dial plans.

- Use the exchucutil.ps1 script to:
    - Create UM IP gateways.
    - Create UM hunt groups.
    - Grant Skype for Business Server permission to read UM Active Directory Domain Services objects.
- Create a UM auto-attendant object.
- Create a subscriber access object.
- Create a SIP URI for each user and associating users with a UM SIP URI dial plan.

### Requirements and Recommendations

Before you begin, the documentation in this section assumes that you have deployed the following Exchange roles: Client Access and Mailbox. In Microsoft Exchange Server, Exchange UM runs as a service on these servers.

Also note the following:
- If Exchange UM is installed in multiple forests, the Exchange Server integration steps must be performed for each UM forest. In addition, each UM forest must be configured to trust the forest in which Skype for Business Server is deployed, and the forest in whichSkype for Business Server is deployed must be configured to trust each UM forest.
- Integration steps are performed on both the Exchange Server roles where Unified Messaging services are running, and on the server running Skype for Business Server. You should perform the Exchange Server Unified Messaging integration steps before you perform the Lync Server 2013 integration steps.
  > [!NOTE]
  > To see which integration steps are performed on which servers and by which administrator roles, see  [Deployment process overview for integrating on-premises Unified Messaging and Skype for Business](../../plan-your-deployment/integrate-with-exchange/deployment-overview.md). 

The following tools must be available on each server running Exchange UM:
- Exchange Management Shell
- The script exchucutil.ps1, which performs the following tasks:
    - Creates a UM IP gateway for each Skype for Business Server.
    - Creates a hunt group for each gateway. The pilot identifier of each hunt group specifies the UM SIP URI dial plan used by the Front End pool or Standard Edition server that is associated with the gateway.
    - Grants Skype for Business Server permission to read Exchange UM objects in Active Directory Domain Services.



### Configure Unified Messaging on Microsoft Exchange with ExchUCUtil.ps1 

When you’re integrating Microsoft Skype for Business Server with Exchange Unified Messaging (UM), you have to run the ExchUcUtil.ps1 script in the Shell. The ExchUcUtil.ps1 script does the following:

- Creates a UM IP gateway for each Skype for Business Server pool.

> [!IMPORTANT]
> The ExchUcUtil.ps1 script creates one or more UM IP gateways. You must disable outgoing calls on all UM IP gateways except one gateway that the script created. This includes disabling outgoing calls on UM IP gateways that were created before you ran the script. 

- Creates a UM hunt group for each UM IP gateway. The pilot identifier of each hunt group specifies the UM SIP URI dial plan used by the Skype for Business Server Front End pool or Standard Edition server that’s associated with the UM IP gateway.
- Grants Skype for Business Server permission to read Active Directory UM container objects such as UM dial plans, auto attendants, UM IP gateways, and UM hunt groups.
  > [!IMPORTANT]
  > Each UM forest must be configured to trust the forest in which Skype for Business Server is deployed, and the forest in which Skype for Business Server 2013 is deployed must be configured to trust each UM forest. If Exchange UM is installed in multiple forests, the Exchange Server integration steps must be performed for each UM forest or you’ll have to specify the Skype for Business Server domain. For example, ExchUcUtil.ps1 –Forest:<lync-domain-controller-fqdn>. 

### Use the Shell to run the ExchUcUtil.ps1 script

Run the ExchUcUtil.ps1 script on any Exchange server in your organization that’s in the same topology as Skype for Business Server. You can run the script from a Mailbox server using the Shell or you can run the script using Remote Windows PowerShell on a Client Access server. If you run the script on a Client Access server in your organization, the Client Access server will proxy the Remote Windows PowerShell session to a Mailbox server in the organization.
> [!IMPORTANT]
> The ExchUcUtil.ps1 script creates one or more UM IP gateways. You must disable outgoing calls on all UM IP gateways except one gateway that the script created. This includes disabling outgoing calls on UM IP gateways that were created before you ran the script. To disable outgoing calls on a UM IP gateway, see Disable outgoing calls on UM IP gateways. 
> [!IMPORTANT]
> You must have the permissions of the Exchange Organization Management role or be a member of the Exchange Organization Administrators security group to run the script. 

1. Open the Exchange Management Shell.
2. At the C:\Windows\System32 prompt, type **cd \<drive letter>:\Program Files\Microsoft\Exchange Server\V15\Scripts>.ExchUcUtil.ps1**, and then press Enter.

#### How do you know this worked?

To verify that the ExchUcUtul.ps1 script completed successfully, do the following:
- Use the Get-UMIPGateway cmdlet or the EAC to view the new UM IP gateway or gateways that were created.
- Use the Get-UMHuntGroup cmdlet or the EAC to view the new UM hunt group or groups that were created.

### Configure certificates on the server running Exchange Server Unified Messaging
 
If you have deployed Exchange Unified Messaging (UM), as described in Planning for Exchange Unified Messaging integration in Skype for Business Server in the Planning documentation, and you want to provide Exchange UM features to Enterprise Voice users in your organization, you can use the following procedures to configure the certificate on the server running Exchange UM.

> [!IMPORTANT]
> For internal certificates, both the servers running Skype for Business Server and the servers running Microsoft Exchange must have trusted root authority certificates that are mutually trusted. The certification authority (CA) can either be the same, or a different certification authority, as long as the servers have the certification authority’s root certificate registered in their trusted root authority certificate store. 

The Exchange Server must be configured with a server certificate in order to connect to Skype for Business Server:
1. Download the CA certificate for the Exchange Server.
2. Install the CA certificate for the Exchange Server.
3. Verify that the CA is in the list of trusted root CAs of the Exchange Server.
4. Create a certificate request for the Exchange Server and install the certificate. 
5. Assign the certificate for the Exchange Server.


**To download the CA certificate:**

1. On the server running Exchange UM, click **Start**, click **Run**, type **http://\<name of your Issuing CA Server>/certsrv**, and then click **OK**.
2. Under Select a task, click **Download a CA certificate, certificate chain, or CRL**.
3. Under **Download a CA Certificate, Certificate Chain, or CRL**, select **Encoding Method to Base 64**, and then click**Download CA certificate**.
   > [!NOTE]
   > You can also specify Distinguished Encoding Rules (DER) encoding at this step. If you select DER encoding, the file type in the next step of this procedure and in step 10 of **To Install the CA certificate** is .p7b rather than .cer. 
4. In the **File Download** dialog box, click **Save**, and then save the file to the hard disk on the server. (The file will have either a .cer or a .p7b file extension, depending on the encoding that you selected in the previous step.)

**To install the CA certificate:**

1. On the server running Exchange UM, open Microsoft Management Console (MMC) by clicking **Start**, clicking **Run**, typing **mmc** in the Open box, and then clicking **OK**.
2. On the **File** menu, click **Add/Remove Snap-in**, and then click **Add**.
3. In the **Add Standalone Snap-ins** box, click **Certificates**, and then click **Add**.
4. In the **Certificate snap-in** dialog box, click **Computer account**, and then click **Next**.
5. In the **Select Computer** dialog box, verify that the **Local computer: (the computer this console is running on)** check box is selected, and then click **Finish**.
6. Click **Close**, and then click **OK**. 
7. In the console tree, expand **Certificates (Local Computer)**, expand **Trusted Root Certification Authorities**, and then click **Certificates**.
8. Right-click **Certificates**, click **All Tasks**, and click **Import**.
9. Click **Next**. 
10. Click **Browse** to locate the file, and then click **Next**. (The file will have either a .cer or a .p7b file extension, depending on the encoding that you selected in step 3 of **To download the CA certificate**.
11. Click **Place All Certificates** in the following store.
12. Click **Browse**, and then select **Trusted Root Certification Authorities**. 
13. Click **Next** to verify the settings, and then click **Finish**. 


**To verify that the CA is in the list of trusted root CAs:**

1. On the server running Exchange UM, in MMC expand Certificates (Local Computer), expand Trusted Root Certification Authorities, and then click Certificates.
2. In the details pane, verify that your CA is on the list of trusted CAs.


