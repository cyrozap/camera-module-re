The camera module is built by [LGIT (LG Innotek)][lgit]. Dimensions are 27.15
mm x 10.05 mm.

The sensor is a Sony IMX135.

I2C clock frequency: 400 kHz

- Burst at power-on.
- Burst at OS boot/driver load.
- Stream while camera app open (AF/OIS).

Addresses:

- read/write: 0x10 (IMX135)
- read/write: 0x24
- read/write: 0x50
- write: 0x0C

On boot, the phone reads exactly 0x900 bytes from the device at address 0x50.
The data format is as follows:

- 12 bytes of unknown data
- 4 17x13 (WxH) blocks of what appear to be circular gradients, with the
  higher values in the center and lower values towards the edges.
- 10 bytes of unknown data.
- Another block of 4 17x13 circular gradients.
- 514 bytes of unknown data.

This may be an EEPROM, though it's unknown why it's accessed via the main
camera I2C bus. Maybe it's sensor calibration data?


[lgit]: https://web.archive.org/web/20171010113933/http://www.lginnotek.com/products/mobile_camera.jsp
