# Install Node-Red node  
1. Copy [MQTTDiscovery.json](MQTTDiscovery.json) and import in Node-Red
2. Change/Update the MQTT nodes with correct security and other settings
3. Deploy it
4. run inject button Save List to create a starting point.


# EasyESP:  
Setup EasyESP:  
**Controller:**  
![EasyEsp Controller](Controller.PNG)

Controller Subscribe: EE/%sysname%/#

Controller Publish: EE/%sysname%/%tskname%/%valname%

Will Retain: True  

if the device needs to use MQTT import device then you need 2 mqtt controllers configurated the same  
but the first has to not have any username or password and can be disabled.  

