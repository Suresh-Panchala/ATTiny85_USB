# ATTiny85_USB
This is about AVR based ATTiny85 Microcontroller , This repository contains the resources to programming / flashing ATTiny85 with USB_CDC 

**Installing Digikey  Bootloader using Arduino UNO**

<b>1. Connection Diagram</b>
                                          


![bootloader](https://github.com/Suresh-Panchala/ATTiny85_USB/assets/40498897/465228de-bc91-406a-9707-d0d684aa36e4)

<b>2. Pinout</b>
  
<table>
  <tr>
    <th>ARDUINO UNO PIN</th>
    <th>ATTiny85 PIN</th>
  </tr>
  <tr>
    <td>VCC</td>
    <td>5V</td>
  </tr>
   <tr>
    <td>GND</td>
    <td>GND</td>
  </tr>
   <tr>
    <td>13</td>
    <td>PIN 2</td>
  </tr>
   <tr>
    <td>12</td>
    <td>PIN 1</td>
  </tr>
   <tr>
    <td>11</td>
    <td>PIN 0</td>
  </tr>
   <tr>
    <td>10</td>
    <td>RESET</td>
  </tr>
</table>


Now Create a file without Extension and Rename it as **"Burn_AT85_bootloader.bat"** 

"%~dp0\hardware\tools\avr/bin/avrdude" -C"%~dp0\hardware\tools\avr/etc/avrdude.conf" -v -pattiny85 -cstk500v1 -PCOM5 -b19200 -Uflash:w:"%~dp0\ATtiny85.hex":i -U lfuse:w:0xe1:m -U hfuse:w:0xdd:m -U efuse:w:0xfe:m
@pause

copy the above text into the file  **"Burn_AT85_bootloader.bat"**  and change the COM port number "PCOM5" with whatever COM port number your Uno is connected to.

Now move the edited "Burn_AT85_bootloader.bat" and "ATtiny85.hex" files into the Arduino IDE root folder (C:\Program Files (x86)\Arduino).

After that, right-click on "Burn_AT85_bootloader.bat" and select "Run as Admin". It takes approx 5 to 6 seconds to flash the boot-loader. If all went well, you should receive this message "AVRdude done. Thank you. Press any key to continue...". 


<b>3. Schematic</b>
![Schematic](https://github.com/Suresh-Panchala/ATTiny85_USB/assets/40498897/96226e4e-9f74-4526-a335-b63d2d74f7e3)


Open Digistump Driver Folder and click on the “DPinst64.exe” application to install the drivers.


<b>4. Programming </b>
</br>
<b>Setting up Arduino IDE to Program ATttiny85</b> </br>
To program the ATtiny85 Board with Arduino IDE, first, we need to add the Digispark board Support to Arduino IDE. For that, go to File > Preferences and add the below link in the Additional Boards Manager URLs and click ‘OK.’

http://digistump.com/package_digistump_index.json

image

After that, go to tools > Board > Board Manager and search for ‘Digistump AVR’ and install the latest version.


image

After installing it, now you would be able to see a new entry in the Board menu titled 'Digispark'.

image

Now, go to file > Examples > Basics and open the Blink example.

image

Change the pin number on there from LED_BUILTIN to 0.

image

Now go back to Tools -> Board and select the “Digispark (Default – 16mhz)” board. Then click on the upload button in Arduino IDE.

Note: Connect the ATtiny85 board to the computer, only when the Arduino IDE displays a message saying “Plugin device now”.

Once the code is uploaded, the LED connected to ATtiny85 should start blinking.


