# Quick Start Guide for SD Card Image 
## SD Card Preparation
1. Download [Debian Wheezy SD card image](https://drive.google.com/file/d/0B2goLqs_HZ3QLUpqd3NZS1FBOTQ/view?usp=sharing)
2. Install Debian image on SD card (see [Raspberry Pi Guide](https://www.raspberrypi.org/documentation/installation/installing-images/README.md))

## Debian Configuration of SD Card Image
### Login 
Username: debian <br>
Password: temppwd

### Global Soundcard Configuration
The required kernel modules will be loaded automatically at boot time (see /etc/rc.local).<br>
By default the soundcard is configured to use 4 input channels and 8 output channels.<br>
If a higher sampling rate of 192 kHz is needed, the soundcard can be configured to use only 4 output channels.<br>
(Change line 22 in /etc/rc.local<br>**sh -c "echo 'BBB-AD193X-8TDM' > /sys/devices/platform/bone_capemgr/slots"** to<br>**sh -c "echo 'BBB-AD193X-4TDM' > /sys/devices/platform/bone_capemgr/slots"**)<br>
The global ALSA configuration /etc/asound.conf contains routings to interact with single ADCs and DACs (ADC1 - ADC2, DAC1 - DAC4)

### Soundcard Control
The multichannel soundcard can be controlled with the ALSA tools "alsamixer" or "amixer".
alsamixer has a dialog based GUI and is simpler, but amixer is more detailed.
The soundcard offers different playback de-emphasis modes, ADC high pass filter configuration and volume controls for single ADCs and DACs.

### Automatic Evaluation
The scripts for the automatic evaluation of the audio system are located in /home/debian/automated_test.
The results will be saved in /home/debian/automated_test/results.
See the [Manual for Automatic Evaluation](https://github.com/ctag-fh-kiel/ctag-face-2-4/blob/master/docs/Automatic_Evaluation_Manual.md) for more details.

### Demo Surround-Delay Audio Effect
The Surround-Delay effect can be executed by running the following command from the home directory of user "debian":
```bash
./delay.sh
```
