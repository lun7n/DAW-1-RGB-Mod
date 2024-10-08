# DAW-1-RGB-Mod
This guide is in progress and is missing pictures/information. Please do not skip the introduction. This guide will explain how to RGB mod your DAW-1 Sony Trinitron Chassis. It will use a variation of the RGB mux method with automatic switching for all 13" DAW-1 Sony Trinitron Chassis found in the KV-13VM40, KV-13VM41, KV-13VM42, and KV-13VM43.
The 20" mod is theoretical and needs testing. KV-20VM40, KV-20VS40, KV-20VM42, and KV-20VS42 all have a 680-ohm to-ground resistor instead of a 560-ohm to-ground resistor in the OSD circuit.
## Introduction
### Hardware Rundown
For this guide, I will be using the KV-13VM42, a 13" mono-composite trinitron that shares its impressive trinitron tube with its more famous and well-documented cousin, the KV-13M42 (lacking the V for VCR). Based on the Service Manual (linked below), all areas of modification share a common motherboard throughout all DAW-1 Chassis listed. My KV-13VM42 is mono audio and physically missing some motherboard components. I believe the 20" models are stereo and will be able to retain stereo sound natively. If mono audio is an issue on the 13", there are ways to modify the cable to have RCA jacks hook into an external audio unit and retain stereo. There could also be an option to re-add the circuitry components to the motherboard, but I was content with mono. Such modifications can be explored in a future guide and are out of the scope of this guide.
### Connector Disclaimer
I will be utilizing a scart connector for this mod. __This is important to make automatic switching/blanking work!__ This mod uses pin 16 on a scart connector as a 5V input __(needs a voltage drop)__ from the console to trigger the display of the RGB without an external switch. So please do not make the mistake I did and order BNC connectors.
### CRT disassembly Disclaimer
If you attempt this modification, please keep in mind that you do so at your own risk, and getting shocked by a CRT can be fatal. This guide is intended for education purposes only.
That being said, here are some key safety points. Be warned, it is not all-encompassing and may leave out some details. If you are not comfortable, I would suggest watching most of the CRT safety videos on YouTube, reading the comments, and forming a general consensus on CRT safety.
Unplug your TV and let it sit for a couple of hours to a day. If the TV's electric discharge circuit is operational, there should be little to no sparks when doing the next step. Have it remain unplugged throughout the entire modification process.
- A long flathead screwdriver with an alligator-clipped wire is used to connect the shaft of the screwdriver and the ground wire of the chassis. Check continuity with your multimeter from the screwdriver's tip to the CRT's chassis ground; do this carefully and take your time. This is to make sure your discharge tool is working. Gently go under the rubber flap of the anode cap using only the screwdriver and find the metal terminal by feeling it (through the screwdriver). Do not touch or come close with your hands to any metal surface of the screwdriver, TV, or alligator clip; only use the rubber grip. Keep your other hand behind your back. Touch the screwdriver to the anode cap terminal, it can spark so be warned. Once it sparks (or doesn't), use the grounded screwdriver to tap and discharge certain metallic elements all over the motherboard and tube to be safe. Be gentle. To wrap up, discharge the terminal of the anode cap before disassembly to ensure it's fully drained of electricity.
- The board should now be safe to handle, but still be careful around the flyback transformer and capacitors.
### Tools/Parts Required
- Magnetic Medium/regular-sized Phillips screwdriver
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
- Scart connector
- Mounting screws (I chose m4x16mm self-tapping, which was slightly too big IMO, but it worked out)
- __ADVANCED USERS__ This mod can also work with 330 ohm and 85 ohm resistors _and more combos_ instead. Use [This Voltage Division Calculator](https://www.digikey.com/en/resources/conversion-calculators/conversion-calculator-voltage-divider) as a guide to find values of resistors that will work. The starting voltage is 3.4V and your goal is end up with around 0.7V.
### Service Manual
[Here is the online link to the PDF service manual](https://elektrotanya.com/sony_kv-13vm40_41_42_43_kv-20vm40_42_kv-20vs40_chassis_daw-1.pdf/download.html#dl)
This service manual is not searchable but otherwise is relatively straightforward. Any changes between the 20" and 13" models are clearly labeled.
### VCR Disclaimer
- From what I can tell, these units are all VCR combos. When re-assembling the unit, before sliding the chassis in, hold up the VCR door and slide the chassis in. There should be no resistance or snaps when doing so. Refer to the service manual if you need clarification. You may have to hold it in the "Right spot" for it to go in. If you place the chassis without doing this, the door will not open all the way, and your tapes __WILL__ get stuck.
## The Mod
### Disassembly
- Make sure everything is discharged and your TV is unplugged.
- Don't forget the power cord holder screw; it's smaller than the other 6 shell screws.
After you slide the back cover off, Unplug everything connected to the motherboard, the chassis, and everything between the neck board and the chassis. After carefully getting the black goop off the connector, you should be able to remove the neck board PCB easily.
- When everything is unplugged, two chassis screws will hold the sliding double-decker tray to the front of the TV shell. They are the same type of screws as the ones holding the shell together. Remove them and slide the chassis out. If a cable is snagging, remove it, and do not forget about the little speaker connectors towards where those two chassis screws are.
- Two smaller screws hold the top layer of the double-decker board assembly. Once removed, you can separate the top tray from the bottom tray.
No work will be done on the top tray, so you can set it aside. The bottom tray has the jungle chip and associated video components.
- Remove the outer shielding on the bottom tray. It's held together with screws on the top and sides.
- remove the little plastic cable holders on the sides of the walls by pinching the tabs and pulling the horns on the other side.
- Unplug the front button board from the bottom tray board if you haven't already done so.
- Remove the shielding from the VCR unit (two screws). Then remove the screw holding the front of the VCR in (There should be a hole at the top for a screwdriver to go through)
- Unplug the three VCR connectors (pull on the orange ribbon cable towards the base of the ribbon and be gentle)
- Pull the VCR off once you have confirmed all three screws and connectors are off.
- __READ__ I still forget about these following screws all the time. There are two tiny screws holding the motherboard to the tray towards the button board. Unscrew those.
- Push in the tabs on the tray and push the motherboard up. Go from one side and work your way to the other, gently lifting the board. In my experience, pushing in all the tabs and pulling the board out at the same time is impossible. You may need to flex the board just a smidge when going tab by tab.
- You should now be able to work on the board itself.
### The OSD RGB Circuit
The original OSD of the 13" model circuit consists of 

__OSD RGB > 1KR > .7V drop Diode > 1.2KR > 560R to ground > 10uF Capacitor > Jungle RGB__

The mod simplifies this circuit and utilizes the original Diode to preserve the RGB's original .7V signal strength without sacrificing OSD brightness to an unusable degree.

__OSD RGB > 280R > .7V drop Diode > Bridged with Solder > 75R to ground > _.7V RGB Injection_ > 10uF capacitor > Jungle RGB__

The 20" models have a 680R to ground instead of 560R. Therefore, this mod is theoretical for those. But I can't see why, with the same chips, the simplified circuit wouldn't operate the same way. From the jungle ICs [Datasheet](https://www.alldatasheet.com/datasheet-pdf/pdf/31184/TOSHIBA/TA1268N.html), we can tell its voltage tolerance is pretty high for analog input, so I don't think having slightly higher OSD voltages than stock would affect it much. I'd argue from the matching ICS that the result should be nearly identical.

### More than you want to know about Diodes
The diodes being in place from the factory hugely benefit the results of this mod. Here is a rundown if you need to get more familiar with how diodes work. Diodes allow current to flow in one direction on a circuit at the expense of dropping the voltage a fixed amount. This circuit utilized ceramic 0.7V drop diodes. The magical part about diodes is that because we have them on the circuit, they essentially prevent the backflow of RGB-injected signal into the resistors on the OSD line. This allows the 75R to ground to be a common termination point for both the injected RGB and the OSD RGB, meaning the Jungle IC receives a full-power RGB signal and does not need to over-amplify the video signal. The injected RGB can backflow into the 75R to ground precisely because the "to ground" allows current to flow through it. If this was an inline resistor, the injected RGB would ignore that resistor and flow directly to the capacitors and jungle IC without termination due to the inline diode.
### Why this mod works so well
If there were no diode, this would be a lot harder to balance because the injected RGB could intermix with existing OSD circuitry components. This is the problem with dim RGB and OSD signals on other mods. People are sacrificing voltage by balancing the entire circuit OSD+Injected RGB by using inline injected RGB resistors after a 75 ohm termination to ground in the connector. Remember that the OSD will make a new circuit with this added inline resistor. However, sometimes, there is no choice with the constraints of the circuit. So YMMV. It just so happens that this exact chassis allows very easy injection and modification. Also, my image is very consistent in brightness and color calibration to the composite input, unlike a lot of mods online where they have to mess __A LOT__ with service menu settings to get it to look right again.
### Blanking signal
The mod taps into the blanking line (EDIT EXACT LOCATION INTO HERE) and sends 1.5V from pin 16 on the scart connector. This original 5V from pin 16 voltages passes through this circuit to reach the Jungle IC at the desired value of 1.5V.

__Pin 16 5V > 8800R > 0.7v drop diode > (EDIT EXACT LOCATION INTO HERE) > Jungle IC__

If automatic switching is not working on your circuit, you could have a bad scart cable, or your console doesn't support blanking. You can test pin 16 voltage on a cable with a multimeter while the console is turned on to make sure it's 5V. You will know the circuit works if you instantly get an image from your console on the plugin.

### Wiring RGB, Blanking, Sync, Ground and Audio
You want to plan ahead and give yourself extra slack so that you can easily assemble the TV when you are putting it back together. Feel free to skip ahead to pictures from the future to get an understanding.
Sync from composite seems to be working perfectly! To use it, tap into the signal and run the cable through the motherboard hole to the connector.
The connector's chassis ground can be tapped right next to the composite signal (the connector is grounded).
- Mono Audio: Only tap in with Audio In Left from the connector, and leave Audio in Right unused.
- Stereo: Tap in with Audio Left and Right into their jack signals.

### Connector
Follow the steps on this link (minus the termination to ground, we have the 75 ohms built into the motherboard) (insert a link to a tutorial for connector creation)
Attach R, G, B, Blanking, Composite Sync, Audio L, and Chassis Ground wires to the connector. 

### Chassis hole (for connector)
This step is a pain to do. You can do a quick and dirty with some files and drills and make a random-sized opening and 3d print a scart cover plate, or you can take your time crafting a form-fitted opening. I have a 3d printer, but I wanted to try to do it right (if I messed up, I would do a cover plate). Safe to say it turned out solid. I used a Dremel tool and honestly would not recommend it; it was dusty, loud, melty, and smelly. I would instead drill holes and connect them by filing.
Key points:
The location I chose for the plug is very specific because it clears the internal lower tray and looks very nice and OEM. Feel free to put the plug wherever you want, but I think this is the best spot on a 13".
- With the self-tapping screws I linked, you do not need to have a drill (I didn't use one), but it would be better to make tiny pilot holes. But it's possible without a drill.

### Reassembly
- If you are an __advanced user__, you can skip to Color calibration and testing before reassembling and test the connection before the CRT is fully reassembled. It's always safer to turn on the CRT with everything assembled, so do this __AT YOUR OWN RISK__.
- Reverse of Assembly, but __don't forget to read the VCR disclaimer__ above!

## Color calibration and Testing
### Service Menu Adjustment
- Get some form of 240p test suite.
- The OSD will be unable to adjust the RGB video for this jungle chip design. This is not a huge problem. To adjust the video, use the service menu.
- __While the TV is powered down, Press Display + 5 + Volume Up + Power in quick succession to get into the service menu__
- Make adjustments to the Red, Green, and Blue Bias based on tutorials online.
- Make adjustments to the geometry based on tutorials online.
- Some other service menu options will do nothing like sub contrast and sub brightness, this is normal.
- When you are finished, press __Muting, then 0, then enter, then muting, then enter, then muting, then 0, then enter__
- Im not completely clear on how the saving works on the service menu, so the long string of actions above more or less guarantees that the settings will be written and saved even if the TV is unplugged. If saving isn't working, keep trying to save until it does.

### OSD
Osd doesn't work to adjust RGB input but still works perfectly with composite. This is actually a benefit because it allows both inputs to be _sort of_ calibrated at the same time. You probably won't get it perfect because service menu changes affect it, too, but it will be a lot closer than if OSD controlled RGB and composite signals at the same time.

### Composite versus RGB
Before RGB modding, I was contemplating if it was even worth it. The display on composite looked awesome on SNES. Smaller screen sizes like 13" makes the composite look a lot better. However, adding the RGB __BLEW__ composite out of the water. I couldn't believe the difference! I can't look the same way at the composite signal anymore because RGB has spoiled me.
