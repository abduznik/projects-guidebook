---
{"dg-publish":true,"dg-path":"esp32/serial.md","permalink":"/esp32/serial/"}
---

# ESP32 Serial Communication

This section covers serial communication with the ESP32 using the Arduino IDE.

## Introduction

The ESP32 has three hardware serial ports, also known as UARTs. These are `Serial`, `Serial1`, and `Serial2`. `Serial` is the default port for communication with the computer over USB.

## Basic Serial Communication

Here's a simple example of how to send and receive data using the `Serial` object:

```cpp
void setup() {
  Serial.begin(115200);
}

void loop() {
  if (Serial.available()) {
    char received = Serial.read();
    Serial.print("I received: ");
    Serial.println(received);
  }
}
```

## Using Other Serial Ports

You can also use `Serial1` and `Serial2` for communication with other devices. You can specify the pins you want to use in the `begin()` function.

```cpp
#include <HardwareSerial.h>

HardwareSerial SerialPort(2); // use UART2

void setup() {
  // Initialize Serial port 2 for communication
  SerialPort.begin(9600, SERIAL_8N1, 16, 17); // RX, TX
}

void loop() {
  SerialPort.println("Hello from ESP32!");
  delay(1000);
}
```

## Recommended Resources

*   **ESP32 UART Communication:** [https://randomnerdtutorials.com/esp32-uart-communication/](https://randomnerdtutorials.com/esp32-uart-communication/)
*   **ESP32 Serial Communication between two boards:** [https://deepbluembedded.com/esp32-serial-communication-uart-example/](https://deepbluembedded.com/esp32-serial-communication-uart-example/)

## Video Tutorial

<iframe width="560" height="315" src="https://www.youtube.com/embed/l-24_q_y_pM" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
