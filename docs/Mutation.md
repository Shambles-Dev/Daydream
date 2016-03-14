## The Intuition

Macroni uses a dynamic effect system that limits the potential harm of mutation by limiting its observability.

These rules always apply:
* Variable names must be unique within the same scope (e.g. an immutable variable and a mutable variable cannot have the same name in the same scope).
* Inner scopes can shadow outer scopes.
* Immutable variables can only be bound to transitively immutable values.  They can be bound to values that are not first-class.
* Mutable variables can store all values that are first-class.
* Implementations of the same generic function must be defined with the same special form.

Special forms, macros, and types are not first-class.  Special forms and macros can only appear in the functional position, so their values cannot be read except to execute them.  Types are in a separate namespace that is only accessible by the object system and type checking predicates.


## Sandbox Boundaries

Sandboxes are mutable values that communicate only via transitively immutable values.

This solves several problems:
* Sandboxes cannot escape the sandbox they were constructed in, so they cannot perform vertical privilege escalation by controlling their super-sandbox.
* Sandboxes cannot access peer sandboxes, so they cannot perform horizontal privilege escalation by controlling their peer sandboxes.
* The sandbox hierarchy is dynamic, which seems to be the most powerful design that can provide security.
* Sandboxes perform complete mediation of their sub-sandboxes.
* Race conditions cannot occur.
* Programmers can think sequentially and use mutation, as is natural for humans, while benefiting from parallelism.


## Lexical Scope

`def-macro` defines a macro and binds it to an immutable variable.  Using this special form in a scope other than module scope is a defect error.

`def-fun` defines a function and binds it to an immutable variable.

Macro and function parameters are immutable variables that are lexically scoped, they can access their lexical and local scope, and they can only return transitively immutable values.  If functions are defined inside a type definition, they can also access that type’s instance variables.

This ensures macros and functions are transitively immutable and referentially transparent, even if they use mutation internally.

Most of Macroni is built from such definitions, forcing uses of observable mutation to be located near execution entry and exit points.

This ensures most code is easy to test, debug, reuse, and optimize.


## Module Scope

`mdef-smproc` defines a stateful mutator procedure and binds it to a mutable variable.  Using this special form in a scope other than module scope is a defect error.

Stateful mutator procedure parameters are mutable variables, they can access their lexical, module, and local scope, and they can return all first-class values.

This makes stateful mutator procedures usable as event handlers because they can retain state.

Imported mutable variables cannot be directly mutated.

This ensures modules are encapsulated.


## Type Scope

`def-type` defines a type.  It performs no binding.

`def-mproc` defines a mutator procedure and binds it to an immutable variable.

Mutator procedure parameters are mutable variables, they can access their lexical and local scope, and they can return all first-class values.  If they are defined inside a type definition, they can also access that type’s instance variables.

This makes mutator procedures usable as mutable type constructors and procedures that mutate mutable types because they can perform mutation but not retain state.  They can be accessed by macros and functions because they can be bound in lexical scope, because they are transitively immutable.


## Local Scope

`def` defines an immutable variable.  If this special form is used in module scope or inside a macro or function body, the value must be specified and the binding will appear in lexical scope.  If it is used in type scope, the value must not be specified, it must be used again to bind the value in the constructor, and the binding will appear in type scope.  Otherwise, the value must be specified and the binding will appear in local scope.

`mdef` defines a mutable variable.  If this special form is used in module scope, the value must be specified and the binding will appear in module scope.  If it is used in type scope, the value must not be specified, it must be used again to bind the value in the constructor, and the binding will appear in type scope.  Otherwise, the value must be specified and the binding will appear in local scope.

Compound forms of `def` and `mdef` have the same semantics.  Parameters are consistent.

This makes it possible for procedures that are referentially transparent to use mutable variables internally and for procedures that are not referentially transparent to use immutable variables internally.


## Interactions


### Types




### Thunks




### Futures




### Continuations
