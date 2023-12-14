# Release Notes

## 14 December 2023: System version 8.2.3
- More responsive default settings for RSSI positioning

## 03 November 2023: System version 8.2.2

- Link-layer security with AES-128 replaces DTLS: lays the grounds for multi-gateway systems and for extended security for all frames on-air.
- Weightless routing for PBs: scalability and efficiency (allows larger number of PBs per deployment)
- Battery conditioning for mains-powered C{x}ameleon devices (requires hardware revision 1.1): mitigates battery deterioration over time
- Reduced data consumption of Gateway
- RPL and CoAP performance improvements
- New network metrics and SLA reporting
- Persistent FOTA progress
- Fixes for the manual update on worn out Flash memory

## 31 May 2023: System version 8.0.3

- Migrate to new Wittra IoT device manager (replaces soon to be phased out Google IoT Core)
- Support for third-party Mioty service centers
- Upgrade Mioty base station and FPGA firmware
- Support for Mioty India RF profile
- Border-router upgrade bug fix
- Optimization of the WIPE positioning engine

## 07 February 2023: System version 7.0.3

- Distributed RSSI: battery-efficient positioning and support for frequent updates
- Weightless tags: scalability and efficiency of WiTTRA Sense 360 (larger number of devices per deployment)
- Gateway upgrade: reliability and observability enhancements
- Gateway resilience to intermittent internet (keep network online while Internet is down for up to 1h)
- Sleepy PBs: enable battery-powered Positioning Beacons by turning them off when not needed.
- Decrease power consumption for devices with low usage: WiTTRA Sense 360 and MiotySense360 can now sleep for arbitrarily long periods of time (no hardcoded heartbeat)
- Floor positioning (aided by barometric pressure on WiTTRA Sense 360 and Positioning Beacons, via LPTH(-C) click-on sensor)
- Support new C{x}ameleon hardware revision (8j)
- Improved network stability and efficiency of MAC retries
- Misc. on-air traffic optimization

## 8 December 2022: System Version 6.1.8
- Fix ability to upgrade gateway via MQTT command

## 19 October 2022: System Version 6.1.7
- Support for power meter click-on sensor
- Fix MiotySense360 configurability (via an update of the BLE application)

## 14 October 2022: System Version 6.1.6
- Support for Australia RF region
- MiotySense360: support for unidirectional sensors (class Z)
- Positioning: add dynamic RSSI and ToF combination algorithm based on a radio environment classification algorithm
- Improved stability in connection between GW and cloud

## 1 September 2022: System Version 6.0.3
- Fix support for latest border-router hardware revision (with bmi270).
- Fix bug that prevented MRs and PBs from posting neighbor data.
- Re-introduce join attempt on motion for MRs and PBs.

## 15 August 2022: System Version 6.0.2
- Unified Gateway: a new gateway that supports multiple protocol stacks simultaneously. Today, 6LoWPAN and MIoTy.
- MiotySense360: a new battery-powered sensor over MIoTy (long-range, low-power communication). Runs on the existing C{x}ameleon hardware.
- Support for third-party MIoTy devices (connected via the Wittra Unified Gateway).
- New bootloader for the Gateway and Unified Gateway.
- More responsive position updates for WiTTRA Sense 360 (30s while in motion).
- Quicker device re-join after offline events.
- Fix sleep bug in North America (915 MHz) release.

## 20 April 2022: System Version 5.4.1
- Fresh and consistent RSSI and neighbor data for network view.
- Support for impact detection.
- Time-of-Flight enhancements and hybrid with RSSI.
- On-demand remote gateway access.
- Improved manual update experience.
## 14 January 2022: System Version 5.3.1
- Time-of-Flight positioning.
- Improved security of release pipelines.
- Improved network scalability and positioning.

## 5 November 2021: System Version 5.2.1
- Improved manual and automatic update procedures.
- Improved network scalability.
- Improved gateway stability.

## 10 September 2021: System Version 5.1.0
- Improved network scalability and positioning accuracy.
- Event-based data posting is now supported in the LPTH click-on sensor.
- New gateway internal controlling services.
- Gateway positioning algorithm updates.
- Fixed a bug where devices would fetch configurations more often than expected.
- Various bug fixes.

## 16 July 2021: System Version 5.0.0
- Support for clip-on hardware.
- Improvements to the WIPE (positioning) algorithm.
- Improvements to the automatic update process for increased efficiency.
- The gateway reports its IP addresses to the cloud service.
- Improved network performance by optimizing radio usage.
- Improved proximity and RSSI probing and responses.

## 4 June 2021: System Version 4.1.0
- Introduced RSSI-based 3D positioning of WiTTRA Sense 360.
- The internal logic in the proximity feature has been improved.

## 18 May 2021: System Version 4.0.0
- New logging functionality in the gateway, to allow for easier troubleshooting and customer support.
- Improved security through increased entropy in the DTLS keys.
- The border router capacity size is now increased to support up to 500 devices in a network.
- Gateways can now be rebooted remotely.
- The functionality of the LED has changed. When a device is connected to a charger, the LED will pulse if the device is charging or be steady ON if the device is fully charged. When a device is not connected to a charger, the LED will be off.
- Data from adjacent Wittra networks will now be filtered out.
- Improved the joining procedure for networks that are populated by many Mesh-Routers.
- Multiple bug fixes to increase long-term network stability, scalability and battery lifetime.

## 18 March 2021: System Version 3.4.0
- The calculation that limits a device from sending too much data now takes the region (Europe or North America) into account.
- Increased the size of each data block when sending firmware to devices, resulting in faster automatic updates.
- Adjusted timings when the device is joining a network to save battery power.
- Fixed a bug that caused the gyroscope to report too small values.
- Fixed a bug when devices posts data that could previously cause the device to run out of free memory.
- The initialization sequence for each device has been refactored for improved stability.
- Various bug fixes.
- Cloud config automatically propagates to GW services.
- Gateways can now update up to three devices simultaneously, in Manual Update Mode.
- New version of Tunslip6 for the border-router in the gateway.
- Gateway contains software license information in the file system.
- Various bug fixes.

## 1 March 2021: System Version 3.3.0
- Improved Manual Update OAD procedure.
- Bug fixes in security chip.
- Minor changes to the HW PIN driver.
- The network traffic through the border router is now monitored, and if the region specific regulations are exceeded it will turn off radio traffic. (This previously existed only on WiTTRA Sense 360 and MRs.)
- Several improvements to RSSI proximity, to achieve higher accuracy and faster responsiveness.
- Fixed an issue where devices would be unable to transmit.
- If a device is put into Manual Update Mode when there is an automatic update running, the device will no longer boot back into the old application.

## 12 February 2021: System Version 3.2.0
- TPM bug fixed in mb-watchdogd on the gateway.
- Several improvements have been done to ensure network stability.

## 22 January 2021: System Version 3.1.0
- Introduced experimental support for geographical positioning of WiTTRA Sense 360. This is built upon RSSI values from WiTTRA Sense 360 and Mesh-Routers, and requires no additional hardware.
- Introduced support for Frequency Hopping, which removes the need to set a specific frequency for the Sub-GHz network, between WiTTRA Sense 360, Mesh-Routers and gateways. This increases reliability as well as throughput, allowing for larger networks to be built and more data to be sent.
- WiTTRA Sense 360 now post battery information, with an expected remaining percentage.
- Now supports greater distance 6LoWPAN updates over the Wittra network
- When upgrading firmware automatically, the estimated time until completion is now sent by the devices that are being updated.
- COAP stability enhancements w.r.t. reconnection and timeout
- WiTTRA Sense 360 now post a heartbeat message every five minutes.
- WiTTRA Sense 360 now post the total transmission (TX) time.
- The underlying operating system for WiTTRA Sense 360 and Mesh-Routers has been changed to TI-RTOS.
- Radio usage for each device is now reported to the cloud portal.
- Temperature and battery data can now be received in the cloud portal as event-based data. The configuration is done in the portal.
- Devices now report their uptime for the duration that they have been on.
