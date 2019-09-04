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


Code with debugging uses serial to output various results as they are generated. This is particularly useful if the results are unexpected as you can see exactly what the arduino is detecting as it runs. It also helps identify problems due to faulty digital pins on the arduino.



Other programs on here can be documented on request, please email me if you require it.
