# Esphome config for my Solar setup

The goal of this project is to interface with my solar inverter.
It is capable of both reading solar metadata from the inverter via modbus as well as emulating a modbus energy meter to make use of the inverters zero export mode (i.e. charge/discharge a battery based on consumption vs solar generation).

I use a Deye SG03LP1, which is a single phase 5kW hybrid solar inverter with 48V pylontech battery compatible inverter.
It might work for other models aswell. However some sources say the three phase Deye inverters are different and might not work.
I also only emulate a single phase Eastron SDM230 energy meter, not a triple phase one, however changing to three phase should be simple by modifying the yaml generation script "gen-mqtt2modbus".
Feel free to add a mention of your model if you successfuly tested this code with it.

For reading data I juse the RJ45 pins 1 (B), 2 (A) and 3 (GND) of the "BMS485/CAN" port (top middle) of the 5 RJ45 ports located inside the inverter.
For emulating the energy meter I use the "Meter" port (top left) of the 5 RJ45 ports.
The CAN line of the "BMS485/CAN" port is used by [battery-emulator for my DIY 48V battery](https://github.com/dalathegreat/Battery-Emulator/wiki/Battery:-Daly-SmartBMS)
I have yet to test using the 12V supplied through the sub-d9 connector and/or use the sub-d9 UART rather than the RS485 connection.

## Credits
Some of the deye specific esphome code was originally taken from [this photovoltaikforum post](https://www.photovoltaikforum.com/thread/191631-fernbedienung-von-deye-5k-wechselrichtern-%C3%BCber-modbus-home-assistant/?postID=3090347#post3090347), however many missing registers were added and the (for me) unused time scheduling was removed.

Even though I do not speak Czech, I was able to find a half-chinese/half-english documentation of all modbus registers in [this forum thread](https://forum.mypower.cz/viewtopic.php?t=6926&start=20)

The Eastron SDM230 registers are officially documented [here](https://eastroneurope.com/images/uploads/products/protocol/SDM230-MODBUS_Protocol.pdf)
