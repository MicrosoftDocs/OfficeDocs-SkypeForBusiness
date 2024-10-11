
Based on organizational requirements, you may wish to customize how the resource account responds to and processes meeting invitations. Using Exchange PowerShell, you can set many properties, review the [Set-CalendarProcessing](/powershell/module/exchange/mailboxes/set-calendarprocessing) cmdlet for all available configurations. The following are recommended for Teams Rooms:

- **AutomateProcessing: `AutoAccept`** Meeting organizers receive the room reservation decision directly without human intervention.

- **AddOrganizerToSubject: `$false`** The meeting organizer isn't added to the subject of the meeting request on the resource account calendar.

- **AllowRecurringMeetings: `$true`** Recurring meetings can be accepted by the resource account.

- **DeleteAttachments: `$true`** Teams Rooms devices can't access meeting attachments, deleting attachments ensures they're not stored on the resource account calendar.

- **DeleteComments: `$false`** Keep any text in the message body of incoming meeting requests which is required to create join buttons for [third-party meetings](/microsoftteams/rooms/third-party-join) on a Teams Rooms device.

- **DeleteSubject: `$false`** Keep the subject of incoming meeting requests on the resource accounts calendar.

- **ProcessExternalMeetingMessages: `$true`** Specifies whether to process meeting requests organized outside your Exchange environment. This option is required for meeting invites sent directly by an external organizer as well external organized meetings forwarded by an internal user.

- **RemovePrivateProperty: `$false`** Ensures the private flag that sent by the meeting organizer in the original meeting request remains as specified.

- **AddAdditionalResponse: `$true`** The text specified by the AdditionalResponse parameter is added to meeting requests.

- **AdditionalResponse: "This is a Microsoft Teams Meeting room!"** The text to add to the meeting acceptance body. You can also format HTML content in the automatic reply if you wish.

To configure these properties, you need to connect to Exchange Online PowerShell. For more information, see [Connect to Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell?view=exchange-ps&preserve-view=true).

The following example sets the properties for the `ConferenceRoom01` resource account:

``` PowerShell
Set-CalendarProcessing -Identity "ConferenceRoom01" -AutomateProcessing AutoAccept -AddOrganizerToSubject $false -AllowRecurringMeetings $true -DeleteAttachments $true -DeleteComments $false -DeleteSubject $false -ProcessExternalMeetingMessages $true -RemovePrivateProperty $false -AddAdditionalResponse $true -AdditionalResponse "This is a Microsoft Teams Meeting room!"
```
