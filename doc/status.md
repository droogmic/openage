openage status
==============

This file contains the current feature set of openage.


The list must grow
------------------

As features don't create and add themselves down there,
you can make it happen! See the [contribution intro](/doc/contributing.md) how to add stuff.

Please update this file accordingly when adding features.


User-Visible Features
---------------------

* Convert all original media files
* Flat, infinite terrain rendering
* Basic map generation

* Global keybindings:
  * `←`,`↑`,`→`,`↓`,`Middle mouse button` - Map scrolling
  * `1`-`8` - Switch to player 1-8
  * `F1` - Toggle HUD
  * `F2` - Screenshot -> `/tmp/openage_2019-12-31_23-59-59_xx.png`
  * `F3` - Toggle debug overlay
  * `F12` - Toggle integrated profiler
  * `M` - Toggle mode
  * `P` - Toggle unit debug
  * `` ` `` - Open ingame console
  * `Space` - Toggle blending
  * `Shft`+`Esc` - Stop game

* Interactive menu modes with on-screen guide
  * Creation mode: Game terrain generation
    * Buttons
      * change_mode
      * save_game
      * generate_game
      * end_game
      * reload_assets
    * Options
      * generation_seed - Seed for random terrain generator
      * terrain_size
      * terrain_base_id
      * player_area
      * player_radius
      * load_filename
      * from_file (checkbox)
      * player_names
  * Construct mode: Terrain and unit placement
    * 5 tab object selection menu
    * Object categories:
      * terrain - terrain painting
      * Projectile - projectile sprites
      * Object - e.g. trees, bushes, rocks, mountains, corpses
      * Living - player units
      * Buildings - player buildings
  * Action mode: Unit control and gameplay!
    * Click+drag area select units
    * Attacking, woodchopping, gathering, ...
    * Basic hud
    * Shortkeys for building creation
    * Keybindings:
      * `Q` - BUILD_MENU
      * `W` - BUILD_MENU_MIL
      * `T` - TRAIN_OBJECT
      * `Y` - ENABLE_BUILDING_PLACEMENT
      * `G` - SET_ABILITY_GARRISON
      * `V` - SPAWN_VILLAGER
      * `Delete` - KILL_UNIT

Under the hood
--------------

There are some openage internals that may be of interest
but would go unnoted otherwise:

#### Python interface

Powered by [cython](http://cython.org/), we have an easy to use bidirectional
Python <-> C++ interface that even translates Exceptions between both.
See the [howto](/doc/code/pyinterface.md).


#### Inotify file reloading

You can edit any texture with your favorite image manipulation software.
When you save the changes, they'll appear in-game instantly.


#### Terminal emulator

We have an integrated [terminal emulator](/libopenage/console) supporting ecma-48.
You can run `vim` or anything else within openage.
This is neat to interactively edit scripts.


#### Buildsystem

Powered mainly by CMake and Python, our [buildsystem](/buildsystem) is dynamically
rebuilding and regenerating only the files it needs to.


#### Job management

Background tasks can be submitted and detached by our [job subsystem](/libopenage/job).
Used for sound decoding and various other computations.
