---
title: "Assigning per-user presence policies in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: fd1097b7-248d-4b78-8c43-456b03257c18

description: "A presence policy is a set of limits and restrictions that affect presence. The following table describes the presence policy settings available in Lync Server 2013."
---

# Assigning per-user presence policies in Lync Server 2013
[]
A presence policy is a set of limits and restrictions that affect presence. The following table describes the presence policy settings available in Lync Server 2013.
  
**Presence Policy Settings**

|**XML name**|**Display name**|**Description**|**Type**|**Value**|
|:-----|:-----|:-----|:-----|:-----|
|CategorySubscriptions  <br/> |Maximum Number of Subscriber Category Subscriptions  <br/> |Limits the number of subscriber category subscriptions. For example, when Communicator subscribes to a user's presence, it obtains a category subscription for each of the contact card, calendar data, notes, services, and state categories.  <br/> A setting of 0 means that the user or contact object cannot be subscribed to by others.  <br/> > [!NOTE]> This setting can have a significant impact on performance if it is set to a high number, and the average user has a large number of users subscribing to his or her presence.           |Integer  <br/> |0-3000  <br/> |
|PromptedSubscribers  <br/> |Maximum Number of Queued Presence Subscription Alerts  <br/> |Limits the number of entries in the prompted subscribers table. This setting determines the maximum number of prompts that can be queued for a given user. For example, when user A subscribes to user B's presence, user B receives a prompt that user A is now subscribed to user B, and an acknowledgement prompt is created in user B's prompted subscribers table. After user B accepts, or acknowledges, the subscription, the acknowledgement prompt is removed from user B's prompted subscribers table.  <br/> A setting of 0 means that the user is not prompted when someone subscribes to his or her presence.  <br/> |Integer or Token  <br/> |0-500  <br/> |
   
By default, the **Default Policy** and **Service: Medium** presence policies are installed when you deploy Lync Server. The following table describes the specific settings of the two presence policies. 
  
**Presence Policies**

|**Policy name**|**Description**|**CategorySubscriptions**|**PromptedSubscribers**|
|:-----|:-----|:-----|:-----|
|Default Policy  <br/> |Policy for typical users. This is the default presence policy.  <br/> |1000  <br/> |200  <br/> |
|Service: Medium  <br/> |Policy for applications that require more users to subscribe to the object's presence.  <br/> |1000  <br/> |0  <br/> |
   

