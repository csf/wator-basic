# Implementation of [Wa-Tor](https://en.wikipedia.org/wiki/Wa-Tor) in Applesoft Basic.

Wa-Tor simulates ecological cycles between fish and sharks on a water-covered toroidal planet. By setting up the number of fish and sharks, the breeding times of each, and the starvation time for sharks, the simulation progresses stepwise with fish randomly moving and reproducing, and sharks "hunting" or randomly moving around a wrapping grid representing Wa-Tor's toroidal surface.

I first saw Wa-Tor described in A.K. Dewdney's [Computer Recreations article](http://home.cc.gatech.edu/biocs1/uploads/2/wator_dewdney.pdf) in the December 1984 issue of _Scientific American_ and it was the first non-trivial program I ever wrote from specs on the Apple IIc computer I finally was able to buy a few months later with money I'd saved.

Both the disk with my original source (and the Apple IIc itself) are long gone, so I set out to recreate it for multiple reasons--one part nostalgia, one part in support of an ongoing writing project, and one part in support of a January 2018 tech talk.

Differences between this version and my original 80's version:

* In this version, sharks and fish can not only evaluate adjacent cells, but _diagonally_ adjacent cells. The Dewdney spec just described basic up/down/left/right moves. This slows things down a bit.
* Three decades later, I've done enough programming in other languages to be able to use GOSUB more than the GOTOs I likely littered the original with. But Applesoft BASIC only gives you so much to work with.
* Probably better line-numbering now. You know, in case someone has to make modifications thirty years later.
* Instead of "X" to represent sharks, I show the time-to-starvation for the shark. So keep the shark starve time single digits! If you want to play with that, look for the `DISPCHAR$` code for sharks around line `910` and mess with it.

If you're interested, I've also put together a [Rust-based WebAssembly version of Wa-Tor](https://github.com/csf/wator-wasm) that runs in your browser and is quite a bit faster and more visually fun. (Or at least fast enough to be measured in frames-per-second instead of seconds-per-frame.)

## Screenshot
![alt text](https://github.com/csf/wator-basic/raw/master/images/wator-screen.png "Wa-Tor Screenshot")

## Run It
You can run the code in your browser by loading or pasting the raw source into Joshua Bell's very cool [Applesoft Basic in JavaScript](http://calormen.com/jsbasic) emulator.

The current implementation runs through the JavaScript emulator at anywhere from about 8 to 12 _seconds per frame_ (depending on the number of fish and sharks), which is about on par with what I recall for the original running on native Apple IIc hardware.

For best results when picking the parameters, you typically want to use something where fish breed faster than sharks, and sharks have to eat before they can spawn.
