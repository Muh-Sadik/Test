g++ src/main.cpp src/ball_contact_count.cpp src/contact_detector.cpp src/tempo.cpp src/ALSACapture.cpp -o tempovolume -Iinclude -lfftw3f -lportaudio -lasound
# Racket Rhythm - sudo raspi-config
Introducing Racket Rhythm: an engaging ping pong experience where gameplay consistency is driven by music. Players maintain rallies to keep the music flowing, with each hit shaping the rhythm. Music tempo adjusts based on gameplay speed, creates a real-time system which offers a dynamic challenge for all skill levels. Experience the fusion of ping pong and rhythm in Racket Rhythm!

Instagram: https://www.instagram.com/racket.rhythm/

# Key Features
* Music-driven gameplay.
* Targets amateur players improving on consistency.
* Dynamic tempo adjustments for players of all levels.

# Hardware Setup
Adrafruit I2S MEMs Microphone breakout board-SPH0645 was used in this setup. 
Microphone breakout board documentation can be found here: [Adafruit I2S MEMS Microphone Breakout](https://cdn-learn.adafruit.com/downloads/pdf/adafruit-i2s-mems-microphone-breakout.pdf), and [SPH0645LM4H-B Rev C Datasheet](https://mm.digikey.com/Volume0/opasdata/d220001/medias/docus/908/SPH0645LM4H-B.pdf). GPIO pins connection are as follows:

```
Mic - RPi
---------
VCC - 3.3v
Gnd – Gnd
BCLK - BCM 18 (pin 12)
DOUT - BCM 20 (pin 38)
LRCL - BCM 19 (pin 35)
SEL  - Mono: no connection needed
     - Stero: right channel 3.3v, left channel Gnd
```

# Software Setup
**I2S Configuration:**  
To enable I2S on Raspberry Pi some modifications are needed:

* Uncomment ```#dtparam=i2s=on``` in ``` sudo nano /boot/firmware/config.txt ```
* Add to a new line ``` dtoverlay=i2s-mmap  ``` and ``` dtoverlay=googlevoicehat-soundcard  ``` This sets up the I2S mapping and activates the I2S sound card overlay.
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
  
* Install Alsa library:
```
$ sudo apt install libasound2-dev
$ sudo apt-get install alsa-utils sox
 ```
* Install PortAudio library: ``` sudo apt-get install portaudio19-dev ```
* Install SoundTouch library: ``` sudo apt install libsoundtouch-dev ```
* Install FFTW library: ``` sudo apt-get install libfftw3-dev ```
* Install PulseAudio library: ``` sudo apt install pulseaudio ```

**Test the Microphone:**
 
* Use this command: ```arecord -f cd -r 44100 -c 1 -D plughw:1,0 -v recording.wav``` with "-v" used to display detailed information about the audio capture process or ```arecord -f cd -r 44100 -c 1 -D plughw:1,0 recording.wav``` Replace "plughw:0,0" with the appropriate device name for your setup based on the output of the aplay -l command.
* For mono system, use ```arecord -c 1 -r 48000 -f S32_LE -t wav -v filename.wav ``` or ``` Mono: arecord -f S32_LE -r 8000 -c 1 filename.wav  ```
* To play the file, use ``` Aplay filename.wav  ```  

# References

 * Alsa library
 * PortAudio library
 * PulseAudio library
 * SoundTouch library
 * FFTW  library
  


### To be added later
Use the alsamixer command to configure ALSA settings and adjust microphone levels, this allows you to control the input volume and other audio settings.  
Run alsamixer from the terminal and use the arrow keys to navigate and adjust the settings.  
*Try this recording command: ```arecord -D plughw:1 -f cd test.wav``` what is the differenec from the ones we used before?  
*Add the data shett page - important - chrome-extension://efaidnbmnnnibpcajpcglclefindmkaj/https://mm.digikey.com/Volume0/opasdata/d220001/medias/docus/908/SPH0645LM4H-B.pdf

* Adafruit link: https://www.digikey.co.uk/en/products/detail/adafruit-industries-llc/3421/6691114?utm_adgroup=&utm_term=&productid=6691114&utm_content=&gad_source=1
OR
https://www.adafruit.com/product/3421

g++ -o D D.cpp -lfftw3f -lportaudio -L/path/to/fftw/library/directory  

* 3 files and main excute command: g++  main.cpp audio_processor.cpp -o class -lfftw3f -lportaudio -L/path/to/fftw/library/directory

 
<div style="text-align:center">
  <img src="https://github.com/Muh-Sadik/Test/assets/157655580/a22e043b-b515-43f9-b24f-d72ecf842bb3" alt="QR Code">
</div>



![Instagram_qr-code](https://github.com/Muh-Sadik/Test/assets/157655580/a22e043b-b515-43f9-b24f-d72ecf842bb3)


