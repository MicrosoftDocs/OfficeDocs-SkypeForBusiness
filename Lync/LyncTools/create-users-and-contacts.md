---
title: Create Users and Contacts
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Create Users and Contacts
ms:assetid: 04b24d07-2864-463d-b508-544c2674c4ab
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ945587(v=OCS.15)
ms:contentKeyID: 51541412
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Create Users and Contacts

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-22_

You must use the Lync Server 2013 User Provisioning Tool (UserProvisioningTool.exe) to create users and contacts in preparation for stress and performance load testing.

Here is a list of terms and definitions that you might find useful as you read through this topic.

  - Organizational Unit – The Active Directory Domain Services organizational unit (OU).

  - Federated / Cross Pool – Users who will be enabled to communicate with users from other Instant Messaging (IM) services, such as MSN network of Internet services, AOL®, and Yahoo\!®.

  - Distribution Lists – The objects in Active Directory Domain Services that contain a list of Active Directory Domain Services users, used for launching communications with groups of people.

  - Location Info Service – The Lync Server 2013 service that, when enabled and configured per phone, enables retrieval of physical location for Enhanced 9-1-1 (E9-1-1) services.

  - U.S. Phone Numbers – The phone numbers that are assigned to users, in addition to the SIP URI that is used for routing inbound and outbound calls and reverse number lookup (RNL).

<div>

## Create Users and Contacts by Using UserProvisioningTool.exe

You must use the Lync Server User Provisioning Tool to create users and contacts for load simulation. The Lync Server User Provisioning Tool is installed with the Lync Server Stress and Performance Tool package. Be sure that the package installer (CapacityPlanningTool.msi) has been run on the Front End Server or the Standard Edition server. Start the Lync Server User Provisioning Tool by running the file UserProvisioningTool.exe (located at %InstalledDirectory%LyncStressAndPerfTool\\LyncStress) on the Front End Server or on the Standard Edition server.

<div>


> [!IMPORTANT]  
> You must be logged on as a member of the Domain Admins security group in order to run UserProvisioningTool.exe. It is necessary to run from this context because UserProvisioningTool.exe will be creating and configuring new Active Directory Domain Services users.



</div>

<div>


> [!NOTE]  
> When you create a significant number of users (10,000 or more), run UserProvisioningTool.exe from a high-end computer. Note that the domain controller will also experience high load while the users are being created.



</div>

When the Lync Server User Provisioning Tool opens, click **Configuration** and select **Load Configuration**. To begin configuring users and contacts, load the default file that is included in the package, SampleData.xml. This will prepopulate the fields with example data that you'll need to revise for your system. If you have a preconfigured XML file that already contains customized settings, load that file instead. Fill in the fields in the Lync Server User Provisioning Tool, as described in the following sections.

![User Creation tab.](images/JJ945587.80d3c17b-7482-4818-8381-1eff8717d2fe(OCS.15).jpg "User Creation tab.")

To configure server options, follow these steps.

1.  In **Front End Pool FQDN**, type the fully qualified domain name (FQDN) of the Standard Edition server or Front End pool where you want to host the users.

2.  In **User Name Prefix**, type a prefix that you want to use to build user names for testing purposes.

3.  In **Password**, specify a password that will be applied for all of the test user accounts.

4.  In **SIP Domain**, type the domain name to be used for test users’ SIP URIs (Uniform Resource Identifiers).

5.  In **Account Domain**, type the domain name of your current Active Directory Domain Services domain, under which you want to create the test users.

6.  In **Organizational Unit**, type the name of the Active Directory Domain Services OU where you want to create the User objects. If the OU does not exist, it will be created.

7.  In **Phone Area Code**, type the three-digit area code that will be used for test user accounts. Be sure that phone area code does not conflict with any other users’ area codes in Active Directory Domain Services.

8.  Select the **Voice Enabled** check box if you want to enable the test users for Enterprise Voice.

9.  In **Number of Users**, specify the total number of test users that you want to create.

10. In **Start Index**, specify the starting number that will be used as suffix to the user name prefix.

<div>

## Create Users Button

When you click on the Create Users button, it will validate all the input parameters.

  - If there are any validation errors, it will prompt you to correct those input values.

  - If all the input values are correct, it will start creating users in Active Directory Domain Services. A progress bar will appear at the bottom of this form. We recommend that you do not close the application while the progress bar is active.

User Creation is a slow process. It can take several minutes. If the number of users is very large, the process could even take a few hours. If the users already exist, they are updated with any changes. You can validate that the users were created by logging on as one of the users in the range. Use the user prefix, user number, and @sipDomain as the user name (for example, LyncUser10@contoso.net), along with the specified password.

</div>

<div>

## Delete Users Button

When you click on Delete Users button, it will validate all the input parameters.

  - If there are any validation errors, it will prompt you to correct those input values.

  - If all the input values are correct, it will start disabling and deleting users in Active Directory Domain Services. A progress bar will appear at the bottom of this form. We recommend that you do not close the application while the progress bar is active.

<div>


> [!NOTE]  
> <OL>
> <LI>
> <P>Only U.S.-formatted phone numbers are supported. Phone numbers are always assigned to users, and all users created by UserProvisioningTool.exe are enabled for Enterprise Voice. Any scenarios that use the phone number, such as Conferencing Auto Attendant or UC-PSTN calls, use this phone number to properly route calls. For this reason, every user must have a unique phone number. If you have to create users twice, the command will fail unless you use a different area code, or if the previous users have been disabled by using the <STRONG>Disable-CsUser</STRONG> cmdlet.</P>
> <LI>
> <P>Before you create contacts, you must first complete user replication, performed from the Users tab. If you have just created your users, you must wait until Lync Server replication completes and populates the user accounts in the database. If the users have not finished replicating, you will see an error. You will know when users have finished replicating if Lync Server 2013 Front End service has started, or by successfully running the <STRONG>Get-CsUser</STRONG> cmdlet on the last user.</P></LI></OL>



</div>

</div>

</div>

<div>

## Contacts Creation Tab

The Contacts Creation tab enables you to specify details for users’ contacts.

![Contacts Creation tab.](images/JJ945587.7508726e-83e6-4878-8edd-114543d9af24(OCS.15).jpg "Contacts Creation tab.")

To configure users’ contacts, follow these steps.

1.  In Average Contacts per User, specify the average number of contacts to populate in contact lists for each of the users.

2.  Select the Fixed check box if you want to create an equal number of contacts for every user. If you want to vary the number of contacts created for users, clear the check box.

3.  In Average Contact Groups per User, specify the number of contact groups per user. This number must be smaller than Average Contacts per User.

4.  In Federated / Cross Pool Contacts Percentage, specify a number between 0 and 100. This percentage of contacts will be created with the federated users.

5.  In Federated / Cross Pool User Prefix, specify the username for federated users that will be added to the contact lists of local users.

6.  In Federated / Cross Pool User SIP Domain, specify the SIP Domain Name of the federated users.
    
    <div>
    

    > [!NOTE]  
    > None of the users should be signed in when creating contacts.

    
    </div>

7.  In User Creation tab, verify that the parameters are correct. The range of users for which contacts will be created is obtained from the User Creation tab.

8.  Click Create Contacts to begin the contact creation. This process can take several minutes. After it completes, a dialog box will appear with the message, "Operation Completed Successfully." You can validate the contacts that were created by logging on as a user that was created from the User Creation tab.
    
    <div>
    

    > [!NOTE]  
    > After the contacts are created, this tool will restart all the Front End Servers in the target pool. It may take longer (up to 2 hours) for the Front End Servers to start, depending on how many contacts were created by this operation.

    
    </div>

</div>

<div>

## Distribution List

One of the features of the Lync Server 2013 Stress and Performance Tool is to simulate the distribution list (DL) expansion feature in Lync 2013. If you are not going to enable DL expansion in UserProvisioningTool, you can skip this step.

![Distribution List Creation tab.](images/JJ945587.0a1d681b-2aea-4724-90d8-efa8a526f600(OCS.15).jpg "Distribution List Creation tab.")

The Distribution List tab enables you to create DLs that the Stress and Performance Tool will use for Distribution List Expansion feature. Prior to creating DLs, Lync Server 2013 must already be installed. You must have run Lync Server 2013 ForestPrep. Otherwise, the DL attributes do not exist in the Active Directory Domain Services schema and the tool will not be able to create DLs.

To configure distribution lists, follow these steps.

1.  In Number of Distribution Lists, specify the total number of DLs that you want to create. (We recommend that you start with twice the number of users). They are numbered from 0 to n-1.

2.  In Distribution List Prefix, specify the prefix that the DLs will have. For example if you specify 100 DLs and a prefix of testDL, the DLs will be named testDL0, testDL1, and so on, through testDL99.

3.  In Minimum Members in a Dist. List, specify the minimum number of users to add in each Distribution List.

4.  In Maximum Members in a Dist. List, specify the maximum number of users to add in each Distribution List.

<div>

## Create Distribution Lists Button

When you click the Create Distribution Lists button, the tool queries Active Directory Domain Services to see if distribution lists matching the prefix and numbers already exist. The tool will create only the ones that do not already exist. When adding members to these newly created Distribution Lists, it will pick the users from the range specified on the User Creation tab.

</div>

</div>

<div>

## Location Info Service Config Tab

One of the features of the Lync Server 2013 Stress and Performance Tool is to generate dummy configuration files for the Location Information Service. The Location Information Service typically does not have any significant performance impact on the servers.

![Location Info Service Config tab.](images/JJ945587.52ea4e9e-d50a-4dc9-982b-31ee5ace4578(OCS.15).jpg "Location Info Service Config tab.")

If you choose to test this feature, you can fill in the values mentioned in the form and then click the Generate LIS Config Files button. It will generate CSV files called LIS\_Subnet.csv, LIS\_Switches.csv, LIS\_Ports.csv, and LIS\_WAP.csv. You can then import these CSV files into LIS database by using the **Set-CsLisSubnet** cmdlet, the **Set-CsLisSwitch** cmdlet, the **Set-CsLisPort** cmdlet, and the **Set-CsWirelessAccessPoint** cmdlet, respectively.

</div>

</div>

<span> </span>

</div>

</div>

</div>

