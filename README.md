# MazeGame

You are a hero (the yellow dot) navigating through a toroidal maze, trying to find the exit (the green square), while monsters (the red dots) are roaming around and trying to eat you. Use WASD to control your character. Can you make it out alive?

IMPORTANT!!! PLEASE READ!!!

To run this program, please pull up the "Bitmap Display" and the "Keyboard and Display MMIO Simulator" under "Tools".
Connect the Keyboard and Display MMIO Simulator to MIPS.

In the bitmap display:
Set the height and width of each unit to be 16, and the height and width of the bitmap to be 512.
Enlarge the bitmap window as to show the entire 512 x 512 bitmap. 
Set the base address of the bitmap display to 0x10000000 (global data). THIS IS VERY IMPORTANT! Then connect the bitmap to MIPS.

You can now run the program. Control your character with repeated taps of WASD in the Keyboard and Display MMIO Simulator.

You control the yellow dot. Find the exit of the maze (the green square). Running into a monster (red dot) will
cause it to eat you, and you immediately lose the game. The monsters move randomly around the maze, but will not move to a space that it just occupied UNLESS it has hit a dead end. The maze is toroidal, as to give the appearance of being infinitely large.

Good luck, and have fun!

Sample Run: https://vimeo.com/664100444/e41cc7aa9f
