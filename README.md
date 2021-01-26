# NodeRED_ESPEASY_AutoDiscovery  
Node to enable autodiscovery for EasyEsp without have the code on each device  
* Hint use MQTT Explorer to debug what is sent to Home Assistant  

**Controller:**  
![EasyEsp Controller](Controller.png)

Controller Subscribe:
homeassistant/%sysname%/#

Controller Publish:
homeassistant/%sysname%/%tskname%/%valname%

Will Retain:
True


**Sensorer:**
You only need to activate the device and set it to use the HA controller:
if the name of the variable is first row then the shown unit will be the secound row

["battery","%"],
        ["humidity","%"],
        ["temperature","°C"],
        ["power","W"],
        ["pressure","hPA"],
        ["current","A"],
        ["energy","KWh"],
        ["voltage","V"]

**Switch:**
Skapa Dummy device med namn som innehåller Relay eller Switch

Lägg till en rule som heter Set%taskname% (tex SetRelay) som sätter berörd taskvalueset
on SetRelay do
 taskvalueset,3,1,%eventvalue%
endon


**Dimmer/Sliders:**
inget stöd i nuläget kommer senare
