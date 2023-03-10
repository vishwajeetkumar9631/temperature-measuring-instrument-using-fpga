# temperature-measuring-instrument-using-fpga
I2C stands for Inter-Integrated Circuit. It is a bus interface connection protocol incorporated into devices for serial communication. It was originally designed by Philips Semiconductor in 1982. Recently, it is a widely used protocol for short-distance communication. It is also known as Two Wired Interface (TWI).
Working of communication protocol I2C
It uses only 2 bi-directional open-drain lines for data communication called SDA and SCL. Both these lines are pulled high.
Serial Data (SDA) – Transfer of data takes place through this pin.
Serial Clock (SCL) – It carries the clock signal.
I2C operates in 2 modes –
⦁	Master mode
⦁	Slave mode
Each data bit transferred on SDA line is synchronized by a high to the low pulse of each clock on the SCL line.
According to I2C protocols, the data line cannot change when the clock line is high, it can change only when the clock line is low. The 2 lines are open drain; hence a pull-up resistor is required so that the lines are high since the devices on the I2C bus are active low. The data is transmitted in the form of packets which comprises 9 bits. The sequence of these bits are
⦁	Start Condition – 1 bit
⦁	Slave Address – 8 bit
⦁	Acknowledge – 1 bit

Start and Stop Conditions:
START and STOP can be generated by keeping the SCL line high and changing the level of SDA. To generate START condition the SDA is changed from high to low while keeping the SCL high. To generate STOP condition SDA goes from low to high while keeping the SCL high, as shown in the figure below.
Repeated Start Condition:

Between each start and stop condition pair, the bus is considered as busy and no master can take control of the bus. If the master tries to initiate a new transfer and does not want to release the bus before starting the new transfer, it issues a new START condition. It is called a REPEATED START condition.
Read/Write Bit :

A high Read/Write bit indicates that the master is sending the data to the slave, whereas a low Read/Write bit indicates that the master is receiving data from the slave. 
ACK/NACK Bit:
After every data frame, follows an ACK/NACK bit. If the data frame is received successfully then ACK bit is sent to the sender by the receiver.  
Addressing:

The address frame is the first frame after the start bit. The address of the slave with which the master wants to communicate is sent by the master to every slave connected with it. The slave then compares its own address with this address and sends ACK.
I2C Packet Format:

In the I2C communication protocol, the data is transmitted in the form of packets. These packets are 9 bits long, out of which the first 8 bits are put in SDA line and the 9th bit is reserved for ACK/NACK i.e. Acknowledge or Not Acknowledge by the receiver. 
 START condition plus address packet plus one more data packet plus STOP condition collectively form a complete Data transfer.
Features of I2C Communication Protocol:

⦁	Half -duplexer Communication Protocol – 
Bi-directional communication is possible but not simultaneously.
⦁	Synchronous communication:
The data is transferred in the form of frames or blocks.
⦁	Can be configured in a multi-master configuration.
⦁	Clock Stretching – 
The clock is stretched when the slave device is not ready to accept more data by holding the SCL line low, hence disabling the master to raise the clock line. Master will not be able to raise the clock line because the wires are AND wired and wait until the slave releases the SCL line to show it is ready to transfer next bit.
⦁	Arbitration – 
I2C protocol supports multi-master bus system but more than one bus cannot be used simultaneously. The SDA and SCL are monitored by the masters. If the SDA is found high when it was supposed to be low it will be inferred that another master is active and hence it stops the transfer of data.
⦁	Serial transmitter 
I2C uses serial transmission for transmission of data.
⦁	Used for low-speed communication.

Temperature sensor used in the I2C:

The Nexys A7 board has an Analog Device ADT7420 temperature sensor. This chip uses an industry-standard I2C interface to communicate with. This two-wire interface is used primarily for slower speed devices. It has the advantage of allowing multiple chips to be connected through the same interface and be addressed individually. In our case, we will be using it to simply read the current temperature from the device and display the value on the 7-segment display.


the FPGA or field programmable gate array i have use is a NEXSYS 4 which containg the above sensor
![WhatsApp Image 2023-02-14 at 11 46 18 PM](https://user-images.githubusercontent.com/125308772/218823105-99397bb5-cae7-4513-8125-8ef13ce360ca.jpeg)
