
# Smart Switch

How to create a Smart Switch in Sinric Pro

1. Log into your  [Sinric](https://sinric.pro/)  account
2. Click on **Devices**
3. Click on **Add Device**
4. Enter the device name, description and select the device type as **Smart Switch**
5. Select a group 
6. Click Save

That's it. 

If you have already linked the Amazon Alexa skill the app will show a popup like this on your mobile phone:

Cool!

Now let's complete the setup process. 

To do that, you must eneter the 
- WiFi credentials
- API key
- Switch ID (Dashboard -> Devices -> )
- Handle the setPowerState action in your IOT module and
  

#### If you are using the Sinric Pro C++ SDK: 
```c++
#include <Arduino.h>
#include <ESP8266WiFi.h>
#include <SinricPro.h>

#define SSID "YOUR WIFI-SSID HERE"
#define PASS "YOUR WIFI-PASS HERE"
#define API_KEY "YOUR-SINRIC-PRO-API-KEY-HERE"
#define SWITCH_ID "YOUR-SWITCH-DEVICE-ID-HERE"
...

bool onPowerState(const char* deviceId, PowerState_t& state) {
 Serial.printf("Device %s turned ", deviceId);
 switch (state) {
 case power_OFF : Serial.printf("off\r\n"); break;
 case power_ON : Serial.printf("on\r\n"); break;
}
 return true;
}
.....
```
Complete Arduino/ESP8266/ESP32 example is available here:
[https://github.com/sinricpro/SinricPro/blob/master/examples/Request/01_Switch](https://github.com/sinricpro/SinricPro/blob/master/examples/Request/01_Switch/src/Switch.cpp)

#### If you are using the Sinric Pro Python SDK: 
Update the credentails in 
[https://github.com/sinricpro/Python-Examples/blob/master/pro_switch_example/credentials.py](https://github.com/sinricpro/Python-Examples/blob/master/pro_switch_example/credentials.py)

then update the code,

```python
def power_state(did, state):
print(did, state['state'])
return True, state['state']
```
Complete Python example is available here:
[https://github.com/sinricpro/Python-Examples/blob/master/pro_switch_example/app.py](https://github.com/sinricpro/Python-Examples/blob/master/pro_switch_example/app.py) 

Supported Alexa capabilities
-  [Alexa.PowerController](https://developer.amazon.com/docs/device-apis/alexa-powercontroller.html)

Supported Google Home Traits
-  action.devices.traits.OnOff

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTU4NzQ5MTg2Nyw3MzA5OTgxMTZdfQ==
-->