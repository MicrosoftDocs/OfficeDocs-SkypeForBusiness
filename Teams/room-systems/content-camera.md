---
title: "Manage a Microsoft Teams Rooms console settings remotely with an XML configuration file"
ms.author: jambirk
author: jambirk
ms.reviewer: gregbari
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: M365-voice
description: "This article discusses remote management of the default settings used by a Microsoft Teams Rooms device, including applying a custom theme."
---

# Content cameras

You can now use a content camera with a Microsoft Teams Room system. A content camera interacts with special image-processing software and a whiteboard to allow a presenter to draw on an analog whiteboard and share the content with remote participants.

See the video [Work like you are in one place, with Microsoft Teams Rooms](https://youtu.be/1XvgH2rNpmk?t=350) for examples of content camera functionality.

## Set up a content camera

> [!NOTE]
> Always adhere to your country or area's building code, which may define a minimum distance from the floor or a requirement that ceiling-mounted equipment be secured to a rafter or other structure. Follow the mounting instruction for the hardware provided with the camera you‘ve selected. OEM camera mounting kits include a camera, USB 2.0 extenders and required cabling.

The size of the whiteboard used for sharing affects the placement of the camera. Board size recommendations are:

- 3–6 ft. (0.9–1.8 m) wide — Supported
- 6–9 ft. (1.8–2.7 m) wide — Recommended
- 9 ft. (2.7 m) wide — Ideal
- 9–12 ft. (2.7–3.6 m) wide — Supported
- Above 12 ft. (3.6 m) wide — camera covers 9–12 ft. (2.7–3.6 m) and crops the rest.

## Camera location

Ideal placement of a content camera is centered vertically and horizontally on the whiteboard. Local building codes may have height restrictions that require the camera be elevated higher than the top of the white board.

You can install the camera up to 6 in. (152 mm) higher than the top of the whiteboard, and centered on the white board as shown. Make sure that the camera image includes a 6 in. (152 mm) border on both sides horizontally. You can use the camera preview in the Microsoft Teams Rooms app to determine final placement of the camera.

![Content camera placement diagram](../media/Magic-whiteboard.png)

### Approximate starting distances

Using typical whiteboard markers, the optimal remote user experience is to share ink strokes in the 1–2 mm per pixel range in the content camera image, best results use 1.5 mm per pixel. All supported cameras provide 1920 x 1080 resolution, and some can exceed that resolution. The distance of the camera from the whiteboard combines with the camera resolution and HFoV to determine the distance from the whiteboard. The following table shows calculated distances from a whiteboard. You can use these values as starting points to determine final placement of the content camera.

**Camera distance from whiteboard (1920 ppi)**

| Camera HFoV |1 mm per pixel | 1.5 mm per pixel <br> (optimal) | 2.0 mm  per pixel|
|:---         |:---           |:---              |:---              |
| 80°         |7.2 ft. (2.2 m)| 11.1 ft.(3.4 m)  | 15 ft. (4.6 m)   |
| 90°         |6.2 ft. (1.9 m)|  9.1 ft. (2.8 m) | 12.4 ft. (3.8 m) |
| 100°        |5.2 ft. (1.6 m)|  7.8 ft. (2.4 m) | 10.5 ft. (3.2 m) |
| 110°        |4.2 ft. (1.3 m)|  6.5 ft. (2.0 m) | 8.8 ft. (2.7 m)  |
| 120°        |3.6 ft. (1.1 m)|  5.2 ft.(1.6 m)  | 7.2 ft. (2.2 m)  |
|             |               |                  |                  |

The distance between the content camera and the wall the whiteboard is mounted on depends on the HFoV for that model of camera, which varies. Install cameras with a larger HFoV (120 degrees for example) closer to the wall, and cameras with a narrower HFoV farther away from the wall. Check the HFoV before you start to install the chosen camera.

If you have whiteboards larger than 12 ft. (3.6 m) or with no corners (like full wall whiteboards), you can place the camera anywhere in the middle. The enhancement software selects an area in the middle if it fails to find whiteboard corners.

> [!NOTE]
> You can use dark-colored tape or other items to create a defined content camera area on a full-wall white board.
>
> You can choose to have the camera mounted on a moveable tripod instead of a permanent mount. Place the tripod centered on the whiteboard. This setup may be temporary or used where there is little chance of knocking over the equipment. If you use a temporary mount, remember that content enhancement will be impacted if you move the camera after the initial share and you will need to re-share to correct for movement.
>
> A writing board that isn't white is not supported.

## Supported cameras

To determine whether you can use a camera as a content camera, refer to [Certified firmware versions for USB audio and video peripherals](requirements.md#certified-firmware-versions-for-usb-audio-and-video-peripherals).

## Camera settings

Once the camera is installed in the room, set it up on that room's Microsoft Teams Rooms console:

1. Select **Settings** ![Settings icon](../media/70f1b43f-16d6-4172-9139-71d845c4ed5c.png),  log in as Admin, and select **Device Settings**.
2. In the **Camera Defaults** section, select the content camera and make sure that the **Content enhancements** option is selected.
3. (Optional) If the camera was installed upside down because the camera was mounted from the ceiling, check the **Rotate content camera 180°** option.
4. Select **Save and exit**.

![Content camera setup](../media/content-camera.png)

You can also adjust these settings remotely using an [XML configuration file](xml-config-file.md). 

## See also

[Manage a Microsoft Teams Rooms console settings remotely with an XML configuration file](xml-config-file.md)

[Microsoft Teams Rooms requirements](requirements.md)
