# Introduction

#book
#interpreter

==Interpreters are magical !==

Interpreters gives random letters, numbers, and characters in <u>meaning</u>. 

General description for interpreters:
Source code as input -> evaluate it (No immediate result) -> Executed later

Contrast to compilers, where they produce output in another language that the underlying system can understand

Higher end of interpreters are highly optimized and use advanced parsing and evaluation techniques, and some even compile inputs into bytecodes and evaluate them.

**JIT Interpreters** compile the input just-in-time into native machine code that gets executed

Between the higher and lower level interpreters, are interpreters that parse the source code, build an abstract syntax tree (AST) and evaluate this tree. (Called "tree-walking" interpreters, and the type of interpreter that will be made in this book).

We will be using [[golang]] for this project

## The Monkey programming language & Interpreter

> We are going to be making an interpreter to parse and evaluate our own language called "Monkey"

Example of monkey code:

``` Monkey
let age = 1;
let name = "Monkey";
let result = 10 * (20/2);
```

``` Monkey
let add = fn(a, b) {return a + b; };
```

``` Monkey
let twice = fn(f, x) {
	return f(f(x));
};

let addTwo = fn(x){
	return x + 2;
}

twice(addTwo, 2); // => 6
```

This ability where functions can be passed in as arguments, and they're treated like any other data types are called <u>First class functions</u>

Major parts of the abstract syntax tree:
- lexer
- Parser
- Abstract Syntax Tree (ABT)
- Internal Object System
- Evaluator


# Chapter 1 Lexing

## 1.1 Lexical Analysis

source code are transformed into a more accessible form for the interpreter.

In order to do this, we change the representation of our source code two times:

![[Pasted image 20250128123253.png]]

The transformation from source code to token is called [[Lexical Analysis]] or "Lexing", done by **Lexers** (Or called tokenizer or scanners)

Tokens -> small, easily categorizable data structure which is fed to the parser
Parser -> Takes the tokens and turns it into [[Abstract Syntax Tree]]

Example:

```
"let x = 5 + 5;"
```
The lexer takes the input above, and transforms it into tokens like this:
```
LET,
IDENTIFIER("x"),
EQUAL_SIGN,
INTEGER(5),
PLUS_SIGN,
INTEGER(5),
SEMICOLON
```

Note: in this case, Whitespace do not show up as tokens this can vary through different interpreters (For example, white space in python does matter)

Some lexer may also attach line number, column number, and file name to a token, so it's able to output error messages in the parsing stage.


## 1.2 Defining Our Tokens

Before our lexer is able to convert source code into tokens, we must define the tokens first.

```
let five = 5;
let ten = 10;
let add = fn(x, y){
	x + y;
};

let result = add(five, ten);
```

Obvious tokens:
- Numbers (5 and 10)
- variable names (x, y)
- add
- result

There are also keywords like `let`, and `fn`. As well as special characters like ( ) { } = , ;

Note that the lexer/parser  don't really care about the exact values like 5 or 10, they just care about the fact that they're **numbers**.

same goes for **identifiers** for variable names, and **keywords** for the ones that look like identifiers but really aren't

we need to create a type called Token which is a struct that has attributes:
- 