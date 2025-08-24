# 🔘 Home Assistant Button Box – Community Spotlight  

<p>This project combines an ESP32 a small Oled screen and some buttons into a compact button box for Home Assistant. Designed originally by <a href="https://makerworld.com/en/models/1478816-habb-home-assistant-button-box-esphome#profileId-1543829">Akelyte</a> 
  (full credit to them), I’ve put my own spin on it with added features, a new enclosure, and extra ESPHome tweaks. Watch the full video <a href="https://youtu.be/jZzNDveuDVY" target="_blank">here</a>.</p>  

<img src="https://github.com/MarkWattTech/MarkWattTech-Tutorials/blob/main/Images/thumbnails/HABB.png" width="500">  
<br>  

## 📦 Features  

- Trigger **Home Assistant automations/scenes** with physical buttons  
- **OLED feedback display** for status, page number, and wake/sleep state  
- **Multi-page support** → up to **16 actions** from just 4 buttons  
- **Customisable screen timeout** (prevents OLED burn-in)  
- **Screen power toggle** (manual on/off)  
- **Guard press** – requires first press to wake screen before triggering  
- **Unique device binding** so multiple boxes don’t conflict  
- **Blueprint included** for simple setup & automation linking  
- Expandable → add a bigger screen, extra buttons, NFC, sensors, or even use it as a base for a DIY alarm keypad  
<br>  

## 🧰 Hardware Required  

| Item                | Notes                                   | Affiliate Link |
|---------------------|-----------------------------------------|----------------|
| ESP32 Dev Board     | ESP-WROOM-32 or similar                 | [Buy on Amazon](https://amzn.to/4mvzI6H) |
| SH1106 OLED Display | 1.3" I²C display                        | [Buy on Amazon](https://amzn.to/45TSo9l) |
| Membrane Keypad     | 1x4 keypad                              | [Buy on Amazon](https://amzn.to/4fPqJuC) |
| Dupont Wires        | Jumper cables for connections           | [Buy on Amazon](https://amzn.to/41jYiz3) |
| 3D Printed Enclosure| Original design by Akelyte, modded by me | [MakerWorld Link](https://makerworld.com/en/models/xxxx) |

💡 Don’t have a 3D printer? Services like **PCBWay** offer on-demand printing — just upload the STL, pick your material/finish, and get it shipped.  
<br>  

## 💻 Software Requirements  

| Software          | Purpose |
|-------------------|---------|
| [Home Assistant](https://www.home-assistant.io/) | Smart home hub & automations |
| [ESPHome](https://esphome.io/) | Firmware & HA integration |
| [My ESPHome YAML](./HABB.yaml) | Modified config with extra features |

A ready-to-use **Home Assistant blueprint** is included to simplify automation setup.  
<br>  

## ⚙️ ESPHome Setup  

1. Flash the provided YAML (`HABB.yaml`) to your ESP32 via ESPHome  
2. Connect OLED & keypad using I²C + GPIOs (see wiring diagram)  
3. Add the device to Home Assistant  
4. Use the **HABB Blueprint** to quickly configure scenes/automations  
5. (Optional) Adjust substitutions to tweak sleep timer, pages, etc.  
<br>  


## 🧠 Custom Logic Highlights  

- **Multi-page actions** → Hold button to cycle pages (displayed in corner)  
- **Guard press** → Screen-off mode prevents accidental triggers  
- **Exposed HA sensors** → Page, screen state, last action, etc.  
- **Device-unique actions** → Multiple button boxes won’t conflict  
<br>  

## 🖼 Enclosure  

- Original slimline case: Akelyte’s MakerWorld project  
- My mod: Taller body to fit Wago clips → no soldering, no header cutting  (In my final version I actually only used the dupont wires)
- Optional **magnet or bracket mount** for walls/racks  
<br>  

## 📢 Credits  

- Original project & enclosure: [Akelyte](https://makerworld.com/en/models/1478816-habb-home-assistant-button-box-esphome#profileId-1543829)  
- Modified code, features, and box: [Mark Watt Tech](https://youtube.com/@MarkWattTech)  
- Community spotlight video: [Watch here](https://youtu.be/jZzNDveuDVY)  

<br>  

## ☕ Support My Work  

If you enjoyed this project and want to support me:  

- 🔗 [YouTube](https://youtube.com/@MarkWattTech)  
- ☕ [Buy Me a Coffee](https://www.buymeacoffee.com/markwatttech)  
- 💸 [PayPal.me](https://paypal.me/markwatttech)  
- ❤️ [Patreon](https://www.patreon.com/markwatttech)  

Thanks for helping me keep making these open-source smart home builds! 🚀  
