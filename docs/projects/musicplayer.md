# Music at HSN

We have a Music Player (MPD) at Hackerspace Nijmegen. If you'd like some music,
you can turn it on.

To use the commands listed on this page, you need to be connected to the HS-NMGN
wifi network or be otherwise connected to the HSN network.

Questions? Ask Sjors!

## Starting it

Find out MPD's status by running `mpc -h barometer status`. The output may look
something like:

```
Maduk - Liquicity Yearmix 2016 (Mixed By Maduk)
[playing] #1/1   2:37/64:15 (4%)
volume: 77%   repeat: off   random: off   single: off   consume: on 
```

Play state is on the second line. If it says 'playing', and you don't hear
anything, check audio settings on `barometer@bar-o-meter` :-(

If it says 'paused' or 'stopped', run `mpc -h barometer play`. If that doesn't
help, restart it.

If it's not running, or broken in some way, you can `ssh barometer@bar-o-meter`
and run `./startmpd.sh`. That'll stop it if it's running, then restart it. It
starts mpd, but also ashuffle, a tool to keep the playlist always filled.

## Stopping it

Done with the music? Last person to leave the space? `mpc -h barometer pause`.

## Adding your own music

`barometer` is running an NFS mount. Try:

```
sudo mkdir -p /media/music
sudo mount -t nfs barometer:/media/music /media/music
```

Make your own directory on it, and add your stuff! Please don't touch other
people's stuff, and don't download any music from it, get it somewhere legally!

Currently there's only about 128 GB of space, so don't upload your entire music
database; if it fills up further, I'll probably add a disk or something.

## Queueing your own music

Take the path to your file, then run:

```
mpc -h barometer add 'yourname/Path To Your Music/Some Artist - His Track (Someones Remix).mp3'
```

## TODO

Not in any particular order:

* It sometimes doesn't start with the correct audio interface. Why?
* Nicer speakers
* Automatic `mpc pause` when the space state is switched to closed, and *perhaps* "mpc play" when
  switched to open
* Revbank plugin for mpd!
* A (matrix LED?) screen that displays what song is currently playing, perhaps some nice animations
* A Something like https://github.com/notandy/ympd on a screen for people who don't care for CLIs
* A fair queueing system
* Force consume mode on (perhaps by patching mpd? Or just a cronjob every minute)
