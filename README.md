# Racket Rhythm
Introducing Racket Rhythm: an engaging ping pong experience where gameplay consistency is driven by music. Players maintain rallies to keep the music flowing, with each hit shaping the rhythm. Music tempo adjusts based on gameplay speed, creates a real-time system which offers a dynamic challenge for all skill levels. Experience the fusion of ping pong and rhythm in Racket Rhythm!

Instagram: https://www.instagram.com/racket.rhythm/

# Key Features
* Music-driven gameplay.
* Targets amateur players improving on consistency.
* Dynamic tempo adjustments for players of all levels.

# Hardware Setup
i2s Configuration

# Kernel Compiling
Paul provides some explaination about installing the proper gcc compiler. I didnt have any propblems with this.

* First update and install necessary dependencies:
  $ sudo apt-get update.
  $ sudo rpi-update.
  $ gcc --version.
  gcc (Raspbian 4.9.2-10) 4.9.2
  
* mics dependencies that needed to be installed
  $ sudo apt-get install bc
  $ sudo apt-get install libncurses5-dev
  
* just for good measure
  $ sudo apt-get update
  $ sudo rpi-update

* Get the kernel source and compile. This takes a very long time on an RPi. I believe there are ways of doing this on a local machine but I didnt try. I would recommend installing the application sudo apt-get install screen.
  $ sudo wget https://raw.githubusercontent.com/notro/rpi-source/master/rpi-source -O /usr/bin/rpi-source
  $ sudo chmod +x /usr/bin/rpi-source
  $ /usr/bin/rpi-source -q --tag-update
  $ rpi-source
