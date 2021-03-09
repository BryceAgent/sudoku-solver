# sudoku-solver
A simple program for solving any sudoku.

To run, simply change the "grid" variable to the unsolved sudoku. '0' is an unsolved square.

The first_nec and hypo functions are doing the heavy lifting of solving.

first_nec will run through the entire grid, checking if there is a single possible number in each square.
first_nec will then check the grid after running through each square and, if a change has been made, it will run again.
If it runs through the grid without making a change, it will pass the grid to hypo.

hypo is a breadth first search function. It will run through the grid to the first open square (a '0').
hypo will then determine the possible numbers for that square, and save them in a queue. It will then
"hypothesize" the last number. It will save the grid before this hypothesis was made. This grid will be saved
in a list concurrent with the queue of possible numbers. Then it will pass the new grid to first_nec, which will run
until it either results in a contradiction or it cannot find any more necessary numbers. If it finds a contradiction,
it will pass back to hypo and revert to the grid before hypothesis, then try the next number in the queue for that square.
If it cannot find any more necessary numbers, it will pass back to hypo which will hypothesize the numbers for the next available
square.

When first_nec detects there are no empty squares, it will print the result and exit the program.
