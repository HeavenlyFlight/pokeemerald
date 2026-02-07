# Pokémon Emerald

This is a fork of the [matching decompilation](https://github.com/pret/pokeemerald) at [PRET](https://github.com/pret).

This fork tries to maintain vanilla compatibility whenever possible. It doesn't increase the size of any save data structure or the object event structure.

* [HGSS-style pokémon followers](https://bulbapedia.bulbagarden.net/wiki/Walking_Pok%C3%A9mon#Pok.C3.A9mon_HeartGold_and_SoulSilver) for all 386 pokémon (including forms & shinies)
* Includes follower emotes and a majority of the HGSS messages. 
in a backwards compatible way
* Custom pokeball sprites for Gen 1-7 pokéballs
* Followers can use field moves in the overworld
* Overworld form changes for Ditto, Mew, Castform, etc.
* Asymmetrical & 64x64 OW support. includes expands OW graphicsIds to 16-bits
in a backwards compatible way
* Dynamic Overworld Palette System (DOWP) & reflections compatible with berry trees, etc.
* ![Pokeball](https://i.imgur.com/OMbS67Q.gif)
![Messages](https://i.imgur.com/sTbGVEY.gif)
![Forms](https://i.imgur.com/wDhFNf4.gif)
![HM](https://i.imgur.com/lnXJGHd.gif)
* All pokemon icons updated to Gen 6, based on [this repo](https://github.com/msikma/pokesprite/tree/master/icons/pokemon/regular) (not the pokemon itself, no extra mons added)
* This includes compatibility with the PC, trade, contests, mail, Battle Dome. Examples:
![PC](https://i.imgur.com/wzwJfd1.png)
![Party](https://i.imgur.com/8hbE88t.png)
![Contest](https://i.imgur.com/S9mCEFL.png)
* Icons share palettes with front sprites, meaning that shiny pokemon will also have shiny icons!
* Day/night shading compatible with weather.
* GSC-style window lights.
* WIP interframe-blended lamp lights at night, i.e in Rustboro.
* HGSS-style alpha-blended shadows for object events.
* Includes support for compressed OW graphics
* Clock can be reset pressing R while watching it
* hidden type potency and coloring
* gendered textboxes

To set up the repository, see [INSTALL.md](INSTALL.md).
To set up the repository, see [INSTALL.md](INSTALL.md).

## FAQ
### `(followers*)` Q: Where are the config settings?
A: Configuration for the follower system is mostly in [event_objects.h](include/constants/event_objects.h):
```c
// If true, follower pokemon will bob up and down
// during their idle & walking animations
#define OW_MON_BOBBING  TRUE

// If true, adds a small amount of overhead
// to OW code so that large (48x48, 64x64) OWs
// will display correctly under bridges, etc.
#define LARGE_OW_SUPPORT TRUE

// Followers will emerge from the pokeball they are stored in,
// instead of a normal pokeball
#define OW_MON_POKEBALLS TRUE

// New/old handling for followers during scripts;
// TRUE: Script collisions hide follower, FLAG_SAFE_FOLLOWER_MOVEMENT on by default
// (scripted player movement moves follower too!)
// FALSE: Script collisions unhandled, FLAG_SAFE_FOLLOWER_MOVEMENT off by default
#define OW_MON_SCRIPT_MOVEMENT TRUE

// If set, the only pokemon allowed to follow you
// will be those matching species, met location,
// and/or met level;
// These accept vars, too: VAR_TEMP_1, etc
#define OW_MON_ALLOWED_SPECIES (0)
#define OW_MON_ALLOWED_MET_LVL (0)
#define OW_MON_ALLOWED_MET_LOC (0)
```

### `(lighting)` Q: How do I mark certain colors in a palette as light-blended?
A: Create a `.pla` file in the same folder as the `.pal` with the same name.

In this file you can enter color indices [0,15]
on separate lines to mark those colors as being light-blended, i.e:

`06.pla:`
```
# A comment
0 # if color 0 is listed, uses it to blend with instead of the default!
1
9
10
```

For contacts and other pret projects, see [pret.github.io](https://pret.github.io/).
