# Boosted Battery Reverse Engineering
This repo contains data, pictures and footage of my teardown of the Boosted Board battery V2 Extended Range

Discussions:
-- [May 8th](https://www.reddit.com/r/boostedboards/comments/gg88ma/boosted_v2_xr_battery_teardown_here_is_the_pcb_in/) -- [May 9th](https://www.reddit.com/r/boostedboards/comments/ggvfu7/success_getting_debug_data_from_the_v2_xr_battery/) -- [May 10th](https://www.reddit.com/r/boostedboards/comments/ghdyi7/bb_v2_xr_bms_pcb_analysis/) -- [May 19th](https://www.reddit.com/r/boostedboards/comments/gmzpmr/explanation_on_how_to_connect_bb_v2_xr_battery_to/) --

#### !!! Other great people who did amazing work on the reverse engineering !!!
https://github.com/jonataubert/RLOD_B2XR

https://github.com/rscullin/beambreak

Repair service: https://www.reddit.com/user/technically_a_nomad/

## About this
So I love electronics. And after watching Doctor Battery's video (https://www.youtube.com/watch?v=XqM4JGT5Mbk) on his V2 battery teardown, it inspired me to look into my old dead V2 battery as well.

I have a ton of pictures and footage of the disassembly process. Gotta filter through all of that soon. And also, I'm happy to say that I was able to get Debug UART working. We are getting debug information back from the BMS.

# Hardware Overview
So after much a lot of effort to pry the battery block out, we get a look at this beautiful PCB. 
![Boosted V2 XR Battery](https://raw.githubusercontent.com/lle/boostedBattery/master/pictures/PCB/topview.JPG)

Using the microscope, we can get the part number of the important ICs which can be relevant for our analysis.
![Battery IC Analysis](https://raw.githubusercontent.com/lle/boostedBattery/master/pictures/PCB/overview.png)

Here is what we are looking at:
* Buck Regulator: [LM5017](http://www.ti.com/lit/ds/symlink/lm5017.pdf?&ts=1589157738344)
* High Voltage Battery charge/discharge NFET driver [BQ76200](http://www.ti.com/lit/ds/symlink/bq76200.pdf?&ts=1589157776395)
* N-CH Power MOSFET [57N08](https://www.infineon.com/dgdl/BSC057N08NS3G_rev2.4.pdf?folderId=db3a304313b8b5a60113cee8763b02d7&fileId=db3a30431add1d95011ae803c9345616)
* I2C LED Driver [TLC59108](http://www.ti.com/lit/ds/symlink/tlc59108.pdf?&ts=1589158260465)
* Microchip 16bit MCU [dsPIC33EP512GP504](https://www.microchip.com/wwwproducts/en/dsPIC33EP512GP504)
* 128Mb Flash Memory [IS25LP128](http://www.issi.com/WW/pdf/IS25LP128.pdf)
* 15-cell battery monitor [BQ769x0](http://www.ti.com/lit/ds/symlink/bq76940.pdf?&ts=1589158546744)as
* FUSE (on top right): [45A](https://www.dexerials.jp/en/products/c3/sfk1245.html) credit to [u /DerDaku](https://www.reddit.com/r/boostedboards/comments/ghdyi7/bb_v2_xr_bms_pcb_analysis/fq9e78y?utm_source=share&utm_medium=web2x) for finding it.

# Let's dig deeper into the BMS
### [1. 13S2P Battery Connector](batConn.md)
### [2. Debug and Programming Port Pinout](debugConn.md)
### [3. Connecting BMS to Computer](uartHowTo.md)
### [4. More Pictures of the PCB](bmsPic.md)
### [5. Game-over... I killed it](deadMCU.md)
