---
title: "Troubleshooting Skype for Business Online sign-in errors for administrators"
ms.reviewer: 
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.topic: article
ms.assetid: cdd4801a-2fe1-4aab-bbb6-db5f95f972d1
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
search.appverid: MET150
ms.collection: Adm_Skype4B_Online
ms.audience: Admin
appliesto:
- Skype for Business
localization_priority: Priority
f1keywords: None
ms.custom:
- Setup
description: "Learn common causes for Skype for Business Online sign-errors and Work through troubleshooting these problems. "
---

# Troubleshooting Skype for Business Online sign-in errors for administrators

To troubleshoot Skype for Business Online sign-in errors, start by eliminating the most common causes of sign-in difficulty. If necessary, you can then follow specific resolution steps based on the type of error. If the user still cannot sign in, collect additional information, and then seek additional help.

## What do you want to do?
<a name="top"> </a>

> [Check for common causes of Skype for Business Online sign-in errors](troubleshooting-sign-in-errors-for-admins.md#toc323194094)
> 
> [Follow resolution steps for a specific error (Enterprise only)](troubleshooting-sign-in-errors-for-admins.md#toc325626440)
> 
> [Add a firewall entry for msoidsvc.exe to your proxy server](troubleshooting-sign-in-errors-for-admins.md#add-a-firewall)
> 
> [Update DNS settings](troubleshooting-sign-in-errors-for-admins.md#update-dns-service)
> 
> [Install a third-party SSL certificate on your ADFS server](troubleshooting-sign-in-errors-for-admins.md#verify-upn-and)
> 
> [Update security credentials](troubleshooting-sign-in-errors-for-admins.md#update-security-credentials)
> 
> [Modify TrustModelData registry keys](troubleshooting-sign-in-errors-for-admins.md#modify-trustmodeldata-registry)
> 
> [Update user settings in Active Directory](troubleshooting-sign-in-errors-for-admins.md#update-user-settings)
> 
> [Use the Microsoft Support troubleshooting guide](troubleshooting-sign-in-errors-for-admins.md#toc325626447)
> 
> [Collect more information and seek additional help ](troubleshooting-sign-in-errors-for-admins.md#collect-more-information)

## Check for common causes of Skype for Business Online sign-in errors
<a name="toc323194094"> </a>

Most sign-in issues can be traced to a small number of causes, and many of these are easy to correct. The table below lists some common causes of sign-in errors and some steps you or the users can take to resolve them.


| **Possible Cause**                                                                                                                                                    | **Resolution**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| During sign-in, a dialog box appears that contains the following phrase: **cannot verify that the server is trusted for your sign-in address. Connect anyway?** <br/> | Verify that the domain name in the dialog box is a trusted server in your organization—for example, **domainName.contoso.com**. Ask the user to select the **Always trust this server** check box, and then click **Connect**. <br/> Enterprise customers can prevent this message from appearing when a user signs in for the first time by modifying the Windows registry on each user's computer. For details, see [Modify TrustModelData registry keys](troubleshooting-sign-in-errors-for-admins.md#modify-trustmodeldata-registry).<br/> |
| Mistyped sign-in address, user name, or password  <br/>                                                                                                               | Confirm that the user's sign-in name and password are correct. <br/>  Verify that the user's sign-in name is formatted as follows: <strong>bobk@contoso.com</strong>. This may be different from the format you use to sign in to your organization's network.  <br/>  Ask the user to try signing in again. <br/>                                                                                                                                                                                                                             |
| Forgotten password  <br/>                                                                                                                                             | Reset the user's password and notify him or her of the new temporary password.  <br/>                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| Not licensed to use Skype for Business Online  <br/>                                                                                                                  | Confirm that the user is registered as a Skype for Business Online user. If not, register the user, and then ask him or her to sign in again.  <br/>                                                                                                                                                                                                                                                                                                                                                                                           |
| Wrong version of Skype for Business Online installed  <br/>                                                                                                           | This issue is usually associated with an error message that contains the following phrase: **the authentication service may be incompatible with this version of the program**.  <br/> Ask the user to uninstall and reinstall Skype for Business Online from the Office 365 Portal.  <br/>                                                                                                                                                                                                                                                    |
| Problem acquiring a personal certificate that is required to sign in  <br/>                                                                                           | If the user's sign-in address has recently changed, they may need to delete cached sign-in data. Ask users to sign out, click the Delete my sign-in info link on the sign-in screen, and then try again.  <br/>                                                                                                                                                                                                                                                                                                                                |
| You set up a custom domain name, and the changes may not have finished propagating through the system.  <br/>                                                         | First, ensure that you have modified the Domain Name Service (DNS) records to reflect the change.  <br/> If you have already made the necessary DNS changes, advise the user to try logging in later. DNS changes can take up to 72 hours to be reflected throughout the system.  <br/>                                                                                                                                                                                                                                                        |
| System clock out of sync with server clock  <br/>                                                                                                                     | Ensure that your network domain controller is synchronizing with a reliable external time source. For details, see the Microsoft Knowledge Base article 816042, [How to configure an authoritative time server in Windows Server](https://go.microsoft.com/fwlink/?linkid=3052&amp;kbid=816042).<br/>                                                                                                                                                                                                                                          |

To troubleshoot Skype for Business Online sign-in errors, start by eliminating the most common causes of sign-in difficulty. If necessary, you can then follow specific resolution steps based on the type of error. If the user still cannot sign in, collect additional information, and then seek additional help.

## Follow resolution steps for a specific error (Enterprise only)
<a name="toc325626440"> </a>

> [!IMPORTANT]
>  These instructions are intended primarily for Microsoft Office 365 Plan E customers. If you are an Office 365 Plan P customer, continue to the following section,[Collect more information and seek additional help ](troubleshooting-sign-in-errors-for-admins.md#collect-more-information).

If the user cannot sign in after you have tried the suggestions in the previous section, then you can do additional troubleshooting based on the type of error. The table below lists the most common error messages and possible causes. Following the table are detailed procedures to address each issue.

|**Error message**|**Possible cause**|**Resolution**|
|:-----|:-----|:-----|
|Sign-in address not found  <br/> |Sign-in requests from the Microsoft Online Services Sign-On Assistant (msoidsvc.exe) are not going through your external firewall, or proxy server.  <br/> |[Add a firewall entry for msoidsvc.exe to your proxy server](troubleshooting-sign-in-errors-for-admins.md#add-a-firewall) <br/> |
|Server is temporarily unavailable  <br/> |If your organization has a custom domain, the necessary Domain Name System (DNS) settings may be missing or incorrect.  <br/> |[Update DNS settings](troubleshooting-sign-in-errors-for-admins.md#update-dns-service) <br/> |
|Server is temporarily unavailable  <br/> |If your organization is using single sign-on with Active Directory Federation Services (ADFS), you may have used a self-signed Secure Socket Layer (SSL) certificate rather than one from a third-party certification authority.  <br/> |[Install a third-party SSL certificate on your ADFS server](troubleshooting-sign-in-errors-for-admins.md#verify-upn-and) <br/> |
|Problem acquiring a personal certificate that is required to sign in  <br/> |If you've already removed the cached server data used to sign in and the error continues to appear, the user's security credentials may be corrupted, or an RSA folder on the user's computer may be blocking authentication.  <br/> |[Update security credentials](troubleshooting-sign-in-errors-for-admins.md#update-security-credentials) <br/> |
|A certificate trust dialog box appears when a user signs in for the first time.  <br/> |This dialog box appears if your Skype for Business server is not yet listed in the **TrustModelData** registry key. <br/> |[Modify TrustModelData registry keys](troubleshooting-sign-in-errors-for-admins.md#modify-trustmodeldata-registry) <br/> |
|User is not SIP enabled  <br/> |If your organization had a previous installation of Microsoft Office Communications Server or Microsoft Lync Server 2010, you may not have deleted your users from the server before decommissioning it. As a result, the **msRTCSIP-UserEnabled** attribute is still set to **FALSE** in Active Directory Domain Services. <br/> |[Update user settings in Active Directory](troubleshooting-sign-in-errors-for-admins.md#update-user-settings)<br/> |

### Add a firewall entry for msoidsvc.exe to your proxy server
<a name="add-a-firewall"> </a>

This procedure is a possible fix for the following error message: **Sign-in address not found**.

> [!NOTE]
> The following steps assume you are using Microsoft Forefront Threat Management Gateway (TMG) 2010. If you have a different web gateway solution, use the settings described in step 4 below.


To create an application entry for Msoidsvc.exe in Forefront TMG 2010, follow these steps:

1. In the Forefront left pane, click **Networking**.

2. Click the **Network** tab. Under the **Tasks** tab in the right pane, click **Configure Forefront TMG Client Settings**.

3. In the **Forefront TMG Client Settings** dialog box, click **New**.

4. In the **Application Entry Setting** dialog box, configure the following rules:

|**Application**|**Key**|**Value**|
|:-----|:-----|:-----|
|**msoidsvc** <br/> |Disable  <br/> |0  <br/> |
|**msoidsvc** <br/> |DisableEx  <br/> |0  <br/> |

For details, see the Microsoft Knowledge Base article 2409256, [You cannot connect to Skype for Business Online because an on-premises firewall blocks the connection](https://go.microsoft.com/fwlink/?linkid=3052&amp;kbid=2409256).

### Update DNS settings
<a name="update-dns-service"> </a>

If your organization has a custom domain, this procedure is a possible fix for the following error message: **Server is temporarily unavailable**.

- Contact your domain name registrar for information on how to add the following CNAME record to your domain:

  - **DNS record type**: CNAME

  - **Name**: sip

  - **Value/Destination**: sipdir.online.lync.com

For details, see the Microsoft Knowledge Base article 2566790, [Troubleshooting Skype for Business Online DNS configuration issues in Office 365](https://go.microsoft.com/fwlink/?linkid=3052&amp;kbid=2566790).

### Install a third-party SSL certificate on your ADFS server
<a name="verify-upn-and"> </a>

To install a third-party SSL certificate on your Active Domain Federation Services (ADFS) server, follow these steps:

1. Obtain an SSL certificate from a third-party certification authority such as VeriSign or Thawte.

2. Install the certificate on your ADFS server by using the ADFS management console.

### Update security credentials
<a name="update-security-credentials"> </a>

This procedure is a possible fix for the error message **Problem acquiring a personal certificate required to sign in**.

To eliminate possible certificate or credential problems, first renew the user's certificate in Windows Certificate Manager. To do this, follow these steps:

1. Open Windows Certificate Manager. To do this, click **Start**, click **Run**, type **certmgr.msc**, and then click **OK**.

2. Double-click **Personal**, and then double-click **Certificates**.

3. Sort by the **Issued By** column, and then look for a certificate that is issued by Communications Server.

4. Right-click the certificate, and then click **Delete**.

Next, if the user is running Windows 7, remove their stored credentials in Windows Credential Manager. To do this, follow these steps:

1. Click **Start**, click **Control Panel**, and then click **Credential Manager**.

2. Locate the set of credentials that is used to connect to Skype for Business Online.

3. Expand the set of credentials, and then click **Remove from Vault**.

4. Sign in again and reenter the user's credentials.

Finally, if the user still cannot sign in after you've updated their credentials, try deleting the RSA folder on the user's computer, because it could be blocking completion of the user authentication process:

1. Sign in to the user's computer using an administrator account.

2. If necessary, turn on the folder view option **Show hidden files**.

3. Type the following into the address bar of File Explorer: **C:\\Documents and Settings\\UserName\\Application Data\\Microsoft\\Crypto\\RSA**, where ***UserName*** is your Windows sign-in name.

4. Delete any folder that begins with the name **S-1-5-21-** followed by a string of numbers.

### Modify TrustModelData registry keys
<a name="modify-trustmodeldata-registry"> </a>

When a user signs in for the first time, they may receive a dialog box that contains something like the following: **Cannot verify that the server is trusted for your sign-in address. Connect anyway?** This is a security feature, and not an error. However, you can prevent the dialog box from appearing by using a Group Policy Object (GPO) to update users' machines with your domain name before they sign in for the first time. To accomplish this, do the following:

- Create and deploy a GPO that appends your Skype for Business domain name—for example, domainName.contoso.com—to the current value of HKEY_LOCAL_MACHINE\\Software\\Policies\\Microsoft\\Communicator\\TrustModelData.

> [!IMPORTANT]
>  You must *append*  your domain name to the existing value, not simply replace it.

For details, see the Microsoft Knowledge Base article 2531068, [Skype for Business (Lync) cannot verify that the server is trusted for your sign-in address](https://go.microsoft.com/fwlink/?linkid=3052&amp;kbid=2531068).

### Update user settings in Active Directory
<a name="update-user-settings"> </a>

If your organization had a previous installation of Microsoft Office Communications Server or Microsoft Lync Server 2010, you may not have deleted your users from the server before decommissioning it. As a result, the **msRTCSIP-UserEnabled** attribute is still set to **FALSE** in Active Directory Domain Services.

To fix this issue, follow these steps:

1. Update the **msRTCSIP-UserEnabled** attribute for all affected users to **TRUE**.

2. Rerun the Microsoft Online Services Directory Synchronization Tool (DirSync). For details, see [AIntegrate your on-premises directories with Azure Active Directory](https://technet.microsoft.com/en-us/library/hh967642.aspx).

To troubleshoot Skype for Business Online sign-in errors, start by eliminating the most common causes of sign-in difficulty. If necessary, you can then follow specific resolution steps based on the type of error. If the user still cannot sign in, collect additional information, and then seek additional help.
## Use the Microsoft Support troubleshooting guide
<a name="toc325626447"> </a>

If you're still not able to resolve the user's sign-in problems, review the suggestions in Microsoft Knowledge Base article 2541980, [How to troubleshoot sign-in issues in Skype for Business Online](https://go.microsoft.com/fwlink/?linkid=3052&amp;kbid=2541980).

## Collect more information and seek additional help
<a name="collect-more-information"> </a>

If you've followed the guidance above and still can't resolve your sign-in issues, you must collect additional information and contact technical support. To do this, follow these steps:

1. Obtain the log files and Windows Event log details from the user's machine. For step-by-step instructions, see the end-user help topic [Turn on error logs in Lync](https://support.office.com/article/eaf6602b-95e0-4c27-869f-36017475806c).

2. Send the log files and detailed information about the error to Microsoft technical support.

You may be asked to supply additional diagnostic information by installing the Microsoft Online Services Diagnostic and Logging (MOSDAL) Support Toolkit on the affected user's machine. For details, see [Using the MOSDAL Support Toolkit](https://support.office.com/article/ddf1f52f-24a1-4675-abe0-141052c88b72).

To troubleshoot Skype for Business Online sign-in errors, start by eliminating the most common causes of sign-in difficulty. If necessary, you can then follow specific resolution steps based on the type of error. If the user still cannot sign in, collect additional information, and then seek additional help.

## Related topics
[Set up Skype for Business Online](set-up-skype-for-business-online.md)

[Let Skype for Business users add Skype contacts](let-skype-for-business-users-add-skype-contacts.md)


