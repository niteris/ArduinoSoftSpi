# ArduinoSoftSpi
Soft Spi for the Arduino. This is useful for those trying to read from an sd card while trying to write an APA102 led strip on the Teensy 3.1. Other platforms are likely supported but haven't been verified with this codebase.

This solution addresses a major pain point for LED artists that are trying to run video from an SD card on a Teensy 3.1. This soft spi library is estimated to have 30 frame per second performance with 14 meters of 144 pixel density led strips.

Usage:
void spi_send(uint8_t data);

This will 

This library initializes on first run.

Recommended hardware/software stack.

Recommended Hardware:
  Teensy 3.1
  Adafruit 5v Ready SD Card Breakout
  APA102 leds
  
Recommended Software
  SdFat library

Example - paint one pixel violet:
      spi_send(0xff);  // control byte.
      spi_send(0x00);  // green
      spi_send(0xff);  // blue
      spi_send(0xff);  // red
      
      // Four zeros triggers color latch in the pixel.
      spi_send(0);
      spi_send(0);
      spi_send(0);
      spi_send(0);
