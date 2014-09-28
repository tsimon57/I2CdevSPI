I2CdevSPI
=========
The SS pin for the /CS on the device is passed as the "I2C" device address in these calls. SS is normally 
held high, but needs to be set low so the slave device will be listening.

I used this to get the MPU6050 code to run on an Ardupilot board - APM mini. 

Changes required:

+ set interrupt to INT6 (yes arduino dev will handle this)
+ add SPIEnabled call after MPU init so MPU6000 runs SPI instead of I2C
+ on this board you must turn off SS on pin 40 (GPS?) by setting it high.
+ tweak include files MPU6050.h to load this lirary instead of stock lib.
+ add this file/lib to your main ino so the lib is read by Arduino IDE
+ SS is 53 on the AMP.


New I2Cdev lib that runs on SPI
