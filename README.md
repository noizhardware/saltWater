# saltWater
#### A library of tiny objects to let ORCΛ swim in a sea of pure data

* [ORCA](https://100r.co/pages/orca.html) is an esoteric programming language, designed to create procedural sequencers.
* [puredata](https://puredata.info/) is a visual programming language for creating interactive computer music and multimedia works.

## Installing the library
The easiest way is to copy the files contained in the `lib` folder in your local externals folder.
That should be here: (from https://puredata.info/docs/faq/how-do-i-install-externals-and-help-files)
* _Linux_
  - User-specific: ~/pd-externals
  - Global: /usr/local/lib/pd-externals
* _Mac OSX_
  - User-specific: ~/Library/Pd
  - Global: /Library/Pd
* _Windows_
  - User-specific: %AppData%/Pd
  - Global: %CommonProgramFiles%/Pd
  
Also, another super-easy way to do that, on any OS, is to just have the library files in the same folder with your patch.

OR, under WINDOWS you can add the `lib` folder path to the registry:
  - (`WIN+R`, type in "regedit", press `Enter`)
  - `Computer\HKEY_CURRENT_USER\Software\Pure-Data`
  - `right-click` >> `New` >> `Expandable String Value`
  - you should name the new value `path##`, where the `##` is a prograssive number, so it depends on the other paths you have in your registry. The value should be your local path to the `lib` folder in this library.
  - ok, now you need to modify the `npath` registry entry, and update it with the new `##` you used before.
  
There should be a way to do a similar thing also under Linux and/or MacOSX, if you know how, please feel free to edit this readme, I'll pull the edit!

## Connecting ORCΛ with puredata
I'm using the simplest way to do that, without setting up external software, using OSC.
A video version is [here](https://youtu.be/Pv7639QqvhI?t=239).
* in ORCA, `Communication` >> `choose OSC port`, type a port number, 9000 is fine.
  - keyboard shortcut is `Alt+O`
  - now you can use the `=` glyph to send OSC data out
* in puredata you don't need to set up anything
  - use `osc-boot portnumber` to start receiving OSC data
  - use `oscc osc-path-name` to route data from a specific OSC path on that port
  
## Data coding system
In ORCA you'll need a 5-characters group to send data to saltWater:
* `osc pathname` [0..z]
* `octave number` [0..a] (nearly-audible-range)
* `note number` [0..b] (12 semitones)
* `attack time` (in msec/10)
* `release time` (in msec/10)

All numeric data is in `base 36`, see https://github.com/hundredrabbits/Orca#base36-table
  
## Library Elements
All the elements in this library start with _"salt"_
* **saltGrain**
  This is the basic building block, translates inputs from ORCA into two elements: a standard MIDI note on the left outlet and an envelope signal on the right outlet.
* **saltSin**
  This will directly output a sinewave, according to the received note, and gated with the received AR enevelope data.
* **saltIvory**
  super-simple piano synth, with one single overtone
