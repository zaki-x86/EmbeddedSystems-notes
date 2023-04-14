# How C code is compiled

When you write C code, it's just a plain text file that can be read by humans but not by machines. The first step in the compilation process is to translate the human-readable C code into machine-readable instructions that the computer can execute. This translation is done by a program called a compiler.

Here are the general steps a C code file goes through during compilation:

1. Preprocessing: This is the first step of the compilation process. The preprocessor program reads your C code file and performs some operations such as substituting macros, including header files, and removing comments. The preprocessed code is then passed on to the compiler.
2. Compilation: The compiler is the program that converts your C code into assembly code, which is a low-level language that can be executed by the computer's processor. The compiler checks your code for syntax and semantic errors, optimizes your code for performance, and generates an object file containing the compiled code.
3. Linking: The object file produced by the compiler contains machine code for the functions defined in your C code, but it doesn't contain machine code for functions that are defined in other files or libraries that your code depends on. The linker program resolves these dependencies by linking together all the object files and libraries needed to produce a single executable file that can be executed by the computer.
4. Loading: The final step is loading the executable file into memory and executing it. The operating system is responsible for this step.
