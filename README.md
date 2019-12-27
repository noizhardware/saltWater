# saltWater
#### A library of tiny objects to let ORCΛ swim in a sea of pure data

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
  
There should be a way to do a similar thing also under Linux and/or MacOSX, if you know how, please feel free to edit this file, I'll pull the edit!
  
## Library Elements
All the elements in this
* saltGrain