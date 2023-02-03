# Wylderbuilds Dactyl Manuform - Python 3 - Cadquery
So, THIS is a fork of a fork of a fork of a... You get the idea.

This one is a direct fork of [joshreve's brilliant adaptation](https://github.com/joshreve/dactyl-keyboard)  of the original Clojure-based dactyl manuform generator redone in Python 3.
Without his work, none of this would have been nearly as easy and straightforward as it has been.  Vast kudos and thanks to him.

This repo is what I've customized and use to generate the models for the prints I sell online at Wylderbuilds, my Etsy store.

## Main Differences and How to Make it Go
Eventually, joshreve and I hope to merge our changes together, but until then, here's a quick rundown on the current changes.

* Wylderbuilds Trackball cluster -- A new, low-rider Trackball cluster. ("thumb_style": "TRACKBALL_WILD")
* Wylderbuilds BTU Trackball cluster -- An even newer Trackball cluster with ball transfer unit support. ("thumb_style": TRACKBALL_BTU")
* 1.5u pinky column support -- Outside 1.5u pinky columns can be generated ("pinky_1_5U": true, "first_1_5U_row": x, "last_1_5U_row": y)
* Full bottom rows -- Default manuforms drop the bottom row keys on outside columns, this keeps them ("full_last_rows": true)
* Clusters broken out into their own classes -- Making it easier to swap among them and add more.
* Updated Kailh Hot swap holder -- If enabled, the hot swap holder is full size and stronger.
* Cadquery builds generate STLs in addition to STEP files -- The bottom plates are (still) only generated properly when the "ENGINE": "cadquery" is set and this will now generate ready-to-print STLs (some models might need a little repair)
* OTHER MISC BITS: OLED mount wall tweaks, tweaks to screw-sizes and some wall placements, manuform angle and heights tweaked, support for an "overrides" json config file.

The main script has been reworked into a single make_dactyl() function.

The setup and run instructions are still more-or-less the same, but here's some tips:

* The docker file likely won't get far, it hasn't been maintained or updated in some time.

* To run locally, the best route is to install Anaconda or Miniconda, start a conda shell and run the "conda.sh" script.  If you're on Windows and don't want to do the WSL Linux thing, you can do the following:

1. Do the Anaconda/Miniconda bit, above.
2. In a conda shell, run the following lines:

        conda create --name=dactyl-keyboard python=3.8 -y

        conda activate dactyl-keyboard

        conda install -c conda-forge -c cadquery cadquery=master -y

        pip install dataclasses-json numpy scipy solidpython

        conda update --all -y

Then, still in the shell, from the base repo directory, run:

    python src/dactyl_manuform.py

This will churn and pump out models into the "things" directory.  In run_config.json, "ENGINE": "solid" or "cadquery" will specify OpenSCAD or STEP/STL files, respectively.  Note that the cadquery option takes considerably longer.  Openscad is best for fast iteration.

I'll update more here as things develop.

### What's Money Got To Do With It?

I opened Patreon and Liberapay accounts to accept any donations folks might want to make.  If I can lessen the need for a day job, I'll have the time to get all the bits and pieces I'd really love to see in this repo. A lot of great work has been done, but it's not easy code to work with or to adapt.  That can change.

[Wylderbuilds on Patreon](https://www.patreon.com/user?u=83640492)

[![Donate using Liberapay](https://liberapay.com/assets/widgets/donate.svg)](https://liberapay.com/Wylderbuilds/donate)


## License

General Code Copyright © 2015-2021 Matthew Adereth, Tom Short, and Joshua Shreve
Mini thumb cluster Copyright © 2015-2018 Matthew Adereth, Tom Short, and Leo Lou
Carbonfet thumb cluster © 2015-2018 Matthew Adereth, Tom Short, and carbonfet (github username)

The source code for generating the models (everything excluding the [things/](things/) and [resources/](resources/) directories is distributed under the [GNU AFFERO GENERAL PUBLIC LICENSE Version 3](LICENSE).  The generated models and PCB designs are distributed under the [Creative Commons Attribution-NonCommercial-ShareAlike License Version 3.0](LICENSE-models).
