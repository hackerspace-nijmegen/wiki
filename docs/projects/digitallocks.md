# Digital entrance Options

The following is a (possibly non exhaustive) set of options to secure the entrance to the building and our own space. We have tried to come up with pro's and con's.

## Considerations
Many of the pro's and con's are self-explanatory but some deserve a little clarification:

* deniability towards other renters:
The hackerspace is likely to hand out a significantly larger number of keys than the other renters (that typically have one key holder per room). Therefore it would be nice to be able to show (but probably not legally prove?) that it was not one of our keys that was used to enter the building if ever something gets stolen from another room in the building. In response it has been argued that this only applies to the hypothetical situation where there was no signs of breakage at the outside of the building but there was on the inside. Also: other renters have locks on their internal doors which should be enough and it is not our problem or our responsibility to prove what happened to our keys in an environment where many keys are probably already circulating.

* revocability:
an advantage of digital keys is that they can be revoked. It should be noted that we are already circulating a number of metal keys that will remain usable forever, so only access can be revoked from people who join later or who faithfully hand over all their metal keys once the digital locks are in place.

* Anonymous access:
this can be either a pro or a con. In some systems access is inherently anonymous or anonymized by the implementation. Keep in mind that anonymity is only guaranteed so far as you trust the impolementation and that there are other ways to identify you than by your key so it can be argued that we don't need to protect against attack vectors that are more complicated than putting a hidden camera somewhere.


## Description of the available options
1. nothing digital, metal keys everywhere:
This will require two keys per user since we have one for building access and one for space-access. This will cost about 5 euros per key at the moment but we can probably get cheaper keys if we order blanks and copy ourselves.

2. digital locks as proposed by SA007 and cyberghost:
This includes keyreaders at 3 doors. Current cost estimation is 350 euros including 40 keys. Extra keys will cost 5 euros each later. Maybe we can go cheaper for the locks. Keys are in theory identifiable but we implement it such that no logs are kept.

3. Same as above with minimal tracking:
Logs of which key is used are kept for some time but not published. Also the mapping between key ids and real names is restricted to a small number of trusted admins. This data could even be encrypted such that only n out of m admins can access the data together.

4. Digital locks with ring encryption (as proposal by stf):
It is not clear how this technically works. Can this be done with iButtons or does it require special hardware? Is hardware and software needed for this available and how much would it cost? Editorial note: I looked it up: what stf proposed is an algorithm in which it is guaranteed that only the "master" can decode who got access but the "dumb doors" can check that permission should be granted without being able to identify the person (like checking a hash but more complicated). An evil Eve could completely take over the door system and not be able to tell who enters, only at what time the door was opened.

5. Metal keys for building, pincode lock on space door:
This is an upgradable temporary solution that can be upgraded to ibuttons later and even later be extended to others doors without wasting too much resources (only the keypad). This would probably cost around 50 euros. The pincode can change so access to the space can effectively be revoked. Access is anonymous.


## Pro/Con matrix
| Criteron/Option | 1 | 2 | 3 | 4 | 5 |
|----|----|----|----|----|----|
| Fast to implement | immediate | several weeks | several weeks | unknown | few weeks |
| Price             | low       | expensive     | expenses      | expensive? | intermediate |
| anonymous access | completely | as far as you trust impl. | as far as you trust impl. & admins | as far as you trust admins | completely |
| key can be copied | yes | no | no | no | outside, and inside temporarily |
| revokeable | no | yes | yes | yes | only inside |
| trouble in case of persona non grata | high | low | low |low | medium |
| number of tokens to carry around | 2 | 1 | 1 | 1? | 1 |
| deniability towards other renters | bad | good | good | good | bad |
| migratable to next space | maybe half | likely | likely | likely | likely half |
| possibility to 'buzz' guests in | no | yes | yes | yes | no |
| cost per extra key | high now, could be low | medium | medium | unknown | low |
| time dependent access | no | possible | possible | probably impossible | no |
| power outage resilience | high | several hours | several hours | several hours | high |
| liability in case of malfunction? | no | don't know | don't know | don't know | no |
| could there be trouble with insurance? | yes | yes | yes | yes | yes |
| implementation readily available | yes |yes |yes | don't know | yes |
| ease of use | medium | good | good | unknown | medium |
| expendable in future |  |  |  |  | yes |
