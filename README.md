# WMR-and-Vive-Tracker
Tutorial on how to use Vive Tracker for head tracking of WMR headset within SteamVR

What you'll need: 
1. WMR Headset (eg. Reverb G2) 
2. Vive tracker (2.0 Recomended, 3.0 manifested increased drift in my testing) 
3. OVR Input Emulator with patched .DLL (Optional) 
4. Long 5m long USB cable. (Optional) 
5. 3D Printed mount for Vive Tracker. (My remix: https://www.thingiverse.com/thing:4817158)

INSTRUCTIONS:

1. Mount your Vive tracker to the Headset, I recommend mounting the Tracker on the front of the headset with Charging port facing upwards. (This is mandatory if you don't want or can't use OVR Input Emulator to correct the offsets) You can use my remix if you want to do this with Reverb G2 (https://www.thingiverse.com/thing:4817158), Mount the tracker with metal screw (Printed one will break for sure ;) I used this screw: https://www.amazon.co.uk/gp/product/B00OOLKD30
2. Connect your vive tracker to SteamVR either using USB cable with 5m extension or via its dongle. (I'm using PASSIVE 5m USB extension cable with Active hub at the end so I can plug in both Tracker and Facial tracker in. Cable: https://www.amazon.co.uk/gp/product/B01M4PKURH?psc=1 , Hub: https://www.amazon.co.uk/gp/product/B00TPMEOYM?psc=1) BIG NOTE: I tried using active 5m USB extension cable wich didn't work and resulted in unusable tracking quality, avoid active cables.
2b. Update your tracker firmware
3.  Assign your tracker a 'Camera' role in SteamVR (Controllers>Manage Vive Trackers). 
4.  Exit SteamVR 
5.  Now you need to edit your steamvr.vrsettings (located in C:\Program Files (x86)\Steam\config)

Add a following line: 

      "TrackingOverrides" : {    
         "/devices/htc/vive_trackerLHR-SERIALGOESHERE" : "/user/head" 
      },
    
    
  Replace SERIALGOESHERE with your trackers serial number wich you can find in "trackers" section use the tracker with camera role:     
      
      "trackers" : {
         "/devices/htc/vive_trackerLHR-YOURSERIAL" : "TrackerRole_Camera"
      }
      
6. Save the file. 
7. Turn on your tracker and start SteamVR.
8. Uppon opening SteamVR your headset shoud be now tracked with Vive Tracker, try to test it by obscuring trackers view and seeing if image stutters. 

OPTIONAL STEPS: 
9. Exit SteamVR
10. Install OVR Input Emulator from here: https://github.com/matzman666/OpenVR-InputEmulator/releases 
11. Replace the driver .dll with patched one from here: https://github.com/matzman666/OpenVR-InputEmulator/files/6096080/driver_00vrinputemulator.2.zip 
12. Open SteamVR and in OVR Input Emulator menu choose your tracker and hit 'Device Offsets' Adjust the DriverFromHead offset Z coordinate (to -8 if you're using my 3D printed mount, if you're using different mount you need to experiment the valuse to get the image just right)


KNOWN ISSUES: 
* You can save your setting in Input Emulator but they won't be automatically applied on startup, you'll need to apply them every time you start SteamVR (If you know how to do this automatically pls message me!)  
* If you're using Full Body Tracking in VRChat than VRChat will recognize your head tracker as one of your legs (VRChat completely ignores the SteamVR tracker roles...), Workaround is to close SteamVR if running, turn off your head tracker, turn on all 3 of your body trackers, open VRChat, calibrate your avatar and lastly turn on your head t racker. In order to do this you'll need Space Calibrator as well to be running but once you turn on your head tracker SpaceCal will be overwritten by the tracker ;)
