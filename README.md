# Flood Monitoring and Mitigation
ECNG 2006 Group Project | GROUP P4 - Flood Monitoring and Mitigation

Course Code: ECNG 2006 Intoduction to Microprocessors
Authors' Names: Anthony Jairam
                Darion Dickson 
                Zachary Soomai
                Vidia Ramlochan
                
Version:  1.0

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The device will detect flooding in the yard of the home by monitoring the level, and the turbidity,
of run-o↵ water in the sump. When the water level in the sump rises above a pre-set level, a pump
will be used to empty the sump. The keypad will be used to set the conditions for pump operation,
and send information to a central home system.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


# Initial Requirements

• The minimum pumping interval is determined by the unsigned number n stored in bits 3:0
of a register labelled NODECONFIG. The interval (in seconds) is 40 + 10 ⇥ n. The default
value of n is 5. The system will allow the value n to be set using the keypad.

• The system will monitor turbidity levels, in the sump, once per minute, using the turbidity
sensor connected to the PIC16 internal A/D converter. The range of turbidity levels to be
stored is between 0.1 NTU and 999.9 NTU. The most recent turbidity reading will be stored
as four packed BCD digits in two registers labelled RDG1 : RDG0.

• The system will display the most recent turbidity reading in NTU on the 7-segment displays.
The range of turbidity - values below 0.1 NTU should display the message ”-lo-”, and values
above 999.9 NTU should display the message ”-hi-”.

• The default pumping speed is 10% of full speed. The pumping speed should be determined
based on the turbidity level - 100% of full speed for turbidity levels above 50 NTU, 10% of
full speed for turbidity levels below 5 NTU, and proportionally-adjusted between 5 NTU and
50 NTU.

• When the water-level sensor indicates that the sump is full, the pump will be switched on, at
the turbidity-determined pumping speed, for the required minimum pumping interval. If the
water-level sensor still indicates that the sump is full at the end of the minimum pumping
interval, the pump will stay on until the water-level sensor no longer indicates that the sump
is full.

• Turbidity readings should also be stored in the internal PIC Data EEPROM. If the Data
EEPROM is full, data should be overwritten, so that the most recent samples are always
available.

** The system will communicate with the main home system via ZigBee as follows:
– A single key on the keypad should be used to initiate transfer of data to the main home
system.

– Turbidity data from the internal PIC EEPROM should be transmitted one reading at
a time. The system will be notified of successful reception of the message by a 16-bit
response from the remote system.

– Upon receipt of a response, the system should transmit the next reading, until all data
has been sent.
