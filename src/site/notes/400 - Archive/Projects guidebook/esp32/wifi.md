---
{"dg-publish":true,"dg-path":"esp32/wifi.md","permalink":"/esp32/wifi/"}
---

# ESP32 Wi-Fi Communication

This section details the use of the ESP32's integrated Wi-Fi capabilities.

## 1. Overview

The ESP32 supports Wi-Fi connectivity, enabling it to function as a client (Station mode) to connect to existing networks or as an access point (AP mode) to create its own network.

## 2. Station Mode: Connecting to a Network

In Station mode, the ESP32 connects to an existing Wi-Fi network.

### Arduino IDE Code

```cpp
#include <WiFi.h>

const char* ssid = "YOUR_WIFI_SSID";       // Network SSID
const char* password = "YOUR_WIFI_PASSWORD"; // Network Password

void setup() {
  Serial.begin(115200);
  Serial.print("Connecting to WiFi: ");
  Serial.println(ssid);

  WiFi.begin(ssid, password); // Initiate connection

  while (WiFi.status() != WL_CONNECTED) { // Wait for connection
    delay(1000);
    Serial.print(".");
  }

  Serial.println("\nWiFi connected.");
  Serial.print("IP Address: ");
  Serial.println(WiFi.localIP()); // Display assigned IP address
}

void loop() {
  // Application code after Wi-Fi connection
}
```

### Functions Used

*   `WiFi.begin(ssid, password)`: Connects to a Wi-Fi network.
*   `WiFi.status()`: Returns the current Wi-Fi connection status (e.g., `WL_CONNECTED`).
*   `WiFi.localIP()`: Returns the ESP32's local IP address.

## 3. Access Point Mode: Creating a Network

In AP mode, the ESP32 establishes its own Wi-Fi network for other devices to connect to.

### Arduino IDE Code

```cpp
#include <WiFi.h>

const char* ap_ssid = "ESP32_AP";             // AP SSID
const char* ap_password = "your_ap_password"; // AP Password (can be NULL for open network)

void setup() {
  Serial.begin(115200);
  Serial.print("Setting up AP: ");
  Serial.println(ap_ssid);

  WiFi.mode(WIFI_AP); // Set Wi-Fi mode to Access Point
  WiFi.softAP(ap_ssid, ap_password); // Start the access point

  Serial.print("AP IP Address: ");
  Serial.println(WiFi.softAPIP()); // Display AP's IP address
}

void loop() {
  // Application code for AP mode
}
```

### Functions Used

*   `WiFi.mode(mode)`: Sets the Wi-Fi operating mode (e.g., `WIFI_AP`, `WIFI_STA`, `WIFI_AP_STA`).
*   `WiFi.softAP(ssid, password)`: Configures and starts the ESP32 as an access point.
*   `WiFi.softAPIP()`: Returns the IP address of the ESP32 when operating as an access point.

## Resources

*   [Random Nerd Tutorials - ESP32 Wi-Fi Examples](https://randomnerdtutorials.com/esp32-wi-fi-examples/)
*   [DeepBlueEmbedded - ESP32 Wi-Fi Tutorial](https://deepbluembedded.com/esp32-wifi-tutorial-station-access-point-modes/)

## Video Tutorial

<iframe width="560" height="315" src="https://www.youtube.com/embed/your_esp32_wifi_video_id" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
