# Hue-Secure-Camera
## Description
This repository is to hold information, analysis and, hopefully, code to access a [Philips Hue Secure Flood Light Camera EU](https://www.philips-hue.com/en-gb/p/hue-philips-hue-secure-flood-light-camera-eu/8720169177703) and other [Philips Hue Secure Cameras](https://www.philips-hue.com/en-gb/products/smart-security).

The **Floodlight Camera** packaging describes it as a [Zigbee Certified Product](https://zigbeealliance.org/wp-content/uploads/2021/04/07-4842-13-Zigbee-certification-policy.pdf). It is two Zigbee devices sharing a common base and power supply.

The floodlight part can be recognised as a colour light and can be commissioned into an existing Zigbee network.

The camera part is not recognised. It can be commissioned into a Zigbee network with a [Philips Hue Bridge](https://www.philips-hue.com/en-gb/p/hue-bridge/8719514342583) as coordinator using the proprietary [Philips Hue App](https://www.philips-hue.com/en-gb/explore-hue/apps/bridge) using WiFi and Bluetooth LE (BLE). The BLE advertisements emitted during setup do not conform to the _BLE Connectable Advertisement example_ in Appendix A of **Zigbee Direct Specification, Version 1.0**. In particular, instead of the 16-bit UUID of the Zigbee Direct Commissioning Service (0xFFF7) it has the 16-bit UUID of Signify Netherlands B.V. (formerly Philips Lighting B.V.) (0xFE0F).

## Hardware

The following hardware is available:
* 1 x [Philips Hue Secure Flood Light Camera EU](https://www.philips-hue.com/en-gb/p/hue-philips-hue-secure-flood-light-camera-eu/8720169177703)
* 1 x [Philips Hue Bridge, v2.1](https://www.philips-hue.com/en-gb/p/hue-bridge/8719514342583)
* 1 x [nRF52840 Dongle](https://www.nordicsemi.com/Products/Development-hardware/nrf52840-dongle)
* 1 x [nRF5340 DK](https://www.nordicsemi.com/Products/Development-hardware/nRF5340-DK)

## Resources
### Zigbee Sniffer
The **nRF52840 Dongle** can be used as a [Zigbee Sniffer](https://www.nordicsemi.com/Products/Development-tools/nRF-Sniffer-for-802154).

It is possible to sniff traffic on a **Philips Hue Bridge** Zigbee network. However, as the encrypted network key is unknown it is not possible to view the encrypted payload. The _clientkey_ looked promising as it was a 128-bit value in hex but doesn't work.
### Zigbee Light Bulb Emulator?
It might be possible to program the **nRF5340 DK** as a Zigbee Light Bulb Emulator that could be commissioned into a **Philips Hue Bridge** Zigbee network to investigate traffic between a **Secure Camera** and a light. Here is the [Zigbee: Light bulb](https://developer.nordicsemi.com/nRF_Connect_SDK/doc/latest/nrf/samples/zigbee/light_bulb/README.html).
Not sure if a **Philips Hue Bridge** would accept this as it may lack the necessary cryptographic information to identifiy it as a **Zigbee Certified Product**.

## References
[1]: https://community.home-assistant.io/t/philips-hue-secure-camera-without-a-hue-bridge/678816  "Philips Hue Secure Camera without a Hue Bridge?"
[2]: https://community.home-assistant.io/t/zigbee-direct/681653 "Zigbee Direct"
