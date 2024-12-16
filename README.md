# Esphome for reading Deye/Sunsnyk Modbus Data

I am using this esphome project running on a [Lilygo T-CAN485](https://github.com/Xinyuan-LilyGO/T-CAN485) for reading metadata about my solar production.
I use a Deye SG03LP1, which is a single phase 5kW hybrid solar inverter with 48V pylontech battery compatible inverter.
It might work for other models aswell. However some sources say the three phase Deye inverters are different and might not work.
Feel free to add a mention of your model if you successfuly tested this code with it.

I connected my T-CAN485 to RJ45 pins 1 (B), 2 (A) and 3 (GND) of the "BMS485/CAN" port (top middle) of the 5 RJ45 ports located inside the inverter.
I have yet to test using the 12V supplied through the sub-d9 connector and/or use the sub-d9 UART rather than the RS485 connection.

## Credits
Some of the deye specific esphome code was originally taken from [this photovoltaikforum post](https://www.photovoltaikforum.com/thread/191631-fernbedienung-von-deye-5k-wechselrichtern-%C3%BCber-modbus-home-assistant/?postID=3090347#post3090347), however many missing registers were added and the (for me) unused time scheduling was removed.

Even though I do not speak Czech, I was able to find a half-chinese/half-english documentation of all modbus registers in [this forum thread](https://forum.mypower.cz/viewtopic.php?t=6926&start=20)
