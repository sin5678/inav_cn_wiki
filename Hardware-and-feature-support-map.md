## Hardware support map ##

This is default, if you download and compile your own firmware you can example add NAZA gps if you example remove ublox gps. 

| Feature       | NAZE | CC3D | CC3D OPBL | RMDO | SPARKY | SP RACING F3 | SP RACING F3EVO | FURY F3 | RC EXPLORER F3 |       COLIBRI RACE | ANYFC | REVO | BLUEJAY F4 |
|---------------|:----:|:----:|:---------:|:----:|:------:|:----------:|:-------------:|:------:|:------------:|:------------:|:-----:|:----:|:----------|
| GYRO MPU3050  | X    |      |           |      |        |            |               |        |              |              |       |      |           |
| GYRO MPU6000  |      | X    | X         |      |        |            |               | X      | X            |              | X     | X    |           |
| GYRO MPU6050  | X    |      |           | X    | X      | X          |               |        |              |              |       |      |           |
| GYRO MPU6500  | X    |      |           |      |        |            | X             | X      |              | X            |       |      | X         |
|               |      |      |           |      |        |            |               |        |              |              |       |      |           |
| ACC ADXL345   | X    |      |           |      |        |            |               |        |              |              |       |      |           |
| ACC MPU6000   | X    | X    | X         |      |        |            |               | X      | X            |              | X     | X    |           |
| ACC MPU6050   | X    |      |           | X    | X      | X          |               |        |              |              |       |      |           |
| ACC MPU6500   | X    |      |           |      |        |            | X             | X      |              | X            |       |      | X         |
|               |      |      |           |      |        |            |               |        |              |              |       |      |           |
| BARO MS5611   | X    |      |           |      | X      | X          | X             | X      | X            | X            | X     | X    | X         |
| BARO BMP085   | X    | X    | X         |      |        | X          |               |        |              |              |       |      | X         |
| BARO BMP280   | X    | X    | X         | X    | X      | X          | X             | X      |              |              |       |      | X         |
|               |      |      |           |      |        |            |               |        |              |              |       |      |           |
| MAG HMC5883   | X    | X    | X         | X    | X      | X          | X             | X      | X            | X            | X     | X    | X         |
| MAG AK8963    |      |      |           | X    |        |            | X             |        |              |              |       |      | X         |
| MAG AK8975    |      |      |           | X    | X      | X          |               | X      | X            | X            |       |      | X         |
| MAG MAG3110   |      |      |           | X    | X      | X          |               | X      |              |              |       |      | X         |
|               |      |      |           |      |        |            |               |        |              |              |       |      |           |
| GPS NMEA      |      |      |           | X    | X      | X          | X             | X      | X            | X            | X     | X    | X         |
| GPS UBLOX     | X    | X    | X         | X    | X      | X          | X             | X      | X            | X            | X     | X    | X         |
| GPS I2C       |      |      |           | X    | X      | X          | X             | X      | X            | X            | X     | X    | X         |
| GPS NAZA      |      |      |           |      | X      | X          | X             | X      | X            | X            | X     | X    | X         |
|               |      |      |           |      |        |            |               |        |              |              |       |      |           |
| Telem FrSky   | X    |      |           | X    | X      | X          | X             | X      | X            | X            | X     | X    | X         |
| Telem HOTT    |      |      |           |      | X      | X          | X             | X      | X            | X            | X     | X    | X         |
| Telem S.Port  |      |      |           |      | X      | X          | X             | X      | X            | X            | X     | X    | X         |
| Telem LTM     | X    | X    | X         | X    | X      | X          | X             | X      | X            | X            | X     | X    | X         |
| Telem MAVLink |      |      |           |      | X      | X          | X             | X      | X            | X            | X     | X    | X         |
|               |      |      |           |      |        |            |               |        |              |              |       |      |           |
| LED STRIP     |      |      |           | X    | X      | X          | X             | X      | X            | X            | X     | X    | X         |
|               |      |      |           |      |        |            |               |        |              |              |       |      |           |
| BLHeli PT     |      |      |           | X    | X      | X          | X             | X      | X            | X            | X     | X    | X         |
|               |      |      |           |      |        |            |               |        |              |              |       |      |           |
| SERIAL RX     | X    | X    |           | X    | X      | X          | X             | X      | X            | X            | X     | X    | X         |
| MSP RX        |      |      |           | X    | X      | X          | X             | X      | X            | X            | X     | X    | X         |
| BLACKBOX      | X    | X    |           | X    | X      | X          | X             | X      | X            | X            | X     | X    | X         |
|               |      |      |           |      |        |            |               |        |              |              |       |      |           |
| SONAR         |     |      |           | X    |       | X          |               | X      | X            | X            | X     | X    | X         |
