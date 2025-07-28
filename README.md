## ARM CORTEX M4 OPERATIONAL MODES DEMO


# ✨ Overview
This project demonstrates context switching between Thread Mode (normal code execution) and Handler Mode (interrupt service routine execution) on an STM32 microcontroller. It uses software-triggered interrupts via the NVIC STIR register to simulate hardware interrupts, providing a clear example of how Cortex-M cores handle interrupts.

# 🔧 Key Features
- Implements UART logging to visualize mode changes.

- Shows manual interrupt triggering using the NVIC STIR register (0xE000EF00).

- Explains Thread Mode → Handler Mode → Thread Mode transitions.

- Uses RTC Wake-Up interrupt handler (RTC_WKUP_IRQHandler) as the ISR.

# 🛠 Hardware & Tools
- Target MCU: STM32 Cortex-M4 (e.g., STM32F4xx)

- IDE: STM32CubeIDE (or STM32CubeMX + GCC toolchain)

- Debug/Flash: ST-Link/V2



# 📂 Project Structure
```
STM32-Interrupt-Demo/
│
├── Core/
│   ├── Inc/
│   │   └── main.h
│   └── Src/
│       └── main.c        # Core application logic
│
├── Drivers/              # HAL and CMSIS drivers
│
└── README.md             # This file

```
# 🚀 How It Works
- Initialization Phase

- System clock and peripherals (GPIO, UART) are configured.

- UART is used to print logs at 115200 baud.

- Thread Mode Execution

- Handler mode execution

# 🖥 Expected Serial Output
```
Instructions being executed in the THREAD MODE during main() execution.
Still in thread mode during trigger_interrupt() function call.
In HANDLER MODE now when RTC_WKUP_IRQHandler called.
Again returned to THREAD MODE after handler execution.

```
# 🧠 Understanding NVIC Registers
1. ISER (Interrupt Set-Enable Register)
Address: 0xE000E100
Enables specific interrupt lines.

2. STIR (Software Trigger Interrupt Register)
Address: 0xE000EF00
Writing interrupt number (0–239) here triggers the ISR manually.
