# Laboratory Activity #5: Python-Arduino Integration

### Overview: PC-Based Lighting Control

This project advances beyond standard Arduino IDE sketching. Instead of relying solely on the microcontroller's internal loop, we construct a custom "remote control" application using the Python programming language. This simulates real-world systems where high-level software manages low-level hardware components.

### What This Project Does

The system effectively converts your computer keyboard into a physical toggle switch panel.

**The Interface:** A Python script executes on the host computer, presenting a text-based menu (Command Line Interface) prompting for input (e.g., "Press [R] to toggle Red").

**The Hardware:** An Arduino microcontroller circuit wired with Red, Green, and Blue LEDs.

**The Operation:** Inputting a specific character (such as 'R') triggers an immediate state change in the corresponding LED. The system also supports macro commands for "All On," "All Off," and mixed-color modes like "Violet."

### How It Works

The architecture functions as a digital dialogue between the host machine and the microcontroller.

**The Transmitter (Python):** You input a command via the Python console. The script processes this input, encoding the text into bytes suitable for serial transmission.

**The Transmission:** The data packet travels through the serial port (USB cable) linking the PC to the Arduino.

**The Receiver (Arduino):** The board continually polls the serial buffer. When data arrives, it parses the character payload.

**The Execution:** If the payload is 'r', the Arduino triggers the voltage for the Red LED. A 'g' signal triggers the Green LED, and so on.

### Code Explanation

To ensure maintainability, the codebase utilizes Modular Programming techniques to separate concerns.

**The Host Script (Python):**

* **The Event Loop:** The program runs an infinite loop, persistently awaiting user input until a termination command is issued.
* **The Encoder:** Since the serial connection requires byte-level data, this script encodes the string characters into a compatible format before transmission.

**The Firmware (Arduino):**

* **The Configuration (Header File):** Hardware settings are isolated here. It defines pin mappings and manages "State variables"—tracking whether a light is currently High or Low to enable toggling.
* **The Logic Controller (Main Sketch):** This section handles signal processing. It evaluates the incoming character using a `switch-case` structure to execute the correct function while filtering out invalid inputs.

### Key Concepts Learned

**Inter-Language Communication:** Establishing a bridge between a high-level language (Python on a PC) and low-level firmware (C++ on a chip).

**State Management:** Implementing logic that retains the current status of the hardware (e.g., knowing "Red is On"), enabling toggle functionality.

**Code Modularity:** Organizing code into separate files and headers to improve readability and debugging efficiency.

**Command Line Interface (CLI):** Developing a text-based User Interface (UI) to interact with physical systems, rather than relying on graphical buttons.
