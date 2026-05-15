# Hang Glider Flight Computer

An onboard flight computer for hang gliders built on ESP32. Displays real-time altitude, airspeed, attitude (pitch/roll horizon), and environmental data on a 3.2" TFT screen.

## Hardware

| Component | Interface | Notes |
|---|---|---|
| ESP32 | — | Main controller |
| BMP280 | I2C (SDA-D21, SCL-D22) | Barometric altitude, temperature, humidity |
| MPU6050/6500 | I2C (SDA-D21, SCL-D22) | Accelerometer + gyroscope |
| NEO-6M GPS | UART2 (RXD2-16, TXD2-17) | Position, speed, GPS altitude |
| ILI9341 TFT 3.2" | SPI | 240×320px display |

## Features

- **Artificial horizon** — pitch/roll visualization with sky/ground rendering
- **Barometric altitude** — derived from BMP280 pressure readings
- **Vertical speed (variometer)** — calculated from consecutive altitude samples
- **GPS speed & position** — via TinyGPS++ over UART2
- **Gyroscope calibration** — 500-sample offset averaging on startup

## Libraries

- `Adafruit_ILI9341` + `Adafruit_GFX`
- `GyverBME280`
- `Adafruit_MPU6050`
- `TinyGPS++`

Install via Arduino Library Manager or PlatformIO.

## Status

Work in progress. Core sensor integration and display rendering are functional. Planned additions:

- [ ] Variometer audio output (buzzer tone mapping)
- [ ] Complementary filter for pitch/roll (gyro + accelerometer fusion)
- [ ] Flight logging to SD card
- [ ] Wireless telemetry (NRF24L01)
