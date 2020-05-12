# Boosted Battery Reverse Engineering
This repo contains data, pictures and footage of my teardown of the Boosted Board battery V2 Extended Range

Discussions:

-- [May 8th](https://www.reddit.com/r/boostedboards/comments/gg88ma/boosted_v2_xr_battery_teardown_here_is_the_pcb_in/) -- [May 9th](https://www.reddit.com/r/boostedboards/comments/ggvfu7/success_getting_debug_data_from_the_v2_xr_battery/) -- [May 10th](https://www.reddit.com/r/boostedboards/comments/ghdyi7/bb_v2_xr_bms_pcb_analysis/) --

## Short Description
So I love electronics. And after watching Doctor Battery's video (https://www.youtube.com/watch?v=XqM4JGT5Mbk) on his V2 battery teardown, it inspired me to look into my old dead V2 battery as well.

I have a ton of pictures and footage of the disassembly process. Gotta filter through all of that soon. And also, I'm happy to say that I was able to get Debug UART working. We are getting debug information back from the BMS.

## Hardware Overview
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

## 13S2P Battery Connector
It has been determined by the Doctor Battery's youtube video that the battery is 13 cells LiFePO4. A fully charged cell is 3.6V, and the nominal voltage is 3.2V. 

By looking under the PCB, we can find test points for each of the cell as well as test points for what appears to be temperature sensor. Here is the test points for the battery inputs.

![Battery Ports](https://raw.githubusercontent.com/lle/boostedBattery/master/pictures/PCB/batteryMon.png)
| Battery Monitor | Testpoints	|
|------------------|----|
| 		| C0	|
| TS1-L	| 		|
| 		| TS1-H |
| C1	| 		|
|		| C2	|
| C3	|		|
|		| C4	|
| C5	|		|
|		| TS2-L	|
| TS2-H	|		|
|		| C6	|
| C9	| 		|
| 		| TS3-L |
| TS3-H | 		|
| 		| C10	|
| C11	| 		|
| 		| C12	|
| C13	|		|

Assuming the temperature sensors are thermistors, we can measure the resistor. The reading was 9.4 kOhm for all 3 sensors.

Using a multimeter, we can determine the voltage of each cells in our test battery. 
| Cell #  |	voltage 	|
|---------|-------------|
| 1		| 3.3	|
| 2		| 3.5	|
| 3		| 3.6	|
| 4		| 3.6	|
| 5 	| 3.6	|
| 6		| 3.6	|
| 7		| 3.6	|
| 8		| 3.7	|
| 9		| 3.6	|
| 10	| 3.6	|
| 11	| 3.6	|
| 12	| 3.6	|
| 13	| 3.3	|

> Hypothesis: 
> Is it possible that the BMS threw a RLOD because the cell were too unbalance?

## Debug and Programming Port Pinout
On the side of the PCB, there are two pogo pin ports: DEBUG and PROGRAMMING. The pogo pin ports adapter can be found here through [Tag-Connect.com](https://www.tag-connect.com/product/tc2030-idc-6-pin-tag-connect-plug-of-nails-spring-pin-cable-with-legs). By looking under the PCB, we can locate test-points. Using a multimeter, we can test continuity and determine where the signals go on the pogo pin.

![Debug Ports](https://raw.githubusercontent.com/lle/boostedBattery/master/pictures/PCB/ports.png)

| DEBUG         |    	 |           |            |
|---------------|--------|-----------|------------| 
|               | 1      | 10        |            |
|               | 2      | 9         |            |
| TX            | 3      | 8         |            |
| RX            | 4      | 7         | BTN        |
| LED-G         | 5      | 6         | LED-R      |

| PROGRAMMING   | 	     |           |              | 
|---------------|--------|-----------|--------------|
| MCLR          | 1      | 2         |              |
|               | 3      | 4         | PG-D (data?) |
| PG-C (clock?) | 5      | 6         |              |
