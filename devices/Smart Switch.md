
# Smart Switch

How to create a Smart Switch 

1. Log into your  [Sinric](https://sinric.pro/)  account
2. Click on **Devices**
3. Click on **Add Device**
4. Enter the device name, description and select the device type as **Smart Switch**
5. Select a group 
6. Click Save

That's it. 

If you have already linked the Amazon Alexa skill, the app will show a popup like this on your phone:


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
-  [Alexa.PowerController](https://developer.amazon.com/docs/device-apis/alexa-powercontroller.html)

Supported Google Home Traits
-  action.devices.traits.OnOff

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTQ4MzEzNzUwMyw3MzA5OTgxMTZdfQ==
-->