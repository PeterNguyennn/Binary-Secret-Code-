# Binary Secret Message Machine

An 8-bit LED display driven by a DIP switch. Encode any ASCII character in binary, flip the switches, press the button to reveal — no microcontroller, no code.

🔗 [View & Simulate on TinkerCAD](https://www.tinkercad.com/things/l2ELaaUQt4R-binary-secret-code) · 🎥 [Demo Video](https://drive.google.com/file/d/1G-LQ21Wpil4ovP0nIzB0rD1e0v_hsWUa/view?usp=drive_link)

---

## How It Works

Each of the 8 DIP switch positions directly controls one LED — switch ON = LED on = bit `1`, switch OFF = LED off = bit `0`. The 8-bit pattern maps directly to an ASCII character code, letting you encode any printable character. A momentary push-button sits in series with the positive rail, acting as a power gate — LEDs only illuminate while the button is held, so you can "reveal" a character on demand.

| Bit | SW8 | SW7 | SW6 | SW5 | SW4 | SW3 | SW2 | SW1 |
|---|---|---|---|---|---|---|---|---|
| Position | MSB | — | — | — | — | — | — | LSB |

> Example: lowercase `a` = decimal 97 = binary `01100001`

---

## Specs

| Property | Value |
|---|---|
| Data width | 8 bits (1 byte) |
| Encoding | ASCII |
| Bit order | MSB left (SW8) → LSB right (SW1) |
| Switch type | DIP switch, 8-position |
| Output | 8× LEDs |
| Power gate | Momentary push-button in series with VCC |
| Supply | 9V battery |

---

## Components

- 8-position DIP switch
- LEDs ×8 (matching colors recommended)
- Resistors: 220Ω ×8 (current limiters)
- Push-button (momentary SPST)
- Full-size breadboard, jumper wires, 9V battery

---

## Lessons Learned

- Bit ordering matters — getting SW1 = LSB vs MSB confused makes every decoded character wrong; label the breadboard
- Grouping LEDs into two nibbles (4 + 4) with a visible gap makes the binary pattern much easier to read at a glance
- The push-button as a power gate is a simple but effective UX touch — makes the "send" action feel intentional
- Color-coding jumper wires by signal type saved a lot of debugging time with 8 parallel connections

---

## Future Improvements

- Add a second identical circuit for full two-way communication
- Add an Arduino to auto-decode the DIP switch value and display the ASCII character on an OLED
- Add a shift register (74HC595) to drive 8 LEDs from 3 control lines — good intro to serial communication
- Design a PCB with labeled bit positions for a cleaner permanent build
