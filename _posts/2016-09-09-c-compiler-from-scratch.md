---
title: 'C Compiler from Scratch'
date: 2020-01-08T02:47:00+01:00
draft: false
---

![](https://avatars2.githubusercontent.com/u/817898?s=400&v=4 "GitHub - DoctorWkt/acwj: A Compiler Writing Journey")  

[](https://github.com/DoctorWkt/acwj#a-compiler-writing-journey)A Compiler Writing Journey
==========================================================================================

In this Github repository, I'm documenting my journey to write a self-compiling compiler for a subset of the C language. I'm also writing out the details so that, if you want to follow along, there will be an explanation of what I did, why, and with some references back to the theory of compilers.

But not too much theory, I want this to be a practical journey.

Here are the steps I've taken so far:

*   [Part 0](https://github.com/DoctorWkt/acwj/blob/master/00_Introduction/Readme.md): Introduction to the Journey
*   [Part 1](https://github.com/DoctorWkt/acwj/blob/master/01_Scanner/Readme.md): Introduction to Lexical Scanning
*   [Part 2](https://github.com/DoctorWkt/acwj/blob/master/02_Parser/Readme.md): Introduction to Parsing
*   [Part 3](https://github.com/DoctorWkt/acwj/blob/master/03_Precedence/Readme.md): Operator Precedence
*   [Part 4](https://github.com/DoctorWkt/acwj/blob/master/04_Assembly/Readme.md): An Actual Compiler
*   [Part 5](https://github.com/DoctorWkt/acwj/blob/master/05_Statements/Readme.md): Statements
*   [Part 6](https://github.com/DoctorWkt/acwj/blob/master/06_Variables/Readme.md): Variables
*   [Part 7](https://github.com/DoctorWkt/acwj/blob/master/07_Comparisons/Readme.md): Comparison Operators
*   [Part 8](https://github.com/DoctorWkt/acwj/blob/master/08_If_Statements/Readme.md): If Statements
*   [Part 9](https://github.com/DoctorWkt/acwj/blob/master/09_While_Loops/Readme.md): While Loops
*   [Part 10](https://github.com/DoctorWkt/acwj/blob/master/10_For_Loops/Readme.md): For Loops
*   [Part 11](https://github.com/DoctorWkt/acwj/blob/master/11_Functions_pt1/Readme.md): Functions, part 1
*   [Part 12](https://github.com/DoctorWkt/acwj/blob/master/12_Types_pt1/Readme.md): Types, part 1
*   [Part 13](https://github.com/DoctorWkt/acwj/blob/master/13_Functions_pt2/Readme.md): Functions, part 2
*   [Part 14](https://github.com/DoctorWkt/acwj/blob/master/14_ARM_Platform/Readme.md): Generating ARM Assembly Code
*   [Part 15](https://github.com/DoctorWkt/acwj/blob/master/15_Pointers_pt1/Readme.md): Pointers, part 1
*   [Part 16](https://github.com/DoctorWkt/acwj/blob/master/16_Global_Vars/Readme.md): Declaring Global Variables Properly
*   [Part 17](https://github.com/DoctorWkt/acwj/blob/master/17_Scaling_Offsets/Readme.md): Better Type Checking and Pointer Offsets
*   [Part 18](https://github.com/DoctorWkt/acwj/blob/master/18_Lvalues_Revisited/Readme.md): Lvalues and Rvalues Revisited
*   [Part 19](https://github.com/DoctorWkt/acwj/blob/master/19_Arrays_pt1/Readme.md): Arrays, part 1
*   [Part 20](https://github.com/DoctorWkt/acwj/blob/master/20_Char_Str_Literals/Readme.md): Character and String Literals
*   [Part 21](https://github.com/DoctorWkt/acwj/blob/master/21_More_Operators/Readme.md): More Operators
*   [Part 22](https://github.com/DoctorWkt/acwj/blob/master/22_Design_Locals/Readme.md): Design Ideas for Local Variables and Function Calls
*   [Part 23](https://github.com/DoctorWkt/acwj/blob/master/23_Local_Variables/Readme.md): Local Variables
*   [Part 24](https://github.com/DoctorWkt/acwj/blob/master/24_Function_Params/Readme.md): Function Parameters
*   [Part 25](https://github.com/DoctorWkt/acwj/blob/master/25_Function_Arguments/Readme.md): Function Calls and Arguments
*   [Part 26](https://github.com/DoctorWkt/acwj/blob/master/26_Prototypes/Readme.md): Function Prototypes
*   [Part 27](https://github.com/DoctorWkt/acwj/blob/master/27_Testing_Errors/Readme.md): Regression Testing and a Nice Surprise
*   [Part 28](https://github.com/DoctorWkt/acwj/blob/master/28_Runtime_Flags/Readme.md): Adding More Run-time Flags
*   [Part 29](https://github.com/DoctorWkt/acwj/blob/master/29_Refactoring/Readme.md): A Bit of Refactoring
*   [Part 30](https://github.com/DoctorWkt/acwj/blob/master/30_Design_Composites/Readme.md): Designing Structs, Unions and Enums
*   [Part 31](https://github.com/DoctorWkt/acwj/blob/master/31_Struct_Declarations/Readme.md): Implementing Structs, Part 1
*   [Part 32](https://github.com/DoctorWkt/acwj/blob/master/32_Struct_Access_pt1/Readme.md): Accessing Members in a Struct
*   [Part 33](https://github.com/DoctorWkt/acwj/blob/master/33_Unions/Readme.md): Implementing Unions and Member Access
*   [Part 34](https://github.com/DoctorWkt/acwj/blob/master/34_Enums_and_Typedefs/Readme.md): Enums and Typedefs
*   [Part 35](https://github.com/DoctorWkt/acwj/blob/master/35_Preprocessor/Readme.md): The C Pre-Processor
*   [Part 36](https://github.com/DoctorWkt/acwj/blob/master/36_Break_Continue/Readme.md): `break` and `continue`
*   [Part 37](https://github.com/DoctorWkt/acwj/blob/master/37_Switch/Readme.md): Switch Statements
*   [Part 38](https://github.com/DoctorWkt/acwj/blob/master/38_Dangling_Else/Readme.md): Dangling Else and More
*   [Part 39](https://github.com/DoctorWkt/acwj/blob/master/39_Var_Initialisation_pt1/Readme.md): Variable Initialisation, part 1
*   [Part 40](https://github.com/DoctorWkt/acwj/blob/master/40_Var_Initialisation_pt2/Readme.md): Global Variable Initialisation
*   [Part 41](https://github.com/DoctorWkt/acwj/blob/master/41_Local_Var_Init/Readme.md): Local Variable Initialisation
*   [Part 42](https://github.com/DoctorWkt/acwj/blob/master/42_Casting/Readme.md): Type Casting and NULL
*   [Part 43](https://github.com/DoctorWkt/acwj/blob/master/43_More_Operators/Readme.md): Bugfixes and More Operators
*   [Part 44](https://github.com/DoctorWkt/acwj/blob/master/44_Fold_Optimisation/Readme.md): Constant Folding
*   [Part 45](https://github.com/DoctorWkt/acwj/blob/master/45_Globals_Again/Readme.md): Global Variable Declarations, revisited
*   [Part 46](https://github.com/DoctorWkt/acwj/blob/master/46_Void_Functions/Readme.md): Void Function Parameters and Scanning Changes
*   [Part 47](https://github.com/DoctorWkt/acwj/blob/master/47_Sizeof/Readme.md): A Subset of `sizeof`
*   [Part 48](https://github.com/DoctorWkt/acwj/blob/master/48_Static/Readme.md): A Subset of `static`
*   [Part 49](https://github.com/DoctorWkt/acwj/blob/master/49_Ternary/Readme.md): The Ternary Operator
*   [Part 50](https://github.com/DoctorWkt/acwj/blob/master/50_Mop_up_pt1/Readme.md): Mopping Up, part 1
*   [Part 51](https://github.com/DoctorWkt/acwj/blob/master/51_Arrays_pt2/Readme.md): Arrays, part 2
*   [Part 52](https://github.com/DoctorWkt/acwj/blob/master/52_Pointers_pt2/Readme.md): Pointers, part 2
*   [Part 53](https://github.com/DoctorWkt/acwj/blob/master/53_Mop_up_pt2/Readme.md): Mopping Up, part 2
*   [Part 54](https://github.com/DoctorWkt/acwj/blob/master/54_Reg_Spills/Readme.md): Spilling Registers
*   [Part 55](https://github.com/DoctorWkt/acwj/blob/master/55_Lazy_Evaluation/Readme.md): Lazy Evaluation
*   [Part 56](https://github.com/DoctorWkt/acwj/blob/master/56_Local_Arrays/Readme.md): Local Arrays
*   [Part 57](https://github.com/DoctorWkt/acwj/blob/master/57_Mop_up_pt3/Readme.md): Mopping Up, part 3
*   [Part 58](https://github.com/DoctorWkt/acwj/blob/master/58_Ptr_Increments/Readme.md): Fixing Pointer Increments/Decrements
*   [Part 59](https://github.com/DoctorWkt/acwj/blob/master/59_WDIW_pt1/Readme.md): Why Doesn't It Work, part 1
*   [Part 60](https://github.com/DoctorWkt/acwj/blob/master/60_TripleTest/Readme.md): Passing the Triple Test
*   [Part 61](https://github.com/DoctorWkt/acwj/blob/master/61_What_Next/Readme.md): What's Next?
*   [Part 62](https://github.com/DoctorWkt/acwj/blob/master/62_Cleanup/Readme.md): Code Cleanup

There isn't a schedule or timeline for the future parts, so just keep checking back here to see if I've written any more.

[](https://github.com/DoctorWkt/acwj#copyrights)Copyrights
----------------------------------------------------------

I have borrowed some of the code, and lots of ideas, from the [SubC](http://www.t3x.org/subc/) compiler written by Nils M Holm. His code is in the public domain. I think that my code is substantially different enough that I can apply a different license to my code.

Unless otherwise noted,

*   all source code and scripts are (c) Warren Toomey under the GPL3 license.
*   all non-source code documents (e.g. English documents, image files) are (c) Warren Toomey under the Creative Commons BY-NC-SA 4.0 license.

  
  
from Hacker News https://ift.tt/2s6kA9H