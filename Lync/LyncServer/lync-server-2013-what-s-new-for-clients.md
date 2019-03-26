---
title: "Lync Server 2013: What's new for clients"
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: What's new for clients
ms:assetid: 5c144677-4d58-4fc3-8445-74b76c9fcf07
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204933(v=OCS.15)
ms:contentKeyID: 48184253
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# What's new for clients in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-19_

Microsoft Lync 2013 has a redesigned user interface and important new features. For administrators, the client is now included with the Office setup program, providing a more streamlined approach to deploying Office and customizing clients in your organization.

<div>


> [!NOTE]  
> For an illustrated view of Lync 2013 user interface updates, see “What’s New in Lync 2013” at <A href="http://go.microsoft.com/fwlink/?linkid=273885">http://go.microsoft.com/fwlink/?LinkId=273885</A>.



</div>

<div>

## Integration with Office Setup

The Lync 2013 client and the Online Meeting Add-in for Lync 2013—which supports meeting management from within the Outlook messaging and collaboration client—are now both included with the Office 2013 Setup program.

In previous versions of Lync and Office Communicator, you could use Windows Installer properties to customize and control the Office installation. Because Lync 2013 is integrated with Office setup, you can use the following methods to customize Lync 2013 setup:

  - Use the Office Customization Tool (OCT)

  - Use the Config.xml to perform installation tasks

  - Use Setup Command-Line Options

<div>


> [!NOTE]  
> The Lync 2013 setup program does not uninstall previous versions of Lync or Office Communicator. The Lync 2013 client installs side-by-side with other Lync or Office Communicator clients



</div>

For details, see [Deploying Lync clients in Lync Server 2013](lync-server-2013-deploying-lync-clients.md).

</div>

<div>

## Group Policy Deployment

Because Lync 2013 is now included in Office setup, the method for deploying Lync Group Policy settings has changed. In previous versions of Lync and Office Communicator, you could use the Communicator.adm to define Group Policy settings, whereas in Lync 2013 you can now use the Lync ADMX and ADML administrative templates that are provided along with the Office Group Policy Administrative Templates.

For details, see [Group Policy settings for Lync 2013](lync-server-2013-group-policy-settings-for-lync-2013.md).

</div>

<div>

## Outlook Scheduling Add-in Updates

The Online Meeting Add-in for Lync 2013 includes meeting invite customization and new meeting options.

  - Administrators can customize the organization’s meeting invitations by adding a custom logo, a support URL, a legal disclaimer URL, or custom footer text. For details, see [Customizing the Online Meeting Add-in in Lync Server 2013](lync-server-2013-customizing-the-online-meeting-add-in.md).

  - New attendee mute controls allow meeting organizers to schedule conferences that have attendee audio and video muted by default.

</div>

<div>

## Virtual Desktop Infrastructure Plug-in

The Lync 2013 client now supports audio and video in a Virtual Desktop Infrastructure (VDI) environment. A user can connect an audio or video device (for example, a headset or a camera) to the local computer (for example, a thin client or repurposed computer). The user can connect to the virtual machine, sign in to the Lync 2013 client that is running on the virtual machine, and participate in real-time audio and video communication as though the client is running locally. The following features are supported in a virtual desktop environment:

  - Device integration for audio and video, including the following:
    
      - Call controls from the device
    
      - Presence integration on the device
    
      - Multiple HID (human interface device) support

  - Location and emergency services support.

  - Support for all Lync modalities, including IM, audio, video, application sharing, desktop sharing, PowerPoint sharing, whiteboard, and file transfer.

  - Audio and video support in person-to-person calls and conference calls.

For information about deploying the VDI plug-in, see [Deploying the Lync VDI plug-in in Lync Server 2013](lync-server-2013-deploying-the-lync-vdi-plug-in.md).

</div>

<div>

## Video Enhancements

Several new features significantly enhance the video experience for conference participants.

  - Video is enhanced with face detection and smart framing, so that a participant’s video moves to help keep them centered in the frame.

  - High-definition video is now supported in two-party calls and multiparty conferences. Users can experience resolutions up to HD 1080P.

  - Participants can select from different meeting layouts: Gallery View shows all participants’ pictures or videos; Speaker View shows the meeting content and only the current speaker’s video or picture; Presentation View shows meeting content only; Compact View shows just the meeting controls.

  - With the new Gallery feature, participants can see multiple video feeds at the same time. If the conference has more than five participants, video feeds of only the most active participants appear in the top row, and pictures appear for the other participants.

  - Participants can use video pinning to select one or more of the available video feeds to be visible at all times.

  - Presenters can use the Video Spotlight feature to select one person’s video feed so that every participant in the meeting sees that participant only.

</div>

<div>

## Chat Room Integration

Lync 2013 now integrates the features previously provided by Lync 2010 Group Chat. A separate group chat client is no longer required.

  - From within Lync 2013, users can search for chat rooms, add chat rooms to their contacts, monitor chat room activity, and read and post messages.

  - Users can create topic feeds so that they’ll be notified if someone in one of their chat rooms adds a post containing specific keywords.

  - With the new **Persistent Chat** options page, users can set notification alerts and sounds that apply when people post messages to their chat rooms.

</div>

<div>

## Lync Web App Updates

Lync Web App is the web-based conferencing client for Lync Server 2013 meetings. In this release, the addition of computer audio and video to Lync Web App provides a complete in-meeting experience for anyone who doesn’t have a Lync client installed locally. Meeting participants have access to all collaboration and sharing features and presenter meeting controls.

When a user tries to join a meeting but doesn’t have a locally installed client, Lync Web App opens. If you want to allow additional options for joining the meeting, you can configure the Meeting Join page; see [Configuring the meeting join page in Lync Server 2013](lync-server-2013-configuring-the-meeting-join-page.md) in the Deployment documentation.

Because of the enhancements to Lync Web App, an updated version of Attendee isn’t available for Lync Server 2013. Lync Web App is the client of choice for participants outside your organization. No local client installation is required, although audio, video, and sharing features require a plug-in to be installed at first use.

</div>

<div>

## Lync 2013 for Mobile Clients Updates

In addition to enhanced presence, contacts, and IM capabilities, Lync 2013 mobile clients now provide voice and video calling over the Internet and cellular data connections. With a single tap of the meeting link in a calendar item, mobile users can join Lync voice and video meetings. For more information about Lync 2013 mobile clients, see [Planning for mobile clients in Lync Server 2013](lync-server-2013-planning-for-mobile-clients.md).

</div>

<div>

## Lync 2013 User Interface Updates

<div>

## Accessibility Updates

Lync 2013 incorporates several new accessibility features.

  - Lync 2013 supports high DPI resolution, enabling users to scale text and graphics for 125% and 150% dots per inch.

  - Lync provides high-contrast support so that the user interface remains fully functional when used with high contrast themes in Windows.

  - Lync offers more than 100 keyboard shortcuts so that users can access important functions without a mouse. For example, users can press Alt+C to accept a call, or Alt + I to ignore it, without having to tab or set the focus. Pressing (Alt+Q) ends a call, (Ctrl+N) starts OneNote, and (Alt+T) opens the Tools menu.

  - Extensive screen reader support in Lync 2013 ensures that all notifications, incoming requests, and instant messages are read aloud when a screen reader is enabled.

</div>

<div>

## Presence While Sharing

When Lync detects that a user is sharing, Lync automatically assigns the user a Presenting presence status. This status blocks all incoming communications unless the sender is assigned the Workgroup privacy relationship. If the user is using the sharing feature entirely on a secondary monitor, Lync does not assign a Presenting presence status.

</div>

<div>

## Conversation Window Updates

The redesigned Conversation window provides quicker access to important features.

  - With the new tabbed conversations feature, users can now keep all their IMs and chat rooms in one Conversation window. The tabs along the left side of the Conversation window let users navigate easily among all active conversations.

  - Users can pop out an individual conversation into a separate window, and then resize the window. They can also pop the window back into the main Conversation window.

  - Lync 2013 reopens a user’s conversations when the user signs out and signs back in to Lync.

  - Users can quickly add IM, video, program sharing, desktop sharing, or web conferencing tools (whiteboard, meeting notes, shared notebooks, and attachments) to any conversation.

  - In a meeting where video or content is being shared, users can pop out the meeting video or shared content, and then resize the window.

</div>

<div>

## Lync Main Window Updates

The new streamlined look retains familiar features such as the **What’s happening today?** note field, the status selector, and the **Set Your Location** selector.

  - When chat rooms are enabled, users see a new **Chat Rooms** icon on the main Lync page. With the **Chat Rooms** icon, users can quickly access their chat rooms and filters.

  - Users can click the view icons to switch to the **Contacts** view, **Chat Rooms** view, **Conversations** view, or **Phone** view.

  - If users have been migrated to Exchange 2013, they can upload a high resolution picture.

</div>

<div>

## Contacts View and Contact Card Updates

Lync 2013 gives users different ways to view contacts and groups in their **Contacts** view.

  - With the new unified contact store, after users' Lync contacts are migrated to Exchange 2013, the users can access and manage their contacts from Lync 2013, Outlook, or Outlook Web App, and their Favorites stay synchronized. For example, if a user adds a contact to Favorites in Outlook, the contact appears in the Favorites group in Lync 2013.

  - If you have added and configured the XMPP proxy and XMPP gateway, users can add contacts from XMPP-based partners for instant messaging and presence.

  - A new **Add a Contact That’s Not in My Organization** feature gives users an easy way to add people who are external to the organization.

  - A new **Favorites** group lets users build a list of people users contact most often for quicker access.

  - Users can use the new **Contacts List** options page to choose how users want to sort and display contacts. Users can select an expanded, two-line view that shows contacts’ pictures, or a condensed one-line view. Users can also sort contacts alphabetically or by availability.

</div>

<div>

## Conferencing Updates

Lync 2013 offers several enhancements to conferencing features.

  - Depending on the type of meeting, users can now mute the audience and allow or block video sharing when scheduling the meeting. These options are available on the **Meeting Options** page and are recommended for large meetings with more than 20 participants.

  - Easy to use audio controls in the meeting room allow the user to control audio options, such as mute, unmute, change device, and so on.

  - When sharing programs, users can select multiple programs to share if they need to work with more than one program.

  - Users can now upload presentations that contain video clips by uploading the PowerPoint file, and pointing the mouse over the slide to display video controls, such as play, pause, and audio controls.

  - While in a meeting, users can merge another open conversation into the meeting by using **Merge This Call Into** on the **More Options** (**…**) menu.

  - To see the participants’ names, users can hover the mouse over the **View Participants** button, or click **Show Participant List** to dock the panel in the meeting.

  - Depending on the meeting type, users can select from several different content and participant views.

  - Meeting recordings are automatically saved in a format that plays in Windows Media Player (MP4). Users can easily share the file with anyone, or use the **Publish** feature in recording manager to post the recording on a shared location.

  - OneNote enables new ways to collaborate in a meeting. During a meeting, users can take notes with OneNote for personal use after the meeting, or use shared notebooks and co-edit with meeting participants in real time. All team members can access the shared notes to contribute information, brainstorm ideas, or use the notebook pages as a virtual whiteboard. People and content shared in the meeting are automatically added to the Notes.

  - Users can switch between content types using **Share content and lead meeting activities** at the bottom of the meeting room. Users can also use the **Manage Presentable Content** menu to choose which content they want to share.

</div>

</div>

<div>

## See Also


[Planning for clients in Lync Server 2013](lync-server-2013-planning-for-clients.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

