# PyxelChip8

## Introduction

PyxelChip8 is a CHIP-8/SUPER-CHIP emulator that runs on Pyxel/Python library.
[Dev Notes](https://github.com/jay-kumogata/PyxelChip8/blob/main/doc/220505_DevNotes.md) here.

<img src="https://github.com/jay-kumogata/PyxelChip8/blob/main/screenshots/amabie02.gif" width="256"> <img src="https://github.com/jay-kumogata/PyxelChip8/blob/main/screenshots/invaders01.gif" width="256"> <img src="https://github.com/jay-kumogata/PyxelChip8/blob/main/screenshots/brix01.gif" width="256"> <img src="https://github.com/jay-kumogata/PyxelChip8/blob/main/screenshots/dodge01.gif" width="256">  <img src="https://github.com/jay-kumogata/PyxelChip8/blob/main/screenshots/lunar01.gif" width="256"> <img src="https://github.com/jay-kumogata/PyxelChip8/blob/main/screenshots/test_opcode.gif" width="256"> 

## How to Play

- (a) Install the Python3.8 (python-3.8.9.exe), which can be obtained from https://www.python.org/downloads/
- (b) Install the Pyxel1.7.0 on Python from the command line:  
  - C> pip install pyxel
- (c) Unzip the Chip8 Game Pack (c8games.zip) archive, which can be obtained from http://www.zophar.net/roms.phtml?op=show&type=chip8
- (d) From the command line, run:
  - C> python PyxelChip8.py \<ROM file name\>
  - Example: C> python PyxelChip8.py c8games/VBRIX
- (e) Click [x] when finished

## How to control
  
The keys are mapped as follows.

	Original |1|2|3|C| Mapping to |1|2|3|4|
	         |4|5|6|D|            |Q|W|E|R|
	         |7|8|9|E|            |A|S|D|F|
	         |A|0|B|F|            |Z|X|C|V|

In addition, 5/7/8/9 are mapped to the Up/Left/Down/Right arrow keys.

## Specification
### Memory
- RAM (200H - F10H)
- Small Hexadecimal font (F10H - F5FH)
- Big Hexadecimal font (F60H - FFFH)

### Registers
- Data Registers (V0 .. VF)
- Address Registers (I)
- Timers (Delay and Sound)
- Stack (16 word length and stack pointer)

### Graphics
- Sprite (Size: 8 x 1 .. 15, 16 x 16 pixel)
- Collision Flag
- Small and big hexadecimal fonts (Size: 8 x 5, 8 x 10 pixel)

### Instruction set
- CHIP-8 instructions 
  - Assignment, Arithmetic, Conditional Branch, Subroutine Call, Draw Sprite, etc.
- SUPER-CHIP instructions 
  - Halt, Enable/Disable High-resolution mode, Draw 16x16 sprite, 
  - Scroll down/left/right, Big font sprites
- XO-CHIP instructions
  - Scroll up

### Keyboard
- Hexadecimal keyboard
