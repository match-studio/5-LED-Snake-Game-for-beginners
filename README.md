# 5-LED-Snake-Game-for-beginners
## description
A simple snack game that can be made with minimal equipment and is fun and cool. I made this for those who have limited equipment and supplies.
## photos of my robot
![she](images/P_20260221_014742.jpg)
![she](images/P_20260221_014757.jpg)
![she](images/P_20260221_014850.jpg)
## video of working
vid
## requeded components
| name | count | description|
| ----- | ----- | --------- |
## shematic
![she](images/P_20260221_014642.jpg)
> [!NOTE]
> if you using arduino or other board works with 5V pins please change 3V3 to 5v

> [!WARNING]
> im using low led power if you using high power please connect led pins with good resistors

> [!TIP]
> if you using esp32 or other board support PULL-UP built-in pin you can remove
> 1k Ohm resistor and replace `INPUT` with `INPUT_PULLUP`

> [!NOTE]
> if you want to use other pins you can change in code `ledPind = [...]` `rightPin = ...` and `leftPin = ...` with your pins
