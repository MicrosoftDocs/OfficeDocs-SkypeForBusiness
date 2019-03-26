---
title: 'Configuring file transfer and URL filtering for instant messaging (IM)'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configuring file transfer and URL filtering for instant messaging (IM)
ms:assetid: 115a1a2c-599f-474c-a063-52f7144b5246
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg520952(v=OCS.15)
ms:contentKeyID: 48183440
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring file transfer and URL filtering for instant messaging (IM) in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-11-01_

The Intelligent IM Filter tool helps protect your Lync Server 2013 deployment against the spread of the most common forms of viruses with minimal degradation to the user experience. Use Intelligent IM Filter to configure filters to block unsolicited or potentially harmful instant messages from unknown endpoints outside the corporate firewall. You configure filters by specifying the criteria to be used to determine what should be blocked, such as instant messages containing hyperlinks with specific prefixes and files with specific extensions.

Intelligent IM Filter provides the following:

  - Enhanced URL filtering.

  - Enhanced file transfer filtering.

Configuring Intelligent IM Filter includes the following:

  - Configuring URL filtering.

  - Configuring file transfer filtering.

<div>

## How Filtering Options Are Applied to Instant Messages

Before you deploy the Intelligent IM Message Filter tool, you need to understand how filtering options are applied as messages are routed from one Lync Server 2013 server to another. The way these filtering options are applied is consistent, regardless of whether the servers are located in a single organization or across organizational boundaries. This consistency applies to the way that the customized notice and warning texts are inserted into messages and sent across servers.

<div>


> [!NOTE]
> The instant message filter increases the amount of CPU resources required to process URLs in a message. This increase in CPU demand also affects the performance of Lync Server.



</div>

By using the **URL Filter** page in the **IM and Presence** group in Lync Server Control Panel, you can block some or all hyperlinks or configure a warning. The warning is inserted at the beginning of an instant message that contains a hyperlink when you choose the **Hyperlink prefix** option **Send warning message**.

When an instant message travels from one server to another, the following general guidelines apply:

  - If a server blocks an instant message (because you selected the **Block URLs with file extension** check box on the **URL Filter** page or because you chose the **Hyperlink prefix** option **Block hyperlinks**), an error message is returned to the client. Subsequent servers do not receive this instant message.

  - If a server (Server1) adds a warning to an instant message that contains an active hyperlink, a subsequent server (Server2) that receives this instant message can still take a different action based on this active hyperlink present in the instant message and block the instant message or add a warning. If Server2 is configured only to add a warning for this URL, the earlier warning added by Server1 is removed, and the warning configured on Server2 is added to the beginning of the instant message.

<div>


> [!NOTE]
> If you are running Lync Server 2013 in a mixed environment, Live Communications Server 2005 with SP1 is the minimum version required to use the Intelligent IM Filter application. The Intelligent IM Filter is not supported on Live Communications Server 2005 without SP1.



</div>

<div>

## URL Filtering

URLs are filtered according to their hyperlink prefix. The following examples are valid prefixes:

  - www\*.

  - ftp.

  - http:

If you do not configure the instant message filter to perform any URL filtering, all URLs contained in instant messages are passed unmodified through the server. If you configure the instant message filter to perform URL filtering, URLs in instant messages are filtered according to the options that you select in the **Edit URL Filter** or **New URL Filter** dialog box.

  - **Enable URL filter**   This option enables URL filtering for the global deployment or for the site that you select.

  - **Block URLs with file extension**   The instant message filter blocks any active intranet or Internet URL that contains a file with an extension listed under **File type extensions to block** in the **Edit File Filter** dialog box. When a URL is blocked, an error message is displayed to the sender. When selected, this option takes precedence over all other filtering options for any file extensions defined under **File type extensions to block**.
    
    <div>
    

    > [!IMPORTANT]
    > Filtering of file extensions is limited to standard file names. Filtering may not work with file extensions embedded in other names.

    
    </div>

To configure how hyperlinks are handled in instant message conversations, select one of the following options under **Hyperlink prefix**:

  - **Do not filter**   URLs in messages are sent through the server. When you choose this option, the **Allow message** box appears. In the **Allow message** box, specify the notice that you want to insert at the beginning of each instant message containing hyperlinks. This notice can consist of no more than 65535 characters.

  - **Block hyperlinks**   Delivery of instant messages containing active hyperlinks is blocked by Lync Server, and an error message is displayed to the sender.

  - **Send warning message**   Lync Server permits active hyperlinks in instant messages, but it includes a warning. When you choose this option, the **Warning message** box appears. In the **Warning message** box, you must type the warning that you want to include with instant messages containing valid hyperlinks. For example, this warning might state the potential dangers of clicking an unknown link, or it might refer to your organization’s relevant policies and requirements. The warning can be no more than 65535 characters.

If you select **Block hyperlinks** or **Send warning message**, the following options are available:

  - **Exclude local intranet hyperlinks**   The instant message filter blocks only Internet URLs. URLs for locations within your intranet are passed unmodified through the server. However, the intranet URLs that individual servers running Lync Server pass depend on which types of local websites are considered part of their intranet zone. To check a server’s intranet zone settings, see the “To configure your intranet settings in Internet Explorer” procedure in [Modify the default URL filter in Lync Server 2013](lync-server-2013-modify-the-default-url-filter.md).

  - **Filter these hyperlink prefixes**   To choose which prefixes you want to block, click **Select**, and then, in **Select Hyperlink Prefix**, add the prefixes to the **Hyperlink prefixes** list.
    
    All prefixes except **href** must end with a period or a colon, or an asterisk followed by a period. Valid prefixes can contain any characters in the set of valid URL characters except the asterisk (\*). The set of valid URL characters is: \#\*+/0123456789=@ABCDEFGHIJKLMNOPQRSTUVWXYZ^\_\` abcdefghijklmnopqrstuvwxyz|~

</div>

<div>

## File Transfer Filtering

Filter transfer filtering affects both instant messages and conferences. For conferences, these settings affect the handout feature in the Office Live Meeting 2007 client and multimedia playback features.

<div>


> [!NOTE]
> Lync Server also offers file transfer setting options. This server-side option is offered in addition to the client-side controls available in Lync Server.



</div>

You can filter file transfers during instant message conversations, when you are using the handout feature in the Office Live Meeting 2007 client, and for multimedia playback features for all file types. You can set the following options to control file transfers:

  - **Enable file filter**   This option enables file filtering for the global deployment or for the site that you select.
    
    When you enable the file filter, you can choose one of the following options in **File transfer**:
    
      - **Block specific file types**   You specify which file transfer requests are filtered by the server by specifying a list of file extensions to block. Entries in the list can contain all standard characters, but not the wildcard character (\*). In the Office Live Meeting 2007 client the handout feature is enabled, but any file with this extension cannot be uploaded or downloaded. If you select the **Block URLs with file extension** check box on the settings for a URL filter listed on the **URL Filter** tab, the URL filter uses this same list to block active hyperlinks that contain any of these file extensions. To choose which file types you want to block, click **Select**, and then, in **Select File Type**, add the file type extensions to the **Selected file type extensions** list.
    
      - **Block All**   The server drops all instant messages that contain file transfer requests and returns an error message to the sender of the request. The handout feature in the Office Live Meeting 2007 client is disabled.

<div>


> [!IMPORTANT]
> Filtering of file extensions is limited to standard file names. Filtering may not work with file extensions embedded in other names.



</div>

</div>

</div>

<div>

## In This Section

  - [Modify the default file transfer filter in Lync Server 2013](lync-server-2013-modify-the-default-file-transfer-filter.md)

  - [Create a new file transfer filter in Lync Server 2013 for a specific site](lync-server-2013-create-a-new-file-transfer-filter-for-a-specific-site.md)

  - [Modify the default URL filter in Lync Server 2013](lync-server-2013-modify-the-default-url-filter.md)

  - [Create a new URL filter in Lync Server 2013 to handle hyperlinks in IM conversations](lync-server-2013-create-a-new-url-filter-to-handle-hyperlinks-in-im-conversations.md)

</div>

<div>

## See Also


[Managing IM and presence settings in Lync Server 2013](lync-server-2013-managing-im-and-presence-settings.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

