# 8-Channel PWM Receiver with nRF24L01

This repository contains an Arduino-based 8-channel PWM receiver code using the nRF24L01 transceiver. The receiver maps wireless signals from a transmitter to PWM signals for controlling up to 8 servos, with a built-in failsafe.

## Features

- **Eight Servo Channels**: Controls 8 individual servos with mapped PWM signals.
- **nRF24L01 Wireless Communication**: Receives data from a paired transmitter.
- **Failsafe Mode**: Resets servo positions to neutral if the signal is lost for more than 1 second.
- **LED Indicator**: Displays data reception status.

## Hardware Requirements

- **Arduino Uno or similar**
- **nRF24L01 Module**
- **8 Servos**
- **LED** (optional, for indication)

## Circuit Connections

| Arduino Pin | Component             |
|-------------|------------------------|
| 9           | nRF24L01 CE           |
| 10          | nRF24L01 CSN          |
| 2-7, A0, A1 | Servo PWM Signals     |
| 8           | LED (optional)        |

### Servo Pin Mappings

| Servo Channel | Arduino Pin |
|---------------|-------------|
| Channel 1     | 2           |
| Channel 2     | 3           |
| Channel 3     | 4           |
| Channel 4     | 5           |
| Channel 5     | 6           |
| Channel 6     | 7           |
| Channel 7     | A0          |
| Channel 8     | A1          |

## Installation

1. **Install Libraries**: Ensure these libraries are in your Arduino IDE:
   - `SPI`
   - `nRF24L01`
   - `RF24`
   - `Servo`

2. **Upload Code**: Open the code in the Arduino IDE, compile, and upload it to your Arduino board.

3. **Connect Components**: Assemble according to the Circuit Connections table above.

4. **Power On**: Power on the receiver and transmitter. Observe LED status for connection (optional).

## Code Overview

- **ResetData()**: Resets `data` struct to default values.
- **recvData()**: Listens for data packets from the transmitter. Sets `lastRecvTime` and turns on LED when data is received.
- **loop()**: Monitors connection status and updates servo PWM signals based on received data. Implements failsafe if needed.

### Debugging

Uncomment `Serial.print` lines in `loop()` for debugging. This will output PWM widths for each channel in the Serial Monitor.

## License

MIT License

---

Author: Ayush Sharma
