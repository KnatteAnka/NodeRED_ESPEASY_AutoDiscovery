# NodeRED_ESPEASY_AutoDiscovery  
[Start](README.md)  
[Main Install](MainInstall.md)  
[Device Install](Devices.md)  
<!--[Advance Settings](Advance.md)  -->


# AdvanceSettings
**Flow Node-Red**
![Flow_Node-Red](PNG/Flow_Node-Red.PNG)
The Node-Red inject Node Settings:
containt 3 different settings arrays:
1. is an Array of Sensor settings
   1. Valuename is the name of the variable to search for exact match needed  
   2. Unit is the sufix for the sensor to use  
   3. Device_Class is the class in Home assistant that it is. https://www.home-assistant.io/docs/configuration/customizing-devices/#device-class  
2. is a Declaration what Value names is not an Senso 
   1. Valuename part of the name that need to match to be regarded as such device
   2. Type is the device type to create
   3. Brightness is the max value to output when home assistent is set to 100%
   4. RGB is if it should output RGB or not and give the device controlls for it.
