# ESP32-WROOM LED Blink Project Summary

## Goal
Make the onboard LED (GPIO2, inverted) on an ESP32-WROOM dev board blink at 500ms intervals, controllable via an ESPHome switch, with reliable operation after power-on and OTA updates.

## Current Behaviour
- **Power up / reboot:** LED starts blinking immediately (switch ON by default).
- **Turning the switch OFF** stops the blinking and turns the LED off.
- **Turning the switch ON** starts the blinking again.
- The device connects to WiFi and exposes the API atesp32-wroom.local`.
- OTA updates are possible (password-protected).

## Files
-esp32-wroom.yaml – Main ESPHome configuration
-secrets.yaml – WiFi and OTA credentials

## Key Configuration Details
- **Board:** esp32dev (ESP32-WROOM-32)
- **LED pin:** GPIO2, inverted logic
- **Blink script:** restart mode, 500ms on/off while switch is active
- **Switch restore_mode:** ALWAYS_ON
- **on_boot:** Checks if switch is ON, starts blink script if so
- **Fallback AP:** "ESP32 Fallback Hotspot" / password: fallback123
- **OTA password:** ota_password
- **API:** Enabled, noise encryption off, reachable on port 6053

## Verified
- ✅ LED blinks correctly after boot
- ✅ Switch toggles blinking on/off
- ✅ OTA updates work
- ✅ API handshake successful
- ✅ WiFi signal: ~ -58 to -62 dBm
