# WMR-and-Vive-Tracker
Tutorial on how to use Vive Tracker for head tracking of WMR headset within SteamVR

## This is new method that involves modification of Firmware of vive tracker, old method can be found in [Old_Method.md](https://github.com/)
**!!!Proceed at your own risk, make sure to back up the configuration files, I'm not responsible if you brick yor equpment following this guide!!!** 

What you'll need: 
1. WMR Headset (eg. Reverb G2) 
2. Vive tracker (2.0 Recomended, 3.0 manifested increased drift in my testing) 
3. 3D Printed mount for Vive Tracker. (My remix: https://www.thingiverse.com/thing:4817158 , you don't need OVR Input Emulator with this mount.)
4. Long 5m long USB cable. (Optional) 


INSTRUCTIONS:

1. Mount your Vive tracker to the Headset, I recommend mounting the Tracker on the front of the headset with Charging port facing upwards. (This is mandatory if you don't want or can't use OVR Input Emulator to correct the offsets) You can use my remix if you want to do this with Reverb G2 (https://www.thingiverse.com/thing:4817158), Mount the tracker with metal screw (Printed one will break for sure ;) I used this screw: https://www.amazon.co.uk/gp/product/B00OOLKD30
2. Connect your vive tracker to SteamVR either using USB cable with 5m extension or via its dongle. (I'm using PASSIVE 5m USB extension cable with Active hub at the end so I can plug in both Tracker and Facial tracker in. Cable: https://www.amazon.co.uk/gp/product/B01M4PKURH?psc=1 , Hub: https://www.amazon.co.uk/gp/product/B00TPMEOYM?psc=1) BIG NOTE: I tried using active 5m USB extension cable which didn't work and resulted in unusable tracking quality, avoid active cables.

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

APPLY OFFSET TO TRACKER FIRMWARE: 

9. Exit SteamVR
10. For safety disconnect all SteamVR devices (HMDs, Trackers, Dongles...)
11. Connect just your head vive tracker with USB cable.
12. Run lighthouse_console.exe (Usually in: C:\Program Files (x86)\Steam\steamapps\common\SteamVR\tools\lighthouse\bin\win64)
13. Execute this commands: 
* serial (you shold see only your tracker connected as LHR-YOURSERIAL from previous steps.
* serial LHR-YOURSERIAL
* downloadconfig 
14. You will now have config file LHR-YOURSERIAL.json in the same directory, Back up this file! **(IMPORTANT)**
15. Open the config with notapad and edit the line: 
"head": {
        "plus_x": [
            1,
            0,
            0
        ],
        "plus_z": [
            0,
            0,
            -1
        ],
        "position": [
            4.5600000930789975e-07,
            0.039768997579813004,
            0.051509737968444824 
        ]
},


* You can save your setting in Input Emulator but they won't be automatically applied on startup, you'll need to apply them every time you start SteamVR (If you know how to do this automatically pls message me!)  
* If you're using Full Body Tracking in VRChat than VRChat will recognize your head tracker as one of your legs (VRChat completely ignores the SteamVR tracker roles...), Workaround is to close SteamVR if running, turn off your head tracker, turn on all 3 of your body trackers, open VRChat, calibrate your avatar and lastly turn on your head tracker. In order to do this you'll need Space Calibrator as well to be running but once you turn on your head tracker SpaceCal will be overwritten by the tracker ;)


CREDITS: 

[Danwillm](https://github.com/danwillm) : Help with OpenVR :)
