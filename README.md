# WaveShare-RP2040-Touch-LCD-1.28

I am attempting to get the AttitudeEngine quaternion out of the QMI8658 IMU on the board. 
So far I am unseccessful. Below are my findings.

I am able to read the register where the quaternion is supposed to be: 

| reg | value | definition |
|:----------|:---------|:---------|
| 73 | 0 | quat W
| 74 | 64 |
| 75 | 0 | quat X
| 76 | 0 |
| 77 | 0 | quat Y
| 78 | 0 |
| 79 | 0 | quat Z
| 80 | 0 |
| 81 | 0 | velo x
| 82 | 0 |
| 83 | 0 |velo y
| 84 | 0 |
| 85 | 0 | velo z
| 86 | 0 |
| 87 | 60 | AE reg 1
| 88 | 0 | AE reg2

Register 87, AE Reg 1, shows 0 at rest but shows errors when violently shaken. The accelerometer and gyro values are showing with no issues.
I can read Status0 (register 46) to display 0 or 8 (`0b00001000`) which means it shows the proper bit (bit 3 sDA) when an AE value is available
I also see the timestamp incrementing as expected.

But Reg 74 always show 64 ( `0b01000000` ) no matter what and all other quaternion registers constantly show 0... I don't understand.

My next step is to check if MoD (Motion on Demand) is able to get the AE values...
