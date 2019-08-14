
# Messages
There are 3 types of messages in Sinric

 1. Request
 2. Respond
 3. Event

An act of doing something in Sinric IOT platform will generate a **request** type message. Eg: Alexa, turn on [device name]. will generate a message like this 
```
{
 "payloadVersion": 1,
 "clientId": "alexa-skill",
 "createdAt": 1561476448,
 "deviceId": "5099803df3f4948bd2f98391",
 "deviceAttributes": "",
 "type": "request",
 "action": "setPowerState",
 "value": {
   "state": "On"
  }
}
```
[https://github.com/sinricpro/sample_messages/blob/master/01_PowerState/01_setPowerState/01_Request.json](https://github.com/sinricpro/sample_messages/blob/master/01_PowerState/01_setPowerState/01_Request.json)

 When you receive a request in your IOT module, you must respond to it by sending a **response** type message. The appropriate response to above request should be
```
{
 "payloadVersion": 1,
 "success": true,
 "message": "OK",
 "createdAt": 1561476448,
 "deviceId": "5099803df3f4948bd2f98391",
 "clientId": "alexa-skill",
 "messageId" : "c71d3cca-180a-49b0-83ca-f5d9f0aef242",
 "type": "response",
 "action": "setPowerState",
 "value": {
     "state": "On"
  }
}
```
[https://github.com/sinricpro/sample_messages/blob/master/01_PowerState/01_setPowerState/02_Response.json](https://github.com/sinricpro/sample_messages/blob/master/01_PowerState/01_setPowerState/02_Response.json)

* If you are using the SDK this is done for you internally!

Upon receiving this response in the server, the server will update the interested parties about the status of the **request** they made.

Let's imagine you want to turn on the device by pushing a button. in that case, you are interacting with a device physically or making a change to the device manually. So you should raise an **event** to let the server know about this change. 
``` 
{
 "payloadVersion": 1,
 "createdAt": 1561476448,
 "messageId": "fca894e9-9c47-4447-9313-be4475508a8d",
 "deviceId": "5099803df3f4948bd2f98391",
 "type": "event",
 "action": "setPowerState",
 "value": {
  "state": "On"
 },
 "cause": {
  "type": "PHYSICAL_INTERACTION"
 }
}
```

## UML diagram

```mermaid
sequenceDiagram
You ->> Alexa: Alexa, turn on [device name]
Alexa->>Sinric: turn on [device name]
Sinric->>IOT Device: {action:on}
IOT Device->>Sinric: {success:ture}
Note right of IOT Device: Responds back <br/>with success or failed <br/>status.
Sinric->> Alexa : Sucess!
Alexa->> You : Okey
```

How an request / response works:

```mermaid
graph LR
A[Alexa] -- 1. turn on tv --> B(Sinric)
B -- 2.turn on tv --> D[IOT Module]
D -- 3. succes --> B
B -- 4. Okey -->A
```

How an eworks:

```mermaid
graph LR
A[Alexa] -- 1. turn on tv --> B(Sinric)
B -- 2.turn on tv --> D[IOT Module]
D -- 3. succes --> B
B -- 4. Okey -->A
```

## Complete actions and events list

|                |Action |Event| 
|----------------|------|---------|------|
|**Smart Switch** | setPowerState | setPowerState 
|**Smart Light Bulb**  |setPowerState, adjustBrightness, setBrightness, setColor, decreaseColorTemperature, increaseColorTemperature, setColorTemperature, setPowerLevel, adjustPowerLevel|setPowerState, setPowerLevel, setColor, setColorTemperature          
|**Smart Switch with Dimmer**|setPowerState, setPowerLevel adjustPowerLevel|setPowerState, setPowerLevel|
|**Doorbell**| setPowerState|DoorbellPress, setPowerState|
|**Temperature Sensor** |setPowerState|setPowerState, currentTemperature|
|**Thermostat**|setPowerState,targetTemperature, setThermostatMode|setPowerState, targetTemperature, setThermostatMode, currentTemperature|
|**Window AC Unit**|setPowerState, targetTemperature, setThermostatMode, setRangeValue, adjustRangeValue|setPowerState, targetTemperature, setThermostatMode, setRangeValue, currentTemperature|
|**Fan**|setPowerState, setRangeValue|setPowerState, setRangeValue|
|**Motion Sensor**|setPowerState|setPowerState, motion|
|**Contact Sensor**|setPowerState|setPowerState, setContactState|
|**TV**|setPowerState, setVolume, adjustVolume, setMute, mediaControl, selectInput, changeChannel, skipChannels|setPowerState, setVolume, setMute, mediaControl, selectInput, changeChannel, skipChannels|
|**Smart Speaker**|setPowerState, setVolume, adjustVolume, setMute, mediaControl, setBands, adjustBands, resetBands, setMode|setPowerState, setVolume, setMute, mediaControl, setBands, resetBands, setMode|
|**Smart Doorlock**|setLockState|setLockState 

 



> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjQ0MzExMTE2LDY0MjQ1NTQzOF19
-->