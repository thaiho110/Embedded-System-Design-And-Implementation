# EEET2481 – Embedded Systems Design and Implementation - Assignment 3
This repository contains the source code and documentation for Assignment 3 of the course EEET2481 – Embedded Systems Design and Implementation. The project was completed by Team A and demonstrates proficiency in using a Nuvoton development board to handle UART communication, ADC/SPI protocols, and implement a complete embedded game.
GitHub repo for display coursework of Embedded System: Design and Implementation course at RMIT VN (2023)

## Team member
Ho Quoc Thai

Phan Trong Nguyen

Ngo Thanh Nguyen

## Project Overview

This project is divided into three main exercises, each designed to explore different facets of embedded systems:

Exercise 1: UART Communication: A simple demonstration of serial communication where a message is sent from a PC terminal to the Nuvoton board and echoed back.

Exercise 2: ADC and SPI Communication: The board reads an analog voltage from a potentiometer. When the voltage exceeds a 2V threshold, an interrupt is triggered, and a predefined message ("Team A") is sent out via the SPI protocol.

Exercise 3: Battleship Game: A fully-featured Battleship game implemented on the board. The game map is loaded via UART, and gameplay is managed using a keypad for input and a 7-segment display, LEDs, and a buzzer for output and feedback.

## Hardware and Software Requirements

### Hardware

Nuvoton Development Board

Oscilloscope (for verifying SPI signal in Exercise 2)

### Software

A C/C++ IDE compatible with the Nuvoton board (e.g., Keil MDK, IAR Embedded Workbench)

A serial terminal program (e.g., Tera Term, PuTTY, RealTerm)

Nuvoton board drivers and support packages

### Exercise Details

#### 1. Exercise 1

This exercise establishes a basic two-way communication link between the Nuvoton board and a PC using the UART module. A predefined message, "Hello, this is thai, nguyen and nguyen from team A", is sent from the terminal, received by the board, and immediately transmitted back to the terminal.

##### Setup and Results

Connections: The UART module's TX is connected to the board's Port B1 (UART_TX) and RX to Port B0 (UART_RX).

Functionality: The program successfully receives the full string from the terminal and echoes it back, confirming that both the transmit and receive functions of the UART are working correctly.

#### 2. Exercise 2

This program monitors an analog voltage from a potentiometer using the ADC. If the input voltage crosses a threshold of 2.0V, an interrupt is triggered. This interrupt service routine sends the string "Team A" via the SPI bus on Port D, pin 1, and simultaneously turns on an LED (PC15) to provide a visual notification of the event.

##### Setup and Results

Functionality: The LCD screen displays the real-time ADC value. When the value is adjusted to be over 2V, the interrupt is successfully triggered.

Verification: The LED on PC15 lights up, and the SPI signal transmitting the ASCII data for "Team A" can be clearly observed and decoded using an oscilloscope.

#### 3. Exercise 3: Battleship Game

This exercise is a complete implementation of the classic game "Battleship." The game operates based on the state diagram below and utilizes multiple hardware peripherals for an interactive experience.

##### Game Flow and State Diagram

The game proceeds through several states:

Welcome: The initial state, prompting the user to load a game map.

Map Loading: The user sends a map layout (where 0 is water and 1 is a ship) via UART.

Game Start: Once the map is loaded, the user presses a designated switch (SW_INT / GP15) to begin playing.

Gameplay Loop:

The player uses the keypad (1-8) to select X and Y coordinates. Key 9 toggles between selecting the X or Y axis.
The 7-segment display shows the remaining number of shots (starts at 16) and the currently selected coordinate.
The player presses the designated switch to "fire" at the selected coordinates.

Feedback:

Miss: A shot is deducted.

Hit: The LED on GPC12 flashes 3 times, and a buzzer beeps to notify the player.

Sunk: When a ship is fully destroyed, an on-screen counter is updated.

Game End:

Win: If all ships are sunk within 16 shots, a "Game Win" status is displayed.

Lose: If the player runs out of shots before sinking all ships, a "Game Over" status is displayed.

##### Results

The game functions exactly as described. The player can successfully load a map, select coordinates, and receive appropriate feedback for hits, misses, and game-end conditions.

### Contribution

Phan Trong Nguyen:	Completed Exercise 1 & 3.

Ngo Thanh Nguyen:	Completed Exercise 1 & 2.

Ho Quoc Thai:	    Completed Exercise 2 & 3.




