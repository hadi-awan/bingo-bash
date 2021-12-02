# LINUX

A bash program to play a game called LINUX (much like BINGO)

## Description

User runs LINUX with a Card (basically, a 5x5 matrix of integers).
LINUX "calls" (provides) random numbers one-by-one. Each time a number
is called, if that number appears on the user's Card, it is "marked".
User wins when a row, or column, or all 4 corners, becomes marked.

## LINUX CARD

A LINUX Card has 5 columns of 5 numbers each.
The number in the middle must ALWAYS be zero (gets marked for free).
column 1 contains 5 unique integers in [01-15]
column 2 contains 5 unique integers in [16-30]
column 3 contains 4 unique integers in [31-45] plus middle integer 00
column 4 contains 5 unique integers in [46-60]
column 5 contains 5 unique integers in [61-75]
Card numbers must have exactly 2 digits, and be separated by one space,
with no extraneous whitespace, not even at the start or end of a line.
e.g. of a LINUX Card:
12 23 42 55 74
04 19 34 46 72
07 17 00 51 69
11 30 44 56 62
09 27 40 47 67

## LINUX Program Input

User supplies input in A FILE, whose name is sent as an argument
to the program ($1).
Input file contains: a seed number (an integer, starting in column 1,
with no extraneous whitespace around it), followed by 25 numbers
comprising the LINUX Card (arranged as a matrix, as above).
The input file must have exactly 6 lines.
e.g., you might run your game as follows:
> LINUX input1

where file input1 contains the 6 lines: <br />
1063 <br />
12 23 42 55 74 <br />
04 19 34 46 72 <br />
07 17 00 51 69 <br />
11 30 44 56 62 <br />
09 27 40 47 67 <br />

## Play The Game Alone

> LINUX myInputFile

LINUX will display the list of called numbers so far followed by the
marked Card (initially, call list is empty and only 00 is marked.)
LINUX always displays Card with column titles "L", "I", "N", "U", "X".
Then, numbers in [01-75] are called until you WIN (which stops program).
User triggers the next call by entering any character. Called numbers
are printed with an appropriate prefix of "L", "I", etc. e.g., I33, X70.
If that called number is in the Card, the number is "marked" on the Card.
LINUX displays a marked number by printing "m" after it (no whitespace
between number and "m").
Each time user triggers a new call, LINUX clears the screen, and displays
the call list followed by the marked Card.
User may quit LINUX at any time, by entering character "q" (any other
character triggers another call).

## Play the Game With Others

2 or more people may play, but they need some extra means of
communication (so they can coordinate).
Each player runs LINUX with the SAME SEED, but a different Card.
Players coordinate entering characters at the same time.
When one player wins, this player must alert the others.

## EXIT STATUS

Incorrect input file causes LINUX to exit before playing the game; it sends
these messages to STDERR and EXIT with these codes:
input file doesn't exist, is not readable, etc.:
  exit 1. "input file missing or unreadable"
input file does not have exactly 6 lines:
  exit 2. "input file must have 6 lines"
seed line is incorrect (contains one or more non-digit characters):
  exit 3. "seed line format error"
card has incorrect layout and/or number(s):
  exit 4. "card format error"
If LINUX finishes because user quits prematurely (enters q), or wins:
  exit 0.

## Authors
Hadi Awan
Mohamed Issa
Ayse Yalcin
Muteeb Syed
