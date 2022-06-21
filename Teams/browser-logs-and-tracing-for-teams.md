---
title: Browser logs and tracing for Teams
author: wlibebe
ms.author: wlibebe
manager: serdars
ms.date: 06/21/2021
audience: admin
ms.topic: troubleshooting
ms.service: msteams
ms.collection: 
  - M365-collaboration
search.appverid: MET150
description: Learn about Browser and WebRTC logs produced by Microsoft Teams, where they can be found, how to collect logs with Microsoft Support, and how they can help with monitoring and troubleshooting.
appliesto: 
  - Microsoft Teams
---
# Browser logs and tracing for Teams

## Browser logs

For some categories of errors, Microsoft Support might require you to collect a browser trace. This information can provide important details about the state of the Teams client when the error occurs.

Before you start the browser trace, make sure that you’re signed in to Teams. It's important to do this before you start the trace so that the trace doesn't contain sensitive sign-in information.

After you’re signed in, select one of the following links, as appropriate for your browser, and follow the provided steps. 

-   [Chrome & Edge (Chromium)](/azure/azure-portal/capture-browser-trace#google-chrome-and-microsoft-edge-chromium?preserve-view=true#resolution)

-   [Edge](/azure/azure-portal/capture-browser-trace#microsoft-edge-edgehtml?preserve-view=true#resolution)

-   [Safari](/azure/azure-portal/capture-browser-trace#apple-safari?preserve-view=true#resolution)

-   [Firefox](/azure/azure-portal/capture-browser-trace#firefox?preserve-view=true#resolution)

> [!NOTE]
> In the steps, replace all references to the Azure portal with the Teams client.
  
## WebRTC logs in browsers

WebRTC logs can assist Microsoft Support by providing connection details for audio and video calls. Follow the steps to access the WebRTC logs in Edge (Chromium) or Chrome:
  
1. Open a new tab and go to one of the following URLs:
    - Edge (Chromium): `edge://webrtc-internals/`
    - Chrome: `chrome://webrtc-internals/`
  
2. Open the Teams Web application and reproduce the problem.
  
3. Go back to the tab that was accessed in step 1 and you will see at least two tabs:
    - GetUserMedia Requests
    - `https://teams.microsoft.com/url`

4. Choose the tab with the name of the Teams application and save the page content.

## Related topics

[Teams Troubleshooting](/MicrosoftTeams/troubleshoot/teams)
[Configure log files for monitoring and troubleshooting in Teams](/MicrosoftTeams/log-files)
