# DAW-1-RGB-Mod
Please do not skip the introduction. This guide will explain how to RGB mod your DAW-1 Sony Trinitron Chassis. This will use a variation of the RGB mux method with automatic switching for all DAW-1 Sony Trinitron Chassis found in the KV-13VM40, KV-13VM41, KV-13VM42, KV-13VM43, KV-20VM40, KV-20VS40, KV-20VM42, KV-20VS42.
## Introduction
### Hardware Rundown
For this guide I will be using the KV-13VM42, a 13" mono-composite trinitron that shares it's impressive trinitron tube with its more popular and well documented cousin, the KV-13M42 (lacking the V for VCR). Based on the Service manual (linked below) all areas of modification share a common motherboard throughout all DAW-1 Chassis listed. My KV-13VM42 is mono audio, and is physically missing some components from the motherboard. I believe the 20" models are stereo and will be able to retain stero sound natively. If mono audio is an issue on the 13", there are ways to modify the cable to have rca jacks to hook into an external audio unit and retain stero. There could also be an option to re-add the circuitry components to the motherboard, but I was content with mono. Such modifications can be explored in a future guide and are out of scope for this guide.
### Connector Disclaimer
I will be utilizing a scart connector for this mod. __This is important to make automatic switching/blanking work!__ This mod uses pin 16 on a scart connector as a 5V input __(needs a voltage drop)__ from the console to trigger the display of the RGB without an external switch. So please do not make the mistake I did and order BNC connectors.
### CRT dissasembly Disclaimer
IF you are going to attempt this modification, please keep in mind that this is at your own risk and it can be fatal if you get shocked by a CRT. This guide is intended for education purposes only.
That being said, here are some key safety points. Be warned, it is not all encompasing and may leave out some details. If you are not comfortable I would suggest watching most of the CRT safety videos on YouTube, reading the comments, and forming a general consensus on CRT safety.
- Unplug your TV and let it sit for a couple hours to a day. If the electric discharge circuit is operational in the TV, there should be little to no sparks when doing the next step, have it remain unplugged throughout the entire modification process.
- Using a long flathead screwdriver with an aligator clipped wire to the shaft of the screwdriver and the ground wire of the chassis. Check continuity with your multimeter from the tip of the screw driver to the chassis ground of the CRT, do this carefully and take your time. This is to make sure your discharge tool is working. Gently go under the rubber flap of the anode cap only using the screwdriver and find the metal plug. Do not touch or come close with your hands any metal surface of the screwdriver, TV, or aligator clip, only use the rubber grip. Keep your other hand behind your back. Touch the screwdriver to the anode cap terminal, it can spark so be warned. Once it sparks (or doesn't) use the grounded screwdriver to tap and discharge certain metallic elements all over the motherbaord and the tube, just to be safe. Be gentle. To wrap up, before disassembly redsicharge the terminal of the anode cap just to make sure its fully drained of electricity.
- The board should now be safe to handle, still be careful around the flyback transformer and capacitors.
### Tools/Parts Required
- Magnetic Medium/regular sized Phillips screwdriver
- Multimeter
- Soldering Station
- Solder
- Flux
- Tweezers
- Helping hands (optional)
- Fume filter (optional)
- Silicon work mat (optional)
- 280 ohm SMD resistor
- 75 ohm SMD resistor
- __ADVANCED USERS__ This mod can also work with 330 ohm and 85 ohm resistors _and more combos_ instead. Use [This Voltage Division Calculator](https://www.digikey.com/en/resources/conversion-calculators/conversion-calculator-voltage-divider) as a guide to find values of resistors that will work. The starting voltage is 3.4V and your goal is end up with around 0.7V.
### Service Manual
[Here is the online link to the PDF service manual](https://elektrotanya.com/sony_kv-13vm40_41_42_43_kv-20vm40_42_kv-20vs40_chassis_daw-1.pdf/download.html#dl)
- This service manual is not searchable but otherwise is realively straightforward, any changes between the 20" and 13" models are clearly labeled.
### VCR Disclaimer
- These units are all VCR combos from what I can tell. When re-assembling the unit, before sliding the chassis in, hold up the VCR door and then slide the chassis in, there should be no resistance or snaps when doing so. Refer to the service manual if you are confused. You may have to hold it in the "Right spot" for it to go in. If you place the chassis without doing this, the door will not open all the way and your tapes __WILL__ get stuck.
## The Mod
### Disassembly
- Make sure everything is discharged and your TV is unplugged.
- Don't forget the power cord holder screw, its smaller than the other 6 shell screws.
- After you slide the back cover off, Unplug everything connected to the motherboard and to the chassis, and everything between the neck board and the chassis.  You should be able to remove the neck board PCB easily after carefully getting the black goop off the connector.
- When everything is unplugged, two chassis screws will hold the silding double decker tray to the front of the TV shell. They are the same type of screws as the ones holding the shell together. Remove them and slide the chassis out. If a cable is snagging remove it, and do not forget about the little speaker connectors towards where those two chassis screws are.
- Two smaller screws hold the top layer of the double decker board assembly. Once removed you can seperate the top tray from the bottom tray.
- No work will be done on the top tray so you can set it aside. The bottom tray has the jungle chip and associated video components.
- Remove the outer shielding on the bottom tray its held together with screws on the top and sides.
- remove the little plastic cable holders on the sides of the walls by pinching the tabs and pulling the horns on the other side.
- Unplug the front button board from the bottom tray board if you haven't already.
- Remove the shielding from the VCR unit (two screws) Then remove the screw holding the front of the vcr in (There should be a hole at the top for a screwdriver to go through)
- Unplug the three VCR connectors (pull on the orange ribbon cable towards the base of the ribbon and be gentle)
- Pull the VCR off once you have confirmed all 3 screws and connectors are off.
- __READ__ I still forget about these next screws all the time. There are two tiny screws holding the motherboard to the tray towards the button board. Unscrew those.
- Push in the tabs on the tray and push the motherboard up. Go from one side and work your way to the other gently lifting the board. In my experience pushing in all the tabs and pulling the board out at the same time is impossible, you may need to flex the board just a smidge when going tab by tab.
- You should now be able to work on the board itself.
### The OSD RGB Circuit
The original OSD circuit consists of 

__OSD RGB > 1KR > .7V drop Diode > 1.2KR > 560R to ground > 10uF Capacitor > Jungle RGB__

The mod simplifies this circuit and utilizes the original Diode to preserve the original .7V signal strength of the RGB while not sacrificing OSD brightness to an unusable degree.

__OSD RGB > 280R > .7V drop Diode > Bridged with Solder > 75R to ground > _.7V RGB Injection_ > 10uF capacitor > Jungle RGB__

### More than you want to know about Diodes
The diodes being in place from the factory hugely benefits the results of this mod. If you aren't familiar with how diodes work, here is a rundown. Diodes allow current to flow in one direction on a circuit at the expense of dropping the voltage a fixed amount. This circuit utilized cermaic 0.7V drop diodes. The magical part about diodes is that because we have them on the circuit, it essentially prevents backflow of RGB injected signal into the resistors on the OSD line. This allows the 75R to ground to be a common termination point for both the injected RGB and the OSD RGB, meaning the Jungle IC recieves full power RGB signal and does not need to over amplify video signal. The reason the injected RGB is able to backflow into the 75R to ground is precisely becasuse the "to ground" allows current to flow through it. If this was an inline resistor, the injected RGB would ignore that resistor and flow directly to the capacitors and jungle IC without termination due to the inline diode.
### Why I think this mod method works better than others
If there was no diode, this would be a lot harder to balance because the injected RGB could intermix with existing OSD circuitry components. I believe this to be the problem with dim RGB signals and dim OSD signals. People are sacrificing voltage by balancing the entire circuit OSD+Injected RGB with using inline injected RGB resistors after a 75 ohm termination to ground in the connector. You have to remember that the OSD will now make a new circuit with this added inline resistor. I will say though, sometimes there is no choice with the constraints of the circuit. So YMMV.
