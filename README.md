# 24-Pin-Tester
Tests the continuity of a 24 pin cable using an arduino.

How it works:
A cable is sonnected to an arduino at both ends. At one end (A) the pins are set to INPUT while the other (B) are INPUT_PULLUP.
At end A, sequentially a pin is set to OUTPUT LOW, and all the pins at B are read for their state. If a pin is LOW, it is connected to the pin being tested at A.
A is then sent back to INPUT and the next PIN is set to OUTPUT LOW and so on.
This is coallated into a 2D array of 576 boolean values, showing every conenction between both ends of the cable.
This is then parsed into another array, in where each pin is assigned a fault value based on the 2d array, and that fault list is then turned into a string of pins that had failure fault values. This is then displayed on an LCD screen.
After testing interrupts are setup to detect the cable being disconnected and reset the program if so.

While this code is written for 24 core cable, this could easily be modified to work with any number of cores, providing the arduino you use has enough digital pins or you use a shift register.

While this code is very niche, it is a fantastic time saving tool for testing large numbers of cables quickly, or cables with a lot of pins that all need testing for shorts.


Code with debugging uses serial to output various results as they are generated. This is particularly useful if the results are unexpected as you can see exactly what the arduino is detecting as it runs. It also helps identify problems due to faulty digital pins on the arduino.

Coincidentally that is why pins start at 4 rather than 0, this code is a remake of my very first program which was made before I could write code. I used arduBlock which works a bit like scratch with drag and drop functions. The code was since lost and after a battery being connected backwards caused issues with the only arduino running it, I had to rewrite it.
Turns out the issue was that a number of the pullup resestors on the board were fried, 2 and 3 specifically, and because I wanted consecutive pins, I decided to just start at 4 as there are enough pins on the Arduino MEGA to spare.

This is still relatively basic code and I'm sure it could easily be improved, I have used what I currently know to get a working, and beyond the first version, this now detects wether the cable has been manually disconnected in order to retest rather than requiring a manual reset each time a new test is needed. 

I welcome any suggestions/pull requests for potential improvements as I'm always looking for ways to improve the code as I learn.
