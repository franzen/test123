# System Capabilities

This page details key capabilities of the system.
The numbers can not be guaranteed as they depend on a large number of environmental parameters.
They are provided for information purposes only, as a guide for system provisioning.

## Performance

Below are selected Key Performance Indicators (KPIs):
<!-- prettier-ignore -->
| KPI | Value |
| --- | --- |
| Maximum network size | No hard limit. Tested: 840. Estimated: >1000 |
| System capacity – sensor post | About 60 post per minute (e.g. 600 tags posting every 10 minutes) |
| System capacity – DRSSI | About 120 positions per minute (e.g. 600 tags positioned every 5 minutes) |
| System capacity – ToF | About 7 positions per minute (e.g. 600 tags positioned every 1.5h) |
| Delay on events (impact, temp threshold..) | Under 1 second tag to portal |
| Delays on position update | 1 minute |

## Battery Life

See below a few selected lifetime estimates for different scenarios:
<!-- prettier-ignore -->
| Scenario | Battery life |
| --- | --- |
| WiTTRA Sense 360 @ 30 min (temp only) | 2 years |
| WiTTRA Sense 360 @ 5 min (temp only) | 1.5 years |
| WiTTRA Sense 360 RSSI position @ 30s | 1 year |
| WiTTRA Sense 360 ToF every 2h + 5 min post | 1 year |
| MiotySense360 @ 30 min (temp only) | 2 years |
| Positioning beacon | w/ off-grid box 3 years |

Cost of system upgrades:
* Automatic firmware upgrade (FOTA): about 1% of a full charge per upgrade
* Manuel firmware upgrade (FOTA): about 0.2% of a full charge per upgrade

Lifetime extension with external batteries:
* [Battery pack](/products-battery-pack.md): lifetime x 4
* Off-grid box with 6 D-CELL: lifetime x 100
