Laboratory Activity #2: Analog Signal Processing - Fading LEDs

Overview: Advancing Beyond Basic Toggling
This exercise represents a progression from simple "On" and "Off" states. While digital processors typically operate in binary (0 or 1), this project instructs the Arduino to function in a "Grayscale" capacity. It illustrates how to manipulate LED intensity, enabling smooth transitions and dimming capabilities.

What This Project Does
The program generates a fluid "breathing" or fading sequence across a set of five LEDs.
The Fade In: The LEDs activate sequentially down the line. However, rather than illuminating instantly, each light gradually increases in intensity from complete darkness to maximum brilliance.
The Fade Out: Once fully illuminated, the lights deactivate sequentially, slowly dimming back down to zero visibility.
The Result: A continuous, fluid visual wave that appears significantly more sophisticated than a standard blinking light.

How It Works: The "PWM" Technique
While the physical wiring remains identical to the previous running light circuit, the software utilizes a method known as PWM (Pulse Width Modulation).
The Visual Trick: The Arduino is physically incapable of outputting "partial voltage." It can only supply 0V (Off) or 5V (On). To simulate 50% brightness, the system toggles the switch on and off so rapidly that the human eye cannot track the flickering, perceiving it instead as a dimmer light.
The Control: We utilize the command analogWrite(). We assign it a value ranging from 0 (Permanently Off) to 255 (Permanently On). A value such as 127 instructs the Arduino to maintain the "On" state for 50% of the cycle and the "Off" state for the other 50%.

Code Explanation
The logic employs "Nested Loops" (loops inside other loops) to handle the animation.
The Setup: An initial loop defines which five specific pins are linked to the LEDs.
The External Loop (The Selector): This loop identifies which specific LED is currently being modified (e.g., "Targeting LED #1").
The Internal Loop (The Fader): Inside that selection, a secondary loop counts rapidly from 0 up to 255. This action incrementally raises the brightness level of the selected LED.

Key Concepts Learned
Simulated Analog: Understanding that digital hardware can mimic analog signals through high-speed switching.
PWM (Pulse Width Modulation): The specific method of regulating power delivery by altering the ratio of time a signal is "on" versus "off."
Nested Loops: Implementing a secondary loop to manage the duration/intensity of the fade, located within a primary loop that manages the order of the lights.
Dynamic Control: Utilizing variables to fluently alter the hardware state over a period of time, rather than relying on static, hard-coded values.
Would you like me to show you the syntax for the "Nested Loop" used in this specific fade effect?

