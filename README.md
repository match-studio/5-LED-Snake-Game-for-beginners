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
// Pin definitions for 5 LEDs
const int ledPins[5] = {13, 12, 14, 27, 26};

// Pin definitions for buttons
const int rightPin = 4;   // Right button pin
const int leftPin = 16;   // Left button pin

// Game variables
int playerPos = 2;        // Player starts at middle LED (index 2)
int foodPos = 0;          // Food starts at position 0

// Button state variables (for detecting button presses)
bool lastRight = HIGH;    // Previous state of right button
bool lastLeft = HIGH;     // Previous state of left button

// Food blinking control
unsigned long lastBlink = 0;  // Stores last time food blinked
bool foodState = true;        // Current state of food LED (ON/OFF)

// Setup function runs once when device starts
void setup() {
  // Set all LED pins as OUTPUT
  for(int i = 0; i < 5; i++) {
    pinMode(ledPins[i], OUTPUT);
  }
  
  // Set button pins as INPUT
  // Note: I'm using INPUT here instead of INPUT_PULLUP
  // If you want to use internal pull-up resistors, change to INPUT_PULLUP
  // With INPUT, you need external pull-up or pull-down resistors
  pinMode(rightPin, INPUT);
  pinMode(leftPin, INPUT);
  
  // Make sure food doesn't start at same position as player
  if(foodPos == playerPos) {
    foodPos = (playerPos + 2) % 5;  // Move food 2 positions ahead
  }
  
  // Turn on LEDs based on initial positions
  updateLEDs();
}

// Main loop runs continuously
void loop() {
  // ===== Food blinking control =====
  // Check if 300ms has passed since last blink
  if(millis() - lastBlink > 300) {
    foodState = !foodState;        // Toggle food state (ON/OFF)
    lastBlink = millis();          // Update last blink time
    updateLEDs();                  // Update LEDs with new state
  }
  
  // ===== Right button check =====
  // Check if right button is pressed (LOW) and wasn't pressed before
  if(digitalRead(rightPin) == LOW && lastRight == HIGH) {
    // Prevent player from moving beyond last LED (position 4)
    if(playerPos < 4) {  
      playerPos++;                 // Move player right
      checkFood();                 // Check if player reached food
      updateLEDs();                // Update LED display
    }
    delay(200);                    // Debounce delay (prevents multiple readings)
  }
  
  // ===== Left button check =====
  // Check if left button is pressed (LOW) and wasn't pressed before
  if(digitalRead(leftPin) == LOW && lastLeft == HIGH) {
    // Prevent player from moving beyond first LED (position 0)
    if(playerPos > 0) {  
      playerPos--;                 // Move player left
      checkFood();                 // Check if player reached food
      updateLEDs();                // Update LED display
    }
    delay(200);                    // Debounce delay
  }
  
  // Save current button states for next loop iteration
  lastRight = digitalRead(rightPin);
  lastLeft = digitalRead(leftPin);
  
  delay(10);                       // Small delay to reduce CPU usage
}

// Function to check if player reached the food
void checkFood() {
  // If player position matches food position
  if(playerPos == foodPos) {
    celebrate();                   // Play celebration animation
    
    // Generate new random food position
    int newFood;
    do {
      newFood = random(0, 5);      // Random position between 0-4
    } while(newFood == playerPos); // Make sure it's not where player is
    
    foodPos = newFood;              // Set new food position
    
    updateLEDs();                   // Update display
  }
}

// Celebration animation when food is eaten
void celebrate() {
  // Blink all LEDs 3 times
  for(int j = 0; j < 3; j++) {
    // Turn all LEDs ON
    for(int i = 0; i < 5; i++) {
      digitalWrite(ledPins[i], HIGH);
    }
    delay(150);                     // Wait 150ms
    
    // Turn all LEDs OFF
    for(int i = 0; i < 5; i++) {
      digitalWrite(ledPins[i], LOW);
    }
    delay(150);                     // Wait 150ms
  }
}

// Function to update all LEDs based on current game state
void updateLEDs() {
  // Turn all LEDs OFF first
  for(int i = 0; i < 5; i++) {
    digitalWrite(ledPins[i], LOW);
  }
  
  // Turn ON the player LED (always ON)
  digitalWrite(ledPins[playerPos], HIGH);
  
  // Turn ON the food LED only if foodState is true (blinking effect)
  if(foodState) {
    digitalWrite(ledPins[foodPos], HIGH);
  }
}
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
