---
title: 'Configuring an on-premises partner application for Lync Server 2013'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configuring an on-premises partner application for Lync Server 2013
ms:assetid: 696f2b26-e5d0-42b5-9785-a26c2ce25bb7
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204975(v=OCS.15)
ms:contentKeyID: 48184412
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring an on-premises partner application for Microsoft Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-04_

After you have assigned the OAuthTokenIssuer certificate you must then configure your Microsoft Lync Server 2013 partner applications. (The procedure about to be discussed configures both Microsoft Exchange Server 2013 and Microsoft SharePoint to act as partner applications.) To configure an on-premises partner application, you must start by copying the following Windows PowerShell script and pasting the code into Notepad (or any other text editor):

    if ((Get-CsPartnerApplication -ErrorAction SilentlyContinue) -ne $Null)
       {
           Remove-CsPartnerApplication app
       }
    
    $exch = Get-CsPartnerApplication microsoft.exchange -ErrorAction SilentlyContinue
            
    if ($exch -eq $null)
       {
          New-CsPartnerApplication -Identity microsoft.exchange -MetadataUrl https://atl-exchange-001.litwareinc.com/autodiscover/metadata/json/1 -ApplicationTrustLevel Full 
        }
    else
        {
           if ($exch.ApplicationIdentifier -ne "00000002-0000-0ff1-ce00-000000000000")
              {
                 Remove-CsPartnerApplication microsoft.exchange
    New-CsPartnerApplication -Identity microsoft.exchange -MetadataUrl https://atl-exchange-001.litwareinc.com/autodiscover/metadata/json/1 -ApplicationTrustLevel Full 
               }
            else
               {
                 Set-CsPartnerApplication -Identity microsoft.exchange -ApplicationTrustLevel Full 
               }
         }
    
    $shp = Get-CsPartnerApplication microsoft.sharepoint -ErrorAction SilentlyContinue
            
    if ($shp -eq $null)
       {
          New-CsPartnerApplication -Identity microsoft.sharepoint -MetadataUrl http://atl-sharepoint-001.litwareinc.com/jsonmetadata.ashx -ApplicationTrustLevel Full 
        }
    else
        {
           if ($shp.ApplicationIdentifier -ne "00000003-0000-0ff1-ce00-000000000000")
              {
                 Remove-CsPartnerApplication microsoft.sharepoint
      
                 New-CsPartnerApplication -Identity microsoft.sharepoint -MetadataUrl http://atl-sharepoint-001.litwareinc.com/jsonmetadata.ashx -ApplicationTrustLevel Full 
               }
            else
               {
                 Set-CsPartnerApplication -Identity microsoft.sharepoint -ApplicationTrustLevel Full 
                }
       }
    
    Set-CsOAuthConfiguration -ServiceName 00000004-0000-0ff1-ce00-000000000000

After copying the code, save the script using a .PS1 file extension (for example, C:\\Scripts\\ServerToServerAuth.ps1). Note that, before you run this script, you must replace the metadata URLs https://atl-exchange-001.litwareinc.com/autodiscover/metadata/json/1 and http://atl-sharepoint-001.litwareinc.com/jsonmetadata.ashx with the metadata URLs used by your Exchange 2013 and SharePoint servers, respectively. See the product documentation for Exchange 2013 and SharePoint for information on how you can identify the respective product's metadata URL.

If you look at the last line of the script you will notice that the Set-CsOAuthConfiguration cmdlet is called using this syntax:

    Set-CsOAuthConfiguration -ServiceName 00000004-0000-0ff1-ce00-000000000000

Because the Realm parameter was not used when calling Set-CsOAuthConfiguration the realm will automatically be set to the fully qualified domain name (FQDN) of your organization (for example, litwareinc.com). If your realm name is different from your organization name then you should include the realm name, like this:

    Set-CsOAuthConfiguration -ServiceName 00000004-0000-0ff1-ce00-000000000000 -Realm "contoso.com"

After making these changes you can then execute the script, and configure both Exchange 2013 and SharePoint as partner applications, by running the script file from within the Lync Server 2013 Management Shell. For example:

    C:\Scripts\ServerToServerAuth.ps1

Note that you can run this script even if you do not have both Exchange 2013 and SharePoint Server installed:, no problems will occur if you, say, configure SharePoint Server as a partner application even though you do not have SharePoint Server installed.

When you run this script you might receive an error message similar to the following:

    New-CsPartnerApplication : Cannot bind parameter 'MetadataUrl' to the target. Exception setting "MetadataUrl": "The metadata document could not be downloaded from the URL in the MetadataUrl parameter or downloaded data is not a valid metadata document."

This error message typically means one of two things: 1) that one of the URLs specified in the script is not valid (that is, one of your metadata URLs is not an actual metadata URL); or, 2) one of the metadata URLs could not be contacted. If this happens, verify that the URLs are correct and are accessible, and the re-run the script.

After creating the partner application for Lync Server 2013 you must then configure Lync Server to be a partner application for Exchange 2013. You can configure partner applications for Exchange 2013 by running the script Configure-EnterprisePartnerApplication.ps1; all you need to do is specify the metadata URL for Lync Server and indicate that Lync Server is the new partner application.

To configure Lync Server as a partner application for Exchange, open the Exchange Management Shell and run a command similar to this

    "c:\Program Files\Microsoft\Exchange Server\V15\Scripts\Configure-EnterprisePartnerApplication.ps1" -AuthMetadataUrl "https://lync.contoso.com/metadata/json/1" -ApplicationType "Lync"

</div>

<span> </span>

</div>

</div>

</div>

