# Laboratory Activity #4: Arduino Serial Connection & Latching Logic

### Overview: The "Sticky" Alarm

This project introduces a system that moves away from full automation and requires human intervention. Unlike previous circuits that functioned independently, this system demands user interaction to restore order. It demonstrates the ability to control hardware states in real-time through keyboard commands.

### What This Project Does

The system functions as a security device that "locks" into an alert state once triggered.

**The Monitor:** A light sensor continuously tracks the ambient brightness of the environment.

**The Trigger:** If the light intensity exceeds a pre-set threshold, the alarm activates, causing an LED to flash repeatedly.

**The "Latch":** This is the defining feature—once the alarm is triggered, it remains active even if the light level returns to normal. The system "remembers" the breach occurred.

**The Reset:** The alarm will continue to blink indefinitely until a human operator physically types the command "stop" into the computer console to deactivate it.

### How It Works

The system operates through a partnership between physical sensing and digital communication.

**Input (Hardware):** A photoresistor (light sensor) monitors physical conditions.

**Input (Software):** The Arduino monitors the USB connection, listening for specific text strings sent by the user.

**The Trap:** When the light threshold is breached, the code enters a specific "Alarm Mode" (a loop). In this state, it ceases to check the light sensor and focuses entirely on blinking the LED and awaiting the password.

**The Escape:** Upon receiving the correct text command ("stop"), the program breaks out of the alarm loop and returns to standard monitoring duties.

### Code Explanation

The software employs specific logic to handle text input and state management.

**Value Scaling:** The sensor generates a broad range of data (0-1023). The code compresses this into a standard byte scale (0-255) to simplify brightness comparisons.

**The "Trap" Loop:** The code utilizes a `while` loop to enforce the alarm state. Think of this as a locked room: once the program enters this block of code, it cannot exit until the specific key (typing "stop") unlocks the door.

**Text Parsing:** The code includes a text reader to capture user input. It also applies a "Lowercase" function, ensuring the system recognizes the command regardless of capitalization (e.g., "STOP," "Stop," or "stop" are all accepted).

### Key Concepts Learned

**Serial Communication:** Utilizing the USB interface to send text-based commands to the microcontroller, rather than using it solely for code upload.

**Latching (State Retention):** Designing a system that maintains a specific state (like "Emergency Mode") until explicitly acknowledged by a human. This is a fundamental concept in industrial safety systems.

**String Processing:** Programming the machine to interpret words and handle variations in text, such as case insensitivity.

**Blocking Code:** A programming style where one task (the alarm loop) pauses or "blocks" all other operations (like reading sensors) until a condition is met.
