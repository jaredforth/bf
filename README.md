# bf

This is an implementation of a minimal programming language abbreviated as `bf`.

This is part of the excellent book [Beautiful Racket](https://beautifulracket.com/bf), which I would highly recommend checking out.


## Grammar

The grammar for this language, in Extended Backus–Naur form is as follows:

```
bf-program : (bf-op | bf-loop)*
bf-op      : ">" | "<" | "+" | "-" | "." | ","
bf-loop    : "[" (bf-op | bf-loop)* "]"
```

## Directory Structure

```
.
├── expander.rkt
├── main.rkt
├── parser.rkt
└── reader.rkt
```

This repository contains three Racket modules and a `main.rkt`, which serves as the package entry point. These modules do what their name suggests. `parser.rkt` contains the grammar for the language and is imported by `reader.rkt`, which tokenizes and creates a parse tree of the source string. `expander.rkt` uses macros to tie everything together and convert the parse tree into Racket functions to implement logic defined by the `bf` language input.

## Usage 

### Installing the package

- This requires [racket](https://download.racket-lang.org/)
- Clone this repository and `cd` into the `bf` directory
- Run `raco pkg install`

### Testing

Once the package is installed, the following programs can be run using `#lang bf`. 

### Hello, World

```racket
#lang bf
++++++[>++++++++++++<-]>.
>++++++++++[>++++++++++<-]>+.
+++++++..+++.>++++[>+++++++++++<-]>.
<+++[>----<-]>.<<<<<+++[>+++++<-]>.
>>.+++.------.--------.>>+.

```

### Factorial

```racket
#lang bf
>++++++++++>>>+>+[>>>+[-[<<<<<[+<<<<<]>>[[-]>[<<+>+>-]
<[>+<-]<[>+<-[>+<-[>+<-[>+<-[>+<-[>+<-[>+<-[>+<-[>+<-
[>[-]>>>>+>+<<<<<<-[>+<-]]]]]]]]]]]>[<+>-]+>>>>>]<<<<<
[<<<<<]>>>>>>>[>>>>>]++[-<<<<<]>>>>>>-]+>>>>>]<[>++<-]
<<<<[<[>+<-]<<<<]>>[->[-]++++++[<++++++++>-]>>>>]<<<<<
[<[>+>+<<-]>.<<<<<]>.>>>>]
```
