# STM32-Button-Controlled-LED
A simple STM32 project demonstrating how to control an LED using a push button with GPIO input and output.
# STM32 Button Controlled LED

## About this project
This is a very simple STM32 project where I used a push button to control an LED.

The idea is straightforward:
- When the button is pressed → LED turns ON  
- When the button is released → LED turns OFF  

This helped me understand how GPIO input and output work together in STM32.

---

## What it does
- Reads input from onboard push button (PC13)  
- Controls onboard LED (PA5)  
- Works continuously inside the main loop  

---

## How it works (simple)
- STM32 reads the button state using `HAL_GPIO_ReadPin()`  
- If button is pressed → LED is turned ON  
- If button is not pressed → LED is turned OFF  

So basically:

**Button → Read Input → Control LED**

---

## Logic used
```c
if (HAL_GPIO_ReadPin(GPIOC, GPIO_PIN_13) == GPIO_PIN_SET)
{
    HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);   // LED ON
}
else
{
    HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_SET);     // LED OFF
}
```

## Important Note 

On most STM32 boards (like Nucleo):

Button (PC13) is active LOW
LED (PA5) is active HIGH or LOW depending on board

In your case:

GPIO_PIN_SET → Button NOT pressed
GPIO_PIN_RESET → Button pressed

That’s why logic may feel reversed.

## Pin Configuration
## Button
Pin → PC13
Mode → Input
LED
Pin → PA5
Mode → Output


## Final note

This was one of my first STM32 experiments to understand how hardware interacts with code.

Simple project, but very important foundation for embedded systems.
