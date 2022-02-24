# Micro_Reticulation_ Controller (Formally: Basic Reticulation Controller)
The Micro-Retic is designed to be small, simple to use, low cost, versatile and customizable.  The reason I started this project is becuase I noticed that frequenty, households have reticulation controllers installed that cost around $300 and are packet with features which is fine if you need them but it makes them complicated to use in some cases. I have found most people only use upto 3 zones and a master solenoid at most. So I designed a small simple controller that would work with Home Assisant, could be mounted inside a Allbro ENL160806P case and could also be used to retrofit into an existing old school controller if you already have one to save on the need to buy a case or 24v transformer to run everything via WIFI.

I have called it a few names but have setted on Micro Reticulation controller or Micro-Retic.  Eventually I would like to make it use able stand alone off WIFI entirely  or with Home Assistant. Stand alone it would operate via Bluetooth with an App and it's time would come from a real time clock module.
But first I would like it to work with Home Assisant nicely then I will work on stand alone model/version.
At the moment this version is available to buy at www.egglec.com.au and also at Tindie. If purchased it will come with the lastest version of the ESPhome YAML installed which will create a AP to connect to and Captive Portal for setup on your network.
# Instructions For First Time Use
- Connect the device to a 24v AC power supply as is usual for reticulation systems
- It has an on board fuse M205 1A Fast Blow
- AC has no polarity so the transformer leads or 24V can go to to either 24 and C(common)
- C terminal is internally linked and is the common side that will go to ones side of every solenoid
- Station Terminal 1 is the Main Solenoid this will turn on whenever 2,3,or 4 are on
- Station Terminals 2, 3, and 4 are the 3 Station that will connect to the other side of each Zone or Solenoid in your system
- Connect your phone or computer to the AP the device creates EG. micro-retic-D2f682 the password is: password
- Wait....be patient and dialog should pop up and you may enter your SSID and PASSWORD, the device is available at 192.168.4.1 if no popup comes up, but you will need to wait still for it to be active
- Once connected to your network Home Assistant will often discover it in configuation/integrations area if it does not you will need to find out the devices IP on your router, and select add new device in the bottom right corner and then enter the IP address your DHCP as given the device
- Once Created it will make 15 entities it will make all the necessary entities in HA for you this includes:
- 3 x Station Duration set these to enter the run time in minutes of each station the device will time the duration and turn off the station when finished so you only need to setup and automation in HA to start the station running, if you ever want to change the run time place the Station Duration Entities in your Dashboard.
- 3 x Stations switches turn these on to start and stop a station running if you allow google home or alexa to access the switch you can ask it to turn on (example: Station One) and Station 1 will run for it's set duration
- 3 x Time Remaining Sensors these will show how much time there is remaining on the current run and can be included on your dashboard as info
- 1 x Status which is disabled in HA by default will show system Standby, Run, or Rain
- 1 x Light Sensor is disabled in HA by default will show if the board is in light or dark you can get a case with a clear lid
- 1 x Rain Switch if this is turned on, the device will not allow the stations to be turned on, you can create an automation in HA to activate this switch for a day if there is rain fall at a certain level in your area
- 1 x Restart switch is disabled by default is used internally to daily reset the system at 1AM as WIFI and API reboot are disable this will prevent the system locking out of the API or off WIFI
- 1 x System up time since last reboot disable by default in HA
- 1 x Switch Main it the switch to turn on the main solenoid relay

The Device can of course be reprogrammed as you would like too, if you have ESPhome installed on your Home Assistant and mDNS is working on your network the ESPhome dashboard will allow you to import and install the YAML code from this repository simply by ADOPTING the device into your system. You can alternatively if mDNS is not working manual copy this code or any YAML code that is valid as you wish into a newly setup device, if you add manual IP address setting to match the IP address the Micro-Retic has you will be able to upload new code to the Micro-Retic device.
# Road Map for Development
- Design new smaller PCB, with additional output and more accessible battery size
- Design ESP32 Variant with ablity to use Bluetooth to control device
- Design add on buttons for mounting in/on case Allbro ENL160806P
- Design application for mobiles to control device stand alone via bluetooth
- Web dash-board for standalone usage
- Integration for Home Assistant 
- Lorawan integration for remote or rental property
