# PCB - weather station transceiver
This PCB uses an ATmega328P microcontroller to receive data from a BMP280 sensor module and to send it over to the nRF24L01+PA+LNA through SPI on the PCB or to a computer through a serial connection for logging/processing the air temperature and pressure data.

If the data is sent to the nRF24L01+PA+LNA module, another PCB acts as the receiver and transmits the received data to a computer through the serial port.

## ATmega328P - Overview
The ATmega328P runs at 16 MHz, controlled by an external crystal oscillator (Y1).

Its operating voltage is 5V.

## Circuit Design Notes
1. 300 ohm resistors are placed in series on the SPI lines between the nRF24L01+PA+LNA module and the MCU. This is done to ensure that the peripheral SPI device(nRF24L01+PA+LNA in this case) does not interfere with programming the MCU as it is programmed through the J3 connector using SPI-based In-system programming.

2. Two 4.7kΩ I2C pull-up resistors are placed on the SDA and SCL lines.

3. Stitching vias are placed on the board to help mitigate interference while the nRF24L01+PA+LNA module is operational.

4. A diode is placed between the power input of the J3 connector and PCB's power plane for reverse voltage protection.

5. An AMS1117 IC is used to convert the 5V input to 3.3V for the BMP280 and nRF24L01+PA+LNA.

6. A 100µF and a 0.1µF decoupling capacitor are placed on the 3.3V and 5V power rail. The 100µF handles large voltage transients while the 0.1µF filters high-frequency noise.

# Powering and programming the board
1. To power the board, a USB-C connector is placed at the top of the board. 
**NOTE:** This connector cannot be used for programming. It can only power the board

2. To program the microcontroller, the J3 connector is used. It is programmed using SPI-based In-system programming.

## Pinouts

1. J3

| Pin | Function |
|-----|----------|
| 1   | RX       |
| 2   | MISO     |
| 3   | TX       |
| 4   | MOSI     |
| 5   | SCK      |
| 6   | GND      |
| 7   | RESET    |
| 8   | +5V      |
