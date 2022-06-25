# NodeRED_ESPEASY_AutoDiscovery  
[Main Install](MainInstall.md)  
[Device Install](Devices.md)  
[Advance Settings](Advance.md)  

* The Flow creates an device on Home assistant according to the name of the variable
* Enable autodiscovery for EasyEsp without have the code on each device 
* If a variable in EE starts with "_" then its skipped

* Hint use [MQTT Explorer](http://mqtt-explorer.com/) to debug what is sent to Home Assistant if you have any problem

 **Support** | **devices:** | **ValueNames** 
--------|---------|---------
Yes | [Sensors](Devices.md#sensor) | All other, GarrageList
Yes | [Binary Sensor](Devices.md#binary-sensor) | LockSens, MotionSens, MoveSens, TampSens
Yes | [Switch](Devices.md#switch) | State,Relay
Yes | [Button](Devices.md#button-beta) | Button
Yes | [Dimmer](Devices.md#dimmer) | Percent,Brightness,CounterTime 
Yes | [RGB Led](Devices.md#rgbdimmer) | RGBBrightness 
Yes  | [Termostat](Devices.md#termostat) (temperature output) | SetTemp, SetTime
Yes | [Select](Devices.md#select-beta) | SelectFan, SelectLock, SelectColor, SelectGarrage
Yes | [Tag Scanner](Devices.md#tag-beta) | Tag
No | Number

## Device list under configuration:
![HA Device List](PNG/HA_Devices.PNG)
## Each device show all entitys that is connected to it.
![HA one Device](PNG/HA_1Device.PNG)



plz tell if you miss any device from 
https://www.home-assistant.io/docs/mqtt/discovery/

![Flow_Node-Red](PNG/Flow_Node-Red.PNG)

