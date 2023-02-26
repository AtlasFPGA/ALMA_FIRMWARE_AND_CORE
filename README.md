# ALMA_FRIMWARE_AND_CORE
The core and firmware that uses nowadays the PI-PICO family for use in ATLAS I/O Board is located in GITLAB.

You can donwload the ALMA FIRMWARE HERE:

https://gitlab.com/fpga-boards/alma-firmware


FPGA RBF Loader
Software to configure an FPGA using JTAG via the GPIO pins of a microcontroller. Currenly the main board supported is the Raspberry Pi Pico. Also, the ESP32doit-devkit is planned to be supported. At the begining it was developed targeting a Maix Bit SBC but this board is no more compatible, as this project was migrated to LVGL v8.x, not available for the Maix Bit.

Building and Installing
This source is built using PlatformIO IDE. Library dependencies are automatically installed by this IDE as they are listed in the project's .ini file.
Using PlatformIO IDE simplifies the installation as the firmware is flashed after being built.

Build using the command line
It is also possible to use the command line to build and upload the firmware to the microcontroller. For instance, to create the binary for the Pi Pico in its HDMI display version, the command is the following:
pio run -e pico -c platformio.ini --target upload
The -e parameter selects the build environment from those listed in the platfom.ini file. Currently, these are the avaialble options:



Environment
Description
Status




pico
Builds a firmware for the Raspberry Pi Pico to be used with an HDMI monitor
working


pico-tft
Builds a firmware for the Raspberry Pi Pico to be used with an SPI TFT display
working


esp32doit-devkit-v1
Builds a firmware for the Esp32doit devkitto be used with an   HDMI monitor
not working


esp32doit-devkit-v1-tft
Builds a firmware for the Esp32doit devkitto be used with an SPI TFT display
not working




FPGA Configuration through JTAG
This project has been designed having the ATLAS carrier board in mind. This carrier board was designed to mount a Raspberry Pi for configuring the FPGA so, an adaptor PCB is needed to map the Raspberry GPIO pins to other boards such as the Raspberry Pi Pico or an ESP32. All the information about the adaptor for using the Pico with the Atlas AT is available in this repository.
JTAG pinout using a Trenz CYC1000



Key
Raspberry Pi Pico
Esp32doit-devkit
Description
FPGA GPIO




TMS
5
26
Test Mode Select
7


TCK
2
32
Test Clock
11


TDI
4
25
Test Data In
15


TDO
3
33
Test Data Out
13





Usage
The configuration file to be sent to the FPGA could be selected usint a serial terminal or the GUI (through HDMI or TFT)

Command Line
Currently you need to connect to the microcontroller using a serial USB cable (e.g /dev/ttyUSB0 in linux). The device is set to 115000 bps.
programrbf msx_atlas.rbf 18 19 20 21

GUI
It is possible to use an HDMI monitor plugged to the Atlas I/O board or to connect a TFT display to the adapter board. In any case, a file system browser will be shown. Only files with RBF extension and directories are visible.
A joystick could be used to browse through the files. Moving up and down the stick the focus will be changed and pressing the button A the file will be sent to the FPGA or a directory will be opened. Another possibility is to use the MCU user button to navigate and select files. A normal press moves the focus to the next item while a long press opens that item, entering into a folder if is another directory or sending the file to the FPGA if is an RBF file.


Credits and acknowledgments
This software is powered by Open-Source Software and reuses code from other projects.
A special thanks to:

Carlos Palmero for the original CYC1000 source code of programrbf used in the Iniciativa Atlas project.
Marcus Andrade for his inspiring code: programrbf



Legal Notices
This project is licensed under the BSD 3-Clause "New" or "Revised" License.
The authors, contributors or any of the maintainers of this project are in no way associated with or endorsed by RISC-V®, Intel®, Altera®, Sipeed® or any other company not implicit indicated. All other brands or product names are the property of their respective holders.
