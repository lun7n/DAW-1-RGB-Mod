# DAW-1-RGB-Mod
Please do not skip the introduction. This guide will explain how to RGB mod your DAW-1 Sony Trinitron Chassis. This will use a variation of the RGB mux method with automatic switching for all 13" DAW-1 Sony Trinitron Chassis found in the KV-13VM40, KV-13VM41, KV-13VM42, KV-13VM43.
The 20" mod is theoretical and needs testing. KV-20VM40, KV-20VS40, KV-20VM42, KV-20VS42 all have a 680 ohm to ground resistor instead of a 560 ohm to ground resistor in the OSD circuit.
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
- Mounting screws (I chose m4x16mm self tapping which were slightly too big imo but it worked out)
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
The original OSD of the 13" model circuit consists of 

__OSD RGB > 1KR > .7V drop Diode > 1.2KR > 560R to ground > 10uF Capacitor > Jungle RGB__

The mod simplifies this circuit and utilizes the original Diode to preserve the original .7V signal strength of the RGB while not sacrificing OSD brightness to an unusable degree.

__OSD RGB > 280R > .7V drop Diode > Bridged with Solder > 75R to ground > _.7V RGB Injection_ > 10uF capacitor > Jungle RGB__

The 20" models have a 680R to ground instead of 560R to ground. Therefore this mod is theoretical for those. But I can't see why with the same chips that the simplified circuit wouldn't operate the same way. From the jungle ICs [Datasheet](https://www.alldatasheet.com/datasheet-pdf/pdf/31184/TOSHIBA/TA1268N.html) we can tell its tolerance for voltage is pretty high for an analog input, so I don't think having slightly higher OSD voltages than stock would affect it much. I'd argue from the matching ICS that the result should be nearly identical.

### More than you want to know about Diodes
The diodes being in place from the factory hugely benefits the results of this mod. If you aren't familiar with how diodes work, here is a rundown. Diodes allow current to flow in one direction on a circuit at the expense of dropping the voltage a fixed amount. This circuit utilized cermaic 0.7V drop diodes. The magical part about diodes is that because we have them on the circuit, it essentially prevents backflow of RGB injected signal into the resistors on the OSD line. This allows the 75R to ground to be a common termination point for both the injected RGB and the OSD RGB, meaning the Jungle IC recieves full power RGB signal and does not need to over amplify video signal. The reason the injected RGB is able to backflow into the 75R to ground is precisely becasuse the "to ground" allows current to flow through it. If this was an inline resistor, the injected RGB would ignore that resistor and flow directly to the capacitors and jungle IC without termination due to the inline diode.
### Why this mod works so well
If there was no diode, this would be a lot harder to balance because the injected RGB could intermix with existing OSD circuitry components. I believe this to be the problem with dim RGB signals and dim OSD signals on other mods. People are sacrificing voltage by balancing the entire circuit OSD+Injected RGB with using inline injected RGB resistors after a 75 ohm termination to ground in the connector. You have to remember that the OSD will now make a new circuit with this added inline resistor. However, sometimes there is no choice with the constraints of the circuit. So YMMV. It just so happens that this exact chassis allows very easy injection and modification. Also, my image is very consitent brightness and color calibration to the composite input, unlike a lot of mods online where they have to mess __A LOT__ with service menu settings to get it to look right again.
### Blanking signal
The mod taps into the blanking line (EDIT EXACT LOCATION INTO HERE) and sends 1.5V from pin 16 on the scart connector. This original 5V from pin 16 voltages passes through this circuit to reach the Jungle IC at the desired value of 1.5V.

__Pin 16 5V > 8800R > 0.7v drop diode > (EDIT EXACT LOCATION INTO HERE) > Jungle IC__

If automatic switching is not working on your circuit, you could have a bad scart cable or your console doesn't support blanking. You can test pin 16 voltage on a cable with a multimeter while the console is turned on to make sure its 5V. You will know the circuit works if you instantly get image from your console on plug in.

### Wiring RGB, Blanking, Sync, Ground and Audio
- You want to plan ahead and give youreself extra slack so that you can easily assemble the TV when you are putting it back together, feel free to skip ahead to picutres from the future to get an understanding.
- Sync from composite seems to be working perfectly! Just simply tap into the signal and run the cable through the mother board hole to the connector.
- Chassis ground for the connector can be tapped into right next to composite signal (the connector is grounded).
- Mono Audio: Only tap in with Audio In Left from the connector leave Audio in Right unused.
- Stereo: Tap in with both Audio in Left and Right into their respective jack signals.

### Connector
Follow the steps on this link (minus the termination to ground, we have the 75 ohm built into the motherboard) (insert link to tutorial for connector creation)
Attach R, G, B, Blanking, Composite Sync, Audio L, and Chassis Ground wires to the connector. 

### Chassis hole (for connector)
This step is a pain to do. You can do a quick and dirty with some files and drills and just make a random sized opening and 3d print a scart cover plate, or you can take your time to craft a form fittd opening. I have a 3d printer but I wanted to try to do it right (if I messed up I would do a cover plate). Safe to say it turned out solid. I used a dremel tool and honestly would not recommend, it was dusty loud melty and smelly, would rather drill holes and connect them by filing.
Key points:
- The location I chose for the plug is very specific because it clears the internal lower tray and looks very nice and oem. Feel free to put the plug wherever you want but I think this is the best spot on a 13".
- With the self tapping screws I linked you do not need to have a drill, (i didn't use one) but it would be better to make tiny pilot holes. But it's possible without a drill.

### Reassembly
- If you are an __advanaced user__ you can skip to Color calibration and testing before reassembling and test the connection before the CRT is fully reassembled. It's always safer to turn on the CRT with everything assembled, so do this __AT YOUR OWN RISK__.
- Reverse of Assembly, but __don't forget to read the VCR disclaimer__ above!

## Color calibration and Testing
### Service Menu Adjustment
- Get some form of 240p test suite.
- The OSD will not be able to adjust RGB video on this jungle chip design. This is not a huge problem at all. In order to adjust the video, use the service menu.
- __While the TV is powered down, Press Display + 5 + Volume Up + Power in a quick succession to get into the service menu__
- Make adjustments to the Red Green and Blue Bias based off of tutorials online.
- Make adjustments to the geometry based off of tutorials online.
- Some other service menu options will do nothing like sub contrast and sub brightness, this is normal.
- When you are finished, press __Muting, then 0, then enter, then muting, then enter, then muting, then 0, then enter__
- Im not completely clear on how the saving works on the service menu so the long string of actions above more or less guarantees that the settings will be written and saved even if the TV is unplugged. If saving isn't working, keep trying to save until it does.

### OSD
Osd doesn't work to adjust RGB input, but still works perfect with composite. This is actually a benefit because it allows to have both inputs be _sort of_ calibrated at the same time. You probably wont get it perfect because service menu changes affect it too, but it will be a lot closer than if OSD controlled RGB and composite signals at the same time.

### Composite versus RGB
Before RGB modding, I was contemplating if it was even worth it. The display on composite looked awesome on SNES. Smaller screen sizes like 13" makes composite look a lot better. However, adding the RGB __BLEW__ composite out of the water. I couldn't believe the difference! I can't look the same way at the composite signal anymore because I have been spoiled by RGB.
