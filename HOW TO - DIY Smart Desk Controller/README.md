# 🛠 Flexispot E7Q + Nextion Control with ESPHome

This ESPHome project turns your ESP32 and Nextion display into a full-fledged control center for your Flexispot E7Q standing desk, smart lights, fan, and more. Perfect for creators, makers, and smart home geeks who want an integrated experience.

![Project Preview](https://your-image-url-here.com)

## 📦 Features

- Control **desk up/down/presets** via UART
- View and control **smart lights, fan, and devices** from Home Assistant
- Sync **real-time notifications** to a dedicated Nextion page
- Multi-page touchscreen UI for seamless navigation
- Custom height range with Home Assistant integration
- Auto screen brightness via virtual switch
- Built-in desk height number entity

## 🧰 Hardware Required

| Item                | Example / Notes                          | Affiliate Link             |
|---------------------|-------------------------------------------|-----------------------------|
| ESP32 Dev Board     | ESP-WROOM-32 or similar                  | [Buy on Amazon](#)         |
| Nextion Display     | 3.2" Basic (NX4024T032)                  | [Buy on Amazon](#)         |
| Flexispot Desk      | E7Q (or any using LoctekMotion protocol) | [Buy on Amazon](#)         |
| Wires + Power       | USB-C or 5V supply                       | [Buy on Amazon](#)         |
| Optional Accessories| LED strips, smart plugs, HA entities     | [Buy on Amazon](#)         |

*The above are affiliate links. Using these doesn't cost you anything extra, but it helps support the channel — thanks!* 💙

## 📁 Repository Structure

```
.
├── flexispot_e7q.yaml         # ESPHome configuration
├── nextion_display.hmi       # (Optional) Nextion editor file
├── images/                   # Screenshots and wiring diagrams
└── README.md                 # You're here!
```

## ⚙️ Getting Started

1. **Clone this repo** or copy the `flexispot_e7q.yaml` file into your ESPHome dashboard
2. Edit the following values:
   ```yaml
   substitutions:
     min_height: "79"    # Your desk's min height + 0.1
     max_height: "113"   # Your desk's max height - 0.1
   ```
3. Replace these Home Assistant entities with your own:
   - `light.left_key_light`
   - `light.right_key_light`
   - `light.ring_light`
   - `switch.playroom_light`
   - `fan.office_fan`
4. Flash to your ESP32 via USB or OTA
5. Connect your Nextion display (TX/RX/GND) to GPIOs 4 and 5 (adjust as needed)
6. Optionally update or load the `.hmi` file to match your screen layout

## 🔌 Wiring Guide

| Component        | ESP32 Pin | Notes                       |
|------------------|-----------|-----------------------------|
| Desk UART TX     | GPIO17    | Desk control TX             |
| Desk UART RX     | GPIO16    | Desk control RX             |
| Nextion TX       | GPIO5     | From Nextion to ESP         |
| Nextion RX       | GPIO4     | From ESP to Nextion         |
| Nextion GND      | GND       | Shared ground               |
| Nextion VCC      | 5V        | Use USB or regulated source |

## 💡 Nextion Pages

| Page ID | Page Name         | Description                  |
|---------|-------------------|------------------------------|
| 0       | Home              | Navigation overview          |
| 1       | Lights            | Toggle lights/fan/buttons    |
| 2       | Desk              | Stand/sit/presets/display cm |
| 3       | Notification      | Title + message from HA      |

## 🧠 Custom Logic Highlights

- Page detection via `on_page:` callback to sync UI with ESP state
- UART commands to move desk or trigger presets
- Home Assistant `text_sensor` to display HA input_text entities on Nextion
- `cover` component used to represent desk with proper open/close/stop

## 📢 Credits

- Desk control: [@iMicknl](https://github.com/iMicknl/LoctekMotion_IoT)
- Project and code: [Mark Watt Tech](https://youtube.com/@MarkWattTech)

## 🧪 Want to Contribute?

PRs welcome! Add new pages, UI improvements, or other desk models. Let's make this the best Flexispot control stack out there 💪

---

### 💬 Questions / Support

Drop an issue in the GitHub repo or hit me up on Twitter/X or YouTube comments!

> "Standing desks are better when you can control them with style."

---

### ☕ Support My Work

If you found this helpful and want to keep the projects coming, you can support me here:

- 🔗 [YouTube](https://youtube.com/@MarkWattTech)
- 🐦 [Twitter / X](https://twitter.com/MarkWattTech)
- 💬 [Discord](https://discord.gg/yourserverlink)
- 📘 [Facebook](https://facebook.com/MarkWattTech)
- ☕ [Buy Me a Coffee](https://www.buymeacoffee.com/markwatttech)
- 💸 [PayPal.me](https://paypal.me/markwatttech)
- ❤️ [Patreon](https://www.patreon.com/markwatttech)

Thanks for the support! You’re helping me build more open, hackable, and awesome projects.

