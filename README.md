# Diminished-Java-Compiler
The compiler I created for COP4620 Compilers at the University of South Florida. The syllabus and assignment descriptions are available [here](https://www.cse.usf.edu/~ligatti/compilers/24/).
> [!IMPORTANT]
> ***The source code is not public*** due to course restrictions prohibiting public posting of coursework. A private copy is available by request.

## Diminished Java
Diminished Java (DJ) is a turing-complete simpilified version of Java with the most basic features retained:
- Object-oriented with single inheritence, method overriding (thus, dynamic method calls), static fields, and mutally recursive classes
- Dynamic expressions: if/else, for, instanceof, this
- Basic I/O (console input & output of integers)
- Basic types (objects, natual numbers, booleans)
- Basic operators (+, -, *, (), <, ==, !, &&, obj.function() etc.) with proper precedence
- Single files (no importing)
- Single line comments
- DJ is compiled into a basic interpreted assembly language called Diminished Instruction Set Machine (DISM). [More information on DISM](https://cse.usf.edu/~ligatti/compilers/24/as1/dism/DISM-definition.pdf)
- [More information on DJ](https://cse.usf.edu/~ligatti/compilers/24/as1/dj/DJ-definition.pdf)

## Lexing / Scanning
- Lexing is accomplished using a [Flex](https://en.wikipedia.org/wiki/Flex_(lexical_analyser_generator)) lexing file (**dj.l**)
- Regular expressions define the rules for recognizing tokens
- A token stream is generated, which is passed to the parser

Example 1:

![](/images/lex1.png)

Example 2 (this is a silly example, but all keywords are present here!):

![](/images/lex2.png)

Example of a lexical error:

![](/images/lex_bad.png)

## Parsing / Syntactic analysis
- Parsing is accomplished using a [Bison](https://en.wikipedia.org/wiki/GNU_Bison) parsing file (**dj.y**)
- A context-free grammar defines the rules for parsing tokens
- An abstract syntax tree is built (**ast.h** and **ast.c**) from recognized tokens

Example 1:

![](/images/parse1.png)

Example 2 (this one is long!):

![](/images/parse2.png)

Example of a syntax error:

![](/images/parse_bad.png)

## Type checking / Semantic analysis
- First, a symbol table (**symtbl.h** and **symtbl.c**) is built from traversing the AST
>[!NOTE]
>- Types T >= 0 denote the Tth defined class (Object is class 0)
>- -1 denotes nat
>- -2 denotes bool
>- -3 is AnyObjectType (aka null)
>- -4 is a special type that Object "extends from"
>- -5 is an error

Example 1:

![](/images/ST1.png)

Example 2 (this image was edited for space and ease of reading):

![](/images/ST2.png)

- Then, the symbol table is traversed, ensuring all type rules are enforced (**typecheck.h** and **typecheck.c**)
- Finally, expressions are type checked recursively (typeExprs() and typeExpr() in typchk.c)

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
