
# Smart Switch

How to create a Smart Switch device in Sinric Pro 

1. Login to  [Sinric](https://sinric.pro/)  
2. Click on **Devices**
3. Click on **Add Device**
4. Enter the device name, description and select the device type as **Smart Switch**
5. Select a group 
6. Click Save

That's it. 

If you have already linked the Amazon Alexa skill, the app will show a popup like this:

Now, eveytime when you turn on or off the smart switch the server will send the setPowerState action to your IOT module. 

```c++
bool onPowerState(const char* deviceId, PowerState_t& state) {
 Serial.printf("Device %s turned ", deviceId);
 switch (state) {
 case power_OFF : Serial.printf("off\r\n"); break;
 case power_ON : Serial.printf("on\r\n"); break;
}
 return true;
}
```
Complete Arduino/ESP8266/ESP32 example:
[https://github.com/sinricpro/SinricPro/blob/master/examples/Request/01_Switch](https://github.com/sinricpro/SinricPro/blob/master/examples/Request/01_Switch/src/Switch.cpp)

```python
def power_state(did, state):
print(did, state['state'])
return True, state['state']
```
Python example:
[https://github.com/sinricpro/Python-Examples/blob/master/pro_switch_example/app.py](https://github.com/sinricpro/Python-Examples/blob/master/pro_switch_example/app.py) 

Supported Alexa capabilities
-  Alexa.PowerController
- 
1.  capabilities:  "[{"type":"AlexaInterface","interface":"Alexa","version":"3"},{"type":"AlexaInterface","interface":"Alexa.EndpointHealth","version":"3","properties":{"supported":[{"name":"connectivity"}],"proactivelyReported":true,"retrievable":true}},{"type":"AlexaInterface","interface":"","version":"3","properties":{"supported":[{"name":"powerState"}],"proactivelyReported":true,"retrievable":true}},{"type":"AlexaInterface","interface":"Alexa.RangeController","version":"3","instance":"TowerFan.Speed","capabilityResources":{"friendlyNames":[{"@type":"asset","value":{"assetId":"Alexa.Setting.FanSpeed"}}]},"properties":{"supported":[{"name":"rangeValue"}],"proactivelyReported":true,"retrievable":true},"configuration":{"supportedRange":{"minimumValue":1,"maximumValue":3,"precision":1},"presets":[{"rangeValue":3,"presetResources":{"friendlyNames":[{"@type":"asset","value":{"assetId":"Alexa.Value.Maximum"}},{"@type":"asset","value":{"assetId":"Alexa.Value.High"}},{"@type":"text","value":{"text":"Highest","locale":"en-US"}}]}}]}}]"
Supported Google Home Traits


> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTA3NzM3MjQ1MSw3MzA5OTgxMTZdfQ==
-->