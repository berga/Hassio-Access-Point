# Hass.io Access Point
Use your hass.io host as a WiFi access point - perfect for off-grid and security focused installations.

## Main features
- Create a WiFi access point with built-in (Raspberry Pi) or external WiFi (USB) cards (using hostapd)
- Hidden or visible SSIDs
- DHCP server (using dnsmasq)
- MAC address filtering (allow/deny)

## Installation

Please add
`https://github.com/mattlongman/hassio-access-point` to your hass.io addon repositories list. If you're not sure how, see [instructions](https://www.home-assistant.io/hassio/installing_third_party_addons/) on the Home Assistant website.

## Config

### Options
- **ssid** (**required**): The name of your access point
- **wpa_passphrase** (**required**): The passkey for your access point
- **channel** (**required**): The WiFi channel to use
- **address** (**required**): The address of your hass.io WiFi card/network
- **netmask** (**required**): Subnet mask of the network
- **broadcast** (**required**): Broadcast address of the network
- **interface** (_optional_): Which wlan card to use. Default: wlan0
- **hide_ssid** (_optional_): Whether SSID is visible or hidden. 0 = visible, 1 = hidden. Defaults to visible
- **dhcp** (_optional_): Enable or disable DHCP server. 0 = disable, 1 = enable. Defaults to disabled
- **dhcp_start_addr** (_optional_): Start address for DHCP range. Required if DHCP enabled
- **dhcp_end_addr** (_optional_): End address for DHCP range. Required if DHCP enabled
- **allow_mac_addresses** (_optional_): List of MAC addresses to allow. Note: if using allow, blocks everything not in list
- **deny_mac_addresses** (_optional_): List of MAC addresses to block. Note: if using deny, allows everything not in list
- **debug** (_optional_): Set logging level. 0 = basic output, 1 = show addon detail, 2 = same as 1 plus run hostapd in debug mode
- **hostapd_config_override** (_optional_): List of hostapd config options to add to hostapd.conf (can be used to override existing options)

Note: use either allow or deny lists for MAC filtering. If using allow, deny will be ignored.

### Example configuration

```
    "ssid": "AP-NAME",
    "wpa_passphrase": "AP-PASSWORD",
    "channel": "6",
    "address": "192.168.10.1",
    "netmask": "255.255.255.0",
    "broadcast": "192.168.10.255",
    "interface": "wlan0",
    "hide_ssid": "1",
    "dhcp": "1",
    "dhcp_start_addr": "192.168.10.10",
    "dhcp_end_addr": "192.168.10.20",
    "allow_mac_addresses": [],
    "deny_mac_addresses": ['ab:cd:ef:fe:dc:ba'],
    "debug": "0",
    "hostapd_config_override": []
```


**Note**: This project was forked from [https://github.com/davidramosweb/hassio-addons](https://github.com/davidramosweb/hassio-addons/tree/f932481fa0503bf0f0b3f8a705b40780d3fe469a). I've submitted a lot of the functionality of this project back as a PR, but some of the extra stuff is outside the scope of a hostapd addon, so I'll leave it here for now as a more expandable hass.io access point addon.