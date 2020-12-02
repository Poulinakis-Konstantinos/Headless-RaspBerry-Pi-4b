# Headless-RaspBerry-Pi-4b
Missing a spare monitor ,micro HDMI or do you just hate having your Pi like a patient in the hospital?
Then this guide will be of use !!
 
**This is a tutorial on how to boot , configure and operate your beloved Pi  remotely over Wifi . Not one cable is needed , just a Wifi !**

**You will Need :**

  #### Hardware: 
 
  - RaspBerry Pi with wifi capability , should work for versions zero , 3 and 4 . ( I use Pi 4B)   
  - A micro SD card of at least 8Gb (empty)
  - A laptop/PC with micro SD slot 
  - Router with Wifi 
  
  
 #### Software:
   - [Raspberry Pi OS with desktop and recommended software](https://www.raspberrypi.org/software/operating-systems/)
   - Rufus 
   - Putty
   - VNC viewer
  
  
 ## 1.Flashing OS to sd card :
 
 Starting we need to give our Pi an operating system to work on . This is why you need the micro SD , as it is used as the Pi's Hard Disk .
 First download the Rasp Pi OS from the official RaspBerry Pi site . Head to this link https://www.raspberrypi.org/software/operating-systems/ 
 and download  " Raspberry Pi OS with desktop and recommended software" . It is 2.5 Gb and contains the necessarry software in order to operate 
 the pi remotely .
 
 After you have downloaded the file , **exctract it and burn the ISO image into a bootable micro SD card** . To do that you can use Rufus ,Etcher or other
 similar programms ,I use Rufus. Insert the micro SD  on your PC and open rufus . It should automatically recognize your micro sd and you should see 
 it's name at the device box .On Boot selection choose "Disk or Iso image " and on the right select the ISO image you downloaded . Hit start , make sure 
 to read and understand the warning rufus gives you **( Any data on the micro SD will be lost! )** and wait till the process finishes . 
 
<img src="https://github.com/Poulinakis-Konstantinos/Headless-RaspBerry-Pi-4b/blob/main/Rufus.PNG" alt="rufus" width="350" height="250">
  
 Now normally ,once rufus has finished you would just insert the sd directly onto the Pi . But this time we will need to first make some configurations ! 
 
 ## 2. Configuring the OS 
 ### Since we don't have a monitor , we need a way to connect our RaspBerry Pi on our wifi network automatically .
 By now you should see that the name of the sd card is boot(D). We now need to add 2 new files in the boot to enable connection with Putty and configure Wifi connection.
 To do that open notepad and :
 - create a blank file and save as **"ssh"** without any extensions inside the boot . This will enable SSH connection on the raspberry .
 - copy the code snipet in the file wpa_supplicant.conf I have in the repository and save it as "wpa_supplicant.conf" inside boot . This Enable Pi to connect
 in your wifi (details in code) . 
 
 ## 3. Accesing Pi's terminal with Putty
  ### We now want to activate the VNC connection with the Pi that will allow it to share it's desktop over wifi.
  Boot your raspberry pi and wait for about a minute until everything has loaded . 
  Open putty and type the pi's IP address in the host name . Choose ssh connect via SSH with your pi. You could use Netwatcher for that .
  Once you have access to the pi's terminal it will ask for username:pi , password:raspberry ( these are the default credentials).
  Now enable VNC . Run `<sudo raspi-config>` , a menu will appear. Search **"Interface Options"** find **VNC and enable it** . 
  Almost done ! 
  
  ## 4. Accesing Pi's Desktop via VNC 
   ### Now it's time to download VNC viewer if you haven't already done .  This is the software that allows Pi to share it's desktop with us .
   Pi already has preinstalled VNC server. Open VNC and create a connection to the pi's IP . 
   
   ### That's  it you're in !!! 
  this is what you expect to see 
  
<img src="https://github.com/Poulinakis-Konstantinos/Headless-RaspBerry-Pi-4b/blob/main/VNC.PNG" alt="VNC view" width="350" height="350">
