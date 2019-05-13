---
title: "Deploy Edge Servers in Skype for Business Server"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: 
- Strat_SB_Hybrid
ms.custom: 
ms.assetid: 63c7251c-080a-4175-99a6-f86d0266d6bc
description: "Summary: Learn how to deploy Edge Servers into your Skype for Business Server environment."
---

# Deploy Edge Servers in Skype for Business Server
 
**Summary:** Learn how to deploy Edge Servers into your Skype for Business Server environment.
  
The following sections contain steps that are meant to be followed after the Skype for Business Server [Plan for Edge Server deployments in Skype for Business Server](../../plan-your-deployment/edge-server-deployments/edge-server-deployments.md) documentation has been reviewed. The deployment steps are as follows:
  
- Network interfaces
    
- Installation
    
- Certificates
    
- Starting the Edge Servers
    
## Network interfaces

As noted in Planning, you will either be configuring your network interface with DNS in the perimeter network hosting your Edge Servers, or without DNS in the perimeter network.
  
### Interface configuration with DNS servers in the perimeter network

1. Install two network adapters for each Edge Server, one for the internal-facing interface, and one for the external-facing interface.
    
    > [!NOTE]
    > The internal and external subnets must not be routable to each other. 
  
2. On your external interface, you'll configure **one** of the following:
    
   a. Three static IP addresses on the external perimeter network subnet, and point the default gateway to the internal interface of the external firewall. Configure the adapter DNS settings to point to a pair of perimeter DNS servers.
    
   b. One static IP address on the external perimeter network subnet, and point the default gateway to the internal interface of the external firewall. Configure the adapter DNS settings to point to a pair of perimeter DNS servers. This configuration is ONLY acceptable if you have previously configured your topology to have non-standard values in the port assignments, which is covered in the [Create your Edge topology for Skype for Business Server](create-your-edge-topology.md) article.
    
3. On your internal interface, configure one static IP on the internal perimeter network subnet, and don't set a default gateway. Configure the adaptor DNS settings to point to at least one DNS server, but preferably a pair of perimeter DNS servers.
    
4. Create persistent static routes on the internal interface to all internal networks where clients, Skype for Business Server, and Exchange Unified Messaging (UM) servers reside.
    
### Interface configuration without DNS servers in the perimeter network

1. Install two network adapters for each Edge Server, one for the internal-facing interface, and one for the external-facing interface.
    
    > [!NOTE]
    > The internal and external subnets must not be routable to each other. 
  
2. On your external interface, you'll configure **one** of the following:
    
   a. Three static IP addresses on the external perimeter network subnet. You'll also need to configure the default gateway on the external interface, for example, defining the internet-facing router or the external firewall as the default gateway. Configure the adapter DNS settings to point to an external DNS server, ideally a pair of external DNS servers.
    
   b. One static IP address on the external perimeter network subnet. You'll also need to configure the default gateway on the external interface, for example, defining the internet-facing router or the external firewall as the default gateway. Configure the adapter DNS settings to point to an external DNS server, or ideally a pair of external DNS servers. This configuration is ONLY acceptable if you have previously configured your topology to have non-standard values in the port assignments, which is covered in the [Create your Edge topology for Skype for Business Server](create-your-edge-topology.md) article.
    
3. On your internal interface, configure one static IP on the internal perimeter network subnet, and don't set a default gateway. Also leave the adapter DNS settings empty.
    
4. Create persistent static routes on the internal interface to all internal networks where clients, Skype for Business Server, and Exchange Unified Messaging (UM) servers reside.
    
5. Edit the HOST file on each Edge Server to contain a record for the next hop server or virtual IP (VIP). This record will be the Director, Standard Edition server or Front End pool you configured as the Edge Server next hop address in Topology Builder. If you're using DNS load balancing, include a line for each member of the next hop pool.
    
## Installation

To complete these steps successfully, you will need to have followed the steps in the [Create your Edge topology for Skype for Business Server](create-your-edge-topology.md) article.
  
1. Log onto the server you've been configuring for the Edge Server role with an account that's in the local Administrator's group.
    
2. You'll need the topology configuration file you copied out at the end of the Edge Server Topology documentation on this machine. Access the external media you placed that configuration file on (like a USB drive or share).
    
3. Start the **Deployment Wizard**.
    
4. Once the wizard opens, click **Install or Update Skype for Business Server System**.
    
5. The wizard will run checks to see if anything's already installed. As this is the first time running the wizard, you'll want to start at **Step 1. Install Local Configuration Store.**
    
6. The **Configure Local Replica of Central Management store** dialog will appear. You need to click **Import from a file (Recommended for Edge Servers)**.
    
7. From here, browse to the location of the topology you exported previously, select the .zip file, click **Open**, and then click **Next**.
    
8. The Deployment Wizard will read the configuration file and write the XML configuration file to the local computer.
    
9. After the **Executing Commands** process is finished, click **Finish**.
    
10. In the Deployment Wizard, click **Step 2. Setup or Remove Skype for Business Server Components**. The wizard will then install the Skype for Business Server Edge components specified in the XML configuration file that's been stored on the local computer.
    
11. Once the installation's complete, you can move onto the steps in the **Certificates** section below.
    
## Certificates

The certificate requirements for the Edge Server can be found in the Edge Certificate Planning documentation. The steps for setting up certificates are below.
  
> [!NOTE]
> When running the Certificate Wizard, you need to be logged in as an account with the correct permissions for the type of certificate template you're going to use. By default, a Skype for Business Server certificate request is going to use the Web Server certificate template. If you're logged in with an account that's a member of the RTCUniversalServerAdmins group to request a certificate via this template, double-check to make sure the group's been assigned the Enroll permissions to use that template. 
  
### Internal Edge interface certificates

 
### 1. Download or export the CA certification chain

 
#### &nbsp;&nbsp;&nbsp; a. Download using certsrv web site

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;i. Log into a Skype for Business Server in your internal network as a member of the local Administrators group.
    
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ii. Open up **Start**, and **Run** (or **Search** and **Run** ), and then type the following:
    
  ```
  https://<NAME OF YOUR ISSUING CA SERVER>/certsrv
  ```

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;For example:
    
  ```
  https://ca01/contoso.com/certsrv
  ```

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;iii. On the issuing CA's certsrv web page, under **Select a task**, click **Download a CA certificate, certificate chain, or CRL**.
    
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;iv. Under **Download a CA certificate, certificate chain, or CRL**, click **Download CA certificate chain**.
    
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;v. In the **File Download** box, click **Save**.
    
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;vi. Save the .p7b file to the hard disk drive on the server, and then copy it to a folder on each of your Edge Servers.
    
### &nbsp;&nbsp;&nbsp;b. Export using MMC

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;i. You can export the CA root certificate from any domain joined machine using the MMC. Either go to **Start** and **Run**, or open **Search**, and type **MMC** to open.
    
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ii. In the MMC console, click **File**, and then click **Add/Remove Snap-In**.
    
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;iii. From the **Add or Remove Snap-ins** dialog list, choose **Certificates**, and then click **Add**. When prompted, select **Computer Account**, and then **Next**. On the **Select Computer** dialog, select **Local Computer**. Click **Finish**, and then **OK**.
    
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;iv. Expand **Certificates (Local computer)**. Expand **Trusted Root Certification Authorities**. Select **Certificates**.
    
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;v. Click the root certificate issued by your CA. Right-click the certificate, choose **All Tasks** on the menu, and then select **Export**.
    
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;vi. The **Certificate Export Wizard** opens. Click **Next**.
    
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;vii. On the **Export File Format** dialog, choose the format you want to export to. Our recommendation is **Cryptographic Message Syntax Standard - PKCS #7 Certificates (P7b)**. If that's your choice as well, remember to also select the **Include all certificates in the certification path if possible** checkbox, as this will also export the certificate chain, including the root CA certificate and any Intermediate certificates. Click **Next**.
    
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;viii. On the **File to Export** dialog, in the file name entry, type a path and file name (the default extension would be .p7b) for the exported certificate. If it's easier on you, choose the **Browse** button to go to the location you want to save the exported certificate to, and name the exported certificate here. Click **Save**, and then **Next** when you're ready.
    
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ix. Review the summary of your actions, and click **Finish** to complete the export of the certificate. Click **OK** to confirm the successful export.
    
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;x. Copy the .p7b file to each of your Edge Servers.
    
### 2. Import the CA certification chain

&nbsp;&nbsp;&nbsp;a. On each Edge Server, open the MMC (choose **Start** and **Run**, or **Search**, and type **MMC** to open).
    
&nbsp;&nbsp;&nbsp;b. On the **File** menu, click **Add/Remove Snap-in**, and then choose **Add**.
    
&nbsp;&nbsp;&nbsp;c. In the **Add or Remove Snap-ins** box, click **Certificates**, and then click **Add**.
    
&nbsp;&nbsp;&nbsp;d. In the **Certificate snap-in** dialog box, click **Computer account**, and then click **Next**.
    
&nbsp;&nbsp;&nbsp;e. In the **Select Computer** dialog box, ensure that the **Local Computer: (the computer this console is running on)** check box is selected, and then click **Finish**.
    
&nbsp;&nbsp;&nbsp;f. Click **Close**, and then **OK**.
    
&nbsp;&nbsp;&nbsp;g. In the console tree, expand **Certificates (Local Computer)**, right-click **Trusted Root Certification Authorities**, go to **All Tasks**, and then click **Import**.
    
&nbsp;&nbsp;&nbsp;h. In the wizard that appears, in the **File to Import** textbox, specify the file name of the certificate (the name you gave the .p7b file in the previous section). Click **Next**.
    
&nbsp;&nbsp;&nbsp;i. Leave the radio button on **Place all certificates in the following store, as Trusted Root Certification Authorities** should be selected. Click **Next**.
    
&nbsp;&nbsp;&nbsp;j. Review the summary, and click **Finish** to complete the import.
    
&nbsp;&nbsp;&nbsp;k. This will need to be done for every Edge Server you're deploying.
    
### 3. Create the certificate request

&nbsp;&nbsp;&nbsp;a. Log on to one of your Edge Servers, start the Deployment Wizard, and on **Step 3: Request, Install, or Assign Certificates**, click **Run** (or **Run Again**, if you've already run this wizard).
    
&nbsp;&nbsp;&nbsp;b. On the **Certificate Request** page, ensure **Internal Edge Certificate** is selected, and click **Request**.
    
&nbsp;&nbsp;&nbsp;c. On the **Delayed or Immediate Requests** page, choose **Send the request immediately to an online certification authority** if you have access to one from your Edge environment, or **Prepare the request now, but send it later** otherwise.
    
&nbsp;&nbsp;&nbsp;d. On the **Certificate Request File** page, enter the full part and file name for where the file will be saved (such as c:\SkypeInternalEdgeCert.cer). Click **Next**.
    
&nbsp;&nbsp;&nbsp;e. On the **Specify Alternate Certificate Template** page, to use a template other than the default WebServer template, check the **Use alternative certificate template for the selected Certificate Authority** check box. Otherwise, do nothing.
    
&nbsp;&nbsp;&nbsp;f. On the Name and Security Settings page, do the following:
    
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;   i. In **Friendly name**, enter a display name for the certificate (such as Internal Edge).
    
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  ii. In **Bit length**, choose your bit length (the default is 2048, you can go higher and be more secure, but it will make performance slow down).
    
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  iii. If you need an exportable certificate, you must check the **Mark certificate private key as exportable** check box.
    
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  iv. Click **Next**.
    
&nbsp;&nbsp;&nbsp;g. On the **Organization Information** page, enter the name for your organization and organizational unit (OU). You might enter your division or department (IT, for example).
    
&nbsp;&nbsp;&nbsp;h. On the **Geographical Information** page, enter your location information.
    
&nbsp;&nbsp;&nbsp;i. On the **Subject Name/Subject Alternate Names** page, this should be auto-populated by the wizard.
    
&nbsp;&nbsp;&nbsp;j. On the **Configure Additional Subject Alternate Names** page, you need to add any additional subject alternative names that you need.
    
&nbsp;&nbsp;&nbsp;k. On the **Request Summary** page, look over the certificate information that's going to be used to generate your request. If you need to make changes, go back and do so now.
    
&nbsp;&nbsp;&nbsp;l. Then click **Next** to generate the CSR file you'll need to provide to the CA (you can also click **View Log** to look at the log for the certificate request).
    
&nbsp;&nbsp;&nbsp;m. Once the request has been generated, you can click **View** to look at the certificate, and **Finish** to close out the window. The contents of the CSR file need to be given to your CA, so they can generate a certificate for you to import to this computer in the next section.
    

### 4. Import the certificate

&nbsp;&nbsp;&nbsp;a. Log on, as a member of the local Administrators group, to the Edge Server you made your certificate request from in the last procedure.
    
&nbsp;&nbsp;&nbsp;b. In the Deployment Wizard, next to **Step 3. Request, Install or Assign Certificates**, click **Run Again**.
    
&nbsp;&nbsp;&nbsp;c. On the **Available Certificates Tasks** page, click **Import a certificate from a .P7b, .pfx or .cer file**.
    
&nbsp;&nbsp;&nbsp;d. On the **Import Certificate** page, type the full path and file name of the certificate you got in the previous section (or you can click **Browse** to find and choose the file that way).
    
&nbsp;&nbsp;&nbsp;e. If you're importing certificates for other members of your Edge pool, and your certificate contains a private key, be sure to select the **Certificate file that contains certificate's private key** check box, and specify the password. Click **Next** to continue.
    
&nbsp;&nbsp;&nbsp;f. On the**Summary** page, click **Next** once you've confirmed the information, and **Finish** once the certificate is successfully imported.
    
 
### 5. Export the certificate

&nbsp;&nbsp;&nbsp;a. Make sure you've logged onto the Edge Server you imported the certificate to previously, as a member of the local Administrators group.
    
&nbsp;&nbsp;&nbsp;b. Click **Start**, **Run** (or open **Search** ), and type **MMC**.
    
&nbsp;&nbsp;&nbsp;c. From the MMC console, click **File**, and click **Add/Remove Snap-in**.
    
&nbsp;&nbsp;&nbsp;d. From the **Add or Remove Snap-ins** box, click **Certificates**, and click **Add**.
    
&nbsp;&nbsp;&nbsp;e. In the **Certificates** snap-in dialog box, choose **Computer account**. Click **Next**.
    
&nbsp;&nbsp;&nbsp;f. On the **Select Computer** dialog, select **Local computer: (the computer this console is running on)**. Click **Finish**. Click **OK**, and the configuration of the MMC console is completed.
    
&nbsp;&nbsp;&nbsp;g. Double-click **Certificates (Local Computer)** to expand the certificate stores. Double-click **Personal**, and then click **Certificates**.
    
  > [!NOTE]
  > You may be here, and you don't see any certificates in the Certificates Personal store for the local computer. You don't need to hunt around, if the key's not there, the imported certificate didn't have a private key associated with it. Try the request and import steps above one more time, and if you're sure you got all that right, talk to your CA administrator or provider. 
  
&nbsp;&nbsp;&nbsp;h. In the **Certificates Personal store** for the local computer, right-click the certificate that you're exporting. Select **All Tasks** from the resulting menu, and then click **Export**.
    
&nbsp;&nbsp;&nbsp;i. In the **Certificate Export Wizard**, click **Next**. Select **Yes, export the private key**. Click **Next**.
    
&nbsp;&nbsp;&nbsp;j. On the **Export File Formats** dialog, select **Personal Information Exchange - PKCS#12 (.PFX)**, and then select the following:
    
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;   i. Include all certificates in the certification path, if possible.
    
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;   ii. Export all extended properties.
    
   > [!NOTE]
   > **NEVER** select **Delete the private key if the export is successful**. It'll mean you have to reimport the certificate and private key back to this Edge Server.
  
&nbsp;&nbsp;&nbsp;k. If you want to assign a password to protect the private key, you can type a password for the private key. Reenter the password to confirm, and then click **Next**.
    
&nbsp;&nbsp;&nbsp;l. Type a path and file name for the exported certificate, using a file extension of **.pfx**. The path either needs to be accessible by the other Edge Servers in the pool, or you'll need to move the file by means of external media (such as a USB drive). Click **Next** when you've made your choice.
    
&nbsp;&nbsp;&nbsp;m. Review the summary on the **Completing the Certificate Export Wizard** dialog, and then click **Finish**.
    
&nbsp;&nbsp;&nbsp;n. Click **OK** in the successful export dialog.
    
 
### 6. Assign the certificate

&nbsp;&nbsp;&nbsp;a. On EACH Edge Server, in the Deployment Wizard, next to **Step 3. Request, Install or Assign Certificates**, click **Run again**.
    
&nbsp;&nbsp;&nbsp;b. On the **Available Certificates Tasks** page, click **Assign an existing certificate**.
    
&nbsp;&nbsp;&nbsp;c. On the **Certificate Assignment** page, select **Edge Internal** in the list.
    
&nbsp;&nbsp;&nbsp;d. On the **Certificate Store** page, select the certificate you've imported for the internal Edge (from the previous section).
    
&nbsp;&nbsp;&nbsp;e. On the **Certificate Assignment Summary** page, look over the settings, and then click **Next** to assign the certificate.
    
&nbsp;&nbsp;&nbsp;f. On the wizard completion page, click **Finish**.
    
&nbsp;&nbsp;&nbsp;g. Once you've completed this procedure, it's a really good idea to open the Certificates MMC snap-in on each Edge Server, expand **Certificates (Local computer)**, expand **Personal**, click **Certificates**, and confirm that the internal Edge certificate is listed in the details pane.
    
### External Edge interface certificates

 
### 1. Create the certificate request

&nbsp;&nbsp;&nbsp;a. Log on to one of your Edge Servers, start the Deployment Wizard, and on **Step 3: Request, Install, or Assign Certificates, click Run** (or **Run Again**, if you've already run this wizard).
    
&nbsp;&nbsp;&nbsp;b. On the **Available Certificate Tasks** page, click **Create a new certificate request**.
    
&nbsp;&nbsp;&nbsp;c. On the **Certificate Request** page, ensure **External Edge Certificate** is selected, and click **Next**.
    
&nbsp;&nbsp;&nbsp;d. On the **Delayed or Immediate Requests** page, click **Prepare the request now, but send it later**.
    
&nbsp;&nbsp;&nbsp;e. On the **Certificate Request File** page, enter the full part and file name for where the file will be saved (such as c:\SkypeInternalEdgeCert.cer). Click **Next**.
    
&nbsp;&nbsp;&nbsp;f. On the **Specify Alternate Certificate Template** page, to use a template other than the default WebServer template, check the **Use alternative certificate template for the selected Certificate Authority** check box.
    
&nbsp;&nbsp;&nbsp;g. On the Name and Security Settings page, do the following:
    
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;   i. In **Friendly name**, enter a display name for the certificate (such as External Edge).
    
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  ii. In **Bit length**, choose your bit length (the default is 2048, you can go higher and be more secure, but it will make performance slow down).
    
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  iii. If you need an exportable certificate, you must check the **Mark certificate private key as exportable** check box.
    
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; iv. Click **Next**.
    
&nbsp;&nbsp;&nbsp;h. On the **Organization Information** page, enter the name for your organization and organizational unit (OU). You might enter your division or department (IT, for example).
    
&nbsp;&nbsp;&nbsp;i. On the **Geographical Information** page, enter your location information.
    
&nbsp;&nbsp;&nbsp;j. On the **Subject Name/Subject Alternate Names** page, the needed information should be auto-populated by the wizard.
    
&nbsp;&nbsp;&nbsp;k. On the **SIP Domain Setting on Subject Alternate Names (SANs)** page, check the domain checkbox to add a sip.<sipdomain> entry to the subject alternative names list.
    
&nbsp;&nbsp;&nbsp;l. On the **Configure Additional Subject Alternate Names** page, you need to add any additional subject alternative names that you need.
    
&nbsp;&nbsp;&nbsp;m. On the **Request Summary** page, look over the certificate information that's going to be used to generate your request. If you need to make changes, go back and do so now.
    
&nbsp;&nbsp;&nbsp;n. When you're ready, click **Next** to generate the CSR file you'll need to provide to the CA (you can also click **View Log** to look at the log for the certificate request).
    
&nbsp;&nbsp;&nbsp;o. Once the request has been generated, you can click **View** to look at the certificate, and **Finish** to close out the window. The contents of the CSR file need to be given to your CA, so they can generate a certificate for you to import to this computer in the next section.
    
&nbsp;&nbsp;&nbsp;p. (OPTIONAL) You may, when submitting the contents of the CSR, be asked for certain information, as follows (CAs vary greatly, so this may not be required):
    
  - **Microsoft** as the server platform
    
  - **IIS** as the version
    
  - **Web Server** as the usage type
    
  - **PKCS7** as the response format
    
 
### 2. Import the certificate

&nbsp;&nbsp;&nbsp;a. Log on, as a member of the local Administrators group, to the Edge Server you made your certificate request from in the last procedure.
    
&nbsp;&nbsp;&nbsp;b. In the Deployment Wizard, next to **Step 3. Request, Install or Assign Certificates**, click **Run Again**.
    
&nbsp;&nbsp;&nbsp;c. On the **Available Certificates Tasks** page, click **Import a certificate from a .P7b, .pfx or .cer file**.
    
&nbsp;&nbsp;&nbsp;d. On the **Import Certificate** page, type the full path and file name of the certificate you got in the previous section (or you can click **Browse** to find and choose the file that way). If your certificate contains a private key, make sure to select **Certificate file contains certificate's private key**, and enter the password for the private key. Click **Next** when ready.
    
&nbsp;&nbsp;&nbsp;e. On the **Import Certificate Summary** page, review the summary information, and click **Next**.
    
&nbsp;&nbsp;&nbsp;f. On the **Executing Commands** page, you can review the result of the import when it's complete by clicking **View Log**. Click **Finish** to complete the certificate import.
    
&nbsp;&nbsp;&nbsp;g. If you have other Edge Servers in a pool, you'll need to follow the next two procedures as well. If this is a standalone Edge Server, you're done with external certificates.
    
 
### 3. Export the certificate

&nbsp;&nbsp;&nbsp;a. Make sure you've logged onto the Edge Server you imported the certificate to as a local Administrator.
    
&nbsp;&nbsp;&nbsp;b. Click **Start**, **Run** (or open **Search** ), and type **MMC**.
    
&nbsp;&nbsp;&nbsp;c. From the MMC console, click **File**, and then click **Add/Remove Snap-in**.
    
&nbsp;&nbsp;&nbsp;d. From the **Add or Remove Snap-ins** box, click **Certificates**, and click **Add**.
    
&nbsp;&nbsp;&nbsp;e. In the **Certificates** snap-in dialog box, choose **Computer account**. Click **Next**.
    
&nbsp;&nbsp;&nbsp;f. On the **Select Computer** dialog, select **Local computer: (the computer this console is running on)**. Click **Finish**. Click **OK**, and the configuration of the MMC console is completed.
    
&nbsp;&nbsp;&nbsp;g. Double-click **Certificates (Local Computer)** to expand the certificate stores. **Double-click Personal**, and then click **Certificates**.
    
   > [!NOTE]
   > You may be here, and you don't see any certificates in the Certificates Personal store for the local computer. You don't need to hunt around, if the key's not there, the imported certificate didn't have a private key associated with it. Try the request and import steps above one more time, and if you're sure you got all that right, talk to your CA administrator or provider. 
  
&nbsp;&nbsp;&nbsp;h. In the **Certificates Personal store** for the local computer, right-click the certificate that you're exporting. **Select All Tasks** from the resulting menu, and then click **Export**.
    
&nbsp;&nbsp;&nbsp;i. In the **Certificate Export Wizard**, click **Next**. Select **Yes, export the private key**. Click **Next**.
    
   > [!NOTE]
   > If **Yes, export the private key** isn't available, then the private key for this certificate wasn't marked for export before you got it. You need to request the certificate from the provider again, with the private key set to export, before doing this successfully.
  
&nbsp;&nbsp;&nbsp;j. On the Export File Formats dialog, select Personal Information Exchange - PKCS#12 (.PFX) and then select the following:
    
 &nbsp;&nbsp;&nbsp;  i. Include all certificates in the certification path, if possible.
    
 &nbsp;&nbsp;&nbsp;  ii. Export all extended properties.
    
   > [!NOTE]
   > **NEVER** select **Delete the private key if the export is successful**. It'll mean you have to reimport the certificate and private key back to this Edge Server.
  
&nbsp;&nbsp;&nbsp;k. If you want to assign a password to protect the private key, you can type a password for the private key. Reenter the password to confirm, and then click **Next**.
    
&nbsp;&nbsp;&nbsp;l. Type a path and file name for the exported certificate, using a file extension of **.pfx**. The path either needs to be accessible by the other Edge Servers in the pool, or you'll need to move the file by means of external media (such as a USB drive). Click **Next** when you've made your choice.
    
&nbsp;&nbsp;&nbsp;m. Review the summary on the **Completing the Certificate Export Wizard** dialog, and then click **Finish**.
    
&nbsp;&nbsp;&nbsp;n. Click **OK** in the successful export dialog.
    
&nbsp;&nbsp;&nbsp;o. You'll now need to go back to the Import the certificate section prior to this and import the certificate to all your remaining Edge Servers, then proceed with assigning, below.
    
 
### 4. Assign the certificate

&nbsp;&nbsp;&nbsp;a. On **EACH** Edge Server, in the Deployment Wizard, next to **Step 3. Request, Install or Assign Certificates**, click **Run again**.
    
&nbsp;&nbsp;&nbsp;b. On the **Available Certificates Tasks** page, click **Assign an existing certificate**.
    
&nbsp;&nbsp;&nbsp;c. On the **Certificate Assignment** page, select **Edge External** in the list.
    
&nbsp;&nbsp;&nbsp;d. On the **Certificate Store** page, select the certificate you've imported for the external Edge (from the previous section).
    
&nbsp;&nbsp;&nbsp;e. On the **Certificate Assignment Summary** page, look over the settings, and then click **Next** to assign the certificate.
    
&nbsp;&nbsp;&nbsp;f. On the wizard completion page, click **Finish**.
    
&nbsp;&nbsp;&nbsp;g. Once you've completed this procedure, it's a really good idea to open the Certificates MMC snap-in on each server, expand **Certificates (Local computer)**, expand **Personal**, click **Certificates**, and confirm that the internal Edge certificate is listed in the details pane.
    
   > [!NOTE]
   > You will also have needed to set up the certificates for your reverse proxy server. 
  
## Starting the Edge Servers

Once the setup is complete, you'll need to start the services on each Edge server in your deployment:
  
1. On each Edge Server, in the **Deployment Wizard**, next to **Step 4: Start Services**, click **Run**.
    
2. On the **Start Skype for Business Server Services** page, review the list of services, and then click **Next** to start the services.
    
3. After the services are started, you can click **Finish** to close the wizard.
    
4. (Optional) Still under **Step 4: Start Services**, click **Services Status**.
    
5.  In the **Services MMC** on each server, verify that all the Skype for Business Server services are running.
    

