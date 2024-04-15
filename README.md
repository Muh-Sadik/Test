
# Racket Rhythm - sudo raspi-config
# Racket Rhythm
Introducing Racket Rhythm: an engaging ping pong experience where gameplay consistency is driven by music. Players maintain rallies to keep the music flowing, with each hit shaping the rhythm. Music Sound adjusts based on gameplay speed, creates a real-time system which offers a dynamic challenge for all skill levels. Experience the fusion of ping pong and rhythm in Racket Rhythm!

Instagram: https://www.instagram.com/racket.rhythm/

# Key Features
* Music-driven gameplay.
* Targets amateur players improving on consistency.
* Dynamic Sound adjustments for players of all levels.

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
 

* important commmands:
g++ src/main.cpp src/ball_contact_count.cpp src/contact_detector.cpp src/tempo.cpp src/ALSACapture.cpp -o RacketRhythm_V1.0 -Iinclude -lfftw3f -lportaudio -lasound

last for file plying:sudo apt-get install libsndfile1-dev
g++ src/main.cpp src/ball_contact_count.cpp src/contact_detector.cpp src/tempo.cpp src/ALSACapture.cpp src/game_start.cpp -o game_startsound -Iinclude -lfftw3f -lportaudio -lasound -lsndfile

for tempo: g++ main.cpp ball_contact_count.cpp contact_detector.cpp tempo.cpp ALSACapture_Tempomusic.cpp -o tempo -I /usr/include/soundtouch/ -L /usr/lib/arm-linux-gnueabihf/ -lfftw3f -lportaudio -lasound -lSoundTouch
 
