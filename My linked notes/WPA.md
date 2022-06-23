(**W**i-Fi **P**rotected **A**ccess) A security protocol for wireless 802.11 networks from the Wi-Fi Alliance that was developed to provide a migration from WEP. The WPA logo certifies that devices are compliant with a subset of 802.11i, while WPA2 certifies full support.

**Strong Security**

WPA and WPA2 use a sophisticated key hierarchy that generates new encryption keys each time a mobile device establishes itself with an access point. Protocols including 802.1X, EAP and [[RADIUS]] are used for strong authentication. A RADIUS server provides automatic key generation and enterprise-wide authentication.

For home and small business users who do not have an authentication server, WPA can be used in preshared keys (PSK) mode, which requires that a shared secret key be manually entered into the access points and each user's computer. The shared secret is used to automatically generate the encryption keys.

**WPA (2003) - 802.11i Subset for Migration Upgrades**

WPA's Temporal Key Integrity Protocol (TKIP) uses the same RC4 algorithm as WEP for encryption but adds sophisticated key management and effective message integrity checking. TKIP was designed to be efficient enough to work in older WEP devices by updating their firmware to WPA. See [WEP](https://www.pcmag.com/encyclopedia/term/wep).

**WPA2 (2004) - Full 802.11i**

In addition to TKIP, WPA2 supports the AES-CCMP encryption protocol. Based on the very secure AES national standard cipher combined with sophisticated cryptographic techniques, AES-CCMP was specifically designed for wireless networks. AES-CCMP requires more computing power than TKIP, and migration from WEP to WPA2 requires new hardware. Devices running in WPA2 mode are not backward compatible with WEP. See [802.11i](https://www.pcmag.com/encyclopedia/term/80211i), [AES-CCMP](https://www.pcmag.com/encyclopedia/term/aes-ccmp), [802.1X](https://www.pcmag.com/encyclopedia/term/8021x), [EAP](https://www.pcmag.com/encyclopedia/term/eap) and [RADIUS](https://www.pcmag.com/encyclopedia/term/radius).

**WPA3 (2018) - More Secure**

WPA3 provides an encrypted connection in public hotspots. It also makes it extremely difficult to hack the password of the user's connection because a brute force attack would require interaction with the user's Wi-Fi for each "guess" (see [brute force attack](https://www.pcmag.com/encyclopedia/term/brute-force-attack)). In addition, if the password is eventually deciphered, "forward security" prevents the decryption of any data previously captured.

![80211I.GIF](https://i.pcmag.com/imagery/encyclopedia-terms/wpa-80211i.fit_lim.size_640x.gif)

**802.11 Encryption Methods**