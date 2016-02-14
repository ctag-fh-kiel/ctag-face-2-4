# Manual for Automatic Evaluation

## Test Prerequisites
+ ADC1 needs to be connected with DAC1 (loopback)
+ GNU Octave Version>3.8 (already installed on SD card image)

## Description
The automatic evaluation is made up of 4 single tests for:

1. Latency (took from [alsa-lib](http://www.alsa-project.org/alsa-doc/alsa-lib/_2test_2latency_8c-example.html))
2. THD, THD+N, DNR
3. Crosstalk
4. Frequency Response

The test scripts and sample files are located in the directory **/home/debian/automated_test** on the SD card image.<br>
The automatic evaluation can be executed by running
```bash
automated_test.sh
```
from the home directory of user "debian".

## BASH script parameters
1. ALSA Playback Device (e.g. hw:0)
2. ALSA Capture Device
3. Name of soundcard to be tested (will be used in spectrum plots)
4. *Name of single test (latency, thd, crosstalk, frequency-response) (optional)*

