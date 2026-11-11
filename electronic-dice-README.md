# Electronic Dice

An Arduino-based electronic dice. Press the button, watch a short roll animation, and seven LEDs light up in the pip pattern of a real die face.

<!-- FILL: photo of your finished build. A phone photo on a desk is fine — just make it in focus and well lit.
![Assembled dice](images/build.jpg)
-->

## Why seven LEDs, not six

A die face is a pattern, not a count. The six faces are built from seven pip positions, and the centre pip only appears on odd numbers:

```
 1        2        3        4        5        6
.....    o....    o....    o...o    o...o    o...o
..o..    .....    ..o..    .....    ..o..    o...o
.....    ....o    ....o    o...o    o...o    o...o
```

Lighting *N* LEDs in a row is simpler to code but reads as a bar graph, not a dice roll. Mapping the real pip patterns is the part that makes it look like a die.

## Hardware

| Component | Quantity |
|---|---|
| Arduino Uno | 1 |
| LEDs, 5 mm | 7 |
| Resistors, 220 Ω | 7 |
| Push button, tactile | 1 |
| Breadboard | 1 |
| Jumper wires | — |

No pull-down resistor is needed — the button uses the ATmega's internal pull-up via `INPUT_PULLUP`, which removes a component and eliminates the floating-input problem.

## Wiring

| Arduino pin | Connects to |
|---|---|
| D2 | Top-left pip → 220 Ω → GND |
| D3 | Top-right pip → 220 Ω → GND |
| D4 | Middle-left pip → 220 Ω → GND |
| D5 | Centre pip → 220 Ω → GND |
| D6 | Middle-right pip → 220 Ω → GND |
| D7 | Bottom-left pip → 220 Ω → GND |
| D8 | Bottom-right pip → 220 Ω → GND |
| D12 | Button → other leg to GND |

<!-- FILL: add a wiring diagram if you draw one in Tinkercad or Fritzing
![Circuit diagram](images/schematic.png)
-->

## Design notes

**Button debouncing.** A mechanical switch doesn't close cleanly — the contacts bounce for several milliseconds, and a naive `digitalRead` in the main loop reads that as multiple presses. The sketch ignores state changes within a <!-- FILL: 50 --> ms window after the first edge, so one physical press produces exactly one roll.

**Edge detection, not level detection.** The roll triggers on the transition from released to pressed, rather than on the pin simply being held low. Holding the button down therefore rolls once, not continuously.

**Seeding the generator.** `random()` on Arduino is deterministic — without seeding it produces the same sequence on every power-up. Reading the floating analog pin A0 gives enough electrical noise to vary the seed between boots.

## Running it

1. Wire the circuit as in the table above
2. Open `electronic_dice.ino` in the Arduino IDE
3. **Tools → Board →** Arduino Uno, then select your port
4. Upload

## Repository contents

```
electronic-dice/
├── electronic_dice.ino    # main sketch
├── images/                # build photo and wiring diagram
└── README.md
```

## What I'd improve

- Hardware debouncing with an RC filter, to compare against the software approach
- A 7-segment display or 8×8 matrix variant, to show the number as a digit
- Battery power and a 3D-printed enclosure so it works as a standalone die
<!-- FILL: keep what's true for you, drop the rest -->

## Author

**Kunche Gowtham** — B.Tech Electronics & Communication Engineering, MLR Institute of Technology, Hyderabad

[GitHub](https://github.com/gowtham2214) · [LinkedIn](https://linkedin.com/in/kunche-gowtham-180950275) · gowthamkunche2214@gmail.com
