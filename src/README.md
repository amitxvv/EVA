# Build EVA from source

 - I have a specific order of building the ISO. If you do not follow my order & decide to build the ISO from a single session in NTLite you will get unexpected results & features will not properly be disabled.

### Host machine requirements

 - [NTLite](https://www.ntlite.com/download/) `While installing NTLite run it as an administrator`
 - [7-Zip](https://www.7-zip.org/download.html) `While installing 7-zip run it as an administrator`
 - [Windows 10 1803 build 17134.1](https://archive.org/details/win-1803x-64)

## Creating the base ISO

  Clone the latest EVA repository & place EVA-main in the ``C:\ `` directory.
  I will build EVA 1803 in the following instructions. Replace 1803 with whichever EVA version you would like to build. As of now, only 1803 is available.

 - Extract the ISO respectively, in this case it's 1803, with 7-Zip & Place it in ``C:\EVA-main\src\1803\PREREQUISITES`` (where 1803 is the windows version you are building) & rename it "BASE" so the folder structure is as follows: ``C:\EVA-main\src\1803\PREREQUISITES\BASE\sources\...``. 
   
 - Place install.bat in the ISO directory then drag the ISO folder into NTLite & Double click Windows Pro to mount the image.

    <img src="https://github.com/amitxvv/EVA/blob/main/content/img/BUILD INSTRUCTIONS - Mount image.png" width="600" >
    
 - Go to the Features tab & untick everything apart from (see image).

    <img src="https://github.com/amitxvv/EVA/blob/main/content/img/BUILD INSTRUCTIONS - Disable features.png" width="300" >

 - Go to the Apply tab & copy the setting exactly as shown (see image). Click process after you are done.

    <img src="https://github.com/amitxvv/EVA/blob/main/content/img/BUILD INSTRUCTIONS - Process base image.png" width="300" >

 - Go to the Source tab & mount the image again. Windows Pro is the only edition you should see under the install.wim if you followed the previous steps correctly
    
 - Place the respective xml for the Windows version you are building in ``C:\Program Files\NTLite\Presets`` & right click > load > overwrite the XML in NTLite. If you get file location errors then you need to track back & ensure all the files are in the correct locations.

    <img src="https://github.com/amitxvv/EVA/blob/main/content/img/BUILD INSTRUCTIONS - Load XML.png" width="800" >

 - Delete the following folders:
	
	```
    %temp%\NLTmpMnt\PerfLogs
    %temp%\NLTmpMnt\ProgramData\WindowsHolographicDevices
    %temp%\NLTmpMnt\ProgramData\USOPrivate
    %temp%\NLTmpMnt\ProgramData\SoftwareDistribution
    %temp%\NLTmpMnt\ProgramData\regid.1991-06.com.microsoft
	```

 - Take ownership of the following folders:
 
	```
     %temp%\NLTmpMnt\ProgramData\Microsoft\User Account Pictures
     %temp%\NLTmpMnt\Windows\Web
	```
	
 - Search & delete for the following files in ``%temp%\NLTmpMnt\Windows`` with <a href="https://www.iobit.com/en/iobit-unlocker.php">IOBitUnlocker</a>
   
	```
    Backgroundtaskhost.exe
    mcupdate_GenuineIntel.dll
    mcupdate_AuthenticAMD.dll
    WindowsDefenderApplicationGuard.wim
	```
    
 - Once you are done, copy & paste everything in ``C:\EVA-main\src\1803\EXPLORE MOUNT DIRECTORY`` (where 1803 is the windows version you are building) to ``%temp%\NLTmpMnt``. You should get no errors if you correctly took ownership of the folders listed previously.
 
 - Go to the Updates tab & uninstall the Internet Explorer update. NTLite may become unresponsive for a few seconds, be patient.

 - Go to the apply tab & click "Process" at the top left of the screen
    
 - The final iso will be created in the ``C:\ `` Directory

 - If you have any issues ask for help at [EVA Support server](https://discord.gg/Kssq8QrpcJ)
 
