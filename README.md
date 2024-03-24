# Diminished-Java-Compiler
The compiler I created for COP4620 Compilers at the University of South Florida. The syllabus and assignment descriptions are available [here](https://www.cse.usf.edu/~ligatti/compilers/24/).
> [!NOTE]
> **The source code is not public** due to course restrictions prohibiting public posting of coursework. A private copy is available by request.

## Diminished Java
Diminished Java (DJ) is a turing-complete simpilified version of Java with the most basic features retained:
- Object-oriented with single inheritence, method overriding (thus, dynamic method calls), static fields, and mutally recursive classes
- Dynamic expressions: if/else, for, instanceof, this
- Basic I/O (console input & output of integers)
- Basic types (objects, natual numbers, booleans)
- Basic operators (+, -, *, (), <, ==, !, &&, obj.function() etc.) with proper precedence
- Single files (no importing)
- DJ is compiled into a basic interpreted assembly language called Diminished Instruction Set Machine (DISM). [More information on DISM](https://cse.usf.edu/~ligatti/compilers/24/as1/dism/DISM-definition.pdf)
- [More information on DJ](https://cse.usf.edu/~ligatti/compilers/24/as1/dj/DJ-definition.pdf)

## Lexing
- Lexing is accomplished using a [Flex](https://en.wikipedia.org/wiki/Flex_(lexical_analyser_generator)) lexing file (**dj.l**)
- Regular expressions define the rules for recognizing tokens
- A token stream is generated, which is passed to the parser

## Parsing
- Parsing is accomplished using a [Bison](https://en.wikipedia.org/wiki/GNU_Bison) parsing file (**dj.y**)
- A context-free grammar defines the rules for parsing tokens
- An abstract syntax tree is built (**ast.h** and **ast.c**) from recognized tokens

## Type checking
- First, a symbol table (**symtbl.h** and **symtbl.c**) is built from traversing the AST
- Then, the symbol table is traversed, ensuring all type rules are enforced (**typchk.h** and **typchk.c**)
- Finally, expressions are type checked

## Code Generation
- To be continued

## Progress
- [x] Lexing
- [x] Parsing the token stream
- [x] Building ASTs from parsing
- [x] Building symbol tables from ASTs
- [ ] (in progress) Type checking the symbol table
- [ ] (in progress) Type checking expressions
- [ ] Generating DISM assembly from the AST
