# hp-41_observe

Control your telescope via the HP-41 calculator! Create observation lists, start observing, control the telescope mount via an INDI server.

This program makes it easy to create observation lists for the night. And the program makes it possible to use your HP-41 to control your telescope. The way this works is that the HP-41 "prints" the RA/DEC coordinates (stored in the observation list of choice) via Diego Diaz's USB41 module to your PC running the Ruby program "observe41.rb". This program connects to the INDI server running on your PC and sends the coordinates to your telescope mount via either Kstars or Stellarium (or similar program) that is set up to interface with your telescope.

For this to work, you need a PC running Linux or Mac OSX with Ruby installed as well as Kstars (and Stellarium if you prefer that interface over Kstars) and a working connection PC <-> mount (cable, wifi or bluetooth). You also need the USB41 module as well as (obviously) an HP-41 calculator. The HP-41 needs to have the ISENE ROM loaded as the program depends on this (you could copy the programs SKPTACR and FLSZ+ from that module or from relevant GitHub repos instead).

The program works on two files, the Primary "observation file" and a Source file from which you copy objects to the primary file. When you first run the program, you would want to create a set of source files, such as "\*MESS" for your Messier objects, "\*NGC" for NGC objects and "\*DBL" for double stars, etc. Then, when you create your observation file for the night (for example "\*OBS1"), you can use the object files as Source and pick the objects to go into your observation file. You would pick the observation file as Primary (F1) and an object file as Source (F2) - pick objects from that file, swap to another Source and keep picking objects.

Notice that all the file names start with an asterisk (\*). This is because the file listing (LBL A) only shows files with an asterisk as the first character in the file name. The program will only show and will only create files starting with an asterisk.

Upon **XEQ "OBSERVE"**, the program first shows the active Primary file (F1), if any (stored in Reg #01). If there are none, or if you want to change the F1 shown, simply enter the new file name to become F1 and press R/S. Remember that the file name must start with an asterisk. If you are happy to proceed with the Primary file (F1) already stored in Reg #01, then just press R/S. The program will then give you the menu "?F 1= L1 + O" for the top row keys. After pressing R/S, it will show the menu "ED 2= L2 - M" for the shifted top row keys. Pressing R/S again shows the current selection of Primary (F1) and Source (F2) files.

Label (Menu) |Description
-------------|-----------
LBL A (?F)   |List all files with a file name starting with an asterisk (\*). When a file is shown, press "B" to set it as F1 or "b" to set it as F2
LBL B (1=)   |Set the file name in Alpha as F1 (must start with an asterisk to be accepted)
LBL C (L1)   |List Primary file (F1). Object name in Alpha, RA in Y and DEC in X
LBL D (+)    |Add object to end of F1. Object name in Alpha, RA in Y and DEC in X
LBL E (O)    |Start observing, using F1 as observation file. As each object is displayed, it sends RA and DEC to your PC to move the scope to the object (or print it to a printer if you have not hooked up your telescope mount via an INDI server)
             | 
LBL a (ED)   |EDit the current Primary file (F1)
LBL b (2=)   |Set the file name in Alpha as F2 (must start with an asterisk to be accepted)
LBL c (L2)   |List Source file (F2). Object name in Alpha, RA in Y and DEC in X
LBL d (-)    |Remove last object in Primary file (F1)
LBL e (M)    |Go back to the main menu

## License
This software is released into the Public Domain.
