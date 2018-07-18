# Mini RC Hovercrafts

## Prototype notes:
To get started, it was suggested that we start with one and we don't immediately go for miniature but rather try to get some experience first. Like: what are important design characteristics? Is the outer shape important? How much motor/airflow do you need? Does a regular rc propeller work or do you need something with lower speed and more air movement per rotation? Which factors influence stability? How does one make the skirt?

So we first mock about a little with some quadcopter parts to get a better feeling for what is important when designing something smaller.

If people want to get started I suggest to start with a v0.0 prototype that has only hover and no propulsion made out of cardboard/foam/mdf/whatever you can find.

#### What you'll likely need to get lift-off:

* board/mdf and a (manual/electric) jigsaw
* plastic bag and sciccors to make a skirt
* arduino to translate between receiver and motor controller(esc). I believe the former to output pulse-width-modulated signal and the latter to take pulse-density modulated signals. I believe that in theory the speed controller can be flashed to take pwm directly but I don't have a clue how. An arduino inbetween has the added benefit that a low signal can be translated to a full-off which is not possible with a direct connection.

#### Here are some more thoughts:

* In the purple crate there are 4 spare (silver) motors. One of them has a bent shaft. look out for that one ;-) It is not in the same box as the three good ones. The quadcopter was not flying properly last time I used it. I believe that at least one of the red motors that are currently mounted on it has an issue too. The safe bet is to use one of the three silver motors from the cardboard box in the crate.
* please be carefull with motors with props on them ;-) Always verify that they twist the way you expect before letting them spin with props or even nuts on them (i.e. such that the nut tightens itself and not loosens when rotating). If you spin a prop clockwise on a motor with normal clockwise thread the nut WILL come of and kill someone. The direction of fastening should always be the opposite of the direction the prop will spin. 
* I suggest you use one of the mdf quadcoper arms to hold the motor in place. Simply hotglue that to a baseplate with a large hole. We can add something fancy later.
* One of the things I've seen people do is to cut a propeller to a smaller diameter to get better results. You have my permission to cut some props if you believe this is needed.
* The ESC (electronics speed controllers) are designed to feed logic level voltage (3.3 or 5V I don't remember) back to a microcontroller through the 3-pin input plug. orange wire is signal. They won't be damaged if more than one is feeding the microcontroller at the same time.
* You have my permission to unsolder unneeded ESC's from the power distribution board.





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
A bit of everything. We need software, we need electronics, we need hardware. We could delve into radio-stuff if someone like to do that kind of stuff, but we can do with standard radio transmitters/receivers.


## How much time will this take
Let's aim to come up with a rough design in 1 or 2 weeks, have a one-off prototype ready after 2-3 months. Then plan a workshop where people can build their own and then we have a fleet to race against each-other ;-)


## Number of people involved
This is really flexible. See sub-projects above. It would be nice to make sub-teams of 1-3 people, so I'd say anything between 2 and 10 is feasible.



## Wild ideas
### single propeller for everything

With 2 servo's controlling "flaps" that release air from the propeller shroud it could be possible to steer the craft. (essentially making it a 2-servo-1-bldc instead of 2-blcd-1-servo operation). Note also how air escapes even in neutral position, such that lift is constant no matter what the steering is doing. 

![hovercraft steering design](/img/hovercraft_steering.png "Hovecraft steering")
