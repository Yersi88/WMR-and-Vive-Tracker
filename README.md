# WMR-and-Vive-Tracker
Tutorial on how to use Vive Tracker for head tracking of WMR headset within SteamVR

What you'll need: 
1. WMR Headset (eg. Reverb G2) 
2. Vive tracker (2.0 Recomended, 3.0 manifested increased drift in my testing) 
3. OVR Input Emulator with patched .DLL (Optional) 
4. Long 5m long USB cable. (Optional) 
5. 3D Printed mount for Vive Tracker. (My remix: https://www.thingiverse.com/thing:4817158)

1. Mount your Vive tracker to the Headset, I recommend mounting the Tracker on the front of the headset with Charging port facing upwards. You can use my remix if you want to do this with Reverb G2 (https://www.thingiverse.com/thing:4817158), Mount the tracker with metal screw (Printed one will break for sure ;) I used this screw: https://www.amazon.co.uk/gp/product/B00OOLKD30
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
      
6. Save the file 
7. Turn on your tracker and start SteamVR 
8. 
