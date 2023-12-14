# Portal Release Notes

## 05 October 2023

### Portal Version 8.0.1

- Updated battery status indicator for devices
- Minor bug fixes

## 05 July 2023

### Portal Version 8.0.0

- Introduces a new API version `v4`. See the [API documentation](https://app.swaggerhub.com/apis/wittra-iot/wittra/) for more information.
- Increases accuracy of currentmeter sensor to support milliampere precision.
- Minor bug fixes.

## 15 May 2023

### Portal Version 7.4.1

- Introduces ability to inactivate positioning for devices to have them not report positioning data
- Updated pricing model with data points and fixed monthly pricing
- Minor bug fixes

## 12 April 2023

- Support Australian region
- Bug fixes and improvements for map
- GUI updates for better information
- Improved GW update information
- Performance improvements

## 15 March 2023: Portal Version 7.3.0

This release lays the groundwork for 3D positioning, where WiTTRA Sense 360 devices will be able to also report the height they are positioned on.

- Setting height for Meshrouters and Positioning Beacons in preparation for 3D positioning
- WiTTRA Sense 360 devices now report height as a part of their location in preparation for 3D positioning
- Accurate positioning of Meshrouters and Positioning Beacons by providing longitude and latitude values from "Edit Mode" on map
- Bug fixes and Quality of life changes for map

## 16 February 2023: Portal Version 7.2.0

- Web hook authentication token for verifying HTTP requests and their origin
- Support for new click-on platform with 4-20 mA, RTD, and Digital I/O ([Product](https://docs.wittra.se/#/products-420-rtd-dio) released soon)
- Bug fixes and minor quality of life changes

## 18 January 2023: Portal Version 7.1.0

- Added a new way to report bugs and feature requests, see "Report a Issue" at the bottom right of the page
- Renamed Power Meter to Current Meter
- Many improvements to our user interface
- Improved stability and latency for sensor data

## 7 October 2022: Portal Version 7.0.0

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

## 28 June 2022: Portal Version 6.3.0

- Support for MiotySense360.
- Support for third-party mioty devices.
- Support for the power-meter.
- Authentication using Microsoft account.
- Webhook configuration.
- Conversion of all the devices into C{x}ameleon.
- Support for C{x}ameleon on all devices.
- Disable RSSI and usage event based posting.
- Various improvements and bug fixes.

## 20 April 2022: Portal Version 6.2.0

- Impact detection feature.
- Improved Network View.
- Enabled Time-of-Flight in the US.
- Enabled 1-min posting frequency.
- Added network capacity view.
- Satellite mode for the map.
- Updated icons and names in Device List.

## 8 March 2022: Portal Version 6.1.1

- Support for Chameleon devices.

## 14 January 2022: Portal Version 6.0.4

- Improved support for external sensor.
- Removal of accuracy indicator on the map.
- Support for adding devices using QR code and adding multiple devices to projects.
- Bug fixes.

## 5 November 2021: Portal Version 6.0.0

- Improved Cumulocity integration.
- Bug fixes.

## 10 September 2021: Portal Version 5.1.0

- Better email validation before inviting users to join the organization or project.
- Stricter validation for names when creating an organization or project.
- 'Subscription' is split into two views - 'Active Subscription' and 'Switch Tier'.
- Show the owner of the organization along with the email-id under User Access.
- Option to select/deselect all the permissions at once under User Access.
- Added integration examples to enhance Software Integrator's experience.
- Various bug fixes.

## 16 July 2021: Portal Version 5.0.0

- Support for clip-on hardware.
- Possibility to integrate a project in the portal with Cumulocity.
- New table with network link quality data.
- Possibility to move devices between projects.
- Bug fixes.

## 4 June 2021: Portal Version 4.10.0

- Support for managing floors in the map, to facilitate 3D positioning of WiTTRA Sense 360.
- When adding, changing or removing devices, events are propagated to the integrations of the project in question.
- Increased responsiveness and other improvements to the device list in the project view.
- Improved list of neighbors in the device drawer.
- Devices can no longer be configured in the device drawer. To configure a device, go to the Manage devices view in the project.

## 12 May 2021: Portal Version 4.9.0

- New price model.
- Possibility to configure all your devices in just a few clicks. This is accessible from the Manage button in the device list of a project.
- Improved responsiveness and overall speed when navigating in organizations and projects.
- Storage of historical device data.
- Possibility to set permissions users that have been invited to organizations, even if they haven't responded to the invitation.
- Improved views for users with mobile devices or narrow windows.
- Bug fixes.

## 18 March 2021: Portal Version 4.6.1

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

## 1 March 2021: Portal Version 4.4.2

- Editing the PAN ID of a network is now done in the project settings view.
- Improved the map view when many devices are at located close to each other.
- Several bug fixes.

## 12 February 2021: Portal Version 4.3.0

- New flow for manually updating device firmware.
- Refined network deployment tool.
- Possibility to leave organizations.

## 22 January 2021: Portal Version 4.0.3

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
