---
title: 'Quadcopter Programming Part 2: Using the CMSIS Library and First Takeoff'
date: 2019-12-01T09:29:00+01:00
draft: false
---

Quadcopter Programming Part 2: Using the CMSIS Library and First Takeoff
========================================================================

2019-11-30 - Tim Schumacher

In the [last post](https://timakro.de/blog/bare-metal-stm32-programming/) of the series I explained how to get started programming an STM32 microcontroller without any library dependencies. Today we will improve the LED blinking example from last post with the [CMSIS](https://developer.arm.com/embedded/cmsis) library, making it more readable and adding precise timings. Finally we will drive the rotors of the quadcopter for a somewhat assisted takeoff.

CMSIS setup [#](https://timakro.de/blog/quadcopter-programming-part-2/#cmsis-setup)
-----------------------------------------------------------------------------------

The Cortex Microcontroller Software Interface Standard (CMSIS) library is part of the Standard Peripheral Library developed by STMicroelectronics. You can download the version for your microcontroller from [their website](https://www.st.com/en/embedded-software/stm32-standard-peripheral-libraries.html). For the processor on my quadcopter I needed the STM32F10x version of the Standard Peripheral Library, the newest version at the time of writing was 3.5.0.

After unzipping the archive you will find the relevant library files under `Libraries/CMSIS`. This is a collection of files for different processors and compilers. We will just pick the ones we need and copy them into a `CMSIS` directory alongside our source files.

Before we start, recall the final code from last post:

```
#include   void main () { // Enable I/O port A clock *(volatile uint32_t *)0x40021018 = 0x00000004; // Configure pin 11 as push-pull output *(volatile uint32_t *)0x40010804 &= 0xFFFF0FFF; *(volatile uint32_t *)0x40010804 |= 0x00002000; while (1) { *(volatile uint32_t *)0x40010810 = (1<<11); // Set pin 11 for (int i = 0; i < 1000000; i++); *(volatile uint32_t *)0x40010814 = (1<<11); // Unset pin 11 for (int i = 0; i < 1000000; i++); } }
```

### Library files [#](https://timakro.de/blog/quadcopter-programming-part-2/#library-files)

These hexadecimal memory addresses convey no meaning and are prone to errors. The `stm32f10x.h` header file defines pointers to those registers with identifiers from the reference manual. That will make the code much more readable.

Copy `Libraries/CMSIS/CM3/DeviceSupport/ST/STM32F10x/stm32f10x.h` or the equivalent for your processor to your `CMSIS` directory. For it to compile you have to specify the processor type either by setting a compiler flag as shown later or by uncommenting one of the preprocessor definitions in the file:

```
/* Uncomment the line below according to the target STM32 device used in your application */ #if !defined (STM32F10X_LD) && !defined (STM32F10X_LD_VL) && !defined (STM32F10X_MD) && !defined (STM32F10X_MD_VL) && !defined (STM32F10X_HD) && !defined (STM32F10X_HD_VL) && !defined (STM32F10X_XL) && !defined (STM32F10X_CL)  /* #define STM32F10X_LD */ /*!< STM32F10X_LD: STM32 Low density devices */ /* #define STM32F10X_LD_VL */ /*!< STM32F10X_LD_VL: STM32 Low density Value Line devices */ /* #define STM32F10X_MD */ /*!< STM32F10X_MD: STM32 Medium density devices */ /* #define STM32F10X_MD_VL */ /*!< STM32F10X_MD_VL: STM32 Medium density Value Line devices */ /* #define STM32F10X_HD */ /*!< STM32F10X_HD: STM32 High density devices */ /* #define STM32F10X_HD_VL */ /*!< STM32F10X_HD_VL: STM32 High density value line devices */ /* #define STM32F10X_XL */ /*!< STM32F10X_XL: STM32 XL-density devices */ /* #define STM32F10X_CL */ /*!< STM32F10X_CL: STM32 Connectivity line devices */ #endif
```

Also copy the following files to your new `CMSIS` folder. They are required by the `stm32f10x.h` header file and provide functions to operate some of the peripherals such as the timer we will use later:

*   `Libraries/CMSIS/CM3/CoreSupport/core_cm3.h`
*   `Libraries/CMSIS/CM3/CoreSupport/core_cm3.c`
*   `Libraries/CMSIS/CM3/DeviceSupport/ST/STM32F10x/system_stm32f10x.h`
*   `Libraries/CMSIS/CM3/DeviceSupport/ST/STM32F10x/system_stm32f10x.c`

With these files in the `CMSIS` directory you can already compile the two objects. Instead of uncommenting a line in `stm32f10x.h` I passed the compiler flag `-D STM32F10X_MD` for my medium density chip.

```
arm-none-eabi-gcc -mcpu=cortex-m3 -mthumb -D STM32F10X_MD -c \ CMSIS/core_cm3.c CMSIS/system_stm32f10x.c
```

### Startup and linker script [#](https://timakro.de/blog/quadcopter-programming-part-2/#startup-and-linker-script)

Remember the startup assembly code and the linker script we wrote last post. The startup code was required for pointing the processor to the C entry point and the linker script was telling the linker about the memory layout of the chip. Trying to link the startup and linker script from last post with the two objects we just compiled will throw errors. CMSIS provides its own startup and linker scripts with additional pointer definitions for some memory locations.

I used the assembly startup script at `CM3/DeviceSupport/ST/STM32F10x/startup/gcc_ride7/startup_stm32f10x_md.s` which was compatible with gcc and needed no modifications. Here `md` stands for medium density again.

The linker script is actually not part of CMSIS, but there are many scripts around that come with different IDEs and some are included in the Standard Peripheral Library distribution. I found a few linker scripts from [TrueSTUDIO](https://atollic.com/truestudio/) under the archive root at `Project/STM32F10x_StdPeriph_Template/TrueSTUDIO`. None of them were for my specific chip so I compared them with [diffuse](http://diffuse.sourceforge.net/).

[![Linker script comparison in diffuse](https://timakro.de/generated/quadcopter-programming-part-2/linker-script-diffuse-720-abc75c.png)](https://timakro.de/public/quadcopter-programming-part-2/linker-script-diffuse.png)

The middle file `STM3210B-EVAL/stm32_flash.ld` seemed to be the best match for my processor. I adjusted the flash size from 128 KiB to 64 KiB.

```
MEMORY { FLASH (rx) : ORIGIN = 0x08000000, LENGTH = 64K RAM (xrw) : ORIGIN = 0x20000000, LENGTH = 20K MEMORY_B1 (rx) : ORIGIN = 0x60000000, LENGTH = 0K }
```

And I removed a few lines which are redundant and cause linking errors when using the file outside of TrueSTUDIO:

```
/* Remove the following lines */ /DISCARD/ : { libc.a ( * ) libm.a ( * ) libgcc.a ( * ) }
```

That’s the complete CMSIS installation. Make sure your `CMSIS` directory contains all of the following files or the respective files for your processor:

```
CMSIS ├── stm32f10x.h ├── core_cm3.h ├── core_cm3.c ├── system_stm32f10x.h ├── system_stm32f10x.c ├── startup_stm32f10x_md.s └── stm32_flash.ld
```

Register pointers [#](https://timakro.de/blog/quadcopter-programming-part-2/#register-pointers)
-----------------------------------------------------------------------------------------------

So let’s start by revising the blink LED script from above to make use of the CMSIS library. We begin with the hardcoded memory addresses. Last post we looked up the register memory addresses in the reference manual. But you can also find identifiers for each register there. Let’s revisit the _`APB2` peripheral clock enable register_, it’s the first register we access in our code to be able to write to the `GPIOA` registers later:

```
*(volatile uint32_t *)0x40021018 = 0x00000004;
```

The reference manual tells us the identifier of this register in the heading.

> **APB2 peripheral clock enable register (RCC\_APB2ENR)**

CMSIS also defines variables for the different values registers can take. From the reference manual:

> Bit 2 **IOPAEN:** IO port A clock enable  
> Set and cleared by software.  
> 0: IO port A clock disabled  
> 1: IO port A clock enabled

We can rewrite the line like this:

```
RCC->APB2ENR = RCC_APB2ENR_IOPAEN;
```

Much better, right? This is the code with all memory addresses replaced. Don’t forget to `#include "stm32f10x.h"`.

```
#include "stm32f10x.h"  void main (void) { // Enable I/O port A clock RCC->APB2ENR |= RCC_APB2ENR_IOPAEN; // Configure pin 11 as push-pull output GPIOA->CRH &= ~(GPIO_CRH_MODE11 | GPIO_CRH_CNF11); GPIOA->CRH |= GPIO_CRH_MODE11; while (1) { GPIOA->BSRR = (1<<11); // Set pin 11 for (int i = 0; i < 1000000; i++); GPIOA->BRR = (1<<11); // Unset pin 11 for (int i = 0; i < 1000000; i++); } }
```

Timings [#](https://timakro.de/blog/quadcopter-programming-part-2/#timings)
---------------------------------------------------------------------------

Another issue that needs addressing are the for-loops used for delay.

```
for (int i = 0; i < 1000000; i++);
```

We don’t know how long this for-loop will take to run i.e. we don’t know how many clock cycles one iteration takes. This is not defined and could differ between debug and optimized builds. That’s where the timer peripheral comes into play.

### A word on system clocks [#](https://timakro.de/blog/quadcopter-programming-part-2/#a-word-on-system-clocks)

The STM32 processor on my board runs at 72 MHz. CMSIS defines the `SystemCoreClock` variable with the frequency which it assumes based on the processor type we specified earlier at compile time. I find the way system clocks work really fascinating and I highly recommend two videos by [Steve Mould](https://www.youtube.com/user/steventhebrave/videos) on YouTube. In the [first one](https://www.youtube.com/watch?v=wcJXA8IqYl8) he explains why quartz crystals make electricity when vibrating and in the [second video](https://www.youtube.com/watch?v=_2By2ane2I4) he shows how this is used in quartz watches.

The quartz crystals in processors are generally vibrating at a multiple of their fundamental resonant frequency because it is challenging to manufacture crystals with a resonant frequency above 30 MHz. For example the quartz crystal in my processor vibrating at 72 MHz has a fundamental resonant frequency of 25 MHz. This is referred to as a 3rd overtone crystal.

### Regular interrupts [#](https://timakro.de/blog/quadcopter-programming-part-2/#regular-interrupts)

The timer peripheral is a circuit which can be configured for interrupts every N clock cycles. CMSIS provides the `SysTick_Config` function to configure and enable the timer peripheral. Most functions are documented in `Libraries/CMSIS/Documentation/CMSIS_Core.htm` if you’d like to have a look yourself. The function takes the number of clock cycles between interrupts as an argument. Looking at the code of the function you can see that there’s no magic. It writes to memory like we did before to toggle LEDs. You could write this function yourself with help of the reference manual.

```
static __INLINE uint32_t SysTick_Config(uint32_t ticks) { if (ticks > SysTick_LOAD_RELOAD_Msk) return (1); /* Reload value impossible */ SysTick->LOAD = (ticks & SysTick_LOAD_RELOAD_Msk) - 1; /* set reload register */ NVIC_SetPriority (SysTick_IRQn, (1<<__NVIC_PRIO_BITS) - 1); /* set Priority for Cortex-M0 System Interrupts */ SysTick->VAL = 0; /* Load the SysTick Counter Value */ SysTick->CTRL = SysTick_CTRL_CLKSOURCE_Msk | SysTick_CTRL_TICKINT_Msk | SysTick_CTRL_ENABLE_Msk; /* Enable SysTick IRQ and SysTick Timer */ return (0); /* Function successful */ }
```

We call `SysTick_Config` at the beginning of the main function. We want an interrupt every millisecond for now so we divide the clock frequency by 1000 to get the number of clock cycles per millisecond.

```
// Configure 1 ms interrupts if (SysTick_Config(SystemCoreClock / 1000)) { while (1); }
```

The timer is hardwired to run a function at a specific memory location much like we saw last post where we placed the call to the C entry point at the right location in memory. The assembly startup script that comes with CMSIS already places a call to `SysTick_Handler` for us at that location.

Now it’s just a matter of counting up the milliseconds and writing a delay function. The final code should be quite self-explanatory.

```
#include "stm32f10x.h"  volatile uint32_t msTicks; void SysTick_Handler (void) { msTicks++; } __INLINE static void Delay (uint32_t dlyTicks) { uint32_t curTicks = msTicks; while ((msTicks - curTicks) < dlyTicks); } void main (void) { // Configure 1 ms interrupts if (SysTick_Config(SystemCoreClock / 1000)) { while (1); } // Enable I/O port A clock RCC->APB2ENR |= RCC_APB2ENR_IOPAEN; // Configure pin 11 as push-pull output GPIOA->CRH &= ~(GPIO_CRH_MODE11 | GPIO_CRH_CNF11); GPIOA->CRH |= GPIO_CRH_MODE11; while (1) { GPIOA->BSRR = (1<<11); // Set pin 11 Delay(500); GPIOA->BRR = (1<<11); // Unset pin 11 Delay(500); } }
```

Inlining the `Delay` function seems appropriate here because it is so small and the function overhead could potentially lead to very slight inaccuracies in the timing. The millisecond counter would overflow after about 50 days, way after the batterie runs out when the quadcopter is in the air.

Rotating lights [#](https://timakro.de/blog/quadcopter-programming-part-2/#rotating-lights)
-------------------------------------------------------------------------------------------

Before we finally drive the rotors let’s make the LEDs on all four arms blink in a rotating fashion as a final example. We need to take another look at the quadcopter schematics to find the corresponding pins.

[![LED schematic extract](https://timakro.de/generated/quadcopter-programming-part-2/led-schematic-720-1bb2ef.png)](https://timakro.de/public/quadcopter-programming-part-2/led-schematic.png)

This time because we have pins on the `GPIOB` registers we need to turn on that clock first. Then we configure all four pins as output pins and between some delay always turn the current pin on and the one before off. Straight forward, right?

```
#include "stm32f10x.h"  volatile uint32_t msTicks; void SysTick_Handler (void) { msTicks++; } __INLINE static void Delay (uint32_t dlyTicks) { uint32_t curTicks = msTicks; while ((msTicks - curTicks) < dlyTicks); } void main (void) { // Configure 1 ms interrupts if (SysTick_Config(SystemCoreClock / 1000)) { while (1); } // Enable I/O port A clock RCC->APB2ENR |= RCC_APB2ENR_IOPAEN; // Enable I/O port B clock RCC->APB2ENR |= RCC_APB2ENR_IOPBEN; GPIOA->CRH &= ~(GPIO_CRH_MODE11 | GPIO_CRH_CNF11); GPIOA->CRH |= GPIO_CRH_MODE11; GPIOA->CRH &= ~(GPIO_CRH_MODE8 | GPIO_CRH_CNF8); GPIOA->CRH |= GPIO_CRH_MODE8; GPIOB->CRL &= ~(GPIO_CRL_MODE1 | GPIO_CRL_CNF1); GPIOB->CRL |= GPIO_CRL_MODE1; GPIOB->CRL &= ~(GPIO_CRL_MODE3 | GPIO_CRL_CNF3); GPIOB->CRL |= GPIO_CRL_MODE3; while (1) { GPIOA->BSRR = (1<<11); GPIOB->BRR = (1<<3); Delay(100); GPIOA->BSRR = (1<<8); GPIOA->BRR = (1<<11); Delay(100); GPIOB->BSRR = (1<<1); GPIOA->BRR = (1<<8); Delay(100); GPIOB->BSRR = (1<<3); GPIOB->BRR = (1<<1); Delay(100); } }
```

Let’s have a look at the result.

But wait, one light is not working. The white LED is just the power LED, but both the bottom and the top blue LED on one arm are not working. The fact that both LEDs are not turning on made me pretty sure the LEDs are okay. Pin `PB3` wasn’t powered. After digging through the reference manual for a while I noticed that the pin is configured for JTAG debugging by default. According to the reference manual you have a few options to free the pin.

> To optimize the number of free GPIOs during debugging, this mapping can be configured in different ways by programming the **SWJ\_CFG\[2:0\]** bits in the _Alternate function remap and debug I/O configuration register_ (**AFIO\_MAPR**).

[![Alterante function table](https://timakro.de/generated/quadcopter-programming-part-2/alternate-function-table-720-d78d84.png)](https://timakro.de/public/quadcopter-programming-part-2/alternate-function-table.png)

The developers of the drone wired a JTAG pin to an LED, they obviously didn’t account for JTAG debugging. But there is still SWD debugging which just requires two pins and they connected those to an easily accessible debug port. So we will disable the JTAG debug port to free pin `PB3` but keep SWD debugging enabled. Again CMSIS has us covered for writing to the `AFIO_MAPR` register, no hardcoding memory addresses necessary.

```
// Remap JTAG ports to alternate function (frees PA15, PB3, PB4) AFIO->MAPR |= AFIO_MAPR_SWJ_CFG_JTAGDISABLE;
```

Before we can write to the register we need to enable the correspoding clock as usual.

```
// Enable alternate function I/O clock // (required for alternate function remapping) RCC->APB2ENR |= RCC_APB2ENR_AFIOEN;
```

Voilà, ready for takeoff!

Driving the motors [#](https://timakro.de/blog/quadcopter-programming-part-2/#driving-the-motors)
-------------------------------------------------------------------------------------------------

For this test we will drive all four rotors full throttle while holding the quadcopter down with a makeshift cardboard construction. I attached adhesive hook and loop tape to the batteries and drone for easy battery swapping.

[![Hook and loop attachment](https://timakro.de/generated/quadcopter-programming-part-2/hook-and-loop-720-9ace28.jpg)](https://timakro.de/public/quadcopter-programming-part-2/hook-and-loop.jpg)

Each of the four motors is connected directly to the battery via a transistor. The transitor base pins labeled `PWMA` to `PWMD` in this schematic correspond to GPIO pins `A0` to `A4`.

[![Motors schematic extract](https://timakro.de/generated/quadcopter-programming-part-2/motors-schematic-720-43bf48.png)](https://timakro.de/public/quadcopter-programming-part-2/motors-schematic.png)

To regulate the speed of the rotors you would use pulse width modulation (PWM), basically switching power on and off quickly to simulate an intermediate voltage. The code for this test though just turns on the transistors for 20 seconds after 10 seconds of LED blinking for me to get my cardboard construction in place. I won’t include the code here because it is completely analogous to what we did with the LEDs but it’s [here](https://github.com/timakro/stm32-quadcopter/blob/master/drive_rotors/main.c) if you want to take a look.

Again all the examples including Makefiles are on [GitHub](https://github.com/timakro/stm32-quadcopter).

Future plans [#](https://timakro.de/blog/quadcopter-programming-part-2/#future-plans)
-------------------------------------------------------------------------------------

The next post will be about gdb debugging on embedded systems with [OpenOCD](http://openocd.org/) via Serial Wire Debug (SWD). Let’s see if that post takes me another half a year… To be fair I just came back to the project and finally got SWD working. This used to give me lot’s of trouble and was the main reason this post took me so long.

As always you can leave feedback and suggestions on [Hacker News](https://news.ycombinator.com/item?id=21669936).

  
  
from Hacker News https://ift.tt/37UJIk3