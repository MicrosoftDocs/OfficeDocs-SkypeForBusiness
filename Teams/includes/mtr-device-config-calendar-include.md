### Configure distribution groups for Teams Calendar

To organize your meeting room locations, you can add your device resource accounts to Exchange distribution groups. For example, if you have offices in three different geographic locations, you can create three distribution groups and add the appropriate resource accounts to each location. For more information, see [Create a rooms list](/exchange/recipients/room-mailboxes?view=exchserver-2019#create-a-room-list).

### Configure places for Outlook Calendar
In order for meeting room locations to appear in the Outlook Room Finder, you need to use the Set-Place Exchange PowerShell cmdlet. Not only does Set-Place populate the Room Finder in Outlook, it also allows you to add additional metadata such as the capacity of the room or the floor of building the room is in. For more information, see [Set-Place](/powershell/module/exchange/set-place).