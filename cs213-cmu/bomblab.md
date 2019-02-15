# Bomb Lab
Labs + description from [CS:APP3e](http://csapp.cs.cmu.edu/3e/labs.html) - A "binary bomb" is a program provided to students as an object code file. When run, it prompts the user to type in 
6 different strings. If any of these is incorrect, the bomb "explodes," printing an error message and logging the 
event on a grading server. Students must "defuse" their own unique bomb by disassembling and reverse engineering the 
program to determine what the 6 strings should be. The lab teaches students to understand assembly language, and also 
forces them to learn how to use a debugger. It's also great fun. A legendary lab among the CMU undergrads.

## Phase 1
Helpful commands:
- `disas <function name>`
- `x/s <memory>` (examine contents of memory in string format)
- `print $<register>` (print value stored in a register)
- `break <function name>` (set breakpoint) or `b *<instruction address>` (asterisk to dereference the address)
- `si` (step through a single instruction)

Tips to solve: disassemble main to get a better idea of what's going on. Basically, the program initializes the bomb, prompts
user for input with `<read_line>`, and begins phase_1. It might be helpful to know which register contains your input. Next, 
disassemble phase_1. To jump past the `<explode_bomb>` function call, the input needs to past the test. Step into `<strings_not_equal>` and examine memory contents along the way. It's probably not necessary because the function name is self-explanatory, but if you want to be sure it does what's expected, definitely study the function.

## Phase 2
More helpful commands:
- `info registers` or `i r` (get register values)
- `print *<memory address>` (prints value contained in an address)
- `set <$register> = <value>` (you can use this to set the value of a register. useful if a `cmp` will fail, but you want to keep stepping in the function)

Tips: step through `<read_six_numbers>` to figure out the first condition. Next, look at the jumps and comparisons. If you follow the jumps, you'd notice that it is a loop. What values are being compared? When a `cmp` fails, is the next instruction to jump to `<explode_bomb>`? Which register holds the arguments?

New operation and operand specifier:
- `lea` (load effective address) copies an address to a location (rather than read from that address like `mov`)
- `(<register>)` is a memory reference
