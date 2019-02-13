# Liquid Crystal over I2C Library for Arduino

This library allows an Arduino-compatible board (including ESP8266/ESP32) to control Liquid Crystal Displays (LCDs) based on the Hitachi HD44780 (or a compatible) chipset, using the widely-available I2C 'backpack' adaptor.

This modification is intended to provide a minimal deviation from the original Arduino LiquidCrystal library, providing a near drop-in replacement for existing code with few modifications.

To use in place of an existing LiquidCrystal implementation, simply replace the following lines of code:

`#include <LiquidCrystal.h>` with `#include <LiquidCrystalOverI2C.h>`, and  
`LiquidCrystal lcd(rs, en, d4, d5, d6, d7);` with `LiquidCrystal lcd(i2c_addr);` (usually 0x27).

**LCD backlight control** can be controlled through the `lcd.backlight()` and `lcd.noBacklight()` functions as required.

**VFD-specific brightness control** has also been implemented through the `lcd.setBrightness(value)` function, where brightness is a 2-bit value (0 is brightest, and 3 is dimmest.)  This function will have no effect on traditional LCDs.

In testing, I've found this implementation to be aroud 63% faster than other comparable implementations; this is particularly useful for displays such as VFDs which feature much faster response times than traditional LCDs.

## License

Copyright (C) 2006-2008 Hans-Christoph Steiner. All rights reserved.  
Copyright (C) 2010 Arduino LLC. All right reserved.

Modification for I2C backpack (C) 2019 Chris Stone.

This library is free software; you can redistribute it and/or
modify it under the terms of the GNU Lesser General Public
License as published by the Free Software Foundation; either
version 2.1 of the License, or (at your option) any later version.

This library is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
Lesser General Public License for more details.

You should have received a copy of the GNU Lesser General Public
License along with this library; if not, write to the Free Software
Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA 02110-1301 USA
