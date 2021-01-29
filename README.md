# NodeRED_ESPEASY_AutoDiscovery  
[Main Install](MainInstall.md)  
[Device Install](Devices.md)  
[Advance Settings](Advance.md)  

* The Flow creates an device on Home assistant according to the name of the variable
* Enable autodiscovery for EasyEsp without have the code on each device 
* If a variable starts with "_" then its skipped

* Hint use MQTT Explorer to debug what is sent to Home Assistant if you have any problem


Support | devices:  
--------|---------
Yes | Sensors 
Yes | Switch
Yes | RGB Led  
Yes | Dimmer 0-100  
Yes | Dimmer 0-255  
Not yet  | Termostat temperature output

plz tell if you miss any device from 
https://www.home-assistant.io/docs/mqtt/discovery/


### Install Node-Red node  
1. Copy [MQTTDiscovery.json](MQTTDiscovery.json) and import in Node-Red
2. Change/Update the MQTT nodes with correct security and other settings
3. Deploy it
4. run inject button Save List to create a starting point.


### Setup EasyESP Controller:  
![EasyEsp Controller](Controller.PNG)

Controller Subscribe: EE/%sysname%/#

Controller Publish: EE/%sysname%/%tskname%/%valname%

Will Retain: True  

if the device needs to use MQTT import device then you need 2 mqtt controllers configurated the same  
but the first has to not have any username or password and can be disabled.  



