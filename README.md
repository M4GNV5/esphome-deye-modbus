# Esphome config for my Solar setup

The goal of this project is to interface with my solar inverter and:
- read solar inverter metadata
- emulate a SDM230/SDM630 energy meter

I use a Deye SG03LP1, which is a single phase 5kW hybrid solar inverter which is compatible to 48V pylontech batteries.
It might work for other models aswell, however some sources say the three phase Deye inverters are different and might not work.
Feel free to add a mention of your model if you successfuly tested this code with it.

I also emulate the power registers of an Eastron SDM630 energy meter, feeding it with [SML data from my EVU meter](https://github.com/M4GNV5/esphome-smart-meter-reader).
This allows to use the inverter zero export functionality.

For reading data I juse the RJ45 pins 1 (B), 2 (A) and 3 (GND) of the "BMS485/CAN" port (top middle) of the 5 RJ45 ports located inside the inverter.
For emulating the energy meter I use the "Meter" port (top left) of the 5 RJ45 ports.
The CAN line of the "BMS485/CAN" port is used by [battery-emulator for my DIY 48V battery](https://github.com/dalathegreat/Battery-Emulator/wiki/Battery:-Daly-SmartBMS)

## Credits
Some of the deye specific esphome code was originally taken from [this photovoltaikforum post](https://www.photovoltaikforum.com/thread/191631-fernbedienung-von-deye-5k-wechselrichtern-%C3%BCber-modbus-home-assistant/?postID=3090347#post3090347), however many missing registers were added and the (for me) unused time scheduling was removed.

Even though I do not speak Czech, I was able to find a half-chinese/half-english documentation of all modbus registers in [this forum thread](https://forum.mypower.cz/viewtopic.php?t=6926&start=20)

The Eastron SDM230 registers are officially documented [here](https://eastroneurope.com/images/uploads/products/protocol/SDM230-MODBUS_Protocol.pdf)
