# Mastermind
FPGA implementation of the popular logic game using VHDL and Altera DE1. It stands by the [original rules](https://en.wikipedia.org/wiki/Mastermind_(board_game)) of this game, except for the secret pattern of four code pegs, that can contain duplicates. For this project, we used Quartus 13.0sp1, for it's the last version supporting our board Altera DE1, who is mounting a Cyclone II FPGA. 

## How it works

It's a project divided in three parts: **data-path**, **control-unit** and **view** (like MVC pattern for high-level applications). There are also some files supporting **VGA communications** with displays.
### Data-path
It's represented by a single file, **datapath.vhd**, that contains, among other things, a finite state machine mantaining game data memorized and computing changes related to user inputs.

### Control-unit
It's represented by a single file, **controller.vhd**, that contains a process handling user inputs appropriately, to avoid sending asserted signals to other modules more than enough.

### View
It's represented by a single file, **view.vhd**, which contains, among other things, a finite state machine describing the current part of the scene which is being written to the SRAM (see next section for this).

### VGA communications
It's represented by a single master file, **vga_framebuffer**, which instantiates many other modules inside, such as **vga_timing** or **text_controller**, to appropriately manage VGA communications with displays and SRAM read/write access. This because, in particular, for this project, we chose to use a framebuffer (represented by the board's SRAM), to comfortably write (in terms of timing) the next scene to be rendered on screen while outputting the current one. If you're not familiar with VGA in such low-level terms and you're interested in knowing more, we suggest you to read our files inside **docs** folder or this [webpage](https://eewiki.net/pages/viewpage.action?pageId=15925278)

## Docs

Inside folder **docs**, you can find some documents, where all the files in this repository (that were not generated automatically by our IDE), among many other things, are described in detail, if you are interested.

## Automatically generated folders and files

There are some folders and files (**db**, **incremental_db** and **output_files**) that were automatically generated by our IDE: we will not explain their functionality here; if you're interested, please refer to our **docs** folder or to [Quartus documentation](https://www.altera.com/content/dam/altera-www/global/en_US/pdfs/literature/hb/qts/archives/quartusii_handbook_archive_130.pdf).

## License and more

Mastermind is published under **MIT License**. Special thanks to [**Primiano Tucci**](https://github.com/primiano), for his [Tetris](https://github.com/primiano/tetris-vhdl) implementation, and to [**Derek Wang**](https://github.com/Derek-X-Wang), for his [VGA-Text-Generator](https://github.com/Derek-X-Wang/VGA-Text-Generator).

Copyright (©) [**Davide Di Donato**](https://github.com/MrOverflOOw), **Silvia Damiani** & **Marco Valli** 2018.
