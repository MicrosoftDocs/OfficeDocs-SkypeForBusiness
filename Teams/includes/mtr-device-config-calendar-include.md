
To help your users more easily schedule meetings in a Teams Room, you can create room lists and places in Exchange Online. 

Exchange room lists and Outlook Places are used to control which resource accounts (and therefore the Teams Rooms they're associated with) appear in Outlook's Room Finder. Room Finder is an Outlook feature that helps users find rooms that are near them, available for reservation, and meet other criteria such as the availability of a display.

Room lists are a special type of Exchange distribution group that let you group resource accounts (and therefore the Teams Rooms they're associated with) together in a meaningful way. For example, you might want to create room lists for all the rooms in each building on your campus.

Outlook Places lets you set specific attributes about a resource account and its Teams Room. Some of the attributes you can set are:

- Building
- City
- Capacity
- Whether the location is wheelchair-accessible
- Audio, video, and display names

Using a combination of room lists and place attributes selected by a user, Room Finder in Outlook will show a list of rooms available to them for reservation. To make the best use of room lists and places, create room lists based on a place attribute, such as building. For example, set the city and building place attributes for each resource account, and then add each resource account to a building room list. When a user tries to choose a room to reserve, Outlook will show a list of cities and the room lists available in each of those cities.

> [!IMPORTANT]
> Each resource account needs to have its place attributes set. If these attributes, especially city, building, and capacity, aren't set, those rooms won't show up as available options for reservation even if a room list contains them.

To create a room list, follow the instructions in [Create a rooms list](/exchange/recipients/room-mailboxes?view=exchserver-2019#create-a-room-list).

To configure the place attributes for a resource account, see [Set-Place](/powershell/module/exchange/set-place).
