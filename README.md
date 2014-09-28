I2CdevSPI
=========
Why would you want this? So you can use the excellent MPU6050 library in I2Cdev for
your own coding on the Ardupilot 2.6. It has the ATMEGA 2560, so there is lots of RAM.
But the APM has the MPU connected to the ATMEGA using teh SPI pins.

I briefly thought about doing a softI2C on the SPI pin #'s, but SPI is faster and simpler.

The SS pin for the /CS on the device is passed as the "I2C" device address in these calls. SS is normally 
held high, but needs to be set low so the slave device will be listening.

I used this to get the MPU6050 code to run on an Ardupilot board - APM mini. 

Changes required:

+ set interrupt to INT6 (yes arduino dev will handle this)
+ add SPIEnabled call after MPU init so MPU6000 runs SPI instead of I2C
+ on this board you must turn off SS on pin 40 (GPS?) by setting it high.
+ tweak include files MPU6050.h to load this lirary instead of stock lib.
+ add this file/lib to your main ino so the lib is read by Arduino IDE
+ SS is 53 on the APM. SO use this as the 'device' address in the call to the I2Cdev class.


New I2Cdev lib that runs on SPI
