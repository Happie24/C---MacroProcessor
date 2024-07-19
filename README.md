# C-Macro-Processor

## Introduction

System software acts as a crucial intermediary between hardware and application software, ensuring the efficient functioning of a computer system. It provides a platform for other software applications and offers essential services such as memory management, input/output operations, and communication between hardware components. The primary goal of system software is to ensure that computer hardware operates smoothly and efficiently, creating a stable environment for running various applications.

Macroprocessors significantly enhance the flexibility and efficiency of programming languages. In C, a macroprocessor performs textual substitution on the source code before compilation using the #define directive to define macros. These macros, representing reusable and parameterized code snippets, facilitate modularity, reduce redundancy, and improve readability. Macros can range from simple constants or inline functions to more complex code generation customizations.


##  Algorithm and Design

### Data Structure

**NAMTAB:** The Name Table (NAMTAB) is essential in the macro preprocessor, acting as a repository for macro names encountered in the source code. Its primary function is to prevent accidental macro redefinitions. When a #define directive is encountered, the macro's name is added to NAMTAB, ensuring each macro has a unique identity. This prevents conflicts and helps identify instances of multiple macro definitions, avoiding ambiguity and errors during preprocessing. NAMTAB uses an ofstream object to write to the "NAMTAB.txt" file.

**DEFTAB:** The Definition Table (DEFTAB) stores macro definitions found in the source code. When a #define directive is processed, both the macro's name and its definition are added to DEFTAB. This table is crucial for later stages of preprocessing when macro calls are encountered, allowing efficient retrieval of definitions based on macro names. This enables the replacement of macro calls with their corresponding definitions in the source code. DEFTAB is implemented using an ofstream object to write data to the "DEFTAB.txt" file.

**ARGTAB:** The Argument Table (ARGTAB) stores information about macros with parameters, specifically their names and associated arguments. This table is vital for handling macro calls with arguments. When a #define directive with arguments is processed, both the macro's name and its arguments are added to ARGTAB. This information ensures that macro calls with the correct number of arguments are appropriately replaced during preprocessing. Like NAMTAB and DEFTAB, ARGTAB uses an ofstream object to write to the "ARGTAB.txt" file.


### Algorithm

This algorithm processes C macro-processors. It reads an input file, handles directives, and generates an output file accordingly.

### Algorithm

```
begin:
  read line from input file
  if directive="#define":
    check if the name of macro is in NAMTAB
    if yes:
      set ERROR: MACRO REDEFINED.
    else:
      Put the name of macro into NAMTAB
      Put the definition of macro into DEFTAB
      Put the arguments of macro into ARGTAB.
  if directive="#ifdef" or directive="#ifndef":
    check if the macro is defined in case of #ifdef or not defined in case of #ifndef.
    Store this in isSkipping.
    if isSkipping is true:
      Execute the block.
  else if directive="#else" && !isSkipping:
    Execute the block.
  else:
    check if there is macro in the line
    if there is:
      replace the dummy arguments with actual arguments.
      replace the definition.
  put the line into output file.
  read next line
end
```

---



Here is the c++ code for ![C Pre-Processor](https://github.com/PragatiDBhat/C-Macro-Processor/blob/main/cmacroprocessor.cpp)
