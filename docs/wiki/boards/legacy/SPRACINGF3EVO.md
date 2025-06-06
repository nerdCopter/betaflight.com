# Seriously Pro SP Racing F3 EVO

The Seriously Pro Racing F3 Evo board (SPRacingF3EVO) is the evolution of the first board designed specifically for Cleanflight.

Purchasing boards directly from SeriouslyPro / SP Racing and official retailers helps fund Cleanflight development, it's the reason the Seriously Pro boards exist! Official retailers are always listed on the SeriouslyPro.com website.

Full details available on the website, here:

http://seriouslypro.com/spracingf3evo

## Hardware Features

- Next-generation STM32 F3 processor with hardware floating point unit for efficient flight calculations and faster ARM-Cortex M4 core.
- MicroSD-Card socket for black box flight log recorder - optimize your tuning and see the results of your setup without guesswork.
- Race transponder built in - just turn up at a race and have your lap times recorded.
- Features the latest Accelerometer, Gyro and Mag/Compass and Baro/Altitude sensor technology.
- Wire up using pin headers for all major connections for excellent crash-durability. Use either right-angled or straight pin-headers.
- No compromise I/O. Use all the features all the time; e.g. Connect your USB + OSD + SmartPort + SBus + GPS + LED Strip + Battery Monitoring + 8 motors - all at the same time! (Sonar will be supported in CF 1.14)
- 8 PWM output lines for ESCs and Servos. Arranged for easy wiring on standard pin headers.
- Supports direct connection of SBus, SumH, SumD, Spektrum1024/2048, XBus receivers. No external inverters required (built-in).
- Supports direct connection of 3.3v Spektrum Satellite receivers via 3 pin through-hole JST-ZH connector.
- Dedicated PPM receiver input.
- 3 Serial Ports - NOT shared with the USB socket.
- Telemetry port
- Micro USB socket.
- Dedicated output for programmable LEDs - great for orientation, racing and night flying. (Currently mutually exclusive with the Transponder).
- Dedicated I2C port for connection of OLED display without needing flight battery.
- Battery monitoring for voltage and current.
- RSSI monitoring (analogue or PWM).
- Buzzer port for audible warnings and notifications.
- Developer friendly debugging port (SWD) and boot mode selection, unbrickable bootloader.
- Symmetrical design for a super tidy wiring.
- JST-SH sockets only for I2C, UART2 and SWD. UART2 also on through-hole pins.
- Flashing via USB or serial port.
- Stackable design - perfect for integrating with OSDs and power distribution boards.
- Standard mounting - 36x36mm with standard 30.5mm mounting holes.
- LEDs for 3v, 5v and Status for easy diagnostics.
- Copper-etched Cleanflight logo.

## Serial Ports

| Value | Identifier | RX         | TX           | 5v Tolerant | Notes                                                                                                                               |
| ----- | ---------- | ---------- | ------------ | ----------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| 1     | USART1     | PA10       | PA9          | YES         | 2 through-hole pins. Use for connecting to OSD/GPS/BlueTooth.                                                                       |
| 2     | USART2     | PA15       | PA14 / SWCLK | YES         | JST socket and PPM header. Use to connect to RX.                                                                                    |
| 3     | USART3     | PB11 / AF7 | PB10 / AF7   | NO          | Available on 4 through-hole pins. 3.3V signals only ! Use for GPS, Spektrum Satellite RX, SmartPort Telemetry, HoTT telemetry, etc. |

- You cannot use SWD and USART2 at the same time.
- When using a Serial RX receiver the TXD (T2) pin cannot be used for telemetry. Use UART3 TXD instead.
- Software serial is not supported
- Windows DFU Flashing requires Zadig (see configurator)

## Pinouts

Full pinout details are available in the manual, here:

http://seriouslypro.com/files/SPRacingF3EVO-Manual-latest.pdf

### IO_1

The 6 pin IO_1 connector has the following pinouts when used in RX_SERIAL mode.

| Pin | Function   | Notes                           |
| --- | ---------- | ------------------------------- |
| 1   | Ground     |                                 |
| 2   | VCC_IN     | Voltage as-supplied by BEC.     |
| 3   | RX_SERIAL  | Enable `feature RX_SERIAL`      |
| 4   |            |                                 |
| 5   | +V BATTERY | Voltage as-supplied by Battery. |
| 6   | -V BATTERY | Voltage as-supplied by Battery. |

When RX_PPM is used the IO_1 pinout is as follows.

| Pin | Function   | Notes                           |
| --- | ---------- | ------------------------------- |
| 1   | Ground     |                                 |
| 2   | VCC_IN     | Voltage as-supplied by BEC.     |
| 3   | RX_PPM     | Enable `feature RX_PPM`         |
| 4   | TELEMETRY  | Enable `feature TELEMETRY`      |
| 5   | +V BATTERY | Voltage as-supplied by Battery. |
| 6   | -V BATTERY | Voltage as-supplied by Battery. |

### IO_2

When TRANSPONDER is used and the IR solder pads are shorted, the 6 pin IO_2 pinout is as follows.

| Pin | Function | Notes                                        |
| --- | -------- | -------------------------------------------- |
| 1   | IR-      | Short leg of the IR LED                      |
| 2   | IR+      | Long leg of the IR LED                       |
| 3   | CURRENT  | Current Sensor                               |
| 4   | RSSI     | RSSI (PWM or Analog - select by solder pads) |
| 5   | BUZZER+  | 5V Source                                    |
| 6   | BUZZER-  | Buzzer signal                                |

When LEDSTRIP is used and the LED solder pads are shorted, the 6 pin IO_2 pinout is as follows.

| Pin | Function | Notes                                        |
| --- | -------- | -------------------------------------------- |
| 1   |          |                                              |
| 2   | LEDSTRIP | WS2812 Ledstrip data                         |
| 3   | CURRENT  | Current Sensor                               |
| 4   | RSSI     | RSSI (PWM or Analog - select by solder pads) |
| 5   | BUZZER+  | 5V Source                                    |
| 6   | BUZZER-  | Buzzer signal                                |

### UART1

| Pin | Function | Notes |
| --- | -------- | ----- |
| 3   | TXD      |       |
| 4   | RXD      |       |

### UART2/3

| Pin | Function | Notes                       |
| --- | -------- | --------------------------- |
| 1   | Ground   |                             |
| 2   | VCC_IN   | Voltage as-supplied by BEC. |
| 3   | TXD      |                             |
| 4   | RXD      |                             |

### Spektrum Satellite

| Pin | Function | Notes |
| --- | -------- | ----- |
| 3   | 3.3V     |       |
| 2   | Ground   |       |
| 1   | RXD      |       |

### I2C

| Pin | Function | Notes                                        |
| --- | -------- | -------------------------------------------- |
| 1   | Ground   |                                              |
| 2   | 5.0v     | Voltage as-supplied by BEC OR USB, always on |
| 3   | SCL      | 3.3V signals only                            |
| 4   | SDA      | 3.3V signals only                            |

### SWD

The port cannot be used at the same time as UART2.

| Pin | Function | Notes |
| --- | -------- | ----- |
| 1   | Ground   |       |
| 2   | NRST     |       |
| 3   | SWDIO    |       |
| 4   | SWDCLK   |       |

### Hardware

- MCU: STM32F3
- IMU: MPU9250 accelerometer/gyro/compass (SPI)
- IMU Interrupt: Yes
- BARO: BMP280
- VCP: Yes
- Hardware UARTS: 3
- OSD: No
- Blackbox: MicroSD card slot (SD/SDHC, up to 32GB)
- PPM/UART Shared: UART2
- Battery Voltage Sensor: Yes
- Integrated Voltage Regulator: Yes (3.3V 100mA max. / 5.0V is also supplied when powering via USB)
- Brushed Motor Mosfets: No
- Buttons: No

### Features

- PPM only: Yes
- RSSI: Yes (Analog/PWM)
- Buzzer: Yes
- Telemetry port: Yes
- Spektrum Satellite Receivers: Yes (Connector supplied)
- Current Sensor: Yes
- BlHeli passthrough: Yes
- WS2811 Led Strip: Yes\*\*
- Transponder: Yes\*\*

\*\* You can only use Led Strip or Transponder, but not both together.

## Hardware Designs (if available)

## Manufacturers and Distributors

[Seriously Pro](http://seriouslypro.com/)

Available here: [Seriously Pro Shop](http://shop.seriouslypro.com/sp-racing-f3-evo)

## Designers

Hardware design by [Dominic Clifton](https://github.com/hydra).

## Maintainers

[Cleanflight firmware](https://github.com/cleanflight/cleanflight/releases) and [GUI tools](https://chrome.google.com/webstore/detail/cleanflight-configurator/enacoimjcgeinfnnnpajinjgmkahmfgb) are maintained by [Dominic Clifton](https://github.com/hydra).

[Betaflight firmware](https://github.com/betaflight/betaflight/releases) and [GUI tools](https://chrome.google.com/webstore/detail/betaflight-configurator/kdaghagfopacdngbohiknlhcocjccjao) are maintained by [Boris B](https://github.com/borisbstyle).

## Similar Targets

_(add links board descriptions here that are similar in features or function, but have a separate target)_

## Variants

_(add links to boards here that are similar in features or function, but use this target when flashing)_

## FAQ & Known Issues

- Softserial is disabled for this target in bf 3.1.7 but works in nightly build 3.2.0 as of today (2017-05-13).
- DSHot does not work out of the box, due to DMA limitations. The solution to enable DSHOT on this board is to remap motor 4 to motor pin 5 (A06), this can be done through CLI as follows:

`resource MOTOR 5 NONE`

`resource MOTOR 4 A06`

`save`

Note that, if you wish to use SDCARD Blackbox logging with DSHOT, you will have to disable SDCARD DMA. This will negatively impact SDCARD logging rate. As of BF 3.2.0-RC3 there is no other solution. This can be done as follows:

`set sdcard_dma = OFF`

`save`

Source: https://github.com/betaflight/betaflight/issues/2162

## Other Resources

Manual: [SPRacingF3EVO PDF manual](http://seriouslypro.com/files/SPRacingF3EVO-Manual-latest.pdf)

Rcgroups Thread: [SPRacingF3EVO flight controller - CHEAP! F3/SDCard Socket/Race Transponder](http://www.rcgroups.com/forums/showthread.php?t=2641205)

## Image

![](http://shop.seriouslypro.com/pub/media/catalog/product/cache/1/image/e9c3970ab036de70892d86c6d221abfe/i/m/img_9310-web.jpg)
