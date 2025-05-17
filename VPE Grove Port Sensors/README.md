# 🌱 Expand Your Home Assistant VPE with Grove Sensors

This ESPHome project shows you how to unlock the hidden potential of the **Home Assistant Voice Panel (VPE)** using its onboard **Grove port**. With simple plug-and-play sensors, no soldering, and native ESPHome support, your VPE can become a powerful, modular smart sensor hub.

[📺 Watch the full video walkthrough here](https://youtu.be/bxOYuOmHW1A)

---

## 📦 Features

* Plug-and-play Grove sensor integration
* Fully wireless firmware updates using ESPHome
* Supports **temperature**, **humidity**, **gas/VOC**, and other I2C-based Grove modules
* Works with **Seeed Studio**, **M5Stack**, and other Grove-compatible devices
* Expand beyond I2C using internal GPIO headers
* Optional support for custom 3D-printed enclosures to expose extra ports

---

## 🧰 Hardware Required

| Item                       | Example / Notes                    | Buy Link                                                                     |
| -------------------------- | ---------------------------------- | ---------------------------------------------------------------------------- |
| Home Assistant VPE         | Voice Assistant Panel              | [Buy from Nabu Casa](https://www.home-assistant.io/voice/)                   |
| Grove Sensor (AHT20)       | Temperature and Humidity Sensor    | [Seeed AHT20](https://www.seeedstudio.com/)                                  |
| Grove Sensor (SGP30)       | VOC + eCO2 Sensor                  | [Seeed SGP30](https://www.seeedstudio.com/)                                  |
| Grove I2C Hub              | 6-Port Expansion Hub               | [Seeed Grove Hub](https://www.seeedstudio.com/)                              |
| Grove Cables               | For connecting sensors             | Included with most sensors                                                   |
| 3D Printed Case (optional) | Custom VPE case with Grove cutouts | [Download STL from HA Docs](https://www.home-assistant.io/voice/vpe/extend/) |

*Affiliate links support the channel at no extra cost. Thanks!* 💙

---

## 💻 Software Requirements

| Software                                                                   | Description                      |
| -------------------------------------------------------------------------- | -------------------------------- |
| [ESPHome](https://esphome.io/)                                             | To configure and upload firmware |
| [Home Assistant](https://www.home-assistant.io/)                           | Central smart home platform      |
| [ESPHome Dashboard](https://esphome.io/guides/getting_started_hassio.html) | UI for managing devices          |

---

## ⚙️ Getting Started

1. **Take control of your VPE in ESPHome Dashboard**
2. Add the I2C configuration for the Grove port:

```yaml
i2c:
  sda: 8
  scl: 9
  scan: true
```

3. Add your sensors (example for AHT20):

```yaml
sensor:
  - platform: aht10
    temperature:
      name: "VPE Temperature"
    humidity:
      name: "VPE Humidity"
    update_interval: 60s
```

4. Save and install wirelessly to your VPE
5. Connect the sensor to the Grove port (access through rear plastic tab)

---

## 🔌 Add Multiple Sensors

To expand with multiple sensors:

1. Use a Grove I2C Hub
2. Connect all sensors into the hub
3. Update ESPHome config to include new devices:

```yaml
sensor:
  - platform: sgp30
    eco2:
      name: "VPE eCO2"
    tvoc:
      name: "VPE TVOC"
    baseline:
      eco2_baseline: 0x8C5C
      tvoc_baseline: 0x8ACB
```

*NOTE: Let the SGP30 run for \~12 hours before setting the baseline values.*

---

## 🧠 Beyond the Grove Port

If you want to go further:

* Open your VPE and access the exposed **GPIO pin headers**
* Connect motion sensors, relays, or addressable LEDs
* Add sensor logic via ESPHome as normal

Refer to the GPIO documentation: [VPE GPIO Guide](https://support.nabucasa.com/hc/en-us/articles/25938342327581)

---

## 🖨️ Custom Enclosures

Home Assistant provides 3D-printable STL files for custom cases:

* Add cutouts for Grove + GPIO headers
* Modify layout to suit your wiring needs

Print it yourself or use a service like **PCBWay** to manufacture your parts.

---

## 🧪 Tips & Notes

* Use **right-angled connectors** for better clearance inside the case
* If your Grove sensor isn’t detected, check pull-up resistors or use external power
* Sensors must use I2C protocol only (Grove analog/digital not supported directly)

---

## 🙌 Credits

* VPE Project: [Home Assistant Team](https://www.home-assistant.io/voice/)
* Sensor Logic: [ESPHome](https://esphome.io/)
* Guide & Video: [MarkWattTech YouTube](https://youtube.com/@MarkWattTech)

---

## 💬 Community & Support

* [💬 Join the Discord](https://discord.gg/DAG2yf7Ev3)
* [🐦 X / Twitter](https://x.com/MarkWattTech)
* [📺 YouTube](https://www.youtube.com/@MarkWattTech)

---

## ☕ Support This Project

If you found this helpful, consider supporting the channel:

* 💙 [Buy Me a Coffee](https://www.buymeacoffee.com/markwatttech)
* 🛒 [Amazon Storefront](https://www.amazon.co.uk/shop/markwatttech)
* 🧡 [Patreon](https://www.patreon.com/markwatttech)
* 💸 [PayPal](https://www.paypal.com/paypalme/markwatttech)

Thanks for helping build a smarter, more hackable smart home! 🏡

