---
title: "Front End General Settings Expander"
ms.reviewer: 
ms.author: kenwith
author: kenwith
manager: serdars
ms.date: 3/25/2015
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.tb.FrontEndGeneralSettingsExpander
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 8a5f21d0-f6c8-4907-9958-5ca36f702542
description: "To edit the settings for an existing Front End pool or Standard Edition server, you are presented with the following sections:"
---

# Front End General Settings Expander

To edit the settings for an existing Front End pool or Standard Edition server, you are presented with the following sections:

- General settings

- Resiliency settings

- Web services settings

- Mediation Server settings

## Front End pool

For a Front End pool, you can configure general, resiliency, web services, and Mediation Server settings. For details, see the information in the following subsections. For details about defining and configuring the settings for the Front End pool, see [Deploying Mediation Servers and Defining Peers](https://technet.microsoft.com/library/a684f1da-6671-4011-adf6-2db49e2528e2.aspx).

### General Settings

You can configure the following general settings:

- **FQDN**. Edit the FQDN of the pool to change it.

- **Enable hardware load balancer monitoring port**. Select the check box and enter the port number that your Hardware Load Balancer will use to monitor the state of the pool servers.

- In **Features and Functionality**, define the additional roles that you want to collocate with this pool. You can configure the following settings:

  - **Conferencing**. Includes audio, video and application sharing. After you select this option, you can select Dial-in (PSTN) conferencing. You specify and define a public switched telephone network (PSTN) gateway in the "Mediation Server Settings" subsection later in this section.

  - **Enterprise Voice**. Enables internal voice over IP calls to qualified handsets and devices and Skype for Business clients. To enable external call capabilities, you need to include a Mediation Server. For details, see "Mediation Server" later in this topic.

- In **Associations**, edit or specify the following:

  - **SQL Store**. Modify an existing SQL Server database or create a new SQL Server-based database to hold the Front End pool databases. You can select a new instance of SQL Server from the list or create a new entry by clicking **New**.

    Select **Enable SQL Server store mirroring**, and then select the server to use for mirroring. Click **New** to create a new SQL Server store.

    Select **Use SQL Server mirroring witness to enable automatic failover** to select a server to use as a mirroring witness. Click **New** to create a new SQL Server store.

  - **File share**. Modify the file store that the Front End pool is using. You can select a new file store from those already defined by selecting it from the list. You can create a new file store by clicking **New**.

    > [!IMPORTANT]
    > Before publishing the newly defined topology, the server that you specify must exist and be joined to the domain.

  - **Archiving**. Associate an Archiving Server store with the Front End pool. You can select from an already defined Archiving SQL Server store by selecting the server from the list, or click **New** to specify a new Archiving Server.

    > [!IMPORTANT]
    > Before publishing the newly defined topology, the server that you specify must exist and be joined to the domain.

    Select **Enable SQL Server store mirroring**, and then select the server to use for mirroring. Click **New** to create a new SQL Server store.

    Select **Use SQL Server mirroring witness to enable automatic failover** to select a server to use as a mirroring witness. Click **New** to create a new SQL Server store.

  - **Monitoring (CDR and QoE metrics)**. Select to associate a Monitoring SQL Server store with the Front End pool. You can select from an already defined Monitoring Server by selecting the server from the list, or click **New** to specify a new Monitoring Server.

    Select **Enable SQL Server store mirroring**, and then select the server to use for mirroring. Click **New** to create a new SQL Server store.

    Select **Use SQL Server mirroring witness to enable automatic failover** to select a server to use as a mirroring witness. Click **New** to create a new SQL Server store.

  - **Associate Edge pool (for media components)**. Associate an Edge Server or pool with the Front End pool. You can select from an already defined Edge Server or pool by selecting the server from the list, or click **New** to specify a new Edge Server or pool.

  - **Associate pool with an Office Web Apps Server**. Select this option to associate an Office Web Apps Server with the Front End pool. Select an existing server from the list, or click **New** to create a new Office Web Apps Server.

### Resiliency

Resiliency provides disaster recovery and high availability for the pool. By providing a backup, if the primary server fails, the backup server can take over, enabling users to sign in and communicate. There may be reduced functionality for users, depending on which systems have failed with the primary server.

From the list, select the Front End pool or Standard Edition server that will act as the backup server for the pool. You can also select to enable Failover and Fallback time intervals. Enabling the failover and fallback time settings (specified in seconds) enables automatic detection of a failed server, and a fallback time to allow for automatic determination that the primary is back up.

> [!IMPORTANT]
> When defining the Failure detection and the Fallback interval, you should be careful not to enter an interval that will cause the failover and fallback to occur if the server fails to respond for a short period of time. It is possible that the primary server may not respond for short periods of time, depending on the loading of the pool or servers. The default values for the failover and fallback are 300 seconds and 600 seconds for pool to pool, or pool to Standard Edition server. In the event of a Survivable Branch Appliance or a Survivable Branch Server in a site to a pool or Standard Edition server, the default values are 120 seconds for failover and 240 seconds for fallback.

> [!CAUTION]
> The minimum value for the **failover interval** should not be set lower than 90 seconds. If you do set the value to less than 90 seconds, the value of 90 seconds is used. The intercluster ping time is 30 seconds, and a setting lower than 90 seconds may cause the primary and backup servers to cycle up and down, causing an undesirable impact to production, as the servers try to resolve the viable status of the other. Less than 90 seconds does not allow for enough time to determine that the primary server is actually unavailable or not.

### Web Services

To edit or specify additional setting for the web services on the Front End pool, modify or specify settings in **Internal Web services** and **External Web services**.

In **Internal Web services**, specify the following:

> [!CAUTION]
> If you have more than one Front End pool or Front End Server, the external Web services FQDN must be unique. For example, if you define the external Web services FQDN of a Front End Server as **pool01.contoso.com**, you cannot use **pool01.contoso.com** for another Front End pool or Front End Server. If you are also deploying Directors, the external Web services FQDN defined for any Director or Director pool must be unique from any other Director or Director pool, as well as from any Front End pool or Front End Server. If you decide to override the Internal web services with a self-defined FQDN, each FQDN must be unique from any other Front End pool, Director, or Director pool.

- If you select **Override FQDN**, you can specify a different FQDN for the **Internal Web** services identity on the pool. By default, the setting is the current pool name as defined for the Front End pool.

- Listening and published ports for HTTP and HTTPS that your deployment requires. The default settings of port 80 for HTTP and port 443 for HTTPS are the most common settings and typically do not need to be changed, unless you have specific requirements within your organization and infrastructure design.

In **External Web services**, specify the following:

- The FQDN of the External Web services. The FQDN specified here will usually be defined by the requirements of your external connection requirements, such as the reverse proxy.

- Listening and published ports for HTTP and HTTPS that your deployment requires. The default settings of port 8080 for HTTP and port 4443 for HTTPS are defined initially. You change these settings for the listening ports based on what the requirements are for your reverse proxy and external network requirements. The published ports are set to default of port 80 for HTTP and port 443 for HTTPS. These values determine what ports the pool will listen for incoming requests. Typically, these do not need to be changed, unless there is a conflict of port requirements on the pool. Internal and external published ports using the same port values are expected. This is not a conflict.

### Mediation Server

In **Mediation Server**, specify the following:

- If you collocate the Mediation Server with the pool, select the **Collocated Mediation Server enabled** check box. If you choose not to collocate the Mediation Server, none of the settings are available in this section.

- If you enable the collocation of the Mediation Server, define the listening port range on the pool servers for Transport Layer Security (TLS). By default, this port is 5067. If you select **Enable TCP port**, you must define a Transmission Control Protocol (TCP) port for the collocated Mediation Server. This is an optional setting, and you should refer to the requirements of your gateway or PSTN requirements to determine if you need this. By default, the TCP port value is 5068.

- Trunks that are associated with the collocated Mediation Server. If you have already defined trunks, they will be available to associate with the Mediation Server.

- If you have more than one trunk associated with a Mediation Server, you can specify a default trunk by selecting the gateway and then clicking **Make Default**. To unselect a gateway as the default, click **Unmake Default**.

For details about defining and configuring the settings for the Front End pool, see [Deploying Mediation Servers and Defining Peers](https://technet.microsoft.com/library/a684f1da-6671-4011-adf6-2db49e2528e2.aspx).

## Standard Edition Server

For a Standard Edition server, you can configure general, resiliency, web services, and Mediation Server settings. For details, see the information in the following subsections. For details about defining and configuring the settings for the Standard Edition server, see [Defining and Configuring the Topology](https://technet.microsoft.com/library/51d1601e-4f83-48d4-ad08-3b4d5e2003aa.aspx) and [Deploying Mediation Servers and Defining Peers](https://technet.microsoft.com/library/a684f1da-6671-4011-adf6-2db49e2528e2.aspx).

### General Settings

You can configure the following general settings:

- **FQDN**. Note that the FQDN cannot be changed. You must remove and redefine the Standard Edition server to change the FQDN associated with it.

- Select **Use all configured IP addresses** or to **Limit service usage to selected IP addresses**. If you select to limit the service to defined IP addresses, you will define the Primary IP address that the server will use for all communications, except for PSTN. You define a separate IP address for PSTN usage. You can also select **Enable IPv6** to enable IPv6 for this server.

- **Enable Hardware Load Balancer monitoring port**. Select the check box and enter the port number that your Hardware Load Balancer will use to monitor the state of the server.

- In **Features and Functionality**, define the additional roles that you want to collocate with this server. You can configure the following settings:

  - **Conferencing**. Includes audio, video and application sharing. After you select this option, you can select **Dial-in (PSTN) conferencing**. You can specify and define a PSTN gateway later under Mediation Server settings.

  - **Enterprise Voice**. Enables internal voice over IP calls to qualified handsets and devices and Skype for Business clients. To enable external call capabilities, you need to include a Mediation Server. For details, see "Mediation Server" later in this topic.

- In **Associations** you can edit or specify the following:

  - Select **SQL Server store** to associate a SQL Server store with the Front End server. You can also enable mirroring and select a mirroring witness server.

  - **File share**. Modify the file store that the Standard Edition server is using. You can select a new file store from those already defined by selecting it from the list. You can create a new file store by clicking **New**.

    > [!IMPORTANT]
    > Before publishing the newly defined topology, the server that you specify must exist and be joined to the domain.

  - **Archiving**. Associate an Archiving SQL Server store with the Standard Edition server. You can select from an already defined Archiving store by selecting the server from the list, or click **New** to specify a new Archiving store.

    > [!IMPORTANT]
    > Before publishing the newly defined topology, the server that you specify must exist and be joined to the domain.

  - **Monitoring (CDR and QoE metrics**. Associate a Monitoring SQL Server store with the Standard Edition server. You can select from an already defined Monitoring Server by selecting the server from the list, or click **New** to specify a new Monitoring Server.

  - **Associate pool with an Office Web Apps Server**. Select this option to associate an Office Web Apps Server with the Front End pool. Select an existing server from the list, or click **New** to create a new Office Web Apps Server.

  - **Associate Edge pool**. Associate an Edge Server or pool with the Standard Edition server. You can select from an already defined Edge Server or pool by selecting the server from the list, or click **New** to specify a new Edge Server or pool.

### Resiliency

Resiliency provides disaster recovery and high availability for the server. By providing a backup, if the primary server fails, the backup can take over, enabling users to sign in and communicate. It is possible that there will be reduced functionality for users, depending on what systems have also failed.

From the list, select the Front End pool or Standard Edition server that will act as the backup for the server. You can also select to enable Failover and Fallback time intervals. Enabling the failover and fallback time settings (specified in seconds) enables automatic detection of a failed Registrar, and a fallback time to allow for automatic determination that the primary is back up.

> [!IMPORTANT]
> When defining the Failure detection and the Fallback interval, you should be careful not to enter an interval that will cause the failover and fallback to occur if the server should fail to respond for a short period of time. It is possible that the primary server may not respond for short periods of time, based on the loading of the pool or servers. The default values for the failover and fallback are 300 seconds and 600 seconds for pool to pool, or pool to Standard Edition server. In the event of a Survivable Branch Appliance or a Survivable Branch Server in a site to a pool or Standard Edition server, the default values are 120 seconds for failover and 240 seconds for fallback.

### Web Services

To edit or specify additional setting for the web services on the server, modify or specify settings in **Internal Web services** and **External Web services**.

For **Internal Web services**, you can specify the following:

- If you select Override FQDN, you can specify a different FQDN for the Internal Web services identity on the server. By default, the setting is the current server name as defined for the Standard Edition server.

- Listening and published ports for HTTP and HTTPS that your deployment requires. The default setting of port 80 for HTTP and port 443 for HTTPS are the most common settings, and typically do not need to be changed unless you have specific requirements within your organization and infrastructure design.

For **External Web services**, you can specify the following:

- The FQDN of the External Web services. The FQDN specified here will usually be defined by the requirements of your external connection requirements, such as the reverse proxy.

- Listening ports for HTTP and HTTPS that your deployment requires. The default setting of port 8080 for HTTP and port 4443 for HTTPS is defined initially. You change these settings for the listening ports based on what the requirements are for your reverse proxy and external network requirements. These values determine what ports the server will listen for incoming requests. Typically, these do not need to be changed, unless there is conflict of port requirements on the server.

### Mediation Server

For **Mediation Server**, you can specify the following:

- If you collocate the Mediation Server with the server, select the check box **Collocated Mediation Server enabled**. If you choose not to collocate the Mediation Server, none of the settings are available in this section.

- If you have enabled the collocation of the Mediation Server, you define the listening port range on the server for TLS. By default, this port is 5067. If you select **Enable TCP port**, you must define a TCP port for the collocated Mediation Server. This is an optional setting, and you should refer to the requirements of your gateway or PSTN requirements to determine if you need this. By default, the TCP port value is 5068.

- Trunks that are associated with the collocated Mediation Server. If you have already defined trunks, they will be available to associate with the Mediation Server.

- If you have more than one gateway associated with a Mediation Server, you can specify a default gateway by selecting the gateway and then clicking **Make Default**. To unselect a gateway as the default, click **Unmake Default**.

For details about defining and configuring the settings for the Standard Edition server, see [Defining and Configuring the Topology](https://technet.microsoft.com/library/51d1601e-4f83-48d4-ad08-3b4d5e2003aa.aspx) and [Deploying Mediation Servers and Defining Peers](https://technet.microsoft.com/library/a684f1da-6671-4011-adf6-2db49e2528e2.aspx).


