# 5-LED-Snake-Game-for-beginners

## Description
A simple snake game that can be made with minimal equipment. It's fun and cool! I made this for those who have limited equipment and supplies.

## Photos of my robot
![snake game 1](images/P_20260221_014742.jpg)
![snake game 2](images/P_20260221_014757.jpg)
![snake game 3](images/P_20260221_014850.jpg)

## Video of working
*[Video coming soon...]*

## Connection
| from | to | with |
|------|----|------|
| GND | LED GND pins | none |
| 3V3 (or 5V) | button one pin | none |
| GND | button two pin | 10K Ohm resistor |
| GPIO 4 | button one other pin | none |
| GPIO 16 | button two other pin | none |
| GPIO 13 | LED 1 | resistor (optional) |
| GPIO 12 | LED 2 | resistor (optional) |
| GPIO 14 | LED 3 | resistor (optional) |
| GPIO 27 | LED 4 | resistor (optional) |
| GPIO 26 | LED 5 | resistor (optional) |

## Schematic
![schematic](images/P_20260221_014642.jpg)

> [!NOTE]
> If you are using Arduino or other boards that work with 5V pins, please change 3.3V to 5V.

> [!WARNING]
> I am using low-power LEDs. If you are using high-power LEDs, please connect them with appropriate resistors.

> [!TIP]
> If you are using ESP32 or other boards that support built-in pull-up, you can remove the 10K Ohm resistors and replace `INPUT` with `INPUT_PULLUP` in the code.

> [!NOTE]
> If you want to use other pins, you can change them in the code:  
> `ledPins[5] = {13, 12, 14, 27, 26};`  
> `rightPin = 4;`  
> `leftPin = 16;`

## main code
```cpp
```
## 🤝 Contributing

You can help make this project better. Here are some ways to contribute:

### 📝 Improve the documentation
Fix spelling mistakes. Make instructions clearer. Translate to your language. Add more details about the circuit.

### 🔧 Improve the hardware
Make a better schematic. Design a PCB. Find cheaper components. Suggest better wiring.

### 💻 Improve the code
Add new features. Make the code faster. Add comments. Fix bugs. Make it work with more boards.

### 📸 Share your build
Take photos of your version. Record a video. Send them to me. Show how you built it differently.

### 🐛 Report problems
Tell me if something doesn't work. Let me know if instructions are confusing. Report bugs in the code.

### 💡 Suggest new ideas
Tell me what features you want. Suggest improvements. Ask questions.

#### How to send your changes
Fork this repository. Make your changes. Send a Pull Request. I will review and add it.

Or message me directly with your ideas.

You don't need to be an expert. Even testing and reporting helps.

## donate
If you like this project and want to support me, I'm 13 years old and I make projects with limited equipment. Even a small donation helps me buy more parts.
Thank you.
my bitcoin public key: `0367fe4e52cec4fef59687718bbae91b4b4a23ac4871a362f1ed2dffd288890cad`
