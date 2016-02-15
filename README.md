# boot to electron

## idea

what if it was easy to boot linux to an electron app?

*simplified version of [`webkit-window-manager`](https://github.com/ahdinosaur/webkit-window-manager)*

## why?

i want to

- play visuals with an [led controller](https://github.com/ahdinosaur/pj)
- record audio with an [audio recorder](https://github.com/ahdinosaur/hardware-recorder)

with a [BeagleBone](http://www.seeedstudio.com/wiki/Beaglebone_green). i can get the usb hardware communication working, so now i want to be able to control it with having to reflash. i was thinking of hosting a web page, but why not interface with the hardware directly via a touch screen?

## how?

use [`Simple-CDD`](https://wiki.debian.org/Simple-CDD/Howto) [Debian](https://debian.org/) installer and [`bspwm`](https://github.com/baskerville/bspwm) window manager to boot to an [`electron`](http://electron.atom.io/) app.
