# Midterm Examination: Smart Light Monitor

### Overview: Intelligent Environment Monitoring

This project serves as the midterm assessment, integrating all previous learning modules into a cohesive "Smart Light Monitor." It functions as an environmental sensing unit that gauges room brightness and visualizes the data using a traffic-light indicator system (Green, Yellow, Red). The core innovation of this system is its dual-mode capability: it can operate in an **Automatic** mode based on pre-programmed logic, or a **Manual** mode that allows for user-defined calibration via text commands.

### What It Does

The device operates using two distinct behavioral protocols:

**Automatic Mode (Default):** The system functions autonomously. It utilizes hard-coded factory presets to classify ambient light levels, activating the appropriate LED (Green for low intensity, Yellow for medium, and Red for high intensity).

**Manual Mode:** The user assumes direct control. You can input text commands to dynamically alter the threshold values that trigger the LEDs. This flexibility allows the device to be calibrated for different environments without the need to modify and re-upload the code.

**Live Dashboard:** The system continuously streams real-time telemetry to the computer console, displaying the current light percentage, the active LED status, and the current operating mode.

### How It Works

The architecture merges analog sensing with serial command processing.

**Input:** A photoresistor (light sensor) continuously monitors the physical brightness of the room.

**Processing:** The system normalizes the sensor's raw voltage data into a readable 0-100% scale. It then evaluates this data against the active mode's rules to determine the necessary reaction.

**Output:** A set of three LEDs (Green, Yellow, Red) illuminates to provide an immediate visual representation of the light intensity.

**Control:** The system accepts specific text strings (e.g., `SET LOW 30`) to instantaneously update configuration variables in real-time.

### Code Explanation

The software architecture is centered around "State Management"—the device's logic path changes entirely based on the selected mode.

**Flexible Configuration:** Unlike previous exercises where threshold values were static (constants), this project utilizes dynamic variables. In Manual mode, user inputs overwrite the default values.

**The Logic:**

* **Automatic Logic:** Adheres to rigid, immutable conditional statements (e.g., *if light < 40%, trigger Green*).
* **Manual Logic:** Evaluates sensor data against the custom variables defined by the user.

**Command Parsing:** The software includes an interpreter to process user input:

* It scans for state-switching keywords like `MODE AUTO` or `MODE MANUAL`.
* It parses configuration commands like `SET LOW` followed by an integer to update thresholds.
* **Safety Protocols:** The code implements validation logic to prevent logical errors, such as ensuring the "Low" threshold cannot be set higher than the "High" threshold.

### Key Concepts Applied

**Runtime Configuration:** The capability to modify system parameters during operation without requiring a system restart or firmware re-flash.

**String Parsing:** Programming the device to interpret complex serial inputs (combining text commands with numerical parameters).

**State Machines (Mode Switching):** Designing a system that can toggle between distinct operational behaviors (Auto vs. Manual) on command.

**Data Normalization:** Converting raw, non-intuitive sensor readings into a user-friendly percentage format.
