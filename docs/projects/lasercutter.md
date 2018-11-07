# 40W Lasercutter

## Why is there suddenly a lasercutter
It was donated to hackerspace nijmegen by hack42 during the [https://hack42.nl/wiki/Hack42_on_Tour](Hack42 on Tour) weekend.

Short backstory: A #42 member saved it from the dumpster, it was *'in working order'* but since this is a crappy old machine it was replaced.

Hack42 already has a very similar machine, rebuild into a nice useable one and no real intrest in haveing two, so it was donated.

## So what does *'in working order'* mean?
That it should work as designed, but the design is horrid.

## What todo do with it
In my (SA007) opinion the steps should be.

- Verify the *'in working order'* claim
    - Make sure the 230V wiring is usable, i've seen it with a negligible amount or actual metal in the wires.
    - Connect the ground to the ground terminal of the power connector.
    - Make the cooling system work (pump, bucket, hoses, see if there are leaks and if the flow is usable.
    - Power the laser up, put some wood under the head and hit test, it should burn the wood, if not, check the alignment.
    - Optional: Actually hook it up to an old windows pc and install the supplies software.
- Add loads of safety's, there aren't any...
    - Switches on the covers, so it can't turn on the high voltage/laser if a cover is opened.
    - Emergency stop switch.
    - Covers for the bit holes in the casing (most are needed for alignment, but can have removable covers.
    - Covers for the slits and gaps in the main/all covers (you should not be able to directly look into the laser bed, with exception of the window.
- Replace electronics
    - There are several options for the main electronics, such as smoothieboard (or clone), laos and several 3d-printerboard are usable as well. The one at hack42 is a laos one, from experience it is 'really meh' so I would pick something else.
    - Replace a lot of the wiring.
    - Probably upgrade the endstops (more range, better accuracy)
    - Add display?
    - Add timer? (laser tubes have a limited life, you want to keep track and/or make people pay for usage)
- Upgrade cooling
    - Keeping the tube cool is important.
    - A 'closed' system is great, a chiller even better.
    - Temps need to be below 30 celcius, 18 is best for long life.
- Upgrade ventilation
    - The exhaust needs to go outside (maybe via the ventilation slits)
    - The fan sucks air from the wrong place (alignment sucks)
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
