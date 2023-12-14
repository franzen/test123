# Release Notes

## 14 December 2023

### System version 8.2.3

- More responsive default settings for RSSI positioning

## 03 November 2023

### System version 8.2.2

- Link-layer security with AES-128 replaces DTLS: lays the grounds for multi-gateway systems and for extended security for all frames on-air.
- Weightless routing for PBs: scalability and efficiency (allows larger number of PBs per deployment)
- Battery conditioning for mains-powered C{x}ameleon devices (requires hardware revision 1.1): mitigates battery deterioration over time
- Reduced data consumption of Gateway
- RPL and CoAP performance improvements
- New network metrics and SLA reporting
- Persistent FOTA progress
- Fixes for the manual update on worn out Flash memory

## 05 October 2023

### Portal Version 8.0.1

- Updated battery status indicator for devices
- Minor bug fixes

## 05 July 2023

### Portal Version 8.0.0

- Introduces a new API version `v4`. See the [API documentation](https://app.swaggerhub.com/apis/wittra-iot/wittra/) for more information.
- Increases accuracy of currentmeter sensor to support milliampere precision.
- Minor bug fixes.

## 31 May 2023

### System version 8.0.3

- Migrate to new Wittra IoT device manager (replaces soon to be phased out Google IoT Core)
- Support for third-party Mioty service centers
- Upgrade Mioty base station and FPGA firmware
- Support for Mioty India RF profile
- Border-router upgrade bug fix
- Optimization of the WIPE positioning engine

## 15 May 2023

### Portal Version 7.4.1

- Introduces ability to inactivate positioning for devices to have them not report positioning data
- Updated pricing model with data points and fixed monthly pricing
- Minor bug fixes

## 12 April 2023

### Portal Version 7.4.0

- Support Australian region
- Bug fixes and improvements for map
- GUI updates
- Improved GW update information
- Performance improvements on device configuration
- Introduces a new API version `v3`, with support for the new device configuration structure. See the [API documentation](https://app.swaggerhub.com/apis/wittra-iot/wittra/) for more information.

## 15 March 2023

### Portal Version 7.3.0

This release lays the groundwork for 3D positioning, where WiTTRA Sense 360 devices will be able to report the height they are positioned on.

- Setting height for Mesh Routers and Positioning Beacons in preparation for 3D positioning
- WiTTRA Sense 360 devices now report height as a part of their location in preparation for 3D positioning
- Accurate positioning of Meshrouters and Positioning Beacons by providing longitude and latitude values from "Edit Mode" on map
- Bug fixes and Quality of life changes for map

## 16 February 2023

### Portal Version 7.2.0

- Web hook authentication token for verifying HTTP requests and their origin
- Support for new click-on platform with 4-20 mA, RTD, and Digital I/O ([Product](https://docs.wittra.se/#/products-420-rtd-dio) released soon)
- Bug fixes and minor quality of life changes

## 07 February 2023

### System version 7.0.3

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

## 18 January 2023

### Portal Version 7.1.0

- Added a new way to report bugs and feature requests, see "Report a Issue" at the bottom right of the page
- Renamed Power Meter to Current Meter
- Many improvements to our user interface
- Improved stability and latency for sensor data

## 8 December 2022

### System Version 6.1.8

- Fix ability to upgrade gateway via MQTT command

## 19 October 2022

### System Version 6.1.7

- Support for power meter click-on sensor
- Fix MiotySense360 configurability (via an update of the BLE application)

## 14 October 2022

### System Version 6.1.6

- Support for Australia RF region
- MiotySense360: support for unidirectional sensors (class Z)
- Positioning: add dynamic RSSI and ToF combination algorithm based on a radio environment classification algorithm
- Improved stability in connection between GW and cloud

## 7 October 2022

### Portal Version 7.0.0

- Migrated backend and database to SQL.
- Returns null values in API response body if data does not exists, previously returned empty string.
- Fixed bug that made integrations to always be specified as interval, now clearly distinguishes between interval data and event data.
- Added feature Positioning Markers for device reference positioning.
- Added ability to toggle device deployment mode.
- Introduced new version v2 of the API, see new documentation for details and new endpoints https://app.swaggerhub.com/apis/wittra-iot/wittra
- Stats no longer returned from data endpoints

#### Breaking changes for schemas in API v1

- /countries
  - GET
    - Fields en_US and sv_SE removed
    - Field uuid renamed to code
    - Field eu renamed to inEu

#### Updated endpoints between v1 and v2

- /organization/{organization_id}/projects/{project_id}/devices
  - GET
    - Under field latest, payloadId renamed to telemetryId
    - Field mioty renamed to miotyConfig
    - Field marker added
  - POST
    - Under field latest, payloadId renamed to telemetryId
    - Field mioty renamed to miotyConfig
    - Field marker added
- /organization/{organization_id}/projects/{project_id}/devices/{device_id}
  - GET
    - Under field latest, payloadId renamed to telemetryId
    - Field mioty renamed to miotyConfig
    - Field marker added
  - PATCH
    - Under field latest, payloadId renamed to telemetryId
    - Field mioty renamed to miotyConfig
    - Field marker added
- /organization/{organization_id}/projects/{project_id}/integrations
  - GET
    - Field data renamed to payload
    - Field type changed to lower case
  - POST
    - Field data renamed to payload
    - Field type changed to lower case
- /organization/{organization_id}/projects/{project_id}/integrations/{integration_id}
  - GET
    - Field data renamed to payload
    - Field type changed to lower case
- organization/{organization_id}
  - GET
    - Field uuid renamed to id
    - In field currentSubscription and nextSubscription:
      - Field dateActivated renamed to activatedAt
      - Field dateCancelled renamed to cancelledAt
      - In field periods
        - Field dateStart renamed to startDate
        - Field dateEnd renamed to endDate
        - Field paymentStatus changed to lower case
        - Field type changed to lower case
    - In field customer
      - Field addressLines changed from array type to two separate fields; addressLine1 and addressLine2
      - Field country renamed to countryCode
      - Field customerType renamed to type and changed to lower case
    - Field paymentMethod changed to lower case
    - In field projects
      - Field region changed to lower case
      - Field uuid renamed to id
  - POST changed to PATCH
    - In field currentSubscription and nextSubscription:
      - Field dateActivated renamed to activatedAt
      - Field dateCancelled renamed to cancelledAt
      - In field periods
        - Field dateStart renamed to startDate
        - Field dateEnd renamed to endDate
        - Field paymentStatus changed to lower case
        - Field type changed to lower case
    - In field customer (both request and response)
      - Field addressLines changed from array type to two separate fields; addressLine1 and addressLine2
      - Field country renamed to countryCode
      - Field customerType renamed to type and changed to lower case
    - Field paymentMethod changed to lower case
    - In field projects
      - Field region changed to lower case
      - Field uuid renamed to id
- organizations/{organization_id}/subscriptions/{subscription_id}
  - PATCH
    - Endpoint removed
- organizations/{organization_id}/invitations
  - GET
    - Field timestamp renamed to createdAt
    - Field organizationId added
    - Field membershipRoles added
  - POST
    - Field timestamp renamed to createdAt
    - Field organizationId added
    - Field membershipRoles added
- organizations/{organization_id}/invitations/{invitation_id}
  - PATCH (response schema)
    - Field timestamp renamed to createdAt
    - Field organizationId added
    - Field membershipRoles added
- organizations/{organization_id}/users/{user_id}
  - PATCH
    - Response code changed from 204 to 200
    - Response now includes object with key `permissions` containing an array of the new permission names
- partners/{partner_name}/projects/{project_id}
  - GET
    - Field uuid renamed to id
    - In field devices:
      - Under field latest, payloadId renamed to telemetryId
      - Field mioty renamed to miotyConfig
      - Field marker added
    - In field integrations
      - Field data renamed to payload
      - Field type changed to lower case
- partners/{partner_name}/projects/{project_id}/data
  - GET
    - Field payloadId renamed to telemetryId (also within the data points themselves in the schema)
- partners/{partner_name}/projects/{project_id}/devices/{device_id}
  - GET
    - Under field latest, payloadId renamed to telemetryId
    - Field mioty renamed to miotyConfig
    - Field marker added
- organizations/{organization_id}/projects
  - GET
    - Field uuid renamed to id
    - Field parentOrg renamed to organizationId
    - Field volatile renamed to isVolatile
    - Field region changed to lower case
    - Field createdAt added
    - Field isRemoved added
    - Field isReleaseCandidate added
  - POST
    - Field uuid renamed to id
    - Field parentOrg renamed to organizationId
    - Filed volatile renamed to isVolatile
    - Field region changed to lower case
    - Field createdAt added
    - Field isRemoved added
    - Field isReleaseCandidate added
- organizations/{organization_id}/projects/{project_id}
  - GET
    - Field uuid renamed to id
    - Field parentOrg renamed to organizationId
    - Filed volatile renamed to isVolatile
    - Field region changed to lower case.
    - Field createdAt added
    - Field isRemoved added
    - Field isReleaseCandidate added
  - PATCH
    - uuid renamed to id
    - Field parentOrg renamed to organizationId
    - Field volatile renamed to isVolatile (request and response schema)
    - Field region changed to lower case.
    - Field createdAt added
    - Field isRemoved added
    - Field isReleaseCandidate added
- organizations/{organization_id}/projects/{project_id}/data
  - GET
    - Field payloadId renamed to telemetryId (also within the data points themselves in the schema)

## 1 September 2022

### System Version 6.0.3

- Fix support for latest border-router hardware revision (with bmi270).
- Fix bug that prevented MRs and PBs from posting neighbor data.
- Re-introduce join attempt on motion for MRs and PBs.

## 15 August 2022

### System Version 6.0.2

- Unified Gateway: a new gateway that supports multiple protocol stacks simultaneously. Today, 6LoWPAN and MIoTy https://www.wittra.se/products/unified-gateway/
- MiotySense360: a new battery-powered sensor over MIoTy (long-range, low-power communication). Runs on the existing C{x}ameleon hardware https://www.wittra.se/technology/mioty/
- Support for third-party MIoTy devices (connected via the Wittra Unified Gateway).
- New bootloader for the Gateway and Unified Gateway.
- More responsive position updates for WiTTRA Sense 360 (30s while in motion).
- Quicker device re-join after offline events.
- Fix sleep bug in North America (915 MHz) release.

## 28 June 2022

### Portal Version 6.3.0

- Support for MiotySense360.
- Support for third-party mioty devices.
- Support for the power-meter.
- Authentication using Microsoft account.
- Webhook configuration.
- Conversion of all the devices into C{x}ameleon.
- Support for C{x}ameleon on all devices.
- Disable RSSI and usage event based posting.
- Various improvements and bug fixes.

## 20 April 2022

### Portal Version 6.2.0

- Impact detection feature.
- Improved Network View.
- Enabled Time-of-Flight in the US.
- Enabled 1-min posting frequency.
- Added network capacity view.
- Satellite mode for the map.
- Updated icons and names in Device List.

### System Version 5.4.1

- Fresh and consistent RSSI and neighbor data for network view.
- Support for impact detection.
- Time-of-Flight enhancements and hybrid with RSSI.
- On-demand remote gateway access.
- Improved manual update experience.

## 8 March 2022

### Portal Version 6.1.1

- Support for Chameleon devices.

## 14 January 2022

### Portal Version 6.0.4

- Improved support for external sensor.
- Removal of accuracy indicator on the map.
- Support for adding devices using QR code and adding multiple devices to projects.
- Bug fixes.

### System Version 5.3.1

- Time-of-Flight positioning.
- Improved security of release pipelines.
- Improved network scalability and positioning.

## 5 November 2021

### Portal Version 6.0.0

- Improved Cumulocity integration.
- Bug fixes.

### System Version 5.2.1

- Improved manual and automatic update procedures.
- Improved network scalability.
- Improved gateway stability.

## 10 September 2021

### System Version 5.1.0

- Improved network scalability and positioning accuracy.
- Event-based data posting is now supported in the LPTH click-on sensor.
- New gateway internal controlling services.
- Gateway positioning algorithm updates.
- Fixed a bug where devices would fetch configurations more often than expected.
- Various bug fixes.

### Portal Version 5.1.0

- Better email validation before inviting users to join the organization or project.
- Stricter validation for names when creating an organization or project.
- 'Subscription' is split into two views - 'Active Subscription' and 'Switch Tier'.
- Show the owner of the organization along with the email-id under User Access.
- Option to select/deselect all the permissions at once under User Access.
- Added integration examples to enhance Software Integrator's experience.
- Various bug fixes.

## 16 July 2021

### System Version 5.0.0

- Support for clip-on hardware.

- Improvements to the WIPE (positioning) algorithm.

- Improvements to the automatic update process for increased efficiency.

- The gateway reports its IP addresses to the cloud service.

- Improved network performance by optimizing radio usage.

- Improved proximity and RSSI probing and responses.

### Portal Version 5.0.0

- Support for clip-on hardware.

- Possibility to integrate a project in the portal with Cumulocity.

- New table with network link quality data.

- Possibility to move devices between projects.

- Bug fixes.

## 4 June 2021

### System Version 4.1.0

- Introduced RSSI-based 3D positioning of WiTTRA Sense 360.

- The internal logic in the proximity feature has been improved.

### Portal Version 4.10.0

- Support for managing floors in the map, to facilitate 3D positioning of WiTTRA Sense 360.

- When adding, changing or removing devices, events are propagated to the integrations of the project in question.

- Increased responsiveness and other improvements to the device list in the project view.

- Improved list of neighbors in the device drawer.

- Devices can no longer be configured in the device drawer. To configure a device, go to the Manage devices view in the project.

## 18 May 2021

### System Version 4.0.0

Please note that this is a new major version. If you upgrade to this version, you need to upgrade all devices in the IoT network, and not just a subset of them. The update needs to be performed manually.

- New logging functionality in the gateway, to allow for easier troubleshooting and customer support.

- Improved security through increased entropy in the DTLS keys.

- The border router capacity size is now increased to support up to 500 devices in a network.

- Gateways can now be rebooted remotely.

- The functionality of the LED has changed. When a device is connected to a charger, the LED will pulse if the device is charging or be steady ON if the device is fully charged. When a device is not connected to a charger, the LED will be off.

- Data from adjacent Wittra networks will now be filtered out.

- Improved the joining procedure for networks that are populated by many Mesh-Routers.

- Multiple bug fixes to increase long-term network stability, scalability and battery lifetime.

## 12 May 2021

### Portal Version 4.9.0

- New price model.

- Possibility to configure all your devices in just a few clicks. This is accessible from the Manage button in the device list of a project.

- Improved responsiveness and overall speed when navigating in organizations and projects.

- Storage of historical device data.

- Possibility to set permissions users that have been invited to organizations, even if they haven't responded to the invitation.

- Improved views for users with mobile devices or narrow windows.

- Bug fixes.

## 18 March 2021

### System Version 3.4.0

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

### Portal Version 4.6.1

- Possible to see why a device has rebooted in the in detailed view of a service.

- These release notes are now present in the home page of the portal, as well as in the documentation.

- Users that are added to an organisation are now only invited, and not directly added.

- Some columns/cells in the device table have had descriptions added, visible when hovering above them.

- Possibility to upgrade and downgrade between subscription tiers.

- Each project is now tied to a specific region; Europe or North America.

- Clarifications in the modal for performing manual firmware updates.

- Clarifications when changing the system version for a project.

- Possibility to edit the name of a project.

- Added a column with timestamps indicating when a device was started (uptime).

- Improved and extended documentation.

- Many bug fixes.

## 1 March 2021

### System Version 3.3.0

- Improved Manual Update OAD procedure.

- Bug fixes in security chip.

- Minor changes to the HW PIN driver.

- The network traffic through the border router is now monitored, and if the region specific regulations are exceeded it will turn off radio traffic. (This previously existed only on WiTTRA Sense 360 and MRs.)

- Several improvements to RSSI proximity, to achieve higher accuracy and faster responsiveness.

- Fixed an issue where devices would be unable to transmit.

- If a device is put into Manual Update Mode when there is an automatic update running, the device will no longer boot back into the old application.

### Portal Version 4.4.2

- Editing the PAN ID of a network is now done in the project settings view.

- Improved the map view when many devices are at located close to each other.

- Several bug fixes.

## 12 February 2021

### System Version 3.2.0

- TPM bug fixed in mb-watchdogd on the gateway.

- Several improvements have been done to ensure network stability.

### Portal Version 4.3.0

- New flow for manually updating device firmware.

- Refined network deployment tool.

- Possibility to leave organizations.

## 28 January 2021

### Portal Version 4.1.1

- Optimization of realtime data propagated to the portal
- Minor bug fixes
- Performance update to the data fetching in the portal

## 22 January 2021

### System Version 3.1.0

Please note that this is a new major version. If you upgrade to this version, you need to upgrade all devices in the IoT network, and not just a subset of them.

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

### Portal Version 4.0.3

- The portal has been reworked in its entirety. With the new portal, you will get crucial information about your Wittra IoT devices with fewer clicks, and it is easier to get an overview of your Wittra system.

- It is now possible to put labels on devices, allowing to group devices e.g. in the same building or on the same floor.
- It is now possible to upload image layers on top of the map, e.g. custom blueprints of a building.
- True position of gateways and Mesh-Routers can be set in the map for a project.

- The portal displays battery information received from the WiTTRA Sense 360.

- If the location of a WiTTRA Sense 360 has been measured with the aforementioned experimental RSSI-based positioning, it will show up in the new _Visualization_ tab, in the view for a project in the portal.

- The portal is now event-driven in the sense that both changes and new data are now instantaneously displayed.

- Automatic update of the system is now available. With one click, all devices in
  a project can now be automatically updated within 24-hours.

- It is possible to choose any supported system version for a project, instead of only the latest.

- Deployment tool. A graph showing the relationship between the components in a
  Wittra IoT network.

- Permissions have been added on an organization level. It is now possible to
  restrict or grant users permissions to certain views and actions in the portal.

- In the portal, Data Endpoints have been renamed to Integrations.

- It is possible to configure devices to report data only when changes happen (event-based), in addition to reporting at fixed intervals.

- There is an option to configure multiple devices at the same time.

- New payment system:
  - A dedicated Billing page with all billing information.
  - You can now add one or several payment cards to your organization and choose
    from which card Wittra will charge at the end of the month.
  - Pay outstanding bills directly in the portal.
