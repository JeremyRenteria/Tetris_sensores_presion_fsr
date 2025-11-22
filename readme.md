📋 Descripción General

Implementación del clásico juego Tetris en una ESP32 con interfaz web, pantalla OLED y control mediante sensor de presión FSR.

🛠️ Hardware Requerido
Componentes
ESP32 (NodeMCU-32S o similar)

Pantalla OLED SSD1306 (128x64 píxeles, I2C)

Sensor FSR402 (Force Sensitive Resistor)

Conexiones WiFi

# 🔌 Esquema de Conexiones

## ESP32 ↔ OLED Display (I2C)

| Componente | Pin ESP32 | Descripción |
|---|---|---|
| SDA | GPIO 21 | Datos I2C |
| SCL | GPIO 22 | Reloj I2C |
| VCC | 3.3V | Alimentación |
| GND | GND | Tierra |

## ESP32 ↔ Sensor FSR

| Componente | Pin ESP32 | Descripción |
|---|---|---|
| FSR | GPIO 34 (ADC1_CH6) | Entrada analógica |
| Resistencia | 10KΩ | Pull-down |

🎯 Funcionalidades Principales
1. Servidor Web
Interfaz responsive con diseño moderno

Actualización en tiempo real del estado del juego

Controles web para movimiento y rotación

Visualización del tablero en tiempo real

2. Control por Sensor FSR
Detección de presión para control izquierdo

Umbral configurable para activación

Anti-rebote integrado

3. Lógica del Juego
7 piezas de Tetris clásicas

Sistema de puntuación y niveles

Colisiones y rotaciones

Detección de líneas completas


# 🌐 API Endpoints

| Endpoint | Método | Descripción |
|---|---|---|
| / | GET | Interfaz web principal |
| /status | GET | Estado JSON del juego |
| /left | POST | Mover pieza izquierda |
| /right | POST | Mover pieza derecha |
| /rotate | POST | Rotar pieza |
| /down | POST | Bajar pieza |
| /start | POST | Iniciar/reiniciar juego |
| /ip | GET | Obtener IP del ESP32 |


🕹️ Controles Disponibles
Web Interface
Botones en pantalla ← → ↻ ↓

Teclado: Flechas direccionales

Botón Start/Reset

Sensor FSR
Presionar sensor = Mover izquierda

2. Conexión del Hardware
Conectar OLED via I2C

Conectar FSR al pin 34 con resistencia pull-down

Alimentar con 3.3V

3. Ejecución
Cargar código en ESP32

Abrir Serial Monitor (115200 baudios)

Anotar IP mostrada en Serial/OLED

Acceder via navegador web a http://[IP_ESP32]

🎮 Reglas del Juego
Puntuación
Línea completa: +100 puntos

Subir nivel: Cada 500 puntos

Aumento de velocidad: Por nivel

Controles
Web: Botones/teclado

FSR: Presionar para mover izquierda

Rotación automática: Excepto pieza O

🔄 Flujo del Programa
Setup: Inicializa WiFi, OLED, servidor web

Loop Principal:

Maneja peticiones web

Lee sensor FSR

Ejecuta lógica del juego

Game Loop:

Movimiento automático (caída)

Verificación de colisiones

Detección de líneas

Actualización de puntuación
