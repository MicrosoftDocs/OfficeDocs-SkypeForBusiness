---
title: "Configure IP address types in Skype for Business"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection:
- IT_Skype16
- Strat_SB_Admin
ms.custom:
ms.assetid: 17e756c0-6652-4cd5-b185-4b25929e3a42
description: "Summary: Review the IP Address type considerations below before implementing Skype for Business Server."
---

# Configure IP address types in Skype for Business

**Summary:** Review the IP Address type considerations below before implementing Skype for Business Server.

You deploy IP address types by using topology settings that you configure in Topology Builder. This section describes how to deploy IP address types on Front End Servers, Mediation Servers, and Edge Servers.

## Deploy IP address types on a Front End Server

Using Topology Builder, perform the steps in the following procedure to deploy IP address types on a Front End Server.

### To deploy IP address types on a Front End Server

1. Under **Enterprise Edition Front End pools**, right-click the server within a pool, and then select **Edit Properties**. (Alternatively, select the server, and then click **Edit Properties** from the **Action** menu.)

2. In the **Edit Properties** dialog box, select the IP address type that you want to configure. For a dual-stack configuration, select **Enable IPv4** and **Enable IPv6**.

   **Edit Properties dialog box for the Front End Server pool**

   - **Use all configured IP addresses**. Select this option if you want to allow any IP address defined on the computer to be used.

     > [!NOTE]
     > This is the recommended option for IP version 6 (IPv6) configurations.

   - **Limit service usage to selected IP addresses**. Select this option to specify a specific address to use on the new server. If you select this option, you must enter a value for **Primary IP address**.

   - **Primary IP address**. Enter an IP address that the server will use for all communications except public switched telephone network (PSTN). The IP address entered must match the format of the select address type.

   - **PSTN IP address**. Define a PSTN IP address when a Mediation Server is collocated on the Front End Server. This address must match the format of the selected address type.

> [!NOTE]
> The installation of additional network interface cards (NICs) to support the PSTN IP address configuration (or for any other reason) on Front End Servers is not supported. For more information about supported NIC configurations for Skype for Business Server, see [Server hardware platforms for Lync Server 2013](https://technet.microsoft.com/library/c964c1c0-0153-472b-88ad-a38866e0df0c.aspx).

## Deploy IP address types on a Mediation Server

Using Topology Builder, perform the steps in the following procedure to deploy IP address types on a Mediation Server.

### To deploy IP address types on a Mediation Server

- In Topology Builder, under **Mediation pools**, right-click the server within a pool, and then select **Edit Properties**. (Alternatively, select the server, and then click **Edit Properties** from the **Action** menu.)

- In the **Edit Properties** dialog box, select the IP address type that you want to configure. For a dual-stack configuration, select **Enable IPv4** and **Enable IPv6**, as shown in the following figure.

   **Edit Properties dialog box for the Mediation Server pool**

  - **Use all configured IP addresses**. Select this option if you want to allow any IP address defined on the computer to be used.

    > [!NOTE]
    > This is the recommended option for IP version 6 (IPv6) configurations.

  - **Limit service usage to selected IP addresses**. Select this option to specify a specific address to use on the new server. If you select this option, you must enter a value for Primary IP address.

  - **Primary IP address**. Enter an IP address that the server will use for all communications except public switched telephone network (PSTN). The IP address entered must match the format of the select address type.

  - **PSTN IP address**. Define a PSTN IP address when a Mediation Server is collocated on the Front End Server. This address must match the format of the selected address type.
> [!IMPORTANT]
> We only support two network cards on *dedicated* Mediation Servers. If the Mediation Sserver role is collocated on the Front End, then dual network cards are not supported. 

> [!NOTE]
> - For more information about supported NIC configurations for Skype for Business Server 2015, see [Hardware for Skype for Business Server 2015](../requirements-for-your-environment/server-requirements.md#hardware-for-skype-for-business-server-2015)
> - For more information about supported NIC configurations for Skype for Business Server 2019, see [Hardware for Skype for Business Server 2019](../../../SfBServer2019/plan/system-requirements.md#hardware-for-skype-for-business-server-2019)



## Deploy IP address types on an Edge Server

Using Topology Builder, perform the following steps:

### To deploy IP address types on an Edge Server

1. In Topology Builder, under **Edge pools**, right-click the server within a pool, and then select **Edit Properties**. (Alternatively, select the server, and then click **Edit Properties** from the **Action** menu.)

2. In the **Edit Properties** window, select the IP address configuration that you want to support.

3. For each address type that you select, you must supply appropriate internal and external addresses.
