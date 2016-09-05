CTAG face2|4 Audio Card, based on AD1938 codec
==============================================

This document includes board information, assembly guidelines, extensions and revision remarks, license and authors information.

Board information
-----------------
- 4 layer PCB including ground and power plane
- 10mil tracks offering close to 50Ohms impedance
- We used http://dirtypcbs.com/ to manufacture the board with good experiences
  - You may order it there under this shortlink http://dirtypcbs.com/view.php?share=13783&accesskey=c1dd3754f4a36b5ddce1bc031594a45b
- Part sizes on board are chosen to allow for hand-soldering 0603 as standard size for resistors etc.
- Used http://kicad-pcb.org/ for board design
- Board has 3 logical sections
  - Power supply (digital, analog)
     - Includes separate 3.3V digital supply and 3.3V + 5V analog supply
     - Includes boost converter that allows to run board on dual AA battery pack (3V input)
     - Standard input voltage at P201 should be +5V, see assembly options below
  - Codec including reset circuitry and digital I/O
  - Analog I/O
     - We checked several different single supply rail-to-rail OP Amps, where the cheap TLV272 performed pretty well, similar to the LMV722
- Codec and analog section is mainly based on Analog Devices reference design http://www.analog.com/media/en/technical-documentation/user-guides/UG-087.pdf

Assembly
-------------
- face2|4 BOM shared at Mouser
  - http://www.mouser.com/tools/projectcartsharing.aspx Access ID: 43007b9807
- Start with assembling the power supply sections
  - Several options for configuration are possible
     - A: Simplest possible, assemble only U203, U204, bypass U201 with JP201, bypass L202 with JP206, bypass L203 with JP207, assemble FB202, place JP204. Input voltage can be anything from 6-9V in this configuration.
     - B: No dedicated 3.3V digital do not assemble U202, assemble FB202, input voltage can be anything 2.4V-5V, boost converter will generate 5.5V for low-noise LDOs
     - C: With dedicated 3.3V digital supply, default in schematic, input voltage should be 5V
  - Check if power supply works by observing the LEDs
- Continue with codec, digital I/O and bias circuitry
  - Assembling only C311, C312 + JP301 is enough, using CM bias for test purposes
  - Test codec with microcontroller system, check at R602 R605 for signal output	
- Finally assemble analog section
  - May play around with some different OP amps

Extensions
-------------
- Created cape for Beagle Bone Green / Black including digital isolators to reduce noise (BBG-cape)
- Beagle Board X15 break out adapters for Hirose headers

Revisions
-------------
- face2|4
  - Rev. A 
     - Initial Revision
    - Known Bugs: -
  - Todos for next Rev.
     - Possibly simplify power supply
     - Remove option to choose bias output from codec --> simplify board
	 - Option for balanced inputs
	 - Optimize pins on P1001 to improve routing, i.e. less vias on high speed digital lines, preserve impedance
- BBG-cape
  - Rev. A 
     - Initial Revision
    - Known Bugs: 
	 - Wrong polarity on IN2 at ADC2RP ADC2RN --> results in wrong phase and sound cancellation, needs fix
- X15 adaptor
  - Rev. A
     - Initial Revision, thanks to Michael Welling for review
	 
License
-------
This work is licensed under the Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License. 
To view a copy of this license, visit http://creativecommons.org/licenses/by-nc-sa/4.0/.
Anyone re-using this design needs to attribute to authors and http://www.creative-technologies.de website.

Authors
-------
- Robert Manzke (robert.manzke@fh-kiel.de), PCB Design
- Henrik Langer (henrik.langer@student.fh-kiel.de), Component Selection, Driver Development for Beagle Bone Series