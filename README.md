## Final Fantasy X Lightning Dodger

Automatically dodges lightning bolts in the Thunder Plains by emulating a controller on a SparkFun Pro Micro (ATmega32U4).

[![IMAGE ALT TEXT HERE](https://streamable.com/e/9tc3zi)](https://streamable.com/e/9tc3zi)

#### How to use

Go to this spot in the Thunder Plains

[![IMAGE ALT TEXT HERE](https://i.imgur.com/bxcSTej.jpg)](https://i.imgur.com/bxcSTej.jpg)

Walk up to Pondo until the **(A) Talk** option is available and plug in the controller. It will automatically sync with the console, initiate the bowling game with Pondo, throw a perfect strike, and end the bowling game. It will play the bowling game in a loop.

Note that due to certain weather conditions, Link will sometimes fail to throw a strike, causing the game to enter into a mode where Link has to throw again. Thanks to a [change by exsilium](https://github.com/bertrandom/snowball-thrower/pull/1), the loop will recover from this, given enough time. I've tested this running for over 24 hours.

In case you see issues with controller conflicts while in docked mode, try using a USB-C to USB-A adapter in handheld mode. In dock mode, changes in the HDMI connection will briefly make the Switch not respond to incoming USB commands, skipping parts of the sequence. These changes may include turning off the TV, or switching the HDMI input. (Switching to the internal tuner will be OK, if this doesn't trigger a change in the HDMI input.)

This repository has been tested using a Pro Micro 5V/16MHz (ATmega32U4).

#### Compiling and Flashing onto a Sparkun Pro Micro

If your Pro Micro is a 3.3V/8MHz rather than a 5V/16MHz, go to line 17 in the makefile and change 16000000 to 8000000. For Linux, follow their instructions for installing the [GCC Compiler and Tools](https://www.pjrc.com/teensy/gcc.html). For Windows, you will need the [latest AVR toolchain](http://www.atmel.com/tools/atmelavrtoolchainforwindows.aspx) from the Atmel site.

LUFA has been included as a git submodule, so cloning the repo like this:

```
git clone --recursive git@github.com:crumpmasterjc/ffx-lightning-dodger
```

will put LUFA in the right directory.

Now you should be ready to rock. Open a terminal window in the `ffx-lightning-dodger` directory, type `make`, and hit enter to compile. If all goes well, the printout in the terminal will let you know it finished the build! Follow the directions on flashing `Joystick.hex` onto your Teensy, which can be found page where you downloaded the Teensy Loader application.

#### Thanks

Thanks to Shiny Quagsire for his [Splatoon post printer](https://github.com/shinyquagsire23/Switch-Fightstick) and progmem for his [original discovery](https://github.com/progmem/Switch-Fightstick).

Thanks to [exsilium](https://github.com/bertrandom/snowball-thrower/pull/1) for improving the command structure, optimizing the waiting times, and handling the failure scenarios. It can now run indefinitely!
