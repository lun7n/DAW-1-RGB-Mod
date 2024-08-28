# DAW-1-RGB-Mod
Please do not skip the introduction. This guide will explain how to RGB mod your DAW-1 Sony Trinitron Chassis. This will use a variation of the RGB mux method with automatic switching for all DAW-1 Sony Trinitron Chassis found in the KV-13VM40, KV-13VM41, KV-13VM42, KV-13VM43, KV-20VM40, KV-20VS40, KV-20VM42, KV-20VS42.
## Introduction
### My hardware rundown
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

