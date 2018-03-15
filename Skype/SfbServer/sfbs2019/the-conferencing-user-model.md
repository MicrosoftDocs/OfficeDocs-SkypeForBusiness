---
title: "The conferencing user model in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: ba4bbba9-f2e3-4cab-8eba-b51f12133cab
description: "A critical part of the Lync Server conferencing user model is meeting size. After collecting data from the multiple data points (as described in the previous section), we determined the following:"
---

# The conferencing user model in Lync Server 2013
[]
A critical part of the Lync Server conferencing user model is meeting size. After collecting data from the multiple data points (as described in the previous section), we determined the following:
  
- Most meetings are actually small collaborative meetings with an average of four to six participants
    
- Approximately 80 percent of meetings have fewer than 20 participants.
    
- 99.98 percent of meetings have fewer than 100 participants.
    
In addition to meeting size, the conferencing user model also takes into account a variety of factors, such as:
  
- **Concurrent meetings** How many users are expected to be in meetings at the same time? 
    
- **Media mix** What types of media are available and expected to be used by users in meetings? 
    
- **User types** Are users internal users, remote users, federated users, or anonymous users? 
    
- **Meeting ramp up time** How long does it take for all users of a meeting to join a meeting? 
    
For details about the user model, see [User models in Lync Server 2013](lync-server-2013-user-models.md). 
  
To determine the number of meetings and users to use for testing, we did the following:
  
- Took the total number of users in an organization (for example, 80,000 users) and multiplied it by the meeting concurrency rate (for example, 5% of all users) to determine the total number of users expected to be in meetings at the same time (in this example, 4000 users).
    
- Divided the total number of users by the number of Lync Server 2013, Front End Servers in the deployment (for example, 8 servers) to determine the estimated number of meeting participants per Front End Server (in this example, 500 users per Front End Server).
    
- Divided the number of users per Front End Server by the average meeting size (for example, 4 users) to determine the estimated average number of meetings per Front End Server (in this example, 125 meetings per Front End Server).
    
- To get the per media load on each Front End Server, we estimated the media mix. For example, assuming that 75% of the meetings require more than just audio support and 50% of those meetings require application sharing, an average of 47 meetings and 188 users connect concurrently to each Front End Server for application sharing.
    
- Tested a variety of meeting sizes (based our user model of up to 250 users in a shared pool) to ensure server scalability.
    

