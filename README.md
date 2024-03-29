# Squeezelite-ESP32 DIY Projects

### Squeezebox-Spinner (TAudio-case) 
Portable Squeezebox player using a TTGO TAudio (T9) running Squeezelite-ESP32 in mini a 3d printed case.

![Case Model](taudio-case.jpg)

### [Squeezebox-Tembed](/tembed)
Squeezebox SPDIF player using a TTGO T-Embed module. ***Now with Rhasspy Satellite compatibility!***  

![Tembed](tembed/tembed1.jpg)

### [Squeezebox-Dial](/twatcher-dial)
Squeezebox Bluetooth controller using a TTGO T-Watcher (T4) module (to interface with BT speakers)

### [Squeezebox-Soundbar](/bluetooth-soundbar)
Portable Squeezebox player based on an existing Bluetooth Soundbar.

## Squeezebox-Spinner
This project was designed for a Squeezelite-ESP32 project used with Home-Assistant as an audio and visual notification device.

[youtube link](https://youtu.be/1PFEcQugR4s)

Case supports
- [TTGO T9 Dev Board v1.6](http://www.lilygo.cn/prod_view.aspx?TypeId=50063&Id=1171&FId=t3:50063:3)
- • interchangeable center caps for speaker, [128x64 SSD1306 two-color I2C oled](https://www.amazon.com/gp/product/B072Q2X2LL), [240x240 ST7789 color SPI oled](https://www.amazon.com/gp/product/B08FB77YY2)
- 3 external buttons
- up to 1250mA Lithium Battery

Step files in [case](case/) folder.  Print with natural white PLA (translucent) for LEDs
NOTE:  The board is a sketch only.  Dimensions may not be accurate.

![Case Model](case/t_player.png)

### Configuration
Use the [Projects Web-Installer](https://wizmo2.github.io/TAudio-Case/), or flash the current Squeezelite-ESP32 firmware. 

For squeezelite-esp32 configuration use "I2S Dac" audio output mode (or Bluetooth)

| Hardware Options | NVS Key | Value |
|----------------------|-------------|-------------------------------------------------------------------|
| DAC | dac_config | model=WM8978,bck=33,ws=25,do=26,sda=19,scl=18,i2c=26 |
| Led Strip | led_vu_config | WS2812,length=19,gpio=22 |
| | bat_config | channel=7,scale=6.8,atten=3,cells=1 |
| | actrls_config | buttons (see below) |
| SPDIF Config* | spdif_config | bck=33,ws=25,do=15 |

#### Buttons
Suggested configuration for buttons using one of the display caps.  (The navigation is a little fiddly, but useable in a crunch)

buttons 
```
[{"gpio":34,"type":"BUTTON_LOW","pull":true,"long_press":600, "normal":{"pressed":"ACTRLS_VOLDOWN"}, "longpress":{"pressed":"ACTRLS_PREV"}},  {"gpio":39,"type":"BUTTON_LOW","pull":true,"long_press":600, "normal":{"pressed":"ACTRLS_VOLUP"}, "longpress":{"pressed":"ACTRLS_NEXT"}},  {"gpio":36,"type":"BUTTON_LOW","pull":true,"long_press":600, "normal":{"pressed":"ACTRLS_TOGGLE"}, "longpress":{"pressed":"buttons_nav"}} ]
```

buttons_nav
```
[{"gpio":34,"type":"BUTTON_LOW","pull":true,"long_press":600, "normal":{"pressed":"BCTRLS_DOWN"}, "longpress":{"pressed":"BCTRLS_LEFT"}},  {"gpio":39,"type":"BUTTON_LOW","pull":true,"long_press":600, "normal":{"pressed":"BCTRLS_UP"}, "longpress":{"pressed":"BCTRLS_RIGHT"}},  {"gpio":36,"type":"BUTTON_LOW","pull":true,"long_press":600, "normal":{"pressed":"ACTRLS_PLAY"}, "longpress":{"pressed":"buttons"}} ]
```
Note: Do not set the "green" GPIO option as it shares gpio with the Led strip

Backup files for squeezelite-ESP32 in [config](config/) folder

Example yaml files for Home-Assistant in [hass](hass/) folder

#### SPDIF
Been experimenting with the SPDIF output options, as the performance (especially with a 32bit build) is much better.  Came up with a solution using a SDRAM extension adapter and toslink transmitter soldered (and epoxied) to the back.  I'm using pins 4 and 6 for 3.3V power and pin 3 (GPIO15, DAT0) for the data output. _NOTE: GPIO2 physically made a neater solution, but did not work_

![SPDIF-SD](toslink.png)

## General Notes.
I trimmed the rear IO header to prevent interference with the 1200mA battery (see why it doesn't really matter below).  With a different 1250mAh battery, it was not necessary. 

The T9 board has nearly everything that you need, although there are a couple of issues.
- The I2c header shares a pin with the LED strip.
- The speaker output (disappointingly) needs an external amplifier.    
-  The main IO header pins are a little too short for standard jumpers and connectors ( I assume there is a low profile connector out there somewhere). For the final unit, I soldered  external connections to the header mounting tabs.
-  Most of the exposed IO have pullup resistors pre-installed. (I struggled to get the OLED SPI interface to work without modified code - although it may just be the board I was using)

I haven't yet found a suitable speaker for a "speaker cap" option (as mentioned, will need a driver amp board as well)

If you have issues with getting the server plugin to install, it may be necessary to install the standard SqueezeESP2 plugin and manually update the files on the server.  (On the linux docker, this is located in the mounted config folder /config/cache/InstalledPlugins/Plugins/SqueezeESP32)


