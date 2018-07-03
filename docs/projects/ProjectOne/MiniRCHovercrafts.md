# Mini RC Hovercrafts

## Basis idea
Build miniature hovercrafts for racing around the space or outdoor depending on how small we can make them and how well they work. 

## Alternatives
The simplest form would have one remote for each hovercraft. Maybe that is a good starting point.

Alternatively, they could be centrally controlled and perform some choreography (e.g. making a lightshow by also adding some RGB leds to each craft?).

Alternatively, they could be autonomous. There would have to be some vision processing? Or maybe we can come up with some other way for them to know where they are? I guess GPS is (besides relatively expensive) not precise enough. Or the track could have some special markers so that the crafts know where to go. It would be cool if they can autonomously race against each other. Maybe there can even be some kind of generic racing algorithm so that they get better over time? This is the most ambitious version and the least feasible. 

Maybe they can see each other through some qr tags or other markers (doesn't have to be visible can be IR leds blinking out identifyable patterns, etc...). That way they don't know where they are but they can flock together. That could look kinda cool? 

## Base features
The most basic craft should have:
* a frame with a skirt
* a battery
* a controller
* 1 brushless motor (combining lift and propulsion)
* propellors
* esc to control the motor speed
* one servo attached to a rudder for steering
* a receiver
* a transmitter (if we use wifi or some custom 433MHz/2.4GHz protocol this could be shared, individual control could go via smartphone or something like that).


## Sub-projects
Could be:
* hardware/skirt/steering
* electronics/uC
* communication and remote control


## Rough cost estimation
Bare minimum: 25 euro/craft

Assuming we have one shared transmitter and some app so we don't have to buy a transmitter for each unit:

| What       | How much | How                                                      |
|------------|----------|----------------------------------------------------------|
| frame      | 5        | laser-cut base + skirt from trash bag + 3d printed stuff |
| battery    | 5        | ~1000mAh from hobbyking?                                 |
| controller | 3        | arduino/nodemcu alike                                    |
| bldc       | 5        | the absolute cheapest I saw on hobbyking                 |
| propellor  | 1        | if bought in bulk                                        |
| esc        | 5        | BLHeli-like controller, don't know which one exactly     |
| servo      | 1        | 9g micro; just search aliexpress                         |
| receiver   | 0        | if we use nodemcu/esp8266                                |
| total      | 25       | still seems expensive to me :,-(                         |

 

Any kind of computer vision immediately add rpi-like hardware at 25 euros each + plus the cost of a camera.

IR communication or sensing hardware is probabaly cheap in aliexpress/ebay.


## Feasibility
Problems will certainly arise, but RC hovercrafts are not new so it can be done. The challenge is to make them cheap and to make them small. The former could result in problems if we use cheap hardware it may become harder to control. The latter may cause problems because more bottom surface means more stability.


## Tools needed
* 3d printer could be usefull for brackets/handles etc
* soldering iron and supplies
* programmer? depending on controller

## Skills needed
A bit of everything. We need software, we need electronics, we need hardware. We could delve into radio-stuff if someone like to do that kind of stuff, but we can do with standard radio transmitters/rec


eivers.


## How much time will this take
Let's aim to come up with a rough design in 1 or 2 weeks, have a one-off prototype ready after 2-3 months. Then plan a workshop where people can build their own and then we have a fleet to race against each-other ;-)


## Number of people involved
This is really flexible. See sub-projects above. It would be nice to make sub-teams of 1-3 people, so I'd say anything between 2 and 10 is feasible.

