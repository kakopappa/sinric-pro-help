
# Smart Switch

How to create a Smart Switch device in Sinric Pro 

1. Login to  [Sinric](https://sinric.pro/)  
2. Click on **Devices**
3. Click on **Add Device** on top right corner
4. Enter the device name, description and select the device type as **Smart Switch**
5. Select a group 
6. Click Save

That's it. 

If you have already linked the Amazon Alexa skill, the app will show a popup like this:

Eveytime you turn on or off the device, the server will send  setPowerState action to your IOT module. If you are using the SDK

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
[https://github.com/sinricpro/SinricPro/blob/master/examples/Request/01_Switch/src/Switch.cpp](https://github.com/sinricpro/SinricPro/blob/master/examples/Request/01_Switch/src/Switch.cpp)

```python
def power_state(did, state):
print(did, state['state'])
return True, state['state']
```
[https://github.com/sinricpro/Python-Examples/blob/master/pro_switch_example/app.py](https://github.com/sinricpro/Python-Examples/blob/master/pro_switch_example/app.py) 


> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTU3NjY2MzA1MSw3MzA5OTgxMTZdfQ==
-->