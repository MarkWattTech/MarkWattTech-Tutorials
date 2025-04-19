# 🛠 HOW TO - Create a Smart Touchscreen Desk Controller

<p>This ESPHome project turns your ESP32 and Nextion display into a full-fledged control center for your standing desk, smart lights, fan, and more. Perfect for creators, makers, and smart home enthusiasts who want to add additional functionality to there desks. Watch the full video <a href="https://youtu.be/jZzNDveuDVY" target="_blank">Here</a></p> 
</h2>	
<img src="https://github.com/MarkWattTech/MarkWattTech-Tutorials/blob/main/Images/thumbnails/Smart%20Desk%20Controller%205.png" width="500">
<br>

## 📦 Features

- Control **desk up/down/presets** via UART
- View and control **smart lights, fan, and devices** from Home Assistant
- Sync **real-time notifications** to a dedicated Nextion page
- Multi-page touchscreen UI for seamless navigation
- Custom height range with Home Assistant integration
- Auto screen brightness via virtual switch
- Built-in desk height number entity
<br>
<br>

## 🧰 Hardware Required

| Item                | Example / Notes                          | Affiliate Link             |
|---------------------|-------------------------------------------|-----------------------------|
| ESP32 Dev Board     | ESP-WROOM-32 or similar                  | [Buy on Amazon](https://amzn.to/4cER4tZ)         |
| Nextion Display     | 3.2" Basic (NX4024T032)                  | [Buy on Amazon](https://amzn.to/3Gf7gps)         |
| Nextion Display     | 3.2" Basic (NX4024T032)                  | [Buy on Amazon](https://amzn.to/4iZkVzL)         |
| Nextion Display     | 2.4" Basic (NX4024T032)                  | [Buy on Amazon](https://amzn.to/424bzvi)         |
| Flexispot Desk      | E7Q (or any using LoctekMotion protocol) | [Buy on Amazon](https://amzn.to/4ilDzk9)                               |
| USB to TTL          | FT232 (DSD Tech)                         | [Buy on Amazon](https://amzn.to/4l0A0lO)         |
| Dupont Wires        | Wires used for connecting esp32          | [Buy on Amazon](https://amzn.to/41UTSiZ)         |
| Wago Connectors     | Optional for attatching wires            | [Buy on Amazon](https://amzn.to/3Y2zF8d)         |
| RJ45 Pinout         | Board for ethernet pinout                | [Buy on Amazon](https://amzn.to/4jkL5gp)         |
| SD Card             | Optional                                 | [Buy on Amazon](https://amzn.to/3EvchK8)         |

*The above are affiliate links. Using these doesn't cost you anything extra, but it helps support the channel — thanks!* 💙
<br>
<br>

## 💻 Software Requirements

The following software must be installed and set up:

| Software          | Description |
|-------------------|-------------|
| [Nextion Editor](https://nextion.tech/nextion-editor/) | Used to design and build the touchscreen interface (HMI file). |
| [Home Assistant](https://www.home-assistant.io/)       | Central hub that manages devices, automations, and the interface for notifications and toggles. |
| [ESPHome](https://esphome.io/)                          | Used to compile and upload firmware to the ESP32, and bridge communication between hardware and Home Assistant. |

All three are essential for full functionality.
<br>
<br>

## ✅ Compatible Desks

The following software must be installed and set up:

| Desk               | Controller Model Number |
|--------------------|-------------------------|
| [Flexispot E7Q](https://flexispot.co.uk/4-leg-standing-desk-e7q) | U                       |


<br>


## ⚙️ The ESPHome Section

1. **Clone this repo** or copy the `DeskController.yaml` file into your ESPHome dashboard
2. Edit the substitution values (5 sections):
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
<br>
<br>

## 🔌 Wiring Guide

| Component        | ESP32 Pin | Notes                       |
|------------------|-----------|-----------------------------|
| Desk UART TX     | GPIO17    | Desk control TX             |
| Desk UART RX     | GPIO16    | Desk control RX             |
| Nextion TX       | GPIO5     | From Nextion to ESP         |
| Nextion RX       | GPIO4     | From ESP to Nextion         |
| Nextion GND      | GND       | Shared ground               |
| Nextion VCC      | 5V        | Use USB or regulated source |


See additional diagrams in the diagram folder
<br>
<br>

## 💡 Nextion Pages

| Page ID | Page Name         | Description                  |
|---------|-------------------|------------------------------|
| 0       | Home              | Navigation overview          |
| 1       | Lights            | Toggle lights/fan/buttons    |
| 2       | Desk              | Stand/sit/presets/display cm |
| 3       | Notification      | Title + message from HA      |
<br>
<br>

## 🧠 Custom Logic Highlights

- Page detection via `on_page:` callback to sync UI with ESP state
- UART commands to move desk or trigger presets
- Home Assistant `text_sensor` to display HA input_text entities on Nextion
- `cover` component used to represent desk with proper open/close/stop
<br>
<br>

## 📢 Credits

- Desk control: [@iMicknl](https://github.com/iMicknl/LoctekMotion_IoT)
- Project and code: [Mark Watt Tech](https://youtube.com/@MarkWattTech)
<br>
<br>

## 🧪 Want to Contribute?

PRs welcome! Add new pages, UI improvements, or other desk models. Let's make this the best Flexispot control stack out there 💪

---
<br>

### 💬 Questions / Support

Drop an issue in the GitHub repo or hit me up on Twitter/X or YouTube comments!


---
<br>

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

