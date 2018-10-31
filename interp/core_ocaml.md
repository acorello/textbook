# Core OCaml

As a running example throughout this chapter, we'll use a fragment
of the OCaml language that we call *core OCaml*.  Here is its
syntax in BNF:

```
e ::= x | e1 e2 | fun (x : t) -> e     
    | i | b | e1 bop e2                
    | (e1, e2) | fst e1 | snd e2  
    | Left e | Right e          
    | match e with Left x1 -> e1 | Right x2 -> e2 
    | if e1 then e2 else e3
    | let x : t = e1 in e2     

bop ::= + | * | < | =

t ::= bool | int

x ::= <identifiers>

i ::= <integers>
 
b ::= true | false      

v ::= fun x -> e | i | b | (v1, v2) | Left v | Right v
```

To keep tuples simple in this core model, we represent them with only
two components (i.e., they are pairs).  A longer tuple could be coded up
with nested pairs. For example, `(1,2,3)` in OCaml could be `(1,(2,3))`
in this core language.

Also to keep datatypes simple in this core model, we represent them with
only two constructors, which we name `Left` and `Right`.  A datatype
with more constructors could be coded up with nested applications of
those two constructors.  Since we have only two constructors, match
expressions need only two branches.  One caution in reading the BNF
above:  the occurrence of `|` in the match expression just before the
`Right` constructor denotes syntax, not metasyntax.

There are a few important OCaml constructs omitted from this core
language, including recursive functions, exceptions, mutability,
and modules.  Type inference is also missing; we require the programmer
to annotate variable bindings with their type.  Nonetheless, there 
is enough in this core language to keep us entertained for quite awhile.