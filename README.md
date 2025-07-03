# ESP32-S3-Box-3 LVGL Firmware 
ESP Home Configuration for the S3-Box-3 with an LVGL UI.

All credit and inspiration for the original UI goes to https://github.com/BigBobbas/ESP32-S3-Box3-Custom-ESPHome/

This firmware provides the S3 box with a template for voice assistant, timers, screen saver, analog clock, sleep, 12/24 hour time, media controls, radar sensing, temperature and humidity sensing, battery levels and indicator, alarmo integration, internal and external audio, and multiple pages for lights, thermostats, switches, media, scenes, locks and anything you want to add.

The full configuration requires the S3-Box-3 with sensor dock and battery.

Key Components:
- Radar: https://esphome.netlify.app/components/at581x
- Temperature & Humidity: https://esphome.io/components/sensor/aht10.html
- Wake Word VA: https://github.com/esphome/wake-word-voice-assistants/
- LVGL: https://esphome.io/components/lvgl/

This is effectively a template for others wishing to configure the S3 box as it is a complete UI but it requires integration of the required components to provide functionality.
This configuration is suitable for anyone with an understanding of ESPHOME, the S3-Box-3, Home Assistant and a voice pipeline.

The minimum supported ESPHome version is 2025.6.0.

# Loading
![loading](https://github.com/user-attachments/assets/55e0a1b8-8873-42a3-864f-297fa6826b6e)

# Home
![home](https://github.com/user-attachments/assets/19b1db2c-a7a9-41d6-a72a-3215d64bfcc8)
- The microphone indicator is a mute switch
- The alarm status indicator launches the security page
- The wifi status indicator launches the wifi page
- The red circle button on the device will return to the home page, stop a ringing timer, stop the voice assistant and stop any media.
- The top left button on the device will switch from Home page to screensaver, stop a ringing timer, or a long 10s press will perform a factory reset.
- The bottom left button on the device will reboot the device. 

# Voice Assistant
![voice_assistant](https://github.com/user-attachments/assets/be1ff06e-03ed-4ff1-9946-53632dce12de)

Voice Timer Started

![running_timer](https://github.com/user-attachments/assets/78ba5b8e-90c9-4d29-893d-173daf6c6707)

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

External Audio

![media_exterrnal](https://github.com/user-attachments/assets/cc9af414-de2a-4832-8bc7-78d8c03b7771)

# Screens
![screens](https://github.com/user-attachments/assets/304c2778-a0d5-4183-9f65-31bf96287a61)

# Security
![security](https://github.com/user-attachments/assets/445e7b62-2109-4f29-89e4-6a72aa173744)

Keypad - Pin code is required for alarm deactivation or changing modes, but not activation. 

![security_keypad](https://github.com/user-attachments/assets/e4230884-b372-48e3-96ac-6c31571d2bcd)

# Screensaver
![screensaver](https://github.com/user-attachments/assets/17d3bea1-6a0a-46b7-91c2-18b3a87ae473)

# Settings
![settings](https://github.com/user-attachments/assets/b564ab49-f3aa-40a1-b863-54f2c40d5cb2)

Voice Settings

![voice_settings](https://github.com/user-attachments/assets/13930457-d662-438e-9dca-809a4c969fe4)


Screensaver Settings

![screensaver](https://github.com/user-attachments/assets/56f8845c-0b13-426c-9974-813b05826f19)

Screensaver Timeout Settings

![screensaver timeouts](https://github.com/user-attachments/assets/f2e838ca-03c5-4755-81c4-c77f1ffa28e2)

Info

![settings_info](https://github.com/user-attachments/assets/39b2682f-fff6-46a9-a8d3-f61043336ae7)

Device Settings

![device_settings](https://github.com/user-attachments/assets/ef117464-a6b4-457f-abe3-f7dba3ef3e81)

# Wifi
![wifi](https://github.com/user-attachments/assets/b3d620e6-5143-4904-b3ef-78cab5da5b4a)

# OTA Updates
![ota](https://github.com/user-attachments/assets/b72041fb-3402-4387-a839-bb7c78d40b21)

# Configuration Guidance
LVGL functions differently to the standard ESPHOME UI. Instead of using lambda to construct pages and format them a hierarchical page structure is used combining the touchscreen and UI elements.
This means the LVGL section of the YAML contains all the UI elements including the pages and widgets. These widgets are interactive and have different actions associated to their type. 
The widgets have their appearance and interactions defined in this section. 
Setting the value of these widgets is not done in the LVGL configuration. Instead each component forces appropriate updates to the UI. So when a switch is turned on or off it needs to update the lvgl switch widget to be checked or not checked.
This means the UI updates interactively so that as actions are performed which can send service calls to home assistant or trigger local actions, the corresponding state changes in sensors can update the UI in response.
For each new or modified widget you need to update in the LVGL the action to take when a UI interaction occurs and in parallel you need to update the component to update the UI on value changes. 
