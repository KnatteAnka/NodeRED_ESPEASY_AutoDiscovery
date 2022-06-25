# NodeRED_ESPEASY_AutoDiscovery  
[Start](README.md)  
[Main Install](MainInstall.md)  
[Device Install](Devices.md)  
<!--[Advance Settings](Advance.md)  -->


# AdvanceSettings
**Flow Node-Red**
![Flow_Node-Red](PNG/Flow_Node-Red.PNG)
The Node-Red **inject Node Settings**:  
containts some different settings arrays and variables:  
*Settings inside Function node is if settings is not run or missing!*

![Flow_Node-Red](PNG/Flow_Node-Red_Settings.PNG)

1. "UnitsContainsName" sets if Units Valuename have to be exact match or just contain the word to match.
2. "Units" is an Array of Sensor settings
   1. Valuename is the name of the variable to search for
   2. Unit is the sufix for the sensor to use  
   3. [Device_Class](https://www.home-assistant.io/docs/configuration/customizing-devices/#device-class)   is the class in Home assistant that it is. 
3. "Devices" is a Declaration what Value names specific [Device classes](https://www.home-assistant.io/docs/mqtt/discovery/) has.  
  
   If Value name is not found then it uses default that is Sensor.  
   if First char in a variable is lowercase then its sent directly to HA if not then its processed before its sent. 
   meaning you can change and add settings by just adding them to a device  
   1. **ValueName** part of the name that need to match to be regarded as such device  
   2. **Type** is the device type to create in home assistant  
   3. (Light) **Brightness** is the max value to output when home assistent is set to 100%  
   4. (Light) **RGB** is if it should output RGB or not and give the device controlls for it.  
   5. (Termostat) **Mode_state_topic** can be enabled to have a Fanmode setting parameter that can be set  
   6. (Select) **options** is the Text values to use. in EE it is converted so first option is value 0 secound is 1 and so on.  
   7. (Sensor) **List** is a list of strings to show. 0 indexed like options above  
   8. (Sensor) **unit_of_measurement** Replace default value for this sensor  
   
4. "UseDefaultUnit" is a setting if the unit is not found if it should use ValueName   
5. "DefaultUnit" if variable is defined it Replaces ValueName of UseDefaultUnit.  
      This is to get around standard behavior that it shows states not as a graph in Home assistant.  
      
When adding devices look at one of the examples to see how they are declared and build from that or start an issue and tell what you want EE to send and HA to show and what typ of device and i may be able to help. See [Home Assistant MQTT Discovery](https://www.home-assistant.io/docs/mqtt/discovery/) for HA supported devices and parameters.

# Edit EasyESP_MQTTDisc.txt
settings file that is loaded is located in config folder

1. copy file content to [JsonFramater](https://jsonformatter.curiousconcept.com/#)
2. Paste formated content back to the file
3. Remove any devices you want to redo
4. Press load button in Node red

# Reset Autodiscovery
1. in HA Select all Easy Esp devices that you want to recreate and delete them (under configuration and Devices)
2. In the Node red node hit the Inject button "Clear list" and hit save button
3. When devices is recreated hit the inject button "Save list" 


