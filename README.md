# NodeRED_ESPEASY_AutoDiscovery  
[Main Install](MainInstall.md)  
[Device Install](Devices.md)  
[Advance Settings](Advance.md)  

* The Flow creates an device on Home assistant according to the name of the variable
* Enable autodiscovery for EasyEsp without have the code on each device 
* If a variable starts with "_" then its skipped

* Hint use MQTT Explorer to debug what is sent to Home Assistant if you have any problem

## Device list under configuration:
![HA Device List](PNG/HA%201Devices.PNG)
## Each device show all entitys that is connected to it.
![HA one Device](PNG/HA%2011Device.PNG)

Support | devices:  
--------|---------
Yes | Sensors 
Yes | Switch
Yes | RGB Led  
Yes | Dimmer 0-100  
Yes | Dimmer 0-255  
Yes  | Termostat temperature output

plz tell if you miss any device from 
https://www.home-assistant.io/docs/mqtt/discovery/

![Flow_Node-Red](PNG/Flow_Node-Red_Settings.PNG)

