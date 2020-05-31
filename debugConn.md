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