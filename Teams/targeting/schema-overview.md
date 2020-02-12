---
title: Set up the Team Targeting schema
author: lanachin
ms.author: v-lanac
manager: serdars
ms.topic: conceptual
ms.service: msteams
ms.reviewer: andfried
search.appverid: MET150
description: Learn how to set up the team targeting schema to support a hierarchy of teams.
localization_priority: Normal
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
appliesto: 
- Microsoft Teams
---

# Set up your team targeting schema

To create a hierarchy of teams that can be used by your organization to publish content to a large set of teams, you need to set up your team targeting schema. The schema defines how all the teams in your hierarchy are related to each other, and the attributes that can be used to filter your teams. After you create the schema, you upload it to Teams and it's applied throughout your organization. After the schema is uploaded, apps within the Teams client can use it.

> [!IMPORTANT]
> You won't see a hierarchy of teams when you're browsing teams or channels within them. To see the hierarchy of teams, you need to use an app that supports it. For the initial release of teams targeting, only the Tasks app supports hierarchical teams.

## Plan your schema

Before you create the schema that defines your hierarchy, you need to do some planning and decide how you want to shape your organization. This includes deciding which organizational groups need to publish tasks to other groups. Each node in the hierarchy represents a working group or group of groups. Nodes at the bottom of the hierarchy (those without children) are teams that can be targeted for tasks while other nodes (parents) are organizational groups with permission to publish tasks downward.

For example, in the following hierarchy, Recall, Communications, and HR, can publish tasks to every bottom node in the hierarchy, whereas North East Zonal Office can only publish tasks to New York Store and Boston Store. This hierarchy allows the Recall, Communications, and HR groups to publish tasks that apply to the entire company, such as benefits information or messages from the CEO. The North East Zonal Office group can publish tasks, such as personnel scheduling, weather information, and so on, only to the New York and Boston stores.

![Team targeting hierarchical example](../media/team-targeting-schema-example.png)

## Create your schema

The team targeting schema is based on a comma-separated values (CSV) file. Every row in the CSV file corresponds to one node within the hierarchy of teams. Each row contains information that names the node within the hierarchy, optionally links it to a team, and includes attributes that can be used to filter teams in apps that support it. You can also define buckets, which are categories that the publishing team can use to organize content sent to recipient teams to make it easier to view, sort, and focus on relevant content.

### Add required columns

The CSV file must contain the following three columns, in the following order, starting at the first column. A node must be linked to a team for it to receive tasks. You can have up to 10,000 nodes in the schema.

| Column name   | Required | Description   |
----------------|----------|---------------|
| TargetName    | Yes      | This is the name of the node. The name can be up to 100 characters long and contain only the characters A-Z, a-z, and 0-9. Node names must be unique. |
| ParentName    | Yes       | This is the name of the parent node. The value you specify here must match the value in the TargetName field of the parent node exactly. If you want to add more than one parent node, separate each parent node name with a semicolon (;). You can add up to 25 parent nodes, and each parent node name can be up to 2500 characters long. <br>**IMPORTANT** Be careful not to create a loop where a parent higher up in the hierarchy references a child node lower in the hierarchy. This isn't supported. |
| TeamID        | Yes, if the team receives tasks from a parent node       | This contains the ID of the team you want to link a node to. A node must be linked to a team if you want it to receive tasks from a parent node. If you want to add a node only for organization and filtering purposes, you don't need to link that node to a team and can leave this field blank. You can link each node to only one team.<br>To get the ID of a team you want to link a node to, run the following PowerShell command: `Get-Team | Export-Csv TeamList.csv`. This lists the teams in your organization and includes the name and ID for each team. Find the name of the team you want to link to, and then copy the ID into this field.<br> |

### Add attribute columns

After you add the three required columns, you can add attribute columns. These attributes can be used to filter nodes so that you can more easily select the ones you want to publish tasks to. When you add an attribute column, keep the following in mind:

- The column name you specify becomes the name of the attribute. This value will be displayed in the Teams apps that use the schema.
- The column name can be up to 100 characters long and contain only the characters A-Z, a-z, and 0-9. Column names must be unique.
- You can add a maximum of 50 attribute columns.

Each row can contain one value for each attribute, and each value can be up to 100 characters long. The attribute values you specify in each column will be displayed as available filter values for the attribute in Teams apps that use the schema. Each attribute column can have up to 50 unique values.

### Add bucket columns

You can add bucket columns to create buckets, which are topics into which tasks can be organized. The publishing team can then use these to categorize tasks for the recipient teams who can then sort their tasks by bucket to focus on relevant tasks.

You can map buckets to standard channels of the team. (Mapping to private channels isn't supported at this time.) When you map a bucket to a channel, tasks in that channel are filtered to show only those buckets that are mapped to it.

When you add a bucket column, note the following:

- The column name becomes the name of the bucket. Each bucket you specify will appear in the Buckets list in the Teams apps that use the schema.
- The column name must be preceded by a hashtag (#). It can be up to 100 characters long and contain only the characters A-Z, a-z, and 0-9. **<-IS THIS CORRECT?** For example, #Operations and #Frozen Goods.
- You can map a bucket to only one channel. This means that each row can contain only one value for each bucket.
- To map a bucket, enter the channel name in the field. If you leave a field blank, the bucket is mapped to the General channel by default. You can also enter **:::no-loc text="General":::** if you want to map to the General channel.
- You can add a maximum of 25 bucket columns.

### Example

Here's an example of a schema CSV file that would be created to support the hierarchy shown in the image above. This schema contains the three required columns, `TargetName`, `ParentName`, and `TeamID`, two additional attribute columns named `TimeZone` and `StoreType`, and three bucket columns named `Operations`, `Fresh Foods`, and `Frozen Goods`. The `TimeZone` attribute has values for each of the time zones in the United States. The `StoreType` attribute has values that include `Grocery`, `Electronics`, `Clothing`, and `Corporate`, `Regional`, and `Zone`. The `TimeZone` and `StoreType` attributes aren't shown in the image above; they're added here to help show how attributes can be added to node entries. The same is true for the three bucket columns.

| TargetName             | ParentName                      | TeamId                               | TimeZone | StoreType   |#Operations|#Fresh Foods|#Frozen Goods|
|------------------------|---------------------------------|--------------------------------------|----------|-------------|---|---|---|
| Recall                 |                                 | db23e6ba-04a6-412a-95e8-49e5b01943ba | Central  | Corporate   |||
| Communications         |                                 | 145399ce-a761-4843-a110-3077249037fc | Central  | Corporate   ||||
| HR                     |                                 | b8f7db91-201c-4cf9-9f7e-90a4894ed8e4 | Central  | Corporate   ||||
| East Regional Office   |                                 |                                      | Eastern  | Regional    ||||
| West Regional Office   |                                 |                                      | Pacific  | Regional    ||||
| North East Zone        | East Regional Office            |                                      | Eastern  | Zone        ||||
| South East Zone        | East Regional Office            |                                      | Eastern  | Zone        ||||
| New York Store         | North East Zone                 | e2ba65f6-25e7-488b-b8f0-b8562d5de60a | Eastern  | Electronics ||||
| Boston Store           | North East Zone                 | 0454f08a-0507-437c-969a-682eb2fae7fc | Eastern  | Electronics ||||
| Miami Store            | South East Zone                 | 619d6e4e-5f68-4b36-8e1f-16c98d7396c1 | Eastern  | Grocery     ||||
| New Orleans Store      | South East Zone                 | 6be960b8-72af-4561-a343-9ac4711874eb | Central  | Clothing    ||||
| Seattle Store          | West Regional Office            | 487c0d20-4e55-4dc2-8187-a24c826e0fee | Pacific  | Grocery     ||||
| Los Angeles            | West Regional Office            | 204a1287-2efb-4a8a-88e0-56fbaf5a2389 | Pacific  | Electronics ||||

## Apply your schema

After you've defined your schema CSV file, you're ready to upload it to Teams. To do this, run the following PowerShell command:

```powershell
Set-TeamTargetingHierarchy -FilePath "C:\ContosoTeamSchema.csv"
```

## Troubleshooting

### You receive an error message when you upload your schema file

Take note of the error message as it should include troubleshooting information to indicate why the schema couldn't be uploaded. Review and edit your schema CSV file based on the information in the error message and then try again.