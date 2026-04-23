# Vegetal Feelings

<div class="image-block">
  <p></p>
  <figure>
    <img src="readme_screencap_20260423_231237.png" alt="" style="max-width: 90%; max-height: 180mm; width: auto; height: auto;">
    <figcaption></figcaption>
  </figure>
</div>



<div class="image-block">
  <p></p>
  <figure>
    <img src="2026-04-21 Atividade 2_screencap_20260422_174152.png" alt="" style="max-width: 90%; max-height: 180mm; width: auto; height: auto;">
    <figcaption></figcaption>
  </figure>
</div>



Vegetal Feelings
Introduction

In this activity, an initial exploration of Internet of Things (IoT) platforms was carried out, aiming to understand the operation of sensors, actuators, and microcontrollers, as well as their integration into automation systems.

In addition to the theoretical component, the implementation of a practical system based on an ESP32 microcontroller was also initiated, with integration into the Home Assistant platform, allowing remote monitoring and control of devices.

<div class="image-block"> <figure> <img src="2026-04-21 Atividade 2_screencap_20260421_180938.png" style="max-width: 90%; max-height: 180mm;"> <figcaption>Work environment and initial configuration</figcaption> </figure> </div>
First ESPHome configuration

To configure the microcontroller, ESPHome was used, which allows creating firmware in a simplified manner and integrating it directly with Home Assistant.

The process began by running the configuration wizard:

python -m esphome wizard motion-c3.yaml

This wizard allowed defining:

- Device name
- Microcontroller type (ESP32)
- Wi-Fi network
- Encryption key for communication with Home Assistant

<div class="image-block"> <figure> <img src="2026-04-21 Atividade 2_screencap_20260421_230915.png" style="max-width: 90%; max-height: 180mm;"> <figcaption>ESPHome configuration wizard</figcaption> </figure> </div>

After configuration, the firmware was compiled and sent to the device using the following command:

python -m esphome run motion-c3.yaml

This process includes:

- Firmware compilation
- Upload via USB or OTA (Over-The-Air)
- Real-time monitoring through logs

Xiao Grove

To facilitate the connection of sensors and actuators, the Grove Expansion Board module was used for the XIAO ESP32-S3 microcontroller.

This module allows a simpler and more organized connection, providing ports already prepared for:

- analog signals
- digital signals
- I2C communication
- UART communication

<div class="image-block"> <figure> <img src="2026-04-21 Atividade 2_screencap_20260421_180902.png" style="max-width: 90%; max-height: 180mm;"> <figcaption>XIAO ESP32-S3 board with Grove Expansion Board</figcaption> </figure> </div>
Port Mapping

The following table shows the correspondence between the Grove breakout ports and the XIAO ESP32-S3 GPIOs, which is essential for the correct connection of components.

| Port on breakout | Function on breakout        | GPIO on XIAO ESP32-S3 | Observation                    |
| ----------------- | ------------------------- | --------------------: | ----------------------------- |
| A0 / D0           | analog or digital      |                 GPIO1 | good for analog sensor     |
| A1 / D1           | analog or digital      |                 GPIO2 | already used for the light relay |
| A2 / D2           | analog or digital      |                 GPIO3 | free                         |
| I2C               | SDA/SCL                   |         GPIO4 / GPIO5 | I2C bus                |
| A5 / D5           | analog or digital      |                 GPIO6 | free                         |
| A7 / D7           | analog/digital or UART |                GPIO44 | caution with serial use          |
| A8 / D8           | analog or digital      |                 GPIO7 | free                         |
| A9 / D9           | analog or digital      |                 GPIO8 | free                         |



| Pin XIAO  |   GPIO |
| --------- | -----: |
| D0 / A0   |  GPIO1 |
| D1 / A1   |  GPIO2 |
| D2 / A2   |  GPIO3 |
| D3 / A3   |  GPIO4 |
| D4 / A4   |  GPIO5 |
| D5 / A5   |  GPIO6 |
| D6 / A6   | GPIO43 |
| D7 / A7   | GPIO44 |
| D8 / A8   |  GPIO7 |
| D9 / A9   |  GPIO8 |
| D10 / A10 |  GPIO9 |





### IoT Simulation Platform
Available components

The simulation platform used provides a wide range of typical IoT system components, allowing the creation of virtual circuits interactively.

Among the main components available are:

- Microcontrollers (Arduino, ESP32)
- Sensors (temperature, luminosity, distance, motion)
- Actuators (LEDs, relays, motors)
- Auxiliary components (resistors, breadboard, wiring)

These elements allow simulating real scenarios of data acquisition and device control.

### Circuit construction

Circuits are built through a graphical interface, where components can be selected, positioned, and interconnected by virtual connections (wires).

The connection between components is done intuitively, respecting the basic principles of electronics, such as:

- power supply (VCC and GND)
- signal connections
- use of resistors when necessary

This approach allows validating the circuit's operation before physical implementation.

### Programming area

Programming is done directly on the platform, through an integrated code editor.

In most cases, a C/C++ based language (Arduino) is used, allowing:

- sensor reading
- actuator control
- implementation of conditional logic

The code can be changed in real time, facilitating experimentation and learning.

### Results visualization

Results are visualized in real time during simulation, allowing observation of the system's behavior.

Examples of visualization include:

- LEDs turning on and off
- dynamically updated sensor values
- activation of motors or relays

This functionality allows validating the system's behavior without the need for physical hardware.

## Practical Implementation

## Hardware used

For the practical implementation of the IoT system, the following components were used:

- XIAO ESP32-S3 Sense  
- Grove Expansion Board  
- Grove Relay  
- Temperature sensor (Grove)  
- Luminosity sensor (Grove)  
- Soil moisture sensor  

---

## Integration with Home Assistant

The system integration was carried out using ESPHome, allowing direct communication between the ESP32 microcontroller and Home Assistant.

This approach enables:
- real-time sensor monitoring  
- remote device control  
- creation of automations  

ESPHome simplifies firmware configuration, allowing sensors and actuators to be defined through YAML files.

---

## Actuator control

Relay control was implemented, used to turn external devices on and off, namely the lighting system.

Control is performed through Home Assistant, allowing:
- manual activation  
- future automation based on environmental conditions  

---

## Sensor reading

Sensors were implemented to collect environmental data, allowing monitoring of greenhouse conditions.

The main collected data includes:
- temperature  
- luminosity  

The values are sent in real time to Home Assistant, where they can be viewed and used in automations.

## Power Management

As the Xiao works with 3,3V and we need, do power the Leds with 12V and the water motor wiht 5V, we used relays, to cupply the needed current\voltage.

<div class="image-block">
  <p></p>
  <figure>
    <img src="readme_screencap_20260423_231526.png" alt="" style="max-width: 90%; max-height: 180mm; width: auto; height: auto;">
    <figcaption></figcaption>
  </figure>
</div>

## Future development

The system will be evolved into a smart mini-greenhouse, called "Vegetal Feelings", with the following features:

- Automatic lighting control  
- Automatic irrigation system  
- Soil moisture monitoring  
- Ventilation control  
- Image capture via camera  
- Automatic email sending of images  

---

## OTA Updates (Over-The-Air)

ESPHome allows remote firmware update via Wi-Fi network, without the need for physical connection to the device.

This feature facilitates:
- error correction  
- addition of new features  
- system maintenance  

<div class="image-block">
  <figure>
    <img src="2026-04-21 Atividade 2_screencap_20260421_182820.png" style="max-width: 90%; max-height: 180mm;">
    <figcaption>OTA update through ESPHome</figcaption>
  </figure>
</div>


## The code

```
esphome:
  name: estufa-xiao
  platformio_options:
    build_flags:
      - -DIDF_GIT_VER_OVERRIDE="v5.5.4"

esp32:
  board: esp32-s3-devkitc-1
  framework:
    type: esp-idf

logger:

api:
  encryption:
    key: "wYmECWZutp4UXSJTcX7vwX1WCa5WI7W/I3jOqVukzoE="

ota:
  - platform: esphome

wifi:
  ssid: "ssid"
  password: "password*"

  ap:
    ssid: "Fallback Hotspot"
    password: "hbLR4MnANkQo"

switch:
  - platform: gpio
    id: relay_luz
    name: "Relay Teste"
    pin: GPIO2

sensor:
  - platform: adc
    pin: GPIO1
    name: "Temperatura NTC"
    update_interval: 5s
    attenuation: 12db
    filters:
      - lambda: |-
          float voltage = x;
          if (voltage <= 0.0 || voltage >= 3.3) return NAN;
          float resistance = (3.3 - voltage) * 10000.0 / voltage;
          float temperature = 1.0 / (log(resistance / 10000.0) / 3975.0 + 1.0 / 298.15) - 273.15;
          return temperature;
    unit_of_measurement: "°C"
    accuracy_decimals: 1

  - platform: adc
    id: sensor_luz
    pin: GPIO3
    name: "Luminosidade"
    update_interval: 5s
    attenuation: 12db
    unit_of_measurement: "V"
    accuracy_decimals: 2

interval:
  - interval: 5s
    then:
      - if:
          condition:
            lambda: 'return id(sensor_luz).state < 0.3;'
          then:
            - switch.turn_on: relay_luz
          else:
            - switch.turn_off: relay_luz

captive_portal:
```


---

## Conclusion

The activity allowed understanding the fundamental principles of the Internet of Things, namely the integration between sensors, actuators, and management platforms.

It was possible to develop a functional system based on ESP32, with remote monitoring and control capability through Home Assistant.

The project has expansion potential, and can evolve into a complete small-scale agricultural automation solution.


## Reference:
### initialize Git in the framework directory:
cd C:\Users\CarlosManuelOliveira\.platformio\packages\framework-espidf
git init
git add .
git commit -m "Initial commit"

python -m esphome run estufa.yaml --device 10.0.10.159
