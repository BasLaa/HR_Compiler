_WHATCH OUT: Both the readme and the repo itself are a work in progress!_

# ChocoPy v2.2 Compiler

## What is Chocopy?

The ChocoPy language is a statically typed dialect of Python 3.6. ChocoPy has been designed to be a subset of Python. Almost every valid ChocoPy program is also a valid Python 3.6 program. An execution of a ChocoPy program that does not result in error usually has the same observable semantics as the execution of that program in Python 3.6. 

## What is a Compiler?

A compiler is a program that translates code written in one language into another language. We refer to the input and output languages as the source and target languages, respectively. For example, the input language can be a high-level programming language, whereas the target language could be a low-level programming language such as assembly or byte code.

More specifically, the task of the compiler is (at least) two-fold:

1. It ensures that the input source code is syntactically correct, that is, it adheres to the rules of the programming language it is written in, and, if not, identifies the errors;
2. If the input is correct, it outputs a translated version of the code in the target language; moreover, the target code preserves the semantic meaning of the source code, that is, when executed, the target code performs the task specified by the source program.

We can further divide the compilation process into several consecutive phases, each with a well-defined role, input, and output. 
First is the **lexical-analysis** phase. It takes a source program as input, as a stream of characters, and aggregates the individual characters into so-called tokens, which represent meaningful symbols in the corresponding language (labeled with their type). 
Next, in the **syntax-analysis** phase, the tokens are parsed into a tree structure that reflects the source program’s organization. Syntax errors, if present, are reported. 
The **semantic-analysis** phase performs additional and more intricate correctness checking, most notably type verification. 
The _code generation_ is generally a two-step process: the **intermediate code generation** phase produces somewhat abstract hardware-agnostic code, whereas the **code generation** phase produces assembly or machine code for specific hardware platforms. Dividing the code generation into those two phases offers several advantages, e.g., when it comes to code optimization. 

In addition to passing the output of one phase as an input into the next, the phases generally also use a common data-structure called a symbol-table to store information also relevant to the other phases.

## Why would I care about a Compiler?

Some of the reasons are:

* _"A good craftsman should know his tools"_, and compilers are important tools for programmers and computer scientists. Understanding how a compiler is built allows programmers to get an intuition about what their high-level programs will look like when compiled, and use this intuition to tune programs for better efficiency. Furthermore, the error reports that compilers provide are often easier to understand when one knows about and understands the different phases of compilation, such as knowing the difference between lexical errors, syntax errors, type errors and so on.
* The techniques used for constructing a compiler are useful for other purposes as well. The third reason is also quite valid. In particular, the techniques used for reading (lexing and parsing) the text of a program and converting this into a form (abstract syntax) that is easily manipulated by a computer, can be used to read and manipulate any kind of structured text such as XML documents, address lists, etc.
* There is a good chance that a programmer or computer scientist will need to write a compiler or interpreter for a domain-specific language. Lately is has become more important as domain specific languages (DSLs) are gaining in popularity. A DSL is a (typically small) language designed for a narrow class of problems. Examples are data-base query languages, text-formatting languages, scene description languages for ray-tracers, and languages for setting up economic simulations. The target language for a compiler for a DSL may be traditional machine code, but it can also be another high-level language for which compilers already exist, a sequence of control signals for a machine, or formatted text and graphics in some printer-control language (e.g. PostScript), and DSLs are often interpreted instead of compiled. Even so, all DSL compilers and interpreters will have front-ends for reading and analysing the program text that are similar to those used in compilers and interpreters for general-purpose languages.

