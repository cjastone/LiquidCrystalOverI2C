# Liquid Crystal over I2C Library for Arduino

This library allows an Arduino board to control LiquidCrystal displays (LCDs) based on the Hitachi HD44780 (or a compatible) chipset, using the widely-available I2C backpack adaptor.

This modification represents the most minimal deviation from the original Arduino LiquidCrystal library, providing a near drop-in replacement for existing code with minimal modifications.

To use in place of an existing LiquidCrystal implementation, simply replace the following lines of code:

`#include <LiquidCrystal.h>` with `#include <LiquidCrystalOverI2C.h>`, and  
`LiquidCrystal lcd(rs, en, d4, d5, d6, d7);` with `LiquidCrystal lcd(i2c_addr);` (usually 0x27).

Additionally, any pin-based backlight control can be replaced with `lcd.backlight()` and `lcd.noBacklight()` as required.

In testing, I've found this implementation to be aroud 63% faster than other comparable implementations; this is particularly useful for displays such as VFDs with much faster refresh rates than traditional LCDs.

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
