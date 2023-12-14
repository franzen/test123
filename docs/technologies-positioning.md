# Positioning

![img-application](images/applications/applications-marine.png)

The WiTTRA Sense 360 relies on and combines two positioning technologies:
- **RSSI** (Received Signal Strength Indicator) positioning is achieved
by measuring the radio signal strength between the device and surrounding
Mesh-Routers or Positioning Beacons. The information is then posted
and used for trilateration. The drawback with RSSI positioning is it is
not accurate if the distance between the device and the measuring infrastructure
is too large (typically not more than 15 meters or so).
- **ToF** (Time-of-Flight) positioning is based on a series of send-receive (ping-pong)
sessions between the device and surrounding Positioning Beacons (NB:
Mesh-Routers are not able to participate in ToF). The propagation delay
of the wireless signal is measured, posted, and used again for trilateration;
sometimes in combination with RSSI data. This is much more difficult to do
than measuring RSSI signals, but the advantage is consistent accuracy over much
larger distances. As an example, the Wittra network has shown an accuracy of
plus/minus a few meters at a distance of 100 meters from the network infrastructure.

Depending on the local environment, you can expect better than ±10 meters accuracy
in general, and even ±5 meters most of the time outdoors or in an office environment.
With our [environmental click-on sensor](products-lpth-lpthc.md)
on the WiTTRA Sense 360 and Positioning Beacon, it is also possible to estimate height.
Today we are able to achieve floor-level positioning.

Coming soon is our [UWB (ultrawide band)](products-uwb.md) click-on, which will
enable sub-meter accurate 3D positioning!

**WiPE** (Wittra Intelligent Positioning Engine) is a service that runs on the Gateway.
WiPE takes all the RSSI and ToF timing data and combines it to produce a unique
Latitude / Longitude coordinate (plus height) for each WiTTRA Sense 360, each time a
position update is requested by the WiTTRA Sense 360 device. (There are advantages in
combining both RSSI and ToF data for improved accuracy and consistency).
This coordinate is then transported to the specified data End Point (either the
Wittra portal or a third-party computing resource) where it can be displayed on a map GUI.

## Relevant Pages

To set up your system for positioning:
* Read our [deployment guide](howto-deployment-guide.md)
* [Configure](howto-device-configuration.md) the WiTTRA Sense 360 devices for positioning
* [Set up the map](howto-set-up-map.md)