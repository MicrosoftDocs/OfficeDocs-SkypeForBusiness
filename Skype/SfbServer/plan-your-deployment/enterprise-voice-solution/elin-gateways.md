---
title: "Manage locations for ELIN gateways in Skype for Business Server"
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
ms.assetid: ced79c13-4e7e-4034-95cd-6fc913f4f222
description: "Decisions necessary for planning an the location information database, or a similar external database, for an E9-1-1 deployment using ELIN gateways, in Skype for Business Server Enterprise Voice."
---

# Manage locations for ELIN gateways in Skype for Business Server

Decisions necessary for planning an the location information database, or a similar external database, for an E9-1-1 deployment using ELIN gateways, in Skype for Business Server Enterprise Voice.

To have Skype for Business Server automatically provide locations for clients within a network, you need to perform the following tasks:

- Populate the Location Information service database with a network wiremap, and include the Emergency Location Identification Numbers (ELINs) in the CompanyName field.

- Publish the locations so that they are available for clients in your network.

- Upload the ELINs to your public switched telephone network (PSTN) carrier's Automatic Location Identification (ALI) database.

For details about how to perform these tasks, see [Configure the Location Database](https://technet.microsoft.com/library/8544be31-6958-47ef-b926-fdc80d56191c.aspx) in the Deployment documentation.

> [!NOTE]
> Locations added to the central location database are not available to the client until they have been published by using a Skype for Business Server Management Shell command and are replicated to the pool's local stores. For details, see [Publishing the Location Database](https://technet.microsoft.com/library/dd032b5b-df0e-4017-ac46-e17570c1ab1e.aspx) in the Deployment documentation.

This section describes things to consider as you plan to update and maintain the location database.

## Planning Emergency Locations

When you use ELIN gateways, you populate the Location Information service database with the civic address, a specific location within a building, and at least one ELIN for each location . During the planning phase, it is a good idea to decide how you want to name the locations and how you want to assign ELINs.

### Planning Location Names

The Location Information service **Location** field, which holds the specific location within a building, has a maximum length of 20 characters (including spaces). Within that limited length, try to include the following:

- An easy-to-understand name that identifies the location of the 911 caller to help ensure that emergency responders find the specific location promptly when they arrive at the civic address. This location name may include a building number, floor number, wing designator, room number, and so on. Avoid nicknames that are known only to employees, which might cause emergency responders to go to the wrong location.

- A location identifier that helps users to easily see that their client picked up the correct location. The Skype for Business client automatically concatenates and displays the discovered **Location** and **City** fields in its header. A good practice is to add the street address of the building to each location identifier (for example, "1st Floor <street number>"). Without the street address, a generic location identifier such as "1st Floor" could apply to any building in the city.

- If the location is approximate because it's determined by a wireless access point, you may want to add the word **[Near]** (for example, "Near 1st Floor 1234").

### Planning ELINs

After you decide how you want to divide your building space into locations, you need to decide how many ELINs to assign to each location. For example, in a multifloor or multitenant building, different areas in the building can be assigned different emergency zones. Typically, each floor in a building is designated as a location. Each location is then assigned one or more ELINs, which are used as the calling number(s) during an emergency call. Contact your PSTN carrier for phone numbers that you can use for ELINs. The following table provides an example of locations for a specific street address.

**Sample Location and ELIN Assignments**

|**Building Area**|**Location**|**ELIN**|
|:-----|:-----|:-----|
|First floor  <br/> |1  <br/> |425-555-0100  <br/> |
|Second floor  <br/> |2  <br/> |425-555-0111  <br/> |
|Third floor  <br/> |3  <br/> |425-555-0123  <br/> |

The locations you define should meet the following requirements:

- Comply with local and national/regional regulations in terms of maximum area per location and number of locations per street address.

- Are specific enough to make it easy to locate the emergency caller.

## Populating the Location Database

The following questions will help you determine how to will populate the location database.

 **What process will you use to populate the location database?**

Where does the data exist, and what steps do you need to take to convert the data into the format required by the location database? Will you add locations individually, or in bulk, by using a CSV file?

 **Do you have a third party database that already contains a mapping of locations?**

By using the Secondary Location Information service option to connect to a third-party database, you can group and manage locations by using an offline platform. A benefit to this approach is that in addition to associating locations to network identifiers, you can associate locations to a user. This means that the Location Information service can return multiple addresses, originating from the Secondary Location Information service, to a Skype for Business client. The user can then choose the most appropriate location.

To integrate with the Location Information service, the third-party database must follow the Skype for Business Server Location Request/Response schema. For details, see [Web Service for E911 Support Protocol](https://go.microsoft.com/fwlink/p/?linkid=213819). For details about deploying a Secondary Location Information service, see [Configure a secondary Location Information service in Skype for Business Server](../../deploy/deploy-enterprise-voice/secondary-location-information-service.md) in the Deployment documentation.

For details about populating the location database, see [Configure the Location Database](https://technet.microsoft.com/library/8544be31-6958-47ef-b926-fdc80d56191c.aspx) in the Deployment documentation.

## Maintaining the Location Database

After you populate the location database, you need to develop a strategy for updating the database as the network configuration changes. The following questions will help you determine how to maintain the location database.

 **How will you update the location database?**

There are several scenarios that require an update to the location database, including adding wireless access points (WAPs), office recabling (resulting in different switch assignments), and subnet expansion. Will you directly update each individual location, or will you perform a bulk update of all the locations by using a CSV file?

 **Will you use an SNMP application to match Skype for Business client MAC addresses to port and switch identifiers?**

If you use an SNMP application, you need to develop a manual process for keeping the switch chassis and port information consistent between the SNMP application and the location database. If the SNMP application returns a chassis IP address or port ID that is not included in the database, the Location Information service will not be able to return a location to the client.


