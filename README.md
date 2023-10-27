# Pi Pico Template Instructions

First clone this repo
```
git clone
```

Then cd into the repo and copy over the pico_sdk_import.cmake file:
```
cd pi-pico-template
cp ~/pico/pico-sdk/pico_sdk_import.cmake ./
```

Next create a build directory and go to it:
```
mkdir build
cd build
```

build the template program
```
cmake ../
make 
```

Plug in your pico board to your computer while holding down the `bootsel` button, then flash your program onto the pico. 
```
cp ./template.uf2 /media/joey/RPI-RP2
```

The LED should be blinking on the pico now!

To view the serial output you can use any serial monitor. I like minicom on Ubuntu:
to install it (if you need to )
```
sudo apt install minicom
```
to view the pico print statements over usb:
```
minicom -b 115200 -o -D /dev/ttyACM0
```
*note you may need to use sudo on the above command*

