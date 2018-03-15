---
title: "Capacity planning for Group Call Pickup in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 0d654a19-6cf0-4118-903d-ec2c4e519253

---

# Capacity planning for Group Call Pickup in Lync Server 2013
[]The following table describes the Group Call Pickup user model that you can use as the basis for capacity planning requirements.
  
> [!IMPORTANT]
> Group Call Pickup is based on the Call Park application. Keep in mind that, for disaster recovery capacity planning, each pool of a paired pool should be able to handle the workloads for Call Park services, including Group Call Pickup, in both pools. 
  
**Group Call Pickup User Model**

|**Metric**|**Per Front End pool  <br/>  (with 8 Front End Servers)**|**Per Standard Edition server**|
|:-----|:-----|:-----|
|Recommended number of users per group  <br/> |50  <br/> |50  <br/> |
|Recommended number of groups  <br/> |500  <br/> |60  <br/> |
|Maximum number of users per pool enabled for Group Call Pickup  <br/> |25,000  <br/> |3,000  <br/> |
|Maximum rate of incoming calls to total users enabled for Group Call Pickup per pool per minute  <br/> |500  <br/> |60  <br/> |
|Maximum rate of calls retrieved by users with Group Call Pickup per pool per minute  <br/> |200  <br/> |25  <br/> |
   
> [!NOTE]
>  For Front End pools that have fewer than eight Front End Servers, calculate the metrics linearly. For example, if your Front End pool has one Front End Server, calculate the maximum load as 1/8 of the values shown in the table. >  You can increase or decrease the recommended number of users per group and number of groups as long as you do not exceed the maximum number of users per pool. For example, your Standard Edition server can have 120 groups with 25 users per group because the number of users enabled for Group Call Pickup is still within the user model maximum (that is, 120 groups times 25 users is 3,000 users enabled for Group Call Pickup). 
  

