# 5-LED-Snake-Game-for-beginners

## Description
A simple snake game that can be made with minimal equipment. It's fun and cool! I made this for those who have limited equipment and supplies.

## Photos of my robot
![snake game 1](images/P_20260221_014742.jpg)
![snake game 2](images/P_20260221_014757.jpg)
![snake game 3](images/P_20260221_014850.jpg)

## Video of working
*[Video coming soon...]*

## Required Components
| Name | Count | Description |
|------|-------|-------------|
| LED | 5 | Any color you like |
| 10K Ohm resistor | 2 | You can use `INPUT_PULLUP` in code instead |
| Jumper wires | 9+ | Male to male and male to female |
| Breadboard | 2-3 | Mini, half or full size |
| Buttons | 2 | For left and right movement |
| ESP32 or Arduino | 1 | Any board with enough pins |

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
