# Debian Configuration of SD Card Image
## Login 
Username: debian <br>
Password: temppwd

## Global Soundcard Configuration
The required kernel modules will be loaded automatically at boot time (see /etc/rc.local).<br>
The global ALSA configuration /etc/asound.conf contains routings to interact with single ADCs and DACs (ADC1 - ADC2, DAC1 - DAC4)

## Soundcard Control
The multichannel soundcard can be controlled with the ALSA tools "alsamixer" or "amixer".
alsamixer has a dialog based GUI and is simpler, but amixer is more detailed.
The soundcard offers different playback de-emphasis modes, ADC high pass filter configuration and volume controls for single ADCs and DACs.

## Automatic Evaluation
The scripts for automatic evaluation of the audio system are located in /home/debian/automated_test.
The results will be saved in /home/debian/automated_test/results.
See [Evaluation_Script.md](https://github.com/ctag-fh-kiel/ctag-face-2-4/blob/master/docs/Evaluation_Script.md) for more details.

## Demo Surround-Delay Audio Effect
The Surround-Delay effect can be executed by running the following command from the home directory of user "debian":
```bash
./delay.sh
```
