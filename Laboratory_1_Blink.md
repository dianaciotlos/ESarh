# Laboratory 1 Report: LED Button Control

**Student:** POVAR LUMINITA  
**Date:** April 2, 2026  
**Subject:** Embedded Systems - LED Blinking with Button Input

---

## Objective

The goal of this laboratory exercise was to implement a simple embedded system application where an LED blinks when a button is pressed on the microcontroller board.

## Implementation

Using STM32CubeMX, I created a new project and configured GPIO pins to control an LED and read input from a button. The microcontroller is an STM32 device with the following pin configuration:

- **Button (Input):** GPIO Pin 13 on Port C
- **LED (Output):** GPIO Pin 5 on Port A

## How It Works

The program runs an infinite loop that continuously monitors the button state. The logic is straightforward:

1. **When the button is pressed:** The LED toggles (turns on if off, turns off if on) with a 200-millisecond delay to prevent bouncing effects.
2. **When the button is released:** The LED turns off immediately.

```c
if (HAL_GPIO_ReadPin(GPIOC, GPIO_PIN_13) == GPIO_PIN_RESET)
{
    HAL_GPIO_TogglePin(GPIOA, GPIO_PIN_5);
    HAL_Delay(200);
}
else
{
    HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);
}
```

## Technical Details

- The microcontroller uses the STM32 Hardware Abstraction Layer (HAL) functions for GPIO control
- The 200ms delay helps stabilize button readings and prevents rapid toggling
- The system clock is configured to use the internal HSI oscillator
- UART communication is initialized but not actively used in this exercise

## Conclusion

This exercise successfully demonstrates basic GPIO operations including button input detection and LED output control. The implementation provides a foundation for understanding microcontroller I/O operations and real-time embedded system programming.

