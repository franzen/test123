# FAQ & Troubleshooting

Have an issue? Look here for support.

## General

#### Where do I find my batch token?

The batch token is printed on a sticker inside the box your
devices were delivered in. In the case of IoT Out of the Box,
see inside the plastic case.

#### I do not have a power supply/power cable

The devices require standard Micro-USB charging devices, see details in the
respective device datasheet. The hardware can be purchased
from your Wittra hardware supplier or any supplier who offers a standard
micro-USB charger that follows the requirements in the datasheet and Micro-USB
standards.

#### I don't have a USB-A to USB-Micro-B/USB-C adapter

The adapter can be purchased from any supplier offering the standard adapter
according to the USB standards.

#### My delivery is missing parts

Please contact the supplier from whom you ordered.

#### I would like to buy more or return devices
Please contact the supplier from whom you purchased the device.


## Gateway

For any question regarding connecting your Gateway, opening it, or for
a description of the LED indicators, see [Gateway documentation](products-gateway.md).
For deployment or outdoor use questions, see [Deployment Guide](howto-deployment-guide.md).
Also see our [Advanced Gateway settings page](howto-advanced-gateway-config.md),
which describes for example how to update security keys, and how to use a static IP address.

#### How do I see if my Gateway is working?

In the [Wittra portal](https://portal.wittra.se), navigate to the project for
which you have registered the gateway. Once in the project view, you can see a
list of gateways on the left-hand side. You should now be able to locate your
gateway ID in the list. If the gateway's status shows up as green it is working.

If you have not yet registered the gateway, see our [Getting started guide](/).

#### Why is my Gateway communicating with connman.net?

[ConnMan](https://wiki.archlinux.org/title/ConnMan) is a connection
manager used by the Gateway to maintain Internet connectivity. The
Gateway is expected to initiate traffic to connman.net. If this traffic
is blacklisted by your firewall, you can safely whitelist the website.

#### My Gateway is offline in the Portal - Unified Gateway

Please check that LED 3 (green), LED 4 (yellow), and LED 5 (green) are all
steady on.
If LED 3 (green) is not steady on, please check that all cables are plugged in
correctly and that the Unified Gateway is powered up.
If LED 4 (yellow) is not steady on, it might indicate that either something is
wrong with the LAN itself, or the Unified Gateway can connect to the LAN, but is
not able to connect to the Internet.

#### My Gateway is offline in the Portal - Legacy Gateway

Please start by opening the gateway casing and check that the power LED on the
Raspberry Pi shows a steady red and that the motherboard's (the board on
which the border router is mounted) LED shows a steady green. If not, please
check that all cables are plugged in correctly and that the gateway is powered
up.

If you got the gateway powered up, please proceed with the steps below.

The green LED on the Raspberry Pi itself indicates the network connection state.
First check that the green LED on the Raspberry Pi itself is lit a solid green,
which indicates that the Raspberry Pi has been able to connect to your LAN and
the Internet.

If the LED is not a steady green light this might indicate that something is
wrong with the LAN itself. Otherwise, it could indicate that the gateway can
connect to the LAN, but is not able to connect to the Internet.

#### My Gateway is connected to the Internet but still offline in the Portal

After having verified that the gateway is able to connect to the LAN and
the Internet, try restarting your gateway to see if the error disappears and
that the gateway shows up on the Wittra portal with green status (online).

If the gateway still does not appear online in the portal the problem may
be that the network blocks the Gateway's traffic to the Internet. In this case,
the physical LED would still indicate that the gateway can connect to the network,
but some services on the gateway can not connect to Wittra's cloud services.
See paragrpah below on how your router and firewall need to be configured.

If that does not help, please revisit the setup instructions in the
[Getting started guide](/).

#### What ports do I need open for the Gateway to function?

The Gateway uses the following egress ports: TCP ports 443 and 8883
and UDP port 123. Make sure to configure your router and firewall accordingly.

#### My Gateway is online in the portal but is not working correctly

If the Gateway is online on the Wittra portal it means it has been set up
correctly to the Internet. First, try and restart your gateway to see if the
error disappears.

If that is not the case, please try and update the gateway on the
[Wittra portal](https://portal.wittra.se).

#### The lid is hard to close

If you have installed the cable gland, verify that the nut has the flat surface facing upward.

## C{x}ameleon

For any questions regarding charging or resetting your device,
see [C{x}ameleon documentation](products-cxameleon.md).
For questions about mounting, attaching, and deployment, see
[Deployment Guide](howto-deployment-guide.md).
For questions about device updates, see [Updating your Devices page](howto-system-update.md).

#### My C{x}ameleon is offline

When we have not received data from a device for a given time, the device will be displayed as offline.
[This section](howto-portal.md?id=Devices) details how the offline timeout is calculated.

When a device is offline, the first thing is to check if it was ever seen online (see "Last seen")
in the Portal's device view. If it was not, make sure you have performed the manual update after
registering the device. If you have but the device is offline, see section below.

If the device was seen before, check the last battery level it has reported. If the battery was low
before the device came offline, it is likely that it ran out of battery. Proceed then to
[re-charging the device](howto-maintenance?id=recharging-batteries).

If the device is updated and charged, take it close to any online Mesh-Router or to the Gateway.
If it still does not come online, attempt a [reset with an OTG adapter](products-cxameleon?id=reseting-a-device).

#### After a manual device update, the device is not working

Devices under manual update are blinking rapidly. Please allow some time
for all devices to go through the update. If after some time, a device
seems to never pick up the update, repeat the manual update procedure.

#### After an automatic device update, the device is not working

Please allow some time to pass after an update to allow the device
to come back online. It might be the case that other devices in the
mesh network have not finished updating yet. Also, make sure that
the device is powered (whether on a charged internal battery
or via external power).

If the problem persists after other devices are online with the same version, try using your OTG adapter to reboot the device close to
the gateway or to a Mesh-Router that is showing as online in the portal.

If the device still is not coming online, try to perform the
update procedure again.

## Portal, API & Webhooks

For any documentation on setting up webhooks and using the API,
see [this page](howto-integrations-and-api.md).

#### I cannot log in to Wittra portal

If you have signed up with a Google account and are trying to log in with Microsoft
authentication (or vice versa), please refresh the page. You will then see all
the authentication options. Choose the one you used when you signed up to Wittra portal.
i.e. if you signed up using Google then use Google login.

#### The Webhook is not working

Make sure that the Webhook server is reachable from the internet, i.e. that no
firewall blocks incoming TCP traffic on the port used by the server.
Take a look at our
[examples](https://github.com/wittra/examples) on how to set up a test
Webhook server.

#### Where do I find examples of what applications and services I can build?

There are examples and accompanying documentation available in Wittra's
[examples GitHub repository](https://github.com/wittra/examples).

#### Can I have more than one integration/Webhook?

Yes, you can add multiple integrations to your project. Note that the
same data will be sent to all integrations. This can be useful if
you want your data to go into multiple existing systems.
