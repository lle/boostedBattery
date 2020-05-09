# Boosted Battery Reverse Engineering
This repo contains data, pictures and footage of my teardown of the Boosted Board battery V2 Extended Range

## Short Description
So I love electronics. And after watching Doctor Battery's video (https://www.youtube.com/watch?v=XqM4JGT5Mbk) on his V2 battery teardown, it inspired me to look into my old dead V2 battery as well.

I have a ton of pictures and footage of the disassembly process. Gotta filter through all of that soon. And also, I'm happy to say that I was able to get Debug UART working. We are getting debug information back from the BMS.

![Debug Ports](https://raw.githubusercontent.com/lle/boostedBattery/master/pictures/PCB/ports.png)

## Debug Port Pinout
|               |        |           |            |
|---------------|--------|-----------|------------|
|               | Pin    |           |            | 
|               | 1      | 10        |            |
|               | 2      | 9         |            |
| TX            | 3      | 8         |            |
| RX            | 4      | 7         | BTN        |
| LED-G         | 5      | 6         | LED-R      |

## Programming Port Pinout
|               |        |           |              |
|---------------|--------|-----------|--------------|
|               | Pin    |           |              | 
| MCLR          | 1      | 2         |              |
|               | 3      | 4         | PG-D (data?) |
| PG-C (clock?) | 5      | 6         |              |
