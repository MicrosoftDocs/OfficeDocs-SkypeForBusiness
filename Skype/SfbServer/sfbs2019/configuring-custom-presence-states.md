---
title: "Configuring custom presence states in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: End User
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e17364a8-8b93-45fc-a614-c80e45435d42
description: "To define custom presence states in Lync 2013, create an XML custom presence configuration file, and then specify its location by using the Lync Server Management Shell cmdlets New-CSClientPolicy or Set-CSClientPolicy with the parameter CustomStateURL."
---

# Configuring custom presence states in Lync Server 2013
[]
To define custom presence states in Lync 2013, create an XML custom presence configuration file, and then specify its location by using the Lync Server Management Shell cmdlets **New-CSClientPolicy** or **Set-CSClientPolicy** with the parameter CustomStateURL. 
  
Configuration files have the following properties:
  
- Custom presence states can be configured with the Available, Busy, and Do Not Disturb presence indicators. 
    
- The availability attribute determines which presence indicator is associated with the status text of the custom state. In the example later in this topic, the status text Working from Home is displayed to the right of the green (Available) presence indicator.
    
- The maximum length of the status text is 64 characters.
    
- A maximum of four custom presence states can be added.
    
- The CustomStateURL parameter specifies the location of the configuration file. In Lync 2013, SIP high security mode is enabled by default, so you will need to store the custom presence configuration file on a web server that has HTTPS enabled. Otherwise, Lync 2013 clients will be unable to connect to it. For example, a valid address would be  `https://lspool.corp.contoso.com/ClientConfigFolder/CustomPresence.xml`.
    
> [!NOTE]
>  Although it is not recommended in a production environment, you can test a configuration file that is located on a non-HTTPS file share by using the EnableSIPHighSecurityMode registry setting to disable SIP high security mode on the client. Then you can use the CustomStateURL registry setting to specify a non-HTTPS location for the configuration file. Note that Lync 2013 honors Lync 2010 registry settings, but the registry hive has been updated. You would create the registry settings as follows: >  HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Office\15.0\Lync\EnableSIPHighSecurityMode >  Type: DWORD >  Value data: 0 >  HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Office\15.0\Lync\CustomStateURL >  Type: String (REG_SZ) >  Value data (examples): file://\\lspool.corp.contoso.com\LSFileShare\ClientConfigFolder\Presence.xml or file:///c:/LSFileShare/ClientConfigFolder/Group_1_Pres.xml 
  
Localize your custom presence state by specifying one or more locale ID (LCID) schema in the XML configuration file. The example later in this topic shows localization into English - United States (1033), Norwegian - Bokmål (1044), French - France (1036), and Turkish (1055). For a list of LCIDs, see Locale IDs Assigned by Microsoft at [ https://go.microsoft.com/fwlink/p/?linkid=157331 ](https://go.microsoft.com/fwlink/p/?linkid=157331).
  
## To add custom presence states to Lync 2013

1. Create an XML configuration file that uses the format of the following example:
    
  ```
  <?xml version="1.0"?>
  <customStates xmlns="http://schemas.microsoft.com/09/2009/communicator/customStates">
    <customState ID="1" availability="online">
      <activity LCID="1033">Working from Home</activity>
      <activity LCID="1044">activity 2 for 1044</activity>
      <activity LCID="1055">activity 3 for 1055</activity>
    </customState>
    <customState ID="2" availability="busy">
      <activity LCID="1033">In a Live Meeting</activity>
      <activity LCID="1036">Equivalent French String for - In a Live Meeting </activity>
    </customState>
    <customState ID="3" availability="busy">
      <activity LCID="1033">Meeting with Customer</activity>
      <activity LCID="1055">meeting with client</activity>
      <activity LCID="1036">Equivalent French String for - Meeting with Customer</activity>
    </customState>
    <customState ID="4" availability="do-not-disturb">
      <activity LCID="1033">Interviewing</activity>
    </customState>
  </customStates>
  ```

2. Save the XML configuration file to a web server with HTTPS enabled. In this example, the file is named Presence.xml and saved to the location https://lspool.corp.contoso.com/ClientConfigFolder/CustomPresence.xml.
    
3. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
4. In the Lync Server Management Shell, define the location of your XML configuration file by using a command similar to the following: 
    
  ```
  New-CsClientPolicy -Identity ContosoCustomStates 
  -CustomStateURL "https://lspool.corp.contoso.com/ClientConfigFolder/CustomPresence.xml"
  ```

5. Use the **Grant-CSClientPolicy** cmdlet to assign this new policy to users. 
    
For details, see [New-CsClientPolicy](new-csclientpolicy.md) and [Grant-CsClientPolicy](grant-csclientpolicy.md) in the Lync Server Management Shell documentation. 
  
> [!NOTE]
>  By default, Lync Server 2013 updates client policies and settings every three hours. >  If you want to continue using Group Policy settings from previous releases, such as CustomStateURL, Lync 2013 will recognize the settings if they are located in the new policy registry hive (HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Office\15.0\Lync). However, server-based client policies take precedence. > 
  

