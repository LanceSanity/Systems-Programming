# Bomb Lab
Labs + description from [CS:APP3e](http://csapp.cs.cmu.edu/3e/labs.html) - A "binary bomb" is a program provided to students as an object code file. When run, it prompts the user to type in 
6 different strings. If any of these is incorrect, the bomb "explodes," printing an error message and logging the 
event on a grading server. Students must "defuse" their own unique bomb by disassembling and reverse engineering the 
program to determine what the 6 strings should be. The lab teaches students to understand assembly language, and also 
forces them to learn how to use a debugger. It's also great fun. A legendary lab among the CMU undergrads.

## Phase 1
Helpful commands: `disas <function name>`, `x/s <memory>` (examine contents of memory in string format), `print <memory>` (print value stored in a memory location), `break <function name>` (set breakpoint), `si` (step through a single instruction).
Tips to solve: disassemble main to get a better idea of what's going on. Basically, the program initializes the bomb, prompts
user for input with `<read_line>`, and begins phase_1. It might be helpful to know which register contains your input. Next, 
disassemble phase_1. To jump past the `<explode_bomb>` function call, the input needs to past the test. Step into `<strings_not_equal>`
and examine memory contents along the way. It's probably not necessary because the function name is self-explanatory, but if you
want to be sure it does what's expected, definitely study the function.
