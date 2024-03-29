# NodeRED_ESPEASY_AutoDiscovery  
[Start](README.md)  
[Main Install](MainInstall.md)<!--[Start](Readme.md)  -->  
[Advance Settings](Advance.md)  

---

[Sensor](#sensor) | [Binary Sensor](#binary-sensor) | [Switch](#switch) | [Button](#button-beta) | [Dimmer](#dimmer) | [RGBDimmer](#rgbdimmer) | [Termostat](#termostat) | [Select](#select-beta) | [Tag](#tag-beta)

---

**MQTT Import info:**  
if MQTT import is needed to be used then the first MQTT controller needs to have no username or password and be disabled



# Devices:
**Always do a restart of EasyESP device after name change or changes to MQTT Controller**

## Sensor:
[Home Assistant MQTT Sensors](https://www.home-assistant.io/integrations/sensor.mqtt/)
Variable name | HA Shown text | EE State
--------|---------|-------
GarrageList | Open, Closed, Car found | 0-2
Any non declared| EE value | any  

You only need to activate the device and set it to use the HA controller:

if custom settings is wanted See [Advance Settings](Advance.md) then how to do it.



## Binary Sensor:
[Home Assistant MQTT Binary Sensor](https://www.home-assistant.io/integrations/binary_sensor.mqtt/)
Variable name | HA Shown text | EE State
--------|---------|---------
LockSens | open (unlocked) / closed (locked) | 1/0
MotionSens | motion detected / motion (clear) | 1/0
MoveSens | moving/ not moving (stopped) | 1/0  
TampSens | tampering detected/ no tampering (clear) | 1/0

Same as Sensors but only some device classes is delcared as default if more is needed see [Advance Settings](Advance.md) 
examples

## Switch:
[Home Assistant MQTT Switch](https://www.home-assistant.io/integrations/switch.mqtt/) 
Variable name | EE State
--------|---------
Relay|0/1  
State|0/1  
1. Create a dummy device and set the name of a value to include one of above Valuenames
Note it have to have 0 decimals

2. Add a new rule with the name Set%tskname% (exampel SetRelay if value is Relay)   
this rules job is to set the dummydevice and if needed GPIO  
Exampel:  
```
on SetRelay do
 taskvalueset,3,1,%eventvalue%
 taskrun,3
endon
```
3. Add rule for setting Relay and led of Shelly plug with EE or with button press:
```
on Button#State=0 do
 logentry,Toggeling Relay
 taskValueSet,3,1,1-[Relay#relay]
 event,Relay#relay
endon
on Relay#relay do
 gpio,15,[Relay#relay]
 let,1,1-[Relay#relay]
 gpio,0,%v1%
endon
```


## Button: (Beta)
[Home Assistant MQTT Button](https://www.home-assistant.io/integrations/button.mqtt/)
Variable name | EE State
--------|---------
Button|0/1  

create a dummy device and set the name of a value to include a Value name from above

add a new rule with the name Press%tskname% (exampel PressButton if value is Button)   
this rules job is to set the dummydevice and if needed GPIO  
Exampel:  
```
on PressButton do
 taskvalueset,3,1,%eventvalue%
 taskrun,3
endon
```
rule for setting Relay and led of Shelly plug with EE or with button press:
```
on Button#State=0 do
 logentry,Toggeling Relay
 taskValueSet,3,1,1-[Relay#relay]
 event,Relay#relay
endon
on Button#Button do
 gpio,15,[Relay#relay]
 let,1,1-[Relay#relay]
 gpio,0,%v1%
endon
```


## Dimmer:
[Home Assistant MQTT Light](https://www.home-assistant.io/integrations/light.mqtt/)
Variable name | EE State  
--------|---------
Brightness | 0-255  
Percent | 0-100  
CounterTime | 0-240  

1. Create a dummy device 
2. Set a name of a value to include "Percent"(0-100) or "Brightness"(0-255)
3. Set one more to with prefix "_" example "_Percent" and set it to 0 Decimals
3. Create a MQTT import device
4. Set a name to the same as step 2 and one to State
5. set 1 Topic to the topic that step2 creates and add /Set
6. do the same for topic 2 but with /State
7. Add rules to copy values between them and run task if command is recived  

(Exampel image both Devices)  
**MQTT Import**  
![MQTT Import](PNG/Dimmer_MQTTImport.PNG)
**Dummy Device**  
![Dummy Device](PNG/Dimmer_DummyDevice.PNG)
```
on Import#Percentage do
 taskvalueset,2,1,%eventvalue%
 taskrun,2
endon
on Import#State do
 taskvalueset,2,2,[Import#State]
 if [Import#State]=1 then
  taskvalueset,2,1,[Import#Percentage]
 else
  taskvalueset,2,1,0
 endif
 taskrun,2
endon
```

## RGBDimmer
[Home Assistant MQTT Light](https://www.home-assistant.io/integrations/light.mqtt/)
Variable name | EE State
--------|---------
RGBBrightness| 0-255 + RGB value  

1. Do all 7 Steps from Dimmer but in step 2 set the name to "RGBBrightness"
2. Add an secound MQTT import device
3. set the names to "R","G","B" and topic to MQTT topic of RGBBrightness and add "/_R","/_G","/_B"


## Termostat 
[Home Assistant MQTT Termostat](https://www.home-assistant.io/integrations/climate.mqtt/)  
Variable name | EE State | Extra info  
--------|---------|-----
SetTemp | 17-24 |
SetTime | 0-24 | 1. HA will read Fanmode state  

1. MQTT topic is SetTime topic and "/_FanModeSet"

1. Create a dummy device 
2. Set a name of a value to include "SetTemp" or "SetTime"  
(different settings of max and min temp as default  
this variable is the shown temperature in big at the Termostat)
3. Create a MQTT Import Device
4. Set one variable to the same name as in step 2
5. if needed set one more to SetMode
6. Set first topic to Dummy devices topic and add /Set
7. if Step 5 is done  set next as step 6 but with sufix /FanMode
8. Add below rule for moving value to Dummydevice if needed.
9. use the sent Temperature and Mode how you see fit use
```
on Import#SetTemp do
 Taskvalueset,devicenr,varNr,%eventvalue%
 taskrun,devicenr
endon 
```
**MQTT Import**  
![MQTT Import](PNG/Termostat_MQTTImport.PNG)  
**Dummy Device**  
![Dummy Device](PNG/Termostat_DummyDevice.PNG)  



## Select (Beta)
[Home Assistant MQTT Select](https://www.home-assistant.io/integrations/select.mqtt/)
Variable name | HA Shown text | EE State
--------|---------|--------
SelectFan|Off,Low,Mid,High|0-3
SelectLock|Unlock,Locked,Armed,0-2
SelectGarrage|Open,Closed,Car found,Car not found| 0-3
SelectColor|Black,White,Red,Green,Blue,Yellow,Orange,Purple|0-7

1. Create a dummy device
2. Set a name of a vale to include any of the select variants
3. Create MQTT import Device
4. Set one variable to the same name as in step 2
5. Set first topic to Dummy devices topic and add /Set
6. Add below rule for moving value to Dummydevice if needed. 
7. use the sent Value how you see fit use
8. See above for images of devices if unsure
```
on Import#SelectFan do
 Taskvalueset,devicenr,varNr,%eventvalue%
 taskrun,devicenr
endon 
```


## Tag (Beta)
[Home Assistant MQTT Tag Scanner](https://www.home-assistant.io/integrations/tag.mqtt/)
Variable name | EE State
--------|---------
Tag| Tag reading

Add any RFID device and verify that name contain Tag  
when tag is scanned it will now appear in  
HA/configuration/Tags  
There you can set name for Tags 
