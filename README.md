# ESP32-S3-Box-3 LVGL Firmware 
ESP Home Configuration for the S3-Box-3 with an LVGL UI.

All credit and inspiration for the original UI goes to https://github.com/BigBobbas/ESP32-S3-Box3-Custom-ESPHome/

This firmware provides the S3 box 3 with a template for voice assistant, timers, screen saver with analog/digital clock, sleep, 12/24 hour time, media controls, radar sensing, temperature (in Celsius or Fahrenheit) and humidity sensing, battery levels and indicator, alarmo integration, internal and external audio, notifications with sound, and multiple pages for lights, thermostats, switches, media, scenes, locks and anything you want to add.

A UI Mode feature provides the ability to switch from the standard voice assistant UI to a HAL 9000 animated voice assistant or a Home animated voice assistant. This can easily be extended to add other VA UI experiences.

The On Device Wake Word includes the standard ESPHome wakeword models but also some experimental models including Okay computer, hey home assistant, okay hal and hey luna.

This is effectively a template for others wishing to configure the S3 box as it is a complete UI but it requires integration of the required components to provide functionality.
This configuration is suitable for anyone with an understanding of ESPHOME, the S3-Box-3, Home Assistant and Wake Word Voice Assistants.

Key Components:
- Radar: https://esphome.netlify.app/components/at581x
- Temperature & Humidity: https://esphome.io/components/sensor/aht10.html (but using AHT20 variant)
- Touchscreen: https://esphome.io/components/touchscreen/gt911.html
- Audio ADC: https://esphome.io/components/audio_adc/es7210.html
- Audio DAC: https://esphome.io/components/audio_dac/es8311.html
- Wake Word VA: https://github.com/esphome/wake-word-voice-assistants/
- Micro Wake Word Models: https://github.com/esphome/micro-wake-word-models/
- LVGL: https://esphome.io/components/lvgl/

# Requirements
Requires [S3-Box-3](https://www.espressif.com/en/dev-board/esp32-s3-box-3-en) with sensor dock and battery.

The minimum supported ESPHome version is 2025.6.0.

Last tested on Home Assistant 2025.6.3 and ESPHome Version 2025.7.1.

# Loading
![loading](https://github.com/user-attachments/assets/55e0a1b8-8873-42a3-864f-297fa6826b6e)

# Home
![home](https://github.com/user-attachments/assets/c203e51d-90fa-4515-ab5f-3832160a6f21)
- The microphone indicator is a mute switch
- The alarm status indicator launches the security page
- The wifi status indicator launches the wifi page
- A timer status indicator will appear while a timer is running and will launch the time remaining page
- The red circle button on the device will return to the home page, stop a ringing timer, stop the voice assistant and stop any media.
- The top left button on the device will switch from Home page to screensaver, stop a ringing timer, or a long 10s press will perform a factory reset.
- The bottom left button on the device will reboot the device. 

# Voice Assistant
![voice](https://github.com/user-attachments/assets/8c36d316-00ce-40dd-b0ed-fcafdacbfcda)

Voice Timer Started

![voice_timer](https://github.com/user-attachments/assets/51b9e7ec-b701-449e-9680-143d9a2e822d)

Voice Assistant in HAL UI Mode

https://github.com/user-attachments/assets/6a4cc3aa-5d56-4a20-91e0-ba3e1859db3c
- When enabled this UI replaces the above standard Voice Assistant screens


Time Remaining

![timer_remaining](https://github.com/user-attachments/assets/347f669a-3fff-4e83-b83f-a98d6d2b5891)

Timer Finished

![timer_finished](https://github.com/user-attachments/assets/9937af57-622a-445f-8673-225e46f03e45)

# Climate
![climate](https://github.com/user-attachments/assets/9e9e0256-6dce-487e-b432-e7d0861f1e4e)

Air Conditioner

![airconditioner](https://github.com/user-attachments/assets/5669463c-9815-49a9-aed5-636c6465e256)

# Lights
![lights](https://github.com/user-attachments/assets/650c78d1-3b2e-4940-942f-9be442687ede)

# Controls
![controls](https://github.com/user-attachments/assets/9b612a6d-4c20-4df4-babb-dce395eaa85f)

# Media
Internal Audio

![media](https://github.com/user-attachments/assets/8429813a-2a50-4d6e-b839-2099bf9da5d4)
![media_mute](https://github.com/user-attachments/assets/e01a7fb4-7653-4dcc-9dee-16ae9e02b21e)
- The volume controls on the media page control the volume of the S3 box including the Voice Assistant.

External Audio

![media_exterrnal](https://github.com/user-attachments/assets/cc9af414-de2a-4832-8bc7-78d8c03b7771)

# Screens
![screens](https://github.com/user-attachments/assets/304c2778-a0d5-4183-9f65-31bf96287a61)

# Security
![security](https://github.com/user-attachments/assets/445e7b62-2109-4f29-89e4-6a72aa173744)

Keypad - Pin code is required for alarm deactivation or changing modes, but not activation. 

![security_keypad](https://github.com/user-attachments/assets/e4230884-b372-48e3-96ac-6c31571d2bcd)

# Screensaver
![screensaver](https://github.com/user-attachments/assets/cfd4a9a8-a897-48be-923c-ae969e15e118)
![screensaver_digital](https://github.com/user-attachments/assets/e4175cca-149b-4f56-bf76-430edc172a47)

# Settings
![settings](https://github.com/user-attachments/assets/9f51c38d-4a3f-450a-9771-42b6d3ad4c6e)

Voice Settings

![voice_settings](https://github.com/user-attachments/assets/13930457-d662-438e-9dca-809a4c969fe4)
- WakeWord Location can be changed from On Device to Home Assistant
- Mute Responses will mute any response
- Wake Sound will play a wake sound when voice assistant wakes
- Show Conversation will display an excerpt of the conversation on the voice assistant screens.

Screensaver Settings

![screensaver](https://github.com/user-attachments/assets/56f8845c-0b13-426c-9974-813b05826f19)
- Timeout Settings opens next page
- Enable Screensaver turns on screensaver at time specified
- Wake on Presence wakes the device when the radar detects motion
- Timeout to Blank turns off the screen at time specified

Screensaver Timeout Settings

![screensaver timeouts](https://github.com/user-attachments/assets/f2e838ca-03c5-4755-81c4-c77f1ffa28e2)
- Delay Secs is the time until the screensaver starts
- Dim Brightness is the brightness level to use when the screensaver is enabled
- Screen Off Delay is the time until the screen turns off.

Info

![settings_info](https://github.com/user-attachments/assets/39b2682f-fff6-46a9-a8d3-f61043336ae7)

Device Settings

![settings_device](https://github.com/user-attachments/assets/bb127ed8-8100-4d58-a6f8-a4563086bda5)
- Ext Media Player outputs audio to the external audio player configured in the substitions section.
- Notification sound triggers a sound when a text notification is sent to the device. This is different to the wake sound.
- Brightness slider controls screen brightness

UI Settings

![uisettings](https://github.com/user-attachments/assets/dfa35db8-f2c6-49d7-8f5f-d13f26713a55)
- Time Format provides 12 or 24 HR time shown in all places
- ScreenSaver Clock allows Analog or Digital clock to be shown
- Tperature Unit updates all displayed temperatures to be Celsius or Fahrenheit
- UI Mode provides the ability to choose between the standard HA Voice Assistant UI or a HAL 9000 style animated voice assistant.

# Wifi
![wifi](https://github.com/user-attachments/assets/b3d620e6-5143-4904-b3ef-78cab5da5b4a)

# OTA Updates
![ota](https://github.com/user-attachments/assets/b72041fb-3402-4387-a839-bb7c78d40b21)

# Configuration Guidance
To use the wake, notify and timer sounds with external audio you will need to load the sounds folder to the www folder in your home assistant. This can be done through an add on like Filebrowser or SambaShare.

LVGL functions differently to the standard ESPHOME UI. Instead of using lambda to construct pages and format them separate to the touch screen configuration, LVGL uses a hierarchical page structure combining the touchscreen and UI elements.
This means the LVGL section of the YAML contains all the UI elements including the pages and widgets. These widgets are interactive and have different actions associated to their type. 

Setting the status of these widgets is not done in the LVGL configuration. Instead each component forces appropriate updates to the UI. So when a switch is turned on or off it needs to update the lvgl switch widget to be checked or not checked.
This means the UI updates interactively so that as actions are performed which send service calls to home assistant or trigger local actions, the corresponding state changes in sensors can update the UI in response.
For each new or modified widget you need to update the LVGL to specify the action to take when a UI interaction occurs and in parallel you need to update the entity to update the UI on state changes.

Example entity configuration is included to match the screens above providing starting configuration for how different types of devices can be configured.
