


## How Amazon Alexa works with Sinric Pro

### Request
1.  The Alexa sends a message to the Sinric IOT Platform.
2.  The Sinric IOT Platform creates a request message and forward it to your IOT module.
3. Your IOT module responds back to the Sinric IOT Platform.
4. The Sinric IOT Platform update the device status according to your response and updates Alexa service.

```mermaid
sequenceDiagram
You ->> Alexa: Alexa, turn on [device name]
Alexa->>Sinric: turn on [device name]
Sinric->>IOT Device: {"action":"setPowerState"}
IOT Device->>Sinric: {"success": true}
Note right of IOT Device: Responds back <br/>with success or failed <br/>status.
Sinric->> Alexa : Sucess!
Alexa->> You : Okey
```

More simplified :

```mermaid
graph LR
A[Alexa] -- 1. turn on tv --> B(Sinric)
B -- 2.turn on tv --> D[IOT Module]
D -- 3. succes --> B
B -- 4. Okey -->A
```

### Event

Any Manual interaction with the device

1.  The user change the device state physically. (eg: push a button).
2.  Your IOT module creates an event message and send it to Sinric IOT Platform.
3.  The Sinric IOT platform update the device status  and update any interested 3-rd party service (eg Alexa)


```mermaid
graph LR
A[IOT Module] -- 1. turn on tv --> B(Sinric)
B -- 2.turn on tv --> D[Website/Alexa/GH/App]
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwNzkwODY5NTgsLTU1MjQ3MjI5OSwxOD
M4NTU4MTkzXX0=
-->