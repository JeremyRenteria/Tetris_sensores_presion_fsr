📋 Descripción General
Implementación del clásico juego Tetris en una ESP32 con interfaz web, pantalla OLED y control mediante sensor de presión FSR.

🛠️ Hardware Requerido
Componentes
ESP32 (NodeMCU-32S o similar)

Pantalla OLED SSD1306 (128x64 píxeles, I2C)

Sensor FSR402 (Force Sensitive Resistor)

Conexiones WiFi

ESP32 ↔ OLED Display (I2C):
  SDA → GPIO 21
  SCL → GPIO 22
  VCC → 3.3V
  GND → GND

ESP32 ↔ Sensor FSR:
  FSR → GPIO 34 (ADC1_CH6)
  Resistencia pull-down: 10KΩ
