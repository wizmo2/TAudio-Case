# Tembed Operation Manual
## Assembly
see [Project Page](https://github.com/wizmo2/TAudio-Case/tree/main/tembed#squeezelite-tembed) for details on harware configration and assembly.

## Flashing
Connect your T-Embed device to a PC, then use the [web-installer page](https://wizmo2.github.io/TAudio-Case/) to flash the latest Squuezbox-Tembed firmware

## WiFi Initialization
- Boot the device, look for a new wifi access point showing up, and connect to it. Default ssid and passwords are "squeezelite":"squeezelite". 
- Once connected, your browser should automatically navigate to 192.168.4.1 
- Wait for the list of access points visible from the device to populate in the web page
- Choose an access point and enter any credential as needed
- Once connection is established, make a note of the address the device received; this is the address you will use to configure it going forward 
- Press "OK" and then reboot the device

![Wifi Configuration](img/setup_wifi.png)

## Setup
**This guide assumes you already have a working Logitech Media Server instance running on your local network.**

Install the SqueezeESP32 plugin from the LMS "Server_Settings-Plugin" menu. _NOTE: Material Skin (re. screenshots), LineIn and LineOut plugins are also recommended_

When installed, additional menus are available in “LMS-Player_Settings” to configure the device. The Plugin adds an additional menu item to the device display (Extra-SqueezeESP32)

![Plugin](img/lms-player-settings.png)

### Device Setup
In LMS, use the "Player_Settings-Configuration' button to access the devices Web-UI.
_NOTE:  You can also use your browser to navigate to the device ip address `http://<device_ip>'_  

![Confuguration](img/lms-configuration.png)

A navigation bar provides access to various configuration setting sections.  Each section contains configuration settings with one or more parameters.  The current values are displayed.  Required parameters are indicated with a red (missing) or green icon.  To make changes to a configuration setting, set the parameters as needed and press the "Save" button to commit the changes.  Once all required configuration settings are configured, press the "Apply" button to commit the changes and restart the device. 

#### System-Device Name
![Device Name](img/setup_system_name.png)

The device name sets all named configurations, including the network host name and LMS player name.  _NOTE: additionally the BT, Airplay, and CSpot device names on non-PURE builds_

#### System-Services
![Service](img/setup_system_services.png)

Select "ADC(Line-in/Microphone)" service to enable the microphone service.  see [Voice Assistant Setup Guide](voice_assistant.md) for detailed instructions.

#### Audio Configuration
![Audio Mode](img/setup_audio.png)

The Audio-Squeezelite settings can be used to control the audio stream from LMS. See [README](../README.md#additional-configuration-notes-from-the-web-ui) for detailed information.  Additional settings are availbler in the LMS "Player_Settings" menu.

Set the required audio output mode from the drop-down list
- Analogue - speaker
- Digital - Toslink output
- Bluetooth - (not applicable)


### LMS Setup
![Audio Mode](img/lms-extras.png)

Use the "Player_Settings-Extras_Settings-ESP32_settings' button to access additional player configuration for the device.

Recommended settings are
- Artwork: Enabled 120x32
- Spectrum scaling: 10
- LED Brightness: 40
- LED Visualizer: Digital VU Meter

## Operation
When powered on, the display and rotary controls allow access to the LMS menus to operate the device.  If insstalled, a infra-red remote can be sued to navigate the menus.  Remote control is also available throughout the LMS Squeezebox eco-system.  

## Troubleshooting
The device has a number of additional configuration parameters that can be used for troubleshooting and diagnostics.  

### Hardware
The Hardware "Clear" checkbox can be used to reset the configuration setting parameters to factor defaults.

The following configuration settings can be found
- The DAC configures the audio processing hardware. See [README](../README.md#dac)
- The SPDIF configures the Toslink/SPDIF digital audio output. See [README](../README.md#spdif)
- The SPI bus is the communications bus used for display and ethernet. See [README](../README.md#spi)
- The I2C bus can be used for external axillaries. See [README](../README.md#i2c)
- The built-in OLED Display. See [README](../README.md#display) for details on changing orientation.  Additional configuration is available in the "LMS Player_Setting-Extra_Settings-ESP32_settings" menu
- The Rotary control and button See [README](../README.md#rotary-encoder) for customized operation modes
- The LED Visualizer controls the RGB LED strip. See [README](../README.md#led-strip). The LED visualizer effect and brightness can be changed from the "Playe-Settings-Extra_Settings_ESP32_settings" menu in LMS.
- The ADC configures the microphone input.  see [Voice Assistant Setup Guide](voice_assistant.md) for detailed instructions

![Controls](img/setup_hardware_rotary.png) ![Controls](img/setup_hardware_display.png) ![Controls](img/setup_hardware_led.png) ![Controls](img/setup_hardware_i2c.png)

- The device supports an IR received.  see [README](../README.md#infrared) for details on supported remotes.

### Diagnostics
The NVS Editor can be enabled from the Credits menu to expose and additional section to access the raw configurations settings. see [README](../README.md#Configuration) for detailed explanations for each setting

The Advanced Commands can be enabled to expose and additional section to access diagnostic parameters. 

## Update Squeezelite
_**WARNING:  The Squeezelite Software Updates should not be used, unless you wish to rest the device to standard firmware**_
- From the firmware tab, click on "Check for Updates"
- Select the firmware version from the list
- Click on "Flash Firmware"
- The system will reboot into recovery mode (if not already in that mode), wipe the Squeezelite partition and download/flash the selected version 

You can choose a local file or have a local webserver

