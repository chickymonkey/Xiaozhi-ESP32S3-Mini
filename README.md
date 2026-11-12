# Xiaozhi-ESP32S3-Mini

# Xiaozhi ESP32-S3 Mini – ESPHome config

ESPHome config that turns the AliExpress **"MINI ESP32-S3-N16R8 Xiaozhi AI Voice Dialogue"** board (PCB `XH-S3E-AI_V1.0`, version without the OLED) into a Home Assistant voice satellite and speaker.

The factory firmware is Xiaozhi v1.9.4, SKU `bread-compact-wifi`. The pin map comes from that firmware's board config and was confirmed against the boot log.

## Pinout

| Function | GPIO |
|---|---|
| Mic (INMP441-style I2S) WS / SCK / SD | 4 / 5 / 6 |
| Amp (MAX98357A I2S) LRC / BCLK / DIN | 16 / 15 / 7 |
| BOOT / talk button | 0 |
| Volume Up / Down | 40 / 39 |
| Status LED (WS2812) | 48 |
| Header I2C (OLED, not fitted) SDA / SCL | 41 / 42 |

Flash is 16 MB (QIO) and PSRAM is 8 MB (octal).

## Features

- Media player entity for TTS announcements and audio from HA
- Push-to-talk voice assistant on the BOOT button (no wake word)
- Volume buttons change the volume on the board itself
- Status LED: solid green at 40% when idle, blinking cyan while speaking TTS
- Diagnostics: WiFi signal %, uptime, chip temperature, RAM and PSRAM usage

## Speaker

The MAX98357A drives a mono 4–8 Ω speaker, about 3.2 W into 4 Ω at 5 V. Its output is bridged, so **never connect either speaker wire to GND**.

## Usage

1. Add `wifi_ssid` and `wifi_password` to your ESPHome `secrets.yaml`.
2. Requires ESPHome 2025.10 or later.
3. Flash the first time over USB. After that you can update over the air.
