null pointer = 0

realloc - ask for 100 bytes, couple seconds later need more
here's a block of size x, I'd like to make it bigger -> 2x

realloc can give more space, but it can also move address somewhere else

never use sbrk directly because malloc does it for us


how do you write a matrix? (array of arrays!)
make array of pointers - each pointer points to an array
multiple pointer arrays, each array is a row


3x3 matrix: pointer with 3 entries, each entry points to a 3-entry array

$\\$

matrix[row][column]