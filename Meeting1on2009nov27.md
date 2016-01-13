  * **Topics:** meetings, goals of language, features, getting started

  * **Meetings:** We should document all meetings and upload them goals of language and features: functional language possibly targeting embedded systems, discussed features such as  FRP (functional reactive programming, allowing clean bit access) getting started: We agreed to write a interpretor or compiler (that generates c for now) for miniml and start building the language from bottom up. Experimenting with features etc.


---


  * MiniML grammar to start with:

```
(* unary operators *)
unop  ::= not | ~

(* binary operators *)
binop ::= + | - | * | div | mod | = | <> | > | >= | < | <= | ^ | andalso | orelse

(* declarations *)
d     ::= fun f(x : type) : type = e
        | fun f(x : type) : type = e1 and g(x : type) : type = e2
        | val identifier = e

(* types *)
type  ::= int
        | string
        | bool
        | type1 * type2 * ... * typen
        | type1 -> type2

(* expressions *)
e     ::= integer_constant
	| string_constant
	| identifier
	| true
	| false
	| (e1, e2, ..., en)
	| #integer e
	| fn identifier : type => e
	| if e1 then e2 else e3
	| e1 binop e2
	| let d in e end
	| unop e
	| e1 handle identifier => e2
	| raise identifier e
```