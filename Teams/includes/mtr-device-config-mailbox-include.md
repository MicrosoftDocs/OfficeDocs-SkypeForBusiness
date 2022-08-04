In Exchange PowerShell, either online or on-premises, configure the following settings on the room mailbox to improve the meeting experience:

- **AutomateProcessing: `AutoAccept`** Meeting organizers receive the room reservation decision directly without human intervention.

- **AddOrganizerToSubject: `$false`** The meeting organizer isn't added to the subject of the meeting request.

- **DeleteComments: `$false`** Keep any text in the message body of incoming meeting requests. This is required to process external Teams and third-party meetings to provide One Touch Join experience.

- **DeleteSubject: `$false`** Keep the subject of incoming meeting requests.

- **ProcessExternalMeetingMessages: `$true`** Specifies whether to process meeting requests that originate outside the Exchange organization. Required for external Teams meetings and [third-party meetings](/microsoftteams/rooms/third-party-join).

- **RemovePrivateProperty: `$false`** Ensures the private flag that was sent by the meeting organizer in the original meeting request remains as specified.

- **AddAdditionalResponse: `$true`** The text specified by the AdditionalResponse parameter is added to meeting requests.

- **AdditionalResponse: "This is a Microsoft Teams Meeting room!"** The additional text to add to the meeting acceptance response.

This example configures these settings on a room mailbox named ConferenceRoom01:

``` PowerShell
Set-CalendarProcessing -Identity "ConferenceRoom01" -AutomateProcessing AutoAccept -AddOrganizerToSubject $false -DeleteComments $false -DeleteSubject $false -ProcessExternalMeetingMessages $true -RemovePrivateProperty $false -AddAdditionalResponse $true -AdditionalResponse "This is a Microsoft Teams Meeting room!"
```

For detailed syntax and parameter information, see [Set-CalendarProcessing](/powershell/module/exchange/mailboxes/set-calendarprocessing).
