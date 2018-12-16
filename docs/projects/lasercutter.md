# 40W Lasercutter

## Why is there suddenly a lasercutter
It was donated to hackerspace nijmegen by hack42 during the [Hack42 on Tour](https://hack42.nl/wiki/Hack42_on_Tour) weekend.

Short backstory: A #42 member saved it from the dumpster, it was *'in working order'* but since this is a crappy old machine it was replaced.

Hack42 already has a very similar machine, rebuild into a nice useable one and no real intrest in haveing two, so it was donated.

## So what does *'in working order'* mean?
That it should work as designed, but the design is horrid.

## What todo do with it
In my (SA007) opinion the steps should be.

- Verify the *'in working order'* claim
    - Make sure the 230V wiring is usable, i've seen it with a negligible amount or actual metal in the wires. (Done 12-11-18, wires aren't great but useable)
    - Connect the ground to the ground terminal of the power connector. (Done 12-11-18, casing and HV supply are now grounded via the power connector)
    - Make the cooling system work (pump, bucket, hoses, see if there are leaks and if the flow is usable). (In progress, there seems to be a blocked pipe) (13-11-18, pipe is unblocked, flow seems good, there is now some cleaner in it to remove crud) (3-12-18, Cooling 'done' for now, has 4L cooling circulating nicely)
    - Power the laser up, put some wood under the head and hit test, it should burn the wood, if not, check the alignment. (Very short test done, tube isn't broken, yay)
    - Optional: Actually hook it up to an old windows pc and install the supplies software. (Board removed, no longer an option).
- Add loads of safety's, there aren't any...
    - Switches on the covers, so it can't turn on the high voltage/laser if a cover is opened.
    - Emergency stop switch. (SA007: Done 19-11-18)
    - Temperature/water flow sensors are also nice, also ordered.
    - Covers for the bit holes in the casing (most are needed for alignment, but can have removable covers. (13-11-2018 In progress using ducktape'd alufoil, laser can't cut trough the alufoil) (Done 3-12-18, all relevant slots have been covered)
    - Covers for the slits and gaps in the main/all covers (you should not be able to directly look into the laser bed, with exception of the window. (Done 3-12-18, all relevant slots have been covered)
- Replace electronics
    - There are several options for the main electronics, such as smoothieboard (or clone), laos and several 3d-printerboard are usable as well. The one at hack42 is a laos one, from experience it is 'really meh' so I would pick something else (mks / smoothieboard clone and wires ordered by themba paid by crowdfunding).
    - Replace a lot of the wiring. (12-11-2018 Not as much needed as expected)
    - Probably upgrade the endstops (more range, better accuracy)
    - Add display? (Also ordered, not crowdfunded)
    - Add timer? (laser tubes have a limited life, you want to keep track and/or make people pay for usage)
- Upgrade cooling
    - Keeping the tube cool is important.
    - A 'closed' system is great, a chiller even better.
    - Temps need to be below 30 celcius, 18 is best for long life.
- Upgrade ventilation
    - The exhaust needs to go outside (maybe via the ventilation slits) (Outside airvent is installed)
    - The fan sucks air from the wrong place (alignment sucks) (Alignment is improved)
    - Maybe a (carbon)filter
- Added features
    - Air assist is really awesome, cutting results greatly improve, you can build a cheap one from a fridge compressor.
    - Usable switchable light, 25W bulb is useless.
    - Switched/monitored cooling/ventilation, so you don't run without it.
    - Honeycomb bed
    - Is someone gets creative, a focus adjustment would be nice.
- Calibrate/adjust the machine
    - Align/clean the mirrors.
    - Calibrate the axes, more accuracy.
    - More to come.

## Sources for information
We have a SF40 laser, very similar to K40, which has been modified extensively.
Ask SA007 on IRC/Mail/Whatever

## Costs?
It will probably be around 200 euro to get parts such as replacement electronics, safety gear etc.

Current costs:


| Item                | Price (Paid by)  |
|---------------------|------------------|
| Lasercutter         | Free             |
| [Electronics](https://www.aliexpress.com/item/3D-Printer-Parts-Controller-Board-MKS-SBASE-V1-3-32-bit-Open-Source-Platform-Smoothieboard-Compatible/32853515280.html)         | 40,34 (Themba)   |
| [Display](https://www.aliexpress.com/item/3d-printing-touch-screen-RepRap-controller-panel-MKS-TFT28-V1-2-display-color-TFT-support-WIFI/32808421021.html)             | 24,43 (Themba)   |
| EStop               | Free             |
| Shielding materials | 11,50 (SA007)    |
| [Bucket](https://www.groku.de/fileadmin/web/pdf/EZE5600_en.pdf) | Free |
| Subtotal            | 76,27            |
| Coolant             | 8,70 (SA007)     |
| Exhaust hose        | 6,95 (SA007)     |
| Wiring/plugs        | 5ish (SA007)     |

Currently funded: 50 euro.

There is a donation box on top of the lasercutter.

## Looking for materials:
- Fridge compressor (anyone an old fridge thats going to be dumped?)
- Watercooling items (radiator+fans, hoses, pump etc)

## Small tasks list:
- Add/wire interlock switches.
- Extend Y motor wire
- Change plugs on endstops.
- Find / connect PWM signal.
- Hook pcb up to power.
- Mount temperature sensor somewhere properly to measure coolant temp.
- Fix/connect led strip and find/mount a psu for them.

## More specs?
It is '40W' laser tube, more realisticly it is 30-35W it runs on really high voltage (~2kV).

It is a CO2 laser, they run at 10600nm, which is really really infrared.

## Materials it can cut/engrave?
- Wood -> most types it can cut and engrave, up to about 5mm.
- Plastics PLA/ABS/PET/PS are fine, PVC is a REALLY bad idea, cut and engrave up to 5mm.
- Cardboard/Paper -> see wood, paper can catch fire, which is a lot better with airassist.
- Metals -> No, but engraving is possible by removing a coating of $material such as paint.
- Cookies -> Engrave Work fine, still eatable afterwards.
- Chocolate/Sugary stuff engraves fine.
- Wet foods -> No.

