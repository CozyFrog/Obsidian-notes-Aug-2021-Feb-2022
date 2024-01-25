Tricky Spots:
- Storing variables on stack in recursion.
- Instruction types (really instructions at a conceptual level).
- Overflow.
- Loading 32 bit constants
- Endianness
- Variable definition
- Functions



# Storing Variables on Stack
- Stack grows (down) from higher address toward lower address.
- sp (stack pointer) is the address of the word at the TOP (bottom) of the stack.

$\\$

# Instruction Types
- R-Type
	- instructions using 3 register inputs
- I-Type
	- instructions with immediates, loads
- S-Type
	- store instructions
- SB-Type
	- branch instructions
- U-Type
	- instructions with upper immediates
- UJ-Type
	- jump instructions

$\\$

# Loading 32-bit Constants
- lui for the upper 20 bits (lower 12 bits cleared).
- addi the lower 12 bits
- be careful with sign extensions. if the immd you're adding with addi after lui has a sign bit of 1, offset +1 to the immediate that's being LUI'd (0x789aC instead of 0x789aB).

$\\$

# Endianness
- Big: larger goes lower
- Small: smaller goes lower

$\\$

# Variables
```
# a word with initial value 3:
x: .word 3

# two words with initial values:
y: .word 4, 5
```