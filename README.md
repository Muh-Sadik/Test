# Racket Rhythm
Introducing Racket Rhythm: an engaging ping pong experience where gameplay consistency is driven by music. Players maintain rallies to keep the music flowing, with each hit shaping the rhythm. Music tempo adjusts based on gameplay speed, creates a real-time system which offers a dynamic challenge for all skill levels. Experience the fusion of ping pong and rhythm in Racket Rhythm!

Instagram: https://www.instagram.com/racket.rhythm/

# Key Features
* Music-driven gameplay.
* Targets amateur players improving on consistency.
* Dynamic tempo adjustments for players of all levels.

# Hardware Setup
Adrafruit I2S MEMs Microphone breakout board-SPH0645 was used in this setup. 
Microphone breakout board documentation can be found [here](https://cdn-learn.adafruit.com/downloads/pdf/adafruit-i2s-mems-microphone-breakout.pdf). GPIO pins connection are as follows:

```
Mic - RPi
---------
VCC - 3.3v
Gnd – Gnd
BCLK  - BCM 18 (pin 12)
DOUT  - BCM 20 (pin 38)
LRCL  - BCM 19 (pin 35)
```

# Software Setup
**I2S Configuration:**  
To enable I2S on Raspberry Pi some modifications are needed:

* Uncomment ```#dtparam=i2s=on``` in ``` sudo nano /boot/firmware/config.txt ```
* Add ``` dtoverlay=i2s-mmap  ``` and ``` dtoverlay=googlevoicehat-soundcard  ``` This sets up the I2S mapping and activates the I2S sound card overlay.
* Add ``` snd-bcm2835   ``` to ``` sudo nano /etc/modules ```

**Kernel Compiling:**

* Update and install necessary dependencies:
```
$ sudo apt-get update
$ sudo rpi-update

# Check your Raspbian version:
$ gcc --version
gcc (Raspbian 12.2.0-14+rpi1) 12.2.0

# Mic dependencies that needed to be installed:
  $ sudo apt-get install bc
  $ sudo apt-get install libncurses5-dev
  ```

**Libraries Configuration:**
  
* Install Alsa library
```
$ sudo apt install libasound2-dev
$ sudo apt-get install alsa-utils sox
 ```
**Test the Microphone:**
 
* For mono system, use ```arecord -c 1 -r 48000 -f S32_LE -t wav -v filename.wav ``` or ``` Mono: arecord -f S32_LE -r 8000 -c 1 shaker2.wav  ```
* To play the file, use ``` Aplay filename.wav  ```


# References

 * Alsa library
 * rpi-i2s repositorie: https://github.com/nejohnson2/rpi-i2s.git

### To be added later
Use the alsamixer command to configure ALSA settings and adjust microphone levels, this allows you to control the input volume and other audio settings.  
Run alsamixer from the terminal and use the arrow keys to navigate and adjust the settings.  
*Try this recording command: ```arecord -D plughw:1 -f cd test.wav``` what is the differenec from the ones we used before?  

g++ -o D D.cpp -lfftw3f -lportaudio -L/path/to/fftw/library/directory
