---
{"dg-publish":true,"dg-path":"esp32/setup.md","permalink":"/esp32/setup/"}
---

# ESP32 Setup

This section will guide you through setting up your ESP32 with the Arduino IDE.

## Prerequisites

Before you begin, make sure you have the latest version of the [Arduino IDE](https://www.arduino.cc/en/software) installed on your computer.

## 1. Add ESP32 Board Manager URL

1.  Open the Arduino IDE.
2.  Go to **File > Preferences** (or **Arduino IDE > Settings** on macOS).
3.  In the "Additional Board Manager URLs" field, add the following URL:

    ```
    https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json
    ```

4.  Click "OK".

## 2. Install ESP32 Boards

1.  Go to **Tools > Board > Boards Manager...**.
2.  Search for "esp32" and press Enter.
3.  Click the "Install" button for "esp32 by Espressif Systems".

## 3. Select Your Board

1.  Go to **Tools > Board > ESP32 Arduino** and select your ESP32 board from the list (e.g., "ESP32 Dev Module").
2.  Connect your ESP32 board to your computer.
3.  Go to **Tools > Port** and select the correct COM port for your ESP32.

## Recommended Resources

*   **Random Nerd Tutorials - Getting Started with ESP32:** [https://randomnerdtutorials.com/getting-started-with-esp32/](https://randomnerdtutorials.com/getting-started-with-esp32/)
*   **Last Minute Engineers - ESP32 with Arduino IDE:** [https://lastminuteengineers.com/esp32-arduino-ide-tutorial/](https://lastminuteengineers.com/esp32-arduino-ide-tutorial/)

## Video Tutorial

<iframe width="560" height="315" src="https://www.youtube.com/embed/7g_W4Yd9x_I" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
