![Electronic Dice](https://raw.githubusercontent.com/kuncheGowtham/Electric-Dice-Auduino/main/assets/electronic-dice-banner.svg)

# Electronic Dice

An Arduino-based electronic dice that simulates a traditional six-sided die. Press the button to generate a random number from 1 to 6, then display the result through LEDs arranged in the familiar pip pattern.

## How it works

The project uses seven LED positions to represent the pip layout of a die face. The centre LED appears only on odd-numbered results, while the other positions form the corner and side pips needed for faces 1 through 6.

A button press triggers a roll. The Arduino generates a random value between 1 and 6 and switches the corresponding LEDs on. The result remains visible until the next roll.

## Hardware

| Component | Quantity |
| --- | ---: |
| Arduino Uno | 1 |
| 5 mm LEDs | 7 |
| 220 ohm resistors | 7 |
| Tactile push button | 1 |
| Breadboard | 1 |
| Jumper wires | As required |

## Wiring

| Arduino pin | Connection |
| --- | --- |
| D2 | Top-left pip through a 220 ohm resistor to GND |
| D3 | Top-right pip through a 220 ohm resistor to GND |
| D4 | Middle-left pip through a 220 ohm resistor to GND |
| D5 | Centre pip through a 220 ohm resistor to GND |
| D6 | Middle-right pip through a 220 ohm resistor to GND |
| D7 | Bottom-left pip through a 220 ohm resistor to GND |
| D8 | Bottom-right pip through a 220 ohm resistor to GND |
| D12 | Push button, with the other leg connected to GND |

The button uses the Arduino's internal pull-up configuration, so a separate pull-down resistor is not required.

## Software behaviour

- Detects a button press and triggers one roll.
- Generates a value from 1 to 6.
- Maps each value to the corresponding die-face LED pattern.
- Uses button debouncing so one physical press produces one roll.
- Uses edge detection so holding the button does not continuously roll the die.
- Seeds the random generator from noise read through the floating analog input A0.

## Running the project

1. Assemble the circuit using the wiring table above.
2. Open `electronic_dice.ino` in the Arduino IDE.
3. Select **Arduino Uno** under **Tools → Board**.
4. Select the connected port and upload the sketch.
5. Press the button to roll the electronic die.

## Testing checklist

After assembling the prototype, verify and record:

- Each face displays the correct pip pattern across repeated rolls.
- One button press produces exactly one roll after debouncing.
- Holding the button does not trigger repeated rolls.
- The outcomes show a reasonable distribution across approximately 50 rolls.

These checks should be completed on the physical prototype before reporting measured results.

## Future improvements

- Compare software debouncing with hardware debouncing using an RC filter.
- Add a 7-segment display or 8×8 LED matrix variant.
- Add battery power and a 3D-printed enclosure for standalone use.

## Contribution

Sole author. Designed the circuit, wrote the firmware, and built and tested the prototype.

## Author

**Kunche Gowtham** — B.Tech Electronics & Communication Engineering, MLR Institute of Technology, Hyderabad

[GitHub](https://github.com/kuncheGowtham) · [LinkedIn](https://linkedin.com/in/kunche-gowtham-180950275) · gowthamkunche2214@gmail.com
