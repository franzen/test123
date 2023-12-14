# Accessing Your Data

When referring to _data_ in the Wittra Portal, it may be important to distinguish between _device data_ and _event data_.

**Device data** is the kind of data that is produced by the devices in a Wittra IoT Network.
That could be data from the sensors of a device, such as temperature and motion, but also meta-data such as the list of neighbors of a device.\
**Event data** is the kind of data that is produced by the Wittra Portal.
Typically, that kind of data is produced when various actions are taken in the portal, such as when someone adds one or several devices to a project.

Both device data and event data can be accessed through integrations and the REST API (see [Integrations & API](howto-integrations-and-api.md)).

## Device data

The format for the request body when a piece of sensor data is transmitted is shown below.

```json
{
  "deviceId": <string>,
  "gatewayId": <string>,
  "integrationId": <string>,
  "organizationId": <string>,
  "payload": {
    "accelerometer": {
      "x": <float>,
      "y": <float>,
      "z": <float>
    },
    "battery": {
      "chargingStatus": "NOT_PLUGGED" | "CHARGING" | "FULLY_CHARGED" | "CONDITIONING_DISCHARGING" | "CONDITIONING_CONNECTED" | "CONDITIONING_CHARGING"
      "percentage": <int>, // will be either 0, 25, 50, 75 or 100
      "voltage": <float>
    },
    "location": {
      "accuracy": <float>, // value between 0-1
      "latitude": <float>,
      "level": <int>,  // floor level
      "longitude": <float>,
      "height": <float>, // meters above floor
      "label": <string> // additional position information
    },
    "impact":{
      "x": <float>,
      "y": <float>,
      "z": <float>
    },
    "magnetometer": {
      "x": <float>,
      "y": <float>,
      "z": <float>
    },
    "neighbors": [ // list of the nearest Mesh-Routers and Positioning Beacons
      {
        "id": <string>,
        "rssi": <int>
      },
      {
        "id": <string>,
        "rssi": <int>
      },
      ...
    ],
    "temperature": <float>, // in °C
    "usage": {
      "moving": <int>, // in seconds
      "stationary": <int> //in seconds
    },
    "humidity": {
      "humidity": <float>, // relative humidity in percentage
      "temperature": <float> // °C
    },
    "light": <int>, // in lux
    "pressure": {
      "pressure": <float>, // in hPa
      "temperature": <float> // in °C
    }
    "currentmeter": {
      "average": <float>, // in Amp
      "max": <float>, // in Amp
      "min": <float>, // in Amp
      "nbr_of_samples": <int>, // Number of samples in last measurement window
      "temperature": <float>, // in °C
      "voltage": <int> // Internal battery voltage, in mV
    }

  },
  "payloadId": <string>,
  "payloadType": "DATA",
  "projectId": <string>,
  "source": "p" | "e", // p = periodic posting, e = event-based posting
  "timestamp": <string> // ISO 8601-formatted timestamp
}
```

Remarks about the `payload` object:

1. Not all fields in the object must be present in all posts.
2. A field may be elided e.g. due to the sensor being configured not to send data.
3. Some of the fields will only be present if the corresponding click-on sensor is connected:

- `humidity`, `light`, and `pressure` require [LPTH and LPTH-C](products-lpth-lpthc.md)
- `currentmeter` requires [Current Meter](products-current-meter.md)

## Event data

An example of what a request body can look like when an event from the portal is transmitted is shown below.

```json
{
  "eventType": "DEVICE_UPDATED",
  "integrationId": "gr2QznINzfolbWsBoT6B",
  "organizationId": "q3FLvOBERo4WRnRBXdFk",
  "payload": {
    "changes": {
      "name": {
        "new": "An example",
        "old": null
      }
    },
    "deviceId": "D00124B001E219580"
  },
  "payloadId": "T4AvsBg9T2Y5LpEPOCD6",
  "payloadType": "EVENT",
  "projectId": "44z92iTpbo2sDfirAATJ",
  "timestamp": "2021-06-04T13:47:48.256000+00:00",
  "userId": "5R94c5TaElfe97pCzPI5BxXRQdp1"
}
```
