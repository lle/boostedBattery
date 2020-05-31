## 13S2P Battery Connector
It has been determined by the Doctor Battery's youtube video that the battery is 13 cells LiFePO4. A fully charged cell is 3.6V, and the nominal voltage is 3.2V. 

By looking under the PCB, we can find test points for each of the cell as well as test points for what appears to be temperature sensor. Here is the test points for the battery inputs.

![Battery Ports Top](https://raw.githubusercontent.com/lle/boostedBattery/master/pictures/PCB/batteryMonTop.jpg)
![Battery Ports Bottom](https://raw.githubusercontent.com/lle/boostedBattery/master/pictures/PCB/batteryMon.png)
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