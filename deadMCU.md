## Game Over... I burned my MCU
The is the follow up and conclusion of my post on May 14th and June 13

![Shorted](https://i.redd.it/16ebwhr5ety41.png)
A loose low-voltage wire shorted to the high-voltage battery. Immediately fried the regulator. The chip is heating up!!!
Panic mode! Had to snip away the battery terminal to cut the power to the whole unit... Man this is gonna add some delays.
New next step: scrape away the conformal coating and replace the regulator

![Surgery](https://i.imgur.com/jt74I7V.png)
After lots of effort and heat, the voltage regulator was removed. Wires for GND, 3.3V and 5V was soldered to the PCB and manually powered an external power supply

![Power Draw](https://i.imgur.com/MmTGRy9.png)
Look at channel 2. Unfortunately, the 3.3V rail is drawing wayyyyy to much power. Using the FLIR thermal camera, it can be observed that the PIC micro-controller is heating up.

![MCU Heat](https://i.imgur.com/S90tXcV.png)
At this point, it can be concluded that the MCU died. 

I really wanted to try out the new procedure from u/jonataubert (https://github.com/jonataubert/RLOD_B2XR). 

It is with great disappointment that I have to tag out of the reverse engineering game of the BB XR.