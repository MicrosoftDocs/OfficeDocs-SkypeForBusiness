---
title: "Signing in and using Lync 2013 on the virtual machine"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: End User
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 6140fc19-5bef-4b58-9b0f-19112b5ecd00
description: "After the VDI plug-in is enabled, the following steps occur when the user signs in to Lync 2013."
---

# Signing in and using Lync 2013 on the virtual machine
[]
After the VDI plug-in is enabled, the following steps occur when the user signs in to Lync 2013.
  
1. The user types his or her credentials in to the Lync 2013 client running on the virtual machine.
    
2. After Lync detects the availability of the VDI plug-in, Lync prompts the user to re-enter his or her credentials. In this dialog box, we recommend that the user select the **Save my password** check box so that he or she will not be required to enter credentials during subsequent sign in. 
    
3. Lync begins pairing with the VDI plug-in. Before pairing is complete, the client displays two icons in the Lync status bar. The icon in the lower left indicates that no audio devices are available, and the blinking icon in the lower right indicates that the VDI pairing is in progress, as shown:
    
     ![Lync VDI icon showing successful pairing](media/Deploy_Lync_VDI_Pairing_Error.png)
  
4. After VDI pairing is successful, the icons change to indicate the audio device that will be used for calls and the VDI pairing success:
    
     ![Lync VDI pairing icon showing success](media/Deploy_Lync_VDI_Pairing_Success.png)
  
5. After Lync pairs with the VDI plug-in, the user can see his or her presence on Lync compatible devices that are connected to the local computer. The user can now place and answer calls as usual.
    

