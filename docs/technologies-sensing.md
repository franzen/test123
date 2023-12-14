# Sensing

![img-application](images/applications/applications-agriculture.png)

This page describes the sensing capabilities in a Wittra system;
whether achieved by Wittra products or third-party components.

## Internal C{x}ameleon Sensors

The [C{x}ameleon](products-cxameleon.md) comes with built-in sensor elements.
This holds regardless of the device type: as a WiTTRA Sense 360, MiotySense360, a Mesh-Router, or a Positioning Beacon.
See [this section](products-cxameleon.md?id=internal-sensors) for details.

## External C{x}ameleon (Click-on) Sensors

Wittra also provides a number of click-on sensors that can be added
on the C{x}ameleon for additional sensing capability. Some of the
click-ons even offer a USB relay, which means it is possible to
power a device through the click-on device's USB port. In the future,
it will also be possible to stack multiple sensors on one single device.
See [this section](products-cxameleon.md?id=click-on-sensors) for details.

## Third-party Analog and Digital Sensor Elements

We are building new click-on devices that will offer an open interface
for third-party sensors to be part of any Wittra system.
It will be possible to connect any 4-20 mA loop, Resistance Temperature Detector,
or sensor with digital I/O via the [ADT click-on](products-420-rtd-dio.md).
We will also offer Modbus and HAN port connectivity with the upcoming
[CommBus](products-modbus-han.md).
This will enable you to select any specialized sensor element or meter
and add it in your Wittra system, taking advantage of the 6LoWPAN meshing
or Mioty connectivity, and combined with the other Wittra sensors and
tracking abilities.
Compatible with both WiTTRA Sense 360 and MiotySense360.

## Third-party Mioty Devices

It is also possible to connect third-party Mioty devices directly to
the Wittra Unified Gateway. See [this page](howto-third-party-mioty.md)
to learn how.

## Relevant Pages

To set up your system for positioning:
* The [environmental sensors](products-lpth-lpthc.md)
* The [current meter](products-current-meter.md)
* The [ADT click-on](products-420-rtd-dio.md)
* The [CommBus click-on](products-modbus-han.md)
* [Configure](howto-device-configuration.md) the WiTTRA Sense 360 devices for sensing
* See our [data format](resources-data-format.md) to extract the sensor data you need