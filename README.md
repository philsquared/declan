# Declan
A, data-only, DEClarative LANguage.

Declan is the answer to the question of what happens if you clean JSON up a bit and add types - algebraic data types, at that.
Doesn't YAML answer the same question? Perhaps, but it also goes much further, complicating things too much at the same time. There are some nods to YAML in Declan, but it also goes in its own direction. A primary goal is to be highly human readable, with a minimal of syntax. There are few alternative ways of doing things, although most forms have single/ multi-line variants, the multiline array separators may be redundantly repeated to any length, and the first separator for array and choice types is optional.

## Built in types

```
bool : Bool = true
int : Int = 42
float : Float = 3.141
string : String = "hello"
date : Date = 2018/05/15
datetime : DateTime = 2018/05/15 19:16:00Z
urlOrFilename : Url = https://cpponsea.uk
optionalString : String? = none
``` 


Because of type inference these lines can also be written:

```
bool = true
int = 42
float = 3.141
string = "hello"
date = 2018/05/15
datetime = 2018/05/15 19:16:00Z
urlOrFilename = https://cpponsea.uk
optionalString : String? = none
```

Note that the last type could not be inferred because it represents an optional type and is initialised from the empty value - so the Stringness is missing. Placing the type after the name (and a :) is usually referred to as type annotation, and is common in a number of languages, particularly functional programming languages, or those inspired by them.

Like JSON, Declan also has record types ("Product Types") - but they are statically typed:

```
type MyRecord =
    f1: Int
    f2: String
```
... and we'll get to those - but it also has choice types, a form of discriminated union - or "Sum Type".

In their simplest form a choice type is like an enum in most C-based languages:


`type suits = Clubs | Spades | Hearts | Diamonds`


But each choice can also act like an object - with data of their own:

```
type directoryEntry =
    | File : String
    | Directory : String
```

Note that the first `|` there is optional - but is usually there for aesthetic purposes

_to be continued..._
(in the meantime see [this file](decl.decl) for more examples)