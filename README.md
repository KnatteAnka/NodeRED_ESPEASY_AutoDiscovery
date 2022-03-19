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
Yes | [Sensors](https://www.home-assistant.io/integrations/sensor.mqtt/) | All other, GarrageList [Device Install](Devices.md)  
Yes | [Switch](https://www.home-assistant.io/integrations/switch.mqtt/) | State,Relay
Yes | [RGB Led](https://www.home-assistant.io/integrations/light.mqtt/) | RGBBrightness 
Yes | [Dimmer 0-100](https://www.home-assistant.io/integrations/light.mqtt/) | Percent 
Yes | [Dimmer 0-255](https://www.home-assistant.io/integrations/light.mqtt/) | Brightness 
Yes | [Dimmer 0-240](https://www.home-assistant.io/integrations/light.mqtt/) | CounterTime
Yes  | [Termostat](https://www.home-assistant.io/integrations/climate.mqtt/) (temperature output) | SetTemp(17-24), SetTime(0-24)
Beta | [Select](https://www.home-assistant.io/integrations/select.mqtt/) | SelectFan, SelectLock, SelectColor, GarrageState
Beta | [Button](https://www.home-assistant.io/integrations/button.mqtt/) | Button
Beta | [Tag Scanner](https://www.home-assistant.io/integrations/tag.mqtt/) | Tag
Beta | [Binary Sensor](https://www.home-assistant.io/integrations/binary_sensor.mqtt/) | LockSens, MotionSens, MoveSens  
No | [Number](https://www.home-assistant.io/integrations/number.mqtt/)

## Device list under configuration:
![HA Device List](PNG/HA_Devices.PNG)
## Each device show all entitys that is connected to it.
![HA one Device](PNG/HA_1Device.PNG)



plz tell if you miss any device from 
https://www.home-assistant.io/docs/mqtt/discovery/

![Flow_Node-Red](PNG/Flow_Node-Red.PNG)

