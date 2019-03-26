---
title: Windows PowerShell cmdlets, parameters, and parameter values in Skype for Business Online
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Windows PowerShell cmdlets, parameters, and parameter values
ms:assetid: 04615700-099f-4ac5-a801-ddeffccb9e4f
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Dn362765(v=OCS.15)
ms:contentKeyID: 56558799
ms.date: 05/04/2015
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Windows PowerShell cmdlets, parameters, and parameter values in Skype for Business Online

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-07-05_

If you are familiar with the command window found in all versions of Windows (or if you are familiar with MS-DOS), then you’ll have a head start when it comes to learning how to use Windows PowerShell. In the command window, you type a command and press ENTER. In response, the computer runs a command or an executable file. For example, to return information about all the files and folders in the current directory, you’d type this command at the command prompt and then press ENTER:

    dir

In turn, you get back information about all the files and folders in the current directory:

``` 
    Directory: C:\

03/21/2013  03:39 PM    <DIR>          Deploy
03/21/2013  02:55 PM    <DIR>          Intel
07/26/2012  12:33 AM    <DIR>          PerfLogs
04/10/2013  10:29 AM    <DIR>          Program Files
04/08/2013  10:28 AM    <DIR>          Program Files (x86)
03/22/2013  08:44 AM    <DIR>          Users
04/11/2013  03:00 PM    <DIR>              Windows
03/13/2013  02:53 PM                 117   pldok.log
03/21/2013  03:35 PM                 769   RHDSetup.exe
03/21/2013  03:37 PM            207   setup.doc
              3 File(s)        1,093 bytes
              7 Dir(s)21,386,002,432 bytes free
```

That’s one example of a result when you do type only the name of a command or an executable file. However, many of the commands that are run from within the command window also accept *arguments*. Arguments are additional pieces of information that are passed to the command, which modify the behavior of the command. For example, if you only wanted to see the names of the files and folder in the current directory—no other information, such as the size of the file or folder, or the date and time that the folder or folder was created. In this case, you’d append the **/b** argument when running the dir command:

    dir /b

When you include the **/b** argument, the **dir** command reports back only the names of the folders and files found in the current directory:

    Deploy
    Intel
    PerfLogs
    Program Files
    Program Files (x86)
    Users
    Windows
    pldok.log
    RHDSetup.exe
    setup.doc

In the preceding command, the **/b** argument is the only information required to limit the returned data to file and folder names. This is often the case with command-line commands: the mere presence of an argument is all that’s needed to change the command’s behavior. (That is, you include the **/b** argument to hide additional information, or you exclude the **/b** argument to show the extra information.) At other times, however, you must specify an *argument value*. An argument value is additional information passed to the argument itself. For instance, the **/o** argument enables you to specify how you would like the dir command to sort the returned data. Among other options, you can use the argument value **e** to sort by file extension or the argument value **s** to sort by file size. For example, this command sorts the returned data by file extension. Note how the argument value **e** is included immediately after the **/o** argument:

    dir /oe

Using our sample folder, the returned data will look like this, with the files sorted alphabetically by file extension:

``` 
    Directory: C:\

03/21/2013  03:39 PM    <DIR>          Deploy
03/21/2013  02:55 PM    <DIR>          Intel
07/26/2012  12:33 AM    <DIR>          PerfLogs
04/10/2013  10:29 AM    <DIR>          Program Files
04/08/2013  10:28 AM    <DIR>          Program Files (x86)
03/22/2013  08:44 AM    <DIR>          Users
04/11/2013  03:00 PM    <DIR>              Windows
03/21/2013  03:37 PM            207   setup.doc
03/21/2013  03:35 PM                 769   RHDSetup.exe
03/13/2013  02:53 PM                 117   pldok.log
              3 File(s)        1,093 bytes
              7 Dir(s)21,386,002,432 bytes free
```

Or, to help you pinpoint exactly what we are talking about:

setup. **doc**  
RHDSetup. **exe**  
pldok. **log**

Although Windows PowerShell uses different terminology, the basic approach to working with Windows PowerShell is the same as working with the command window: you type commands, you include arguments and argument values as needed, and then you press ENTER to execute those commands. As noted, however, Windows PowerShell does use a different terminology than the command shell uses. In Windows PowerShell, the commands you execute are known as *cmdlets*. In turn, the arguments passed to a cmdlet are known as *parameters*, and the values passed to a parameter are known as *parameter values*.

The preceding definitions are somewhat simplified. Cmdlets are essentially mini-applications that can be run only from within the Windows PowerShell environment. However, you can also run other commands and applications from within Windows PowerShell, including most of the commands and applications that can be run from a command window. For example, if you want to start Notepad from within Windows PowerShell, all you need to do is type the following and press ENTER:

    notepad.exe

When it comes to managing Skype for Business Online, however, most administrators will rely on Windows PowerShell cmdlets to carry out administrative tasks. At time, there are very few other types of commands or applications that can be used to manage Skype for Business Online. Sometimes the Skype for Business Online cmdlets can be used without any additional arguments (, as noted, arguments are known as parameters in Windows PowerShell). For example, the following command calls the [Get-CsOnlineUser](https://technet.microsoft.com/en-us/library/JJ994026(v=OCS.15)) cmdlet without any additional parameters. By itself, the command returns information about all of your Skype for Business Online users:

    Get-CsOnlineUser

However, most of the Skype for Business Online cmdlets also accept parameters (and parameter values). Consider the following command:

    Get-CsOnlineUser -Identity "kenmyer@litwareinc.com"

This command consists of three parts:

  - The cmdlet **Get-CsOnlineUser**.

  - The Identity parameter. Note that, in Windows PowerShell, parameters are always prefaced with a dash (-). That means that, for this same cmdlet, the UnassignedUser parameter would be indicated by using this syntax:
    
        -UnassignedUser
    
    This is useful to know, not only because parameters must be prefaced with a dash, but also because this differs from the command window, where arguments are prefaced using a forward slash (/):
    
    ``` 
    /b
    ```

  - The parameter value **kenmyer@litwareinc.com**.

That command, incidentally, returns information about a specific user: the user with the identity, kenmyer@litwareinc.com.

<div>

## See Also


[An introduction to Windows PowerShell and Skype for Business Online](https://technet.microsoft.com/en-us/library/Dn362785(v=OCS.15))  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

