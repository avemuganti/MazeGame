
# Anand Vemuganti

# IMPORTANT!!! PLEASE READ!!!

# To run this program, please pull up the "Bitmap Display" and the "Keyboard and Display MMIO Simulator" under "Tools".
# Connect the Keyboard and Display MMIO Simulator to MIPS.

# In the bitmap display:
# Set the height and width of each unit to be 16, and the height and width of the bitmap to be 512.
# Enlarge the bitmap window as to show the entire 512 x 512 bitmap. 
# Set the base address of the bitmap display to 0x10000000 (global data). THIS IS VERY IMPORTANT! Then connect the bitmap to MIPS.

# You can now run the program. Control your character with repeated taps of WASD in the Keyboard and Display MMIO Simulator.

# You control the yellow dot. Find the exit of the maze (the green square). Running into a monster (red dots) will
# cause it to eat you, and you immediately lose the game. The maze is toroidal, as to give the appearance of being infinitely large.

# Good luck, and have fun!

.eqv	RED	0x00960018
.eqv	GRAY	0x00616161
.eqv	WHITE	0x00ffffff
.eqv	GREEN	0x00338333
.eqv	YELLOW	0x00fdce2a
.eqv	MEM	0x10000000

.data

# Load the maze itself into memory. White (movable) are 0, gray (immovable) are 1, and green (ending) is 2.
maze:	.byte	1,1,0,1,1,1,1,1,1,0,1,1,1,1,1,1,1,1,0,1,1,1,1,1,1,1,1,1,1,1,
		0,0,0,0,0,0,0,0,1,0,0,0,1,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,1,0,
		1,0,1,1,1,1,1,1,1,0,1,0,1,0,1,1,1,1,1,0,1,0,1,1,1,0,1,0,1,0,
		1,0,0,0,0,0,1,0,0,0,1,0,1,0,0,0,1,0,0,0,1,0,1,0,1,0,1,0,0,0,
		1,0,1,1,1,1,1,0,1,0,1,1,1,1,1,1,1,0,1,0,1,1,1,0,1,1,1,0,1,1,
		1,0,0,0,0,0,1,0,1,0,1,0,0,0,0,0,0,0,1,0,1,0,0,0,0,0,1,0,1,0,
		1,0,1,0,1,0,1,0,1,1,1,0,1,1,1,1,1,1,1,1,1,1,1,0,1,1,1,0,1,0,
		1,0,1,0,1,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,1,0,0,0,0,0,0,0,
		1,0,1,1,1,1,1,1,1,1,1,1,1,1,1,0,1,1,1,1,1,0,1,1,1,1,1,0,1,0,
		0,0,0,0,1,0,1,0,1,2,0,0,0,0,1,0,0,0,1,0,0,0,0,0,1,0,0,0,1,0,
		1,1,1,0,1,0,1,0,1,1,1,1,1,0,1,0,1,0,1,1,1,0,1,0,1,0,1,1,1,0,
		1,0,1,0,1,0,0,0,0,0,0,0,1,0,1,0,1,0,1,0,0,0,1,0,1,0,0,0,1,0,
		1,0,1,1,1,0,1,1,1,1,1,0,1,0,1,1,1,0,1,0,1,0,1,1,1,0,1,1,1,0,
		1,0,1,0,0,0,1,0,0,0,0,0,0,0,1,0,0,0,0,0,1,0,1,0,0,0,1,0,1,0,
		1,0,1,1,1,1,1,1,1,1,1,0,1,1,1,1,1,1,1,0,1,0,1,1,1,0,1,0,1,0,
		1,0,0,0,0,0,0,0,0,0,1,0,1,0,0,0,0,0,0,0,1,0,1,0,0,0,1,0,1,0,
		1,0,1,1,1,0,1,1,1,0,1,0,1,1,1,1,1,1,1,1,1,0,1,1,1,0,1,0,1,0,
		1,0,0,0,1,0,0,0,1,0,0,0,1,0,0,0,0,0,1,0,0,0,0,0,0,0,1,0,1,0,
		1,1,1,1,1,0,1,0,1,1,1,0,1,1,1,0,1,0,1,0,1,1,1,1,1,0,1,0,1,1,
		0,0,0,0,0,0,1,0,1,0,0,0,1,0,0,0,1,0,1,0,1,0,0,0,0,0,1,0,0,0,
		1,0,1,1,1,0,1,0,1,1,1,1,1,1,1,1,1,0,1,1,1,0,1,1,1,1,1,0,1,0,
		1,0,1,0,1,0,1,0,0,0,0,0,0,0,1,0,1,0,0,0,1,0,0,0,0,0,1,0,1,0,
		1,1,1,0,1,0,1,1,1,1,1,1,1,0,1,0,1,0,1,1,1,1,1,0,1,1,1,1,1,0,
		1,0,0,0,1,0,1,0,1,0,0,0,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,
		1,0,1,1,1,1,1,0,1,1,1,1,1,0,1,1,1,0,1,0,1,1,1,1,1,0,1,1,1,1,
		0,0,0,0,0,0,0,0,0,0,1,0,0,0,1,0,1,0,0,0,1,0,1,0,0,0,1,0,1,0,
		1,1,1,0,1,1,1,1,1,1,1,0,1,1,1,0,1,1,1,0,1,0,1,1,1,1,1,0,1,0,
		1,0,0,0,0,0,0,0,0,0,0,0,0,0,1,0,0,0,1,0,0,0,1,0,0,0,0,0,0,0,
		1,0,1,1,1,1,1,0,1,1,1,1,1,0,1,1,1,0,1,0,1,1,1,0,1,1,1,0,1,0,
		1,0,0,0,0,0,1,0,0,0,0,0,1,0,0,0,1,0,0,0,0,0,0,0,0,0,1,0,1,0

youWin:	.byte	0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,1,0,0,0,1,0,1,1,1,1,1,0,1,0,0,0,1,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,1,0,0,0,1,0,1,0,0,0,1,0,1,0,0,0,1,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,1,1,1,1,1,0,1,0,0,0,1,0,1,0,0,0,1,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,1,0,0,0,1,0,0,0,1,0,1,0,0,0,1,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,1,0,0,0,1,1,1,1,1,0,1,1,1,1,1,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,1,0,1,0,1,0,1,1,1,1,1,0,1,0,0,0,1,0,1,0,0,0,0,0,0,
		0,0,0,0,0,0,0,1,0,1,0,1,0,0,0,1,0,0,0,1,1,0,0,1,0,1,0,0,0,0,0,0,
		0,0,0,0,0,0,0,1,0,1,0,1,0,0,0,1,0,0,0,1,0,1,0,1,0,1,0,0,0,0,0,0,
		0,0,0,0,0,0,0,1,0,1,0,1,0,0,0,1,0,0,0,1,0,0,1,1,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,1,1,1,1,1,0,1,1,1,1,1,0,1,0,0,0,1,0,1,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0

youLose: .byte	0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,1,0,0,0,1,0,1,1,1,1,1,0,1,0,0,0,1,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,1,0,0,0,1,0,1,0,0,0,1,0,1,0,0,0,1,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,1,1,1,1,1,0,1,0,0,0,1,0,1,0,0,0,1,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,1,0,0,0,1,0,0,0,1,0,1,0,0,0,1,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,1,0,0,0,1,1,1,1,1,0,1,1,1,1,1,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,1,0,0,0,0,0,1,1,1,1,1,0,1,1,1,1,1,0,1,1,1,1,1,0,1,0,0,0,
		0,0,0,0,1,0,0,0,0,0,1,0,0,0,1,0,1,0,0,0,0,0,1,0,0,0,0,0,1,0,0,0,
		0,0,0,0,1,0,0,0,0,0,1,0,0,0,1,0,1,1,1,1,1,0,1,1,1,1,1,0,1,0,0,0,
		0,0,0,0,1,0,0,0,0,0,1,0,0,0,1,0,0,0,0,0,1,0,1,0,0,0,0,0,0,0,0,0,
		0,0,0,0,1,1,1,1,1,0,1,1,1,1,1,0,1,1,1,1,1,0,1,1,1,1,1,0,1,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,
		0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0

monst1X:	.word	9
monst1Y:	.word	3
monst1PrevX:	.word	0
monst1PrevY:	.word	0
monst1Dir:	.word	-1

monst2X:	.word	21
monst2Y:	.word	1
monst2PrevX:	.word	0
monst2PrevY:	.word	0
monst2Dir:	.word	-1

monst3X:	.word	13
monst3Y:	.word	9
monst3PrevX:	.word	0
monst3PrevY:	.word	0
monst3Dir:	.word	-1

monst4X:	.word	1
monst4Y:	.word	13
monst4PrevX:	.word	0
monst4PrevY:	.word	0
monst4Dir:	.word	-1

monst5X:	.word	25
monst5Y:	.word	9
monst5PrevX:	.word	0
monst5PrevY:	.word	0
monst5Dir:	.word	-1

monst6X:	.word	21
monst6Y:	.word	17
monst6PrevX:	.word	0
monst6PrevY:	.word	0
monst6Dir:	.word	-1

monst7X:	.word	3
monst7Y:	.word	21
monst7PrevX:	.word	0
monst7PrevY:	.word	0
monst7Dir:	.word	-1

monst8X:	.word	10
monst8Y:	.word	21
monst8PrevX:	.word	0
monst8PrevY:	.word	0
monst8Dir:	.word	-1

monst9X:	.word	9
monst9Y:	.word	29
monst9PrevX:	.word	0
monst9PrevY:	.word	0
monst9Dir:	.word	-1

monst10X:	.word	15
monst10Y:	.word	25
monst10PrevX:	.word	0
monst10PrevY:	.word	0
monst10Dir:	.word	-1

validX:		.word	-1, -1, -1, -1
validY:		.word	-1, -1, -1, -1
validDir:	.word	-1, -1, -1, -1

.text

li	$s0, 27 # The character's x coordinate.
li	$s1, 25 # The character's y coordinate.

li	$s2, 0 # Character's pseudo x coordinate.
li	$s3, 0 # Character's pseudo y coordinate.

li	$s4, 24 # The display x coordinate.
li	$s5, 22 # The display y coordinate.

li	$s7, -1 # The inverse of the directiom the player just went.

jal	draw

loop:
# Check input.
lw	$s6, 0xffff0000
beqz	$s6, loop
# Process input.
lw	$s6, 0xffff0004
beq	$s6, 119, north # W
beq	$s6, 97, west # A
beq	$s6, 115, south # S
beq	$s6, 100, east # D
j	loop

north:
jal	moveNorth
jal	moveMonsters
jal	draw
j 	loop
east:
jal	moveEast
jal	moveMonsters
jal	draw
j	loop
south:
jal	moveSouth
jal	moveMonsters
jal	draw
j	loop
west:
jal	moveWest
jal	moveMonsters
jal	draw
j	loop

exit:
jal	draw
li	$v0, 32
li	$a0, 2000
syscall
jal	displayWin
li	$v0, 10
syscall

lose:
li	$v0, 32
li	$a0, 2000
syscall
jal	displayLoss
li	$v0, 10
syscall

############################ DRAW #################################

draw:

subi	$sp, $sp, 4
sw	$ra, ($sp)

move	$a0, $s4
move	$a1, $s5
jal	drawBitmap

li	$v0, 32
li	$a0, 30
syscall
# The above is to make sure that the character/monsters are drawn on top of the map.

jal	drawMonsters
jal	calcCollisions

move	$a0, $s2
move	$a1, $s3
jal	drawCharacter

lw	$ra, ($sp)
addi	$sp, $sp, 4

jr	$ra

############################ DRAW SQUARE #################################

drawSquare: # a0 is mazeX, a1 is mazeY, a2 is bitmapX, a3 is bitmapY.

# Adjust for x, y >= 30.

subi	$sp, $sp, 4
sw	$ra, ($sp)

jal	fixCoords

move	$a0, $v0
move	$a1, $v1

# Find the color of the associated maze square. Put this in $t0.

la	$t0, maze
mul	$a1, $a1, 30
add	$t0, $t0, $a1
add	$t0, $t0, $a0 # Now the address of the element at x, y should be correct.
lb	$t0, ($t0)
beqz	$t0, white
beq	$t0, 1, gray
li	$t0, GREEN
j	doneColor
white:
li	$t0, WHITE
j 	doneColor
gray:
li	$t0, GRAY
doneColor:

# Draw this color onto the appropriate location of the bitmap. Bitmap x and y are 0-7 inclusive.

li	$t1, MEM
mul	$a3, $a3, 512
mul	$a2, $a2, 16
add	$t1, $t1, $a2
add	$t1, $t1, $a3 # Now the address of the upper left hand corner of the square should be correct.

move	$t3, $zero # t3 is the counter for the outer loop.
drawLoopOuter:
move	$t2, $zero # t2 is the counter for the inner loop.
drawLoopInner:
sw	$t0, ($t1)
addi	$t1, $t1, 4
addi	$t2, $t2, 1
blt	$t2, 4, drawLoopInner
addi	$t1, $t1, 112
addi	$t3, $t3, 1
blt	$t3, 4, drawLoopOuter

lw	$ra, ($sp)
addi	$sp, $sp, 4
jr	$ra

############################ DRAW BITMAP #################################

drawBitmap: # a0 is the mazeX, a1 is the mazeY. These correspond to the top left corner of the bitmap.

subi	$sp, $sp, 4
sw	$ra, ($sp)

jal 	fixCoords

move	$t4, $v0
move	$t5, $v1

# Loop through all values from 0-7 two-dimensionally.

move	$t7, $zero # Outer loop counter [y-loop]
drawBitOuter:
move	$t6, $zero # Inner loop counter [x-loop]
drawBitInner: 
move	$a0, $t4
move	$a1, $t5
move	$a2, $t6
move	$a3, $t7
jal	drawSquare
addi	$t4, $t4, 1
addi	$t6, $t6, 1
blt	$t6, 8, drawBitInner
subi	$t4, $t4, 8
addi	$t5, $t5, 1
addi	$t7, $t7, 1
blt	$t7, 8, drawBitOuter

lw	$ra, ($sp)
addi	$sp, $sp, 4
jr 	$ra

############################ DRAW CHARACTER #################################

drawCharacter: # a0 is the x value (0 or 1), and a1 is the y value (0 or 1).

li	$t0, MEM
addi	$t0, $t0, 1716
mul	$a0, $a0, 16
mul	$a1, $a1, 512
add	$t0, $t0, $a0
add	$t0, $t0, $a1

li	$t1, YELLOW
sw	$t1, ($t0)
sw	$t1, 4($t0)
sw	$t1, 128($t0)
sw	$t1, 132($t0)

jr	$ra

############################ GET SQUARE #################################

getSquare: # a0 is the x coordinate, a1 is the y coordinate. $v0 will be the number code (0, 1, or 2) of the square.
 
subi	$sp, $sp, 4
sw	$ra, ($sp)

jal	fixCoords

move	$a0, $v0
move	$a1, $v1

la	$t9, maze
mul	$a1, $a1, 30
add	$t9, $t9, $a1
add	$t9, $t9, $a0 
lb	$v0, ($t9)

lw	$ra, ($sp)
addi	$sp, $sp, 4
jr	$ra

############################ FIX COORDS #################################

fixCoords: # Takes an a0 and a1 as x and y coordinates. Fixes them, and returns as v0 and v1.

bge	$a0, 30, sub30x
endSub30x:
bge	$a1, 30, sub30y
endSub30y:
bltz	$a0, add30x
endAdd30x:
bltz	$a1, add30y
j 	endAdj
sub30x:
sub	$a0, $a0, 30
j 	endSub30x
sub30y:
sub	$a1, $a1, 30
j	endSub30y
add30x:
add	$a0, $a0, 30
j	endAdd30x
add30y:
add	$a1, $a1, 30
endAdj:

move	$v0, $a0
move	$v1, $a1
jr 	$ra

############################ MOVE NORTH #################################

moveNorth:

subi	$sp, $sp, 4
sw	$ra, ($sp)

li	$s7, 2
move	$a0, $s0
subi	$a1, $s1, 1
jal	getSquare
beq	$v0, 1, endNorth

subi	$s1, $s1, 1
move	$a0, $s0
move	$a1, $s1
jal	fixCoords
move	$s0, $v0
move	$s1, $v1

beq	$s3, 1, subPseudoY 

subi	$s5, $s5, 1
move	$a0, $s4
move	$a1, $s5
jal	fixCoords
move	$s4, $v0
move	$s5, $v1
j 	endNorth

subPseudoY:
subi	$s3, $s3, 1

endNorth:
move	$a0, $s0
move	$a1, $s1
jal	getSquare
beq	$v0, 2, exit
lw	$ra, ($sp)
addi	$sp, $sp, 4
jr 	$ra

############################ MOVE EAST #################################

moveEast:

subi	$sp, $sp, 4
sw	$ra, ($sp)

li	$s7, 3
addi	$a0, $s0, 1
move	$a1, $s1
jal	getSquare
beq	$v0, 1, endEast

addi	$s0, $s0, 1
move	$a0, $s0
move	$a1, $s1
jal	fixCoords
move	$s0, $v0
move	$s1, $v1

beq	$s2, 0, addPseudoX 

addi	$s4, $s4, 1
move	$a0, $s4
move	$a1, $s5
jal	fixCoords
move	$s4, $v0
move	$s5, $v1
j	endEast

addPseudoX:
addi	$s2, $s2, 1

endEast:
move	$a0, $s0
move	$a1, $s1
jal	getSquare
beq	$v0, 2, exit
lw	$ra, ($sp)
addi	$sp, $sp, 4
jr 	$ra

############################ MOVE SOUTH #################################

moveSouth:

subi	$sp, $sp, 4
sw	$ra, ($sp)

li	$s7, 0
move	$a0, $s0
addi	$a1, $s1, 1
jal	getSquare
beq	$v0, 1, endSouth


addi	$s1, $s1, 1
move	$a0, $s0
move	$a1, $s1
jal	fixCoords
move	$s0, $v0
move	$s1, $v1

beq	$s3, 0, addPseudoY 

addi	$s5, $s5, 1
move	$a0, $s4
move	$a1, $s5
jal	fixCoords
move	$s4, $v0
move	$s5, $v1

j 	endSouth

addPseudoY:
addi	$s3, $s3, 1

endSouth:
move	$a0, $s0
move	$a1, $s1
jal	getSquare
beq	$v0, 2, exit
lw	$ra, ($sp)
addi	$sp, $sp, 4
jr 	$ra

############################ MOVE WEST #################################

moveWest:

subi	$sp, $sp, 4
sw	$ra, ($sp)

li	$s7, 1
subi	$a0, $s0, 1
move	$a1, $s1
jal	getSquare
beq	$v0, 1, endWest

subi	$s0, $s0, 1
move	$a0, $s0
move	$a1, $s1
jal	fixCoords
move	$s0, $v0
move	$s1, $v1

beq	$s2, 1, subPseudoX 

subi	$s4, $s4, 1
move	$a0, $s4
move	$a1, $s5
jal	fixCoords
move	$s4, $v0
move	$s5, $v1
j 	endWest

subPseudoX:
subi	$s2, $s2, 1

endWest:
move	$a0, $s0
move	$a1, $s1
jal	getSquare
beq	$v0, 2, exit
lw	$ra, ($sp)
addi	$sp, $sp, 4
jr 	$ra

############################ DISPLAY WIN #################################

displayWin:
li	$t0, MEM
la	$t1, youWin
li	$t2, 0 # The loop counter.
winLoop:
lb	$t3, ($t1)
beqz	$t3, gry
li	$t4, GREEN
sw	$t4, ($t0)
addi	$t0, $t0, 4
addi	$t1, $t1, 1
addi	$t2, $t2, 1
blt	$t2, 1024, winLoop
j	endDispWin
gry:	
li	$t4, GRAY
sw	$t4, ($t0)
addi	$t0, $t0, 4
addi	$t1, $t1, 1
addi	$t2, $t2, 1
blt	$t2, 1024, winLoop

endDispWin:
jr	$ra

############################ ON SCREEN LOCATION #################################

onScreenLoc: # a0 is the x coordinate, and a1 is the y coordinate. Returns bitmap coords in v0 and v1. These will be -1 if offscreen.

sub	$a0, $a0, $s4
sub	$a1, $a1, $s5
bltz	$a0, add30OSLX
contOSL1:
bltz	$a1, add30OSLY
contOSL2:
bgt	$a0, 7, retFalseOSL
bgt	$a1, 7, retFalseOSL
move	$v0, $a0
move	$v1, $a1
j	retOSL

add30OSLX:
addi	$a0, $a0, 30
j	contOSL1

add30OSLY:
addi	$a1, $a1, 30
j	contOSL2

retFalseOSL:
li	$v0, -1
li	$v1, -1

retOSL:
jr	$ra

############################ REVERSE DIRECTION #################################

revDirec: # a0 is the direction code. v0 becomes the reversed direction.
bge	$a0, 2, subRevDirec
addi	$v0, $a0, 2
j 	retRevDirec
subRevDirec:
subi	$v0, $a0, 2
retRevDirec:
jr	$ra

############################ MOVE MONSTERS #################################

moveMonsters: # DEPENDS ON NUMBER OF MONSTERS

subi	$sp, $sp, 4
sw	$ra, ($sp)

# Move Monster 1:

lw	$a0, monst1X
lw	$a1, monst1Y
lw	$a2, monst1PrevX
lw	$a3, monst1PrevY
lw	$v1, monst1Dir
jal	moveMonster
sw	$a0, monst1X
sw	$a1, monst1Y
sw	$a2, monst1PrevX
sw	$a3, monst1PrevY
sw	$v1, monst1Dir

# Move Monster 2:

lw	$a0, monst2X
lw	$a1, monst2Y
lw	$a2, monst2PrevX
lw	$a3, monst2PrevY
lw	$v1, monst2Dir
jal	moveMonster
sw	$a0, monst2X
sw	$a1, monst2Y
sw	$a2, monst2PrevX
sw	$a3, monst2PrevY
sw	$v1, monst2Dir

# Move Monster 3:

lw	$a0, monst3X
lw	$a1, monst3Y
lw	$a2, monst3PrevX
lw	$a3, monst3PrevY
lw	$v1, monst3Dir
jal	moveMonster
sw	$a0, monst3X
sw	$a1, monst3Y
sw	$a2, monst3PrevX
sw	$a3, monst3PrevY
sw	$v1, monst3Dir

# Move Monster 4:

lw	$a0, monst4X
lw	$a1, monst4Y
lw	$a2, monst4PrevX
lw	$a3, monst4PrevY
lw	$v1, monst4Dir
jal	moveMonster
sw	$a0, monst4X
sw	$a1, monst4Y
sw	$a2, monst4PrevX
sw	$a3, monst4PrevY
sw	$v1, monst4Dir

# Move Monster 5:

lw	$a0, monst5X
lw	$a1, monst5Y
lw	$a2, monst5PrevX
lw	$a3, monst5PrevY
lw	$v1, monst5Dir
jal	moveMonster
sw	$a0, monst5X
sw	$a1, monst5Y
sw	$a2, monst5PrevX
sw	$a3, monst5PrevY
sw	$v1, monst5Dir

# Move Monster 6:

lw	$a0, monst6X
lw	$a1, monst6Y
lw	$a2, monst6PrevX
lw	$a3, monst6PrevY
lw	$v1, monst6Dir
jal	moveMonster
sw	$a0, monst6X
sw	$a1, monst6Y
sw	$a2, monst6PrevX
sw	$a3, monst6PrevY
sw	$v1, monst6Dir

# Move Monster 7:

lw	$a0, monst7X
lw	$a1, monst7Y
lw	$a2, monst7PrevX
lw	$a3, monst7PrevY
lw	$v1, monst7Dir
jal	moveMonster
sw	$a0, monst7X
sw	$a1, monst7Y
sw	$a2, monst7PrevX
sw	$a3, monst7PrevY
sw	$v1, monst7Dir

# Move Monster 8:

lw	$a0, monst8X
lw	$a1, monst8Y
lw	$a2, monst8PrevX
lw	$a3, monst8PrevY
lw	$v1, monst8Dir
jal	moveMonster
sw	$a0, monst8X
sw	$a1, monst8Y
sw	$a2, monst8PrevX
sw	$a3, monst8PrevY
sw	$v1, monst8Dir

# Move Monster 9:

lw	$a0, monst9X
lw	$a1, monst9Y
lw	$a2, monst9PrevX
lw	$a3, monst9PrevY
lw	$v1, monst9Dir
jal	moveMonster
sw	$a0, monst9X
sw	$a1, monst9Y
sw	$a2, monst9PrevX
sw	$a3, monst9PrevY
sw	$v1, monst9Dir

# Move Monster 10:

lw	$a0, monst10X
lw	$a1, monst10Y
lw	$a2, monst10PrevX
lw	$a3, monst10PrevY
lw	$v1, monst10Dir
jal	moveMonster
sw	$a0, monst10X
sw	$a1, monst10Y
sw	$a2, monst10PrevX
sw	$a3, monst10PrevY
sw	$v1, monst10Dir

# Fix all the monster coords:

lw	$a0, monst1X
lw	$a1, monst1Y
jal 	fixCoords
sw	$v0, monst1X
sw	$v1, monst1Y

lw	$a0, monst2X
lw	$a1, monst2Y
jal 	fixCoords
sw	$v0, monst2X
sw	$v1, monst2Y

lw	$a0, monst3X
lw	$a1, monst3Y
jal 	fixCoords
sw	$v0, monst3X
sw	$v1, monst3Y

lw	$a0, monst4X
lw	$a1, monst4Y
jal 	fixCoords
sw	$v0, monst4X
sw	$v1, monst4Y

lw	$a0, monst5X
lw	$a1, monst5Y
jal 	fixCoords
sw	$v0, monst5X
sw	$v1, monst5Y

lw	$a0, monst6X
lw	$a1, monst6Y
jal 	fixCoords
sw	$v0, monst6X
sw	$v1, monst6Y

lw	$a0, monst7X
lw	$a1, monst7Y
jal 	fixCoords
sw	$v0, monst7X
sw	$v1, monst7Y

lw	$a0, monst8X
lw	$a1, monst8Y
jal 	fixCoords
sw	$v0, monst8X
sw	$v1, monst8Y

lw	$a0, monst9X
lw	$a1, monst9Y
jal 	fixCoords
sw	$v0, monst9X
sw	$v1, monst9Y

lw	$a0, monst10X
lw	$a1, monst10Y
jal 	fixCoords
sw	$v0, monst10X
sw	$v1, monst10Y

lw	$ra, ($sp)
addi	$sp, $sp, 4
jr	$ra

############################ MOVE MONSTER #################################

moveMonster: # a0 is x, a1 is y, a2 is prevX, a3 is prevY, v1 is direction.

subi	$sp, $sp, 4
sw	$ra, ($sp)

move	$t0, $a0
move	$t1, $a1
move	$t2, $a2
move	$t3, $a3
li	$t5, 0 # Represents the running number of valid squares
la	$t6, validX
la	$t7, validY
la	$t8, validDir
# Check north
move	$a0, $t0
subi	$a1, $t1, 1
beq	$a1, $t3, checkEastMon
jal	getSquare
beq	$v0, 1, checkEastMon
addi	$t5, $t5, 1
sw	$t0, ($t6)
subi	$t4, $t1, 1
sw	$t4, ($t7)
li	$t4, 0
sw	$t4, ($t8)
addi	$t6, $t6, 4
addi	$t7, $t7, 4
addi	$t8, $t8, 4
# Check east
checkEastMon:
addi	$a0, $t0, 1
move	$a1, $t1
beq	$a0, $t2, checkSouthMon
jal	getSquare
beq	$v0, 1, checkSouthMon
addi	$t5, $t5, 1
addi	$t4, $t0, 1
sw	$t4, ($t6)
sw	$t1, ($t7)
li	$t4, 1
sw	$t4, ($t8)
addi	$t6, $t6, 4
addi	$t7, $t7, 4
addi	$t8, $t8, 4
# Check south
checkSouthMon:
move	$a0, $t0
addi	$a1, $t1, 1
beq	$a1, $t3, checkWestMon
jal	getSquare
beq	$v0, 1, checkWestMon
addi	$t5, $t5, 1
sw	$t0, ($t6)
addi	$t4, $t1, 1
sw	$t4, ($t7)
li	$t4, 2
sw	$t4, ($t8)
addi	$t6, $t6, 4
addi	$t7, $t7, 4
addi	$t8, $t8, 4
# Check west
checkWestMon:
subi	$a0, $t0, 1
move	$a1, $t1
beq	$a0, $t2, randMon
jal	getSquare
beq	$v0, 1, randMon
addi	$t5, $t5, 1
subi	$t4, $t0, 1
sw	$t4, ($t6)
sw	$t1, ($t7)
li	$t4, 3
sw	$t4, ($t8)
randMon:
# Find a random number from 0 to # valid squares - 1:
# If there are no valid squares, move back to the previous square.
beqz	$t5, goBackMon
move	$a1, $t5
li	$v0, 42
syscall # Random number is now in a0.
la	$t6, validX
la	$t7, validY
la	$t8, validDir
sll	$a0, $a0, 2
add	$t6, $t6, $a0
add	$t7, $t7, $a0
add	$t8, $t8, $a0
move	$a2, $t0
move	$a3, $t1
lw	$a0, ($t6)
lw	$a1, ($t7)
lw	$v1, ($t8)
j	endMoveMon
goBackMon:
move	$a2, $t0
move	$a3, $t1
move	$t4, $t2 # Move to a0 later.
move	$a1, $t3
move	$a0, $v1
jal	revDirec
move	$v1, $v0
move	$a0, $t4
endMoveMon:

lw 	$ra, ($sp)
addi	$sp, $sp, 4
jr	$ra

############################ DRAW MONSTER AT LOCATION #################################

drawMonAtLoc: # a0 is the bitmap X, and a1 is the bitmap Y.
# Find the "base" location to draw at.
li	$t0, MEM
addi	$t0, $t0, 132
sll	$a0, $a0, 4
sll	$a1, $a1, 9
add	$t0, $t0, $a0
add	$t0, $t0, $a1
# Now, draw the object.
li	$t1, RED
sw	$t1, ($t0)
sw	$t1, 4($t0)
sw	$t1, 128($t0)
sw	$t1, 132($t0)
jr	$ra

############################ DRAW MONSTERS #################################

drawMonsters: # DEPENDS ON NUMBER OF MONSTERS.

subi	$sp, $sp, 4
sw	$ra, ($sp)

lw	$a0, monst1X
lw	$a1, monst1Y
jal	onScreenLoc
beq	$v0, -1, drawMon2
move	$a0, $v0
move	$a1, $v1
jal	drawMonAtLoc

drawMon2:
lw	$a0, monst2X
lw	$a1, monst2Y
jal	onScreenLoc
beq	$v0, -1, drawMon3
move	$a0, $v0
move	$a1, $v1
jal	drawMonAtLoc

drawMon3:
lw	$a0, monst3X
lw	$a1, monst3Y
jal	onScreenLoc
beq	$v0, -1, drawMon4
move	$a0, $v0
move	$a1, $v1
jal	drawMonAtLoc

drawMon4:
lw	$a0, monst4X
lw	$a1, monst4Y
jal	onScreenLoc
beq	$v0, -1, drawMon5
move	$a0, $v0
move	$a1, $v1
jal	drawMonAtLoc

drawMon5:
lw	$a0, monst5X
lw	$a1, monst5Y
jal	onScreenLoc
beq	$v0, -1, drawMon6
move	$a0, $v0
move	$a1, $v1
jal	drawMonAtLoc

drawMon6:
lw	$a0, monst6X
lw	$a1, monst6Y
jal	onScreenLoc
beq	$v0, -1, drawMon7
move	$a0, $v0
move	$a1, $v1
jal	drawMonAtLoc

drawMon7:
lw	$a0, monst7X
lw	$a1, monst7Y
jal	onScreenLoc
beq	$v0, -1, drawMon8
move	$a0, $v0
move	$a1, $v1
jal	drawMonAtLoc

drawMon8:
lw	$a0, monst8X
lw	$a1, monst8Y
jal	onScreenLoc
beq	$v0, -1, drawMon9
move	$a0, $v0
move	$a1, $v1
jal	drawMonAtLoc

drawMon9:
lw	$a0, monst9X
lw	$a1, monst9Y
jal	onScreenLoc
beq	$v0, -1, drawMon10
move	$a0, $v0
move	$a1, $v1
jal	drawMonAtLoc

drawMon10:
lw	$a0, monst10X
lw	$a1, monst10Y
jal	onScreenLoc
beq	$v0, -1, endDrawMon
move	$a0, $v0
move	$a1, $v1
jal	drawMonAtLoc

endDrawMon:
lw	$ra, ($sp)
addi	$sp, $sp, 4
jr	$ra

############################ CALCULATE COLLISIONS #################################

calcCollisions: # DEPENDS ON NUMBER OF MONSTERS.

subi	$sp, $sp, 4
sw	$ra, ($sp)

lw	$a0, monst1X
lw	$a1, monst1Y
lw	$a2, monst1PrevX
lw	$a3, monst1PrevY
lw	$v1, monst1Dir
jal	calcCollisionsMonst

lw	$a0, monst2X
lw	$a1, monst2Y
lw	$a2, monst2PrevX
lw	$a3, monst2PrevY
lw	$v1, monst2Dir
jal	calcCollisionsMonst

lw	$a0, monst3X
lw	$a1, monst3Y
lw	$a2, monst3PrevX
lw	$a3, monst3PrevY
lw	$v1, monst3Dir
jal	calcCollisionsMonst

lw	$a0, monst4X
lw	$a1, monst4Y
lw	$a2, monst4PrevX
lw	$a3, monst4PrevY
lw	$v1, monst4Dir
jal	calcCollisionsMonst

lw	$a0, monst5X
lw	$a1, monst5Y
lw	$a2, monst5PrevX
lw	$a3, monst5PrevY
lw	$v1, monst5Dir
jal	calcCollisionsMonst

lw	$a0, monst6X
lw	$a1, monst6Y
lw	$a2, monst6PrevX
lw	$a3, monst6PrevY
lw	$v1, monst6Dir
jal	calcCollisionsMonst

lw	$a0, monst7X
lw	$a1, monst7Y
lw	$a2, monst7PrevX
lw	$a3, monst7PrevY
lw	$v1, monst7Dir
jal	calcCollisionsMonst

lw	$a0, monst8X
lw	$a1, monst8Y
lw	$a2, monst8PrevX
lw	$a3, monst8PrevY
lw	$v1, monst8Dir
jal	calcCollisionsMonst

lw	$a0, monst9X
lw	$a1, monst9Y
lw	$a2, monst9PrevX
lw	$a3, monst9PrevY
lw	$v1, monst9Dir
jal	calcCollisionsMonst

lw	$a0, monst10X
lw	$a1, monst10Y
lw	$a2, monst10PrevX
lw	$a3, monst10PrevY
lw	$v1, monst10Dir
jal	calcCollisionsMonst

lw	$ra, ($sp)
addi	$sp, $sp, 4
jr	$ra

############################ CALCULATE COLLISIONS FOR MONSTER #################################

calcCollisionsMonst: # a0 is x, a1 is y, a2 is prevX, a3 is prevY, v1 is dir.

# Check for first type of collision (monster and player on same square)
beq	$a0, $s0, calcCol1

# Check for second type of collision (monster and player pass each other).
col2:
beq	$a2, $s0, calcCol2

endCalcCol:
jr	$ra

calcCol1:
beq	$a1, $s1, lose
j	col2

calcCol2:
beq	$a3, $s1, calcCol3
j	endCalcCol

calcCol3:
beq	$s7, $v1, lose
j	endCalcCol

############################ DISPLAY LOSS #################################

displayLoss:

li	$t0, MEM
la	$t1, youLose
li	$t2, 0 # The loop counter.
lossLoop:
lb	$t3, ($t1)
beqz	$t3, grey
li	$t4, RED
sw	$t4, ($t0)
addi	$t0, $t0, 4
addi	$t1, $t1, 1
addi	$t2, $t2, 1
blt	$t2, 1024, lossLoop
j	endDispLoss
grey:	
li	$t4, GRAY
sw	$t4, ($t0)
addi	$t0, $t0, 4
addi	$t1, $t1, 1
addi	$t2, $t2, 1
blt	$t2, 1024, lossLoop

endDispLoss:
jr	$ra



		
