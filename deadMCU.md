## Game Over... I burned my MCU
The is the follow up and conclusion of my post on May 14th and June 13
* https://www.reddit.com/r/boostedboards/comments/gjxo3q/gg_i_just_fried_something_while_debugging_the_xr/
* https://www.reddit.com/r/boostedboards/comments/h8gjj7/boosted_xr_battery_well_the_voltage_regulator/

![Shorted](https://i.redd.it/16ebwhr5ety41.png)

### The story
A loose low-voltage wire shorted to the high-voltage battery. Immediately fried the regulator. The chip is heating up!!!
Panic mode! Had to snip away the battery terminal to cut the power to the whole unit... Man this is gonna add some delays.
New next step: scrape away the conformal coating and replace the regulator

### Surgery & Re-Powering up the BMS

![Surgery](https://i.imgur.com/jt74I7V.png)

After lots of effort and heat, the voltage regulator was removed. 

![ExternalPSU](https://i.imgur.com/ngI7T30.png)

Wires for GND, 3.3V and 5V was soldered to the PCB and manually powered an external power supply

![Power Draw](https://i.imgur.com/MmTGRy9.png)

Look at channel 2. Unfortunately, the 3.3V rail is drawing wayyyyy to much power. Using the FLIR thermal camera, it can be observed that the PIC micro-controller is heating up.

![MCU Heat](https://i.imgur.com/S90tXcV.png)

### Conclusion

At this point, it can be concluded that the MCU died. 

I really wanted to try out the new procedure from u/jonataubert (https://github.com/jonataubert/RLOD_B2XR). 

It is with great disappointment that I have to tag out of the reverse engineering game of the BB XR.
