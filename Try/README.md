# Setting up Instructions
1-Clone the Racket Rhythm repository to your local machine and use the last version contained in RacketRhythm_V1.0 folder to run needed commands. 
Note: src file under the master branch was used for development and initial testing and debugging for systems different devices.
2-Hardware Setup:
-Connect Adrafruit I2S MEMs Microphone breakout boards to Raspberry Pi GPIO pins according to provided specifications in the main README file.
-Use USB ports to connect the audio sound card then make sure to plug the speakers to the output channel of the audio sound card.
-For audio input, use any 3.5mm to 3.5mm audio cable to connect to your PC or mobilephone.
3-Software Setup:
Configure I2S settings on Raspberry Pi by editing /boot/firmware/config.txt and /etc/modules.
Compile kernel and install necessary dependencies.
4-Library Configuration:
Install required libraries such as Alsa, PortAudio, and FFTW.
5-Microphone Testing:
Use arecord command to record audio and aplay command to play back the recorded file for microphone testing.
6-Adjust the ID's of PLAYBACK Hardware Devices:  
Use aplay -l to check the list of connected hardware devices and change the below device numbers accordingly.
7-Compile/CMake:
Compile the RacketRhythm_V1.0 code using CMakeLists or any appropriate compiler.
8-Choose a Song:
Select your favourite song from Spotify or YouTube.
9-Run:
Run the compiled code to start the Racket Rhythm game experience.





*Start your System: 
Run the system with all features using by 
 

 






# Racket Rhythm
Introducing Racket Rhythm: an engaging ping pong experience where gameplay consistency is driven by music. Players maintain rallies to keep the music flowing, with each hit shaping the rhythm. Music Sound adjusts based on gameplay speed, creates a real-time system which offers a dynamic challenge for all skill levels. Experience the fusion of ping pong and rhythm in Racket Rhythm!

Instagram: https://www.instagram.com/racket.rhythm/

# Key Features
* Music-driven gameplay.
* Targets amateur players improving on consistency.
* Dynamic Sound adjustments for players of all levels.

# Setup Instructions
**Hardware Requirements:**
 * Raspberry Pi
 * Adrafruit I2S MEMs Microphone breakout board - SPH0645 x2
 * Audio Sound Card - AU-MMSA
 * Speakers
 * 3.5mm to 3.5mm Audio Cable

**Software Requirements:**
 * C++ for Raspberry Pi control
 
**Hardware Setup:**

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

**Software Setup:**
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
