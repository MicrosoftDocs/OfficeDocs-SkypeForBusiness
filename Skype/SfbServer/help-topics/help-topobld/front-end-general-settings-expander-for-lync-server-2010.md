---
title: "Front End General Settings Expander for Lync Server 2010"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 11/17/2018
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.tb.FrontEndGeneralSettingsExpander2010
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 58269c38-98d9-499f-ab69-6a63a6e5530e
description: "You edit the properties of the Front End Server or Front End pool by editing or configuring the following attributes. The configuration page is separated into the following sections:"
---

# Front End General Settings Expander for Lync Server 2010

You edit the properties of the Front End Server or Front End pool by editing or configuring the following attributes. The configuration page is separated into the following sections:

 **General**

- **FQDN**: The fully qualified domain name of the Front End Server or Front End pool.

- Select **Use all configured IP addresses** to make use of all addresses configured on Front End Server or Front End pool.

    > [!IMPORTANT]
    > You should not select this option if you collocate the Mediation Server on the Front End Server or Front End pool. Mediation Servers and Front End Servers need dedicated IP addresses on which to communicate.

- Select **Limit service usage to selected IP addresses** and enter the IP address for **Primary IP address** for the Front End Server or Front End pool communication with the rest of the deployment. Type in **PSTN IP address** the IP address that is associated with the Mediation Server.

    **Features and functionality**

- **Conferencing**: Select the check box if you want conferencing features in your deployment. Conferencing includes audio, video, application sharing, desktop sharing, and Web conferencing. You will need to create and associate an Office Web Apps Server for Web conferencing (defined later in this Properties page).

- If you selected Conferencing, **Dial-in (PSTN) conferencing** can be selected. Select the check box to enable dial-in conferencing features.

- Select the check box **Enterprise Voice** if you intend to deploy features to enable Lync Server 2013 to act as your telephone voice system using voice over IP (VoIP) technologies, including the option of deploying handset telephones, SIP trunks, or public switched telephone network connectivity using Mediation Server, PSTN Gateways, and IP-PBX, in combination or alone, based on the design and requirements. For detail on Enterprise Voice, see [Enterprise Voice](https://technet.microsoft.com/library/c9da8099-6f4f-4346-ac67-f041bb96072c.aspx) and [Plan for Enterprise Voice in Skype for Business Server 2015](../../plan-your-deployment/enterprise-voice-solution/enterprise-voice.md)

    **Associations**

- **SQL Server store**: The FQDN of the SQL Server (and optionally a named instance) associated with the Front End Server or Front End pool. You select the SQL Server store from the list or you create a new SQL Server store by clicking **New**

- **File store**: You select the FQDN of the server and the share (in the format  `\\<FQDN of server>\<share name>`) that will act as the file store location for the shared files that Lync Server 2013 creates and uses for replication, conference directories, and other purposes. You select the File store from the list or you create a new File store by clicking **New**.

- Select the **Associate Archiving Server** checkbox to enable an Archiving Server for this Front End Server or Front End pool. After selecting the check box, you select an existing Archiving Server from the list or click **New** to create the definitions for a new Archiving Server.

- Select the **Associate Monitoring Server** checkbox to enable a Monitoring Server for this Front End Server or Front End pool. After selecting the check box, you select an existing Monitoring Server from the list or click **New** to create the definitions for a new Monitoring Server.

- Select the **Associate Edge Pool (for media components** checkbox to enable an Edge Server for this Front End Server or Front End pool. After selecting the check box, you select an existing Edge Server or pool from the list or click **New** to create the definitions for a new Edge Server or pool.

  **Resiliency**

- Select the **Associated backup Registrar pool** check box to select from the list a Front End Server or Front End pool that will be the backup Registrar ( that is, the Front End Server or Front End pool designated as a secondary registrar in the event that the primary fails)

- If you selected Associated backup Registrar pool and have chosen a backup registrar, you can select the checkbox for **Automatic failover and failback for Voice**. You can now define numerical properties for **Voice failover detection internal (sec)** and **Voice failback interval (sec)**. For details, see [Planning for Enterprise Voice Resiliency](https://technet.microsoft.com/library/ca116700-1055-4ca5-9b87-4c7f380c3655.aspx)

  **Web services**

- To configure **Internal web services**, you define **Listening ports** for **HTTP** and **HTTPS**. By default, these are TCP port 80 and TCP port 443, respectively. You also configure the **Published ports** for **HTTP** and **HTTPS**. By default, these are TCP port 80 and TCP port 443, respectively. Based on your internal web services configuration and use of load balancers (hardware load balancers and DNS load balancing), adjust the port values to define the listening and published ports.

    > [!IMPORTANT]
    > Internal web services and the defined listening and published ports are for internal clients and devices. External clients and devices use the external web services listening and published ports, along with the defined external web services fully qualified domain name (FQDN).

- To configure **External web services**, you define **Listening ports** for **HTTP** and **HTTPS**. By default, these are TCP port 80 and TCP port 443, respectively. You also configure the **Published ports** for **HTTP** and **HTTPS**. By default, these are TCP port 80 and TCP port 443, respectively. Based on your internal web services configuration and use of load balancers (hardware load balancers and DNS load balancing), adjust the port values to define the listening and published ports.

    > [!IMPORTANT]
    > External web services and the defined listening and published ports are for external clients and devices. External clients and devices use the external web services listening and published ports, typically defined by your reverse proxy along with the defined external web services fully qualified domain name (FQDN). The relationship of the external web services FQDN and the Simple URLs define the uniform resource locator (URL) addresses that external clients will use to access services available for external users and devices. For more details on Simple URLs, see [Planning for Simple URLs](https://technet.microsoft.com/library/20e4f4b6-b7ff-4297-b00d-d1211ee800ac.aspx).

  **Mediation Server**

- To configure **Mediation Server** properties for a collocated Mediation Server (that is, a Mediation Server deployed on the Front End Server or Front End pool), select **Collocated Mediation server enabled**.

- To define the **Listening ports** for a collocated Mediation Server, you type the **TLS** and **TCP** port value that the collocated Mediation Server is listening on. By default, TLS is defined as TCP port 5067.

- To define a TCP port value for the Mediation Server, you select the **Enable TCP port** check box. By default, the Mediation Server uses the transport layer security (TLS) over TCP protocol. TCP ports are available only when the Enable TCP Port selection is enabled.

    > [!NOTE]
    > This is an optional setting, and you should refer to the requirements of your gateway or PSTN to determine if you need this. By default, the TCP port value is 5068.

- You define trunks that are associated with the collocated Mediation Server. If you have already defined trunks, they will be available to associate with the Mediation Server.

    If you have more than one gateway associated with a Mediation Server, you can specify the default gateway by selecting the gateway that you want to make the default, and clicking **Make Default**. If you choose to remove the current default gateway, select the gateway and click **Unmake Default**.

> [!IMPORTANT]
> If you make changes to the properties in this dialog, you must publish the topology and run the Skype for Business Server Deployment Wizard on all affected servers. After publishing the new topology, a list of affected servers where the Skype for Business Server Deployment Wizard must be run is provided for you as a link on the successful topology publishing summary screen. For details on publishing the updated topology, see [Publish the Topology](https://technet.microsoft.com/library/3b5a744b-b3a8-4538-a55e-e2e4f72dff47.aspx). For details on the Skype for Business Server Deployment Wizard , see [Lync Server Administrative Tools](https://technet.microsoft.com/library/9b006f93-4f3d-461d-89b8-e80a34fdb3c5.aspx).

Click **OK** to save and commit your changes to the topology document.

Click **Cancel** to discard your changes and close the **Edit Properties** for the Front End Server or Front End pool.

Click **Help** to read this help topic.

## See also

[Define and Configure a Front End Pool or Standard Edition Server](https://technet.microsoft.com/library/713fc263-23dd-414a-b001-82932e4fe966.aspx)
