The intuition is forcing processes to delegate their time, space, and ability to create subprocesses to their subprocesses, instead of allowing infinite consumption, prevents attacks on availability.

The realization is a sandbox: a mutable range of memory addresses containing scheduling and quota data, a reference to a module, and data structures for asynchronous inter-process communication, garbage collection, and managing sub-sandboxes.

A sandbox differs from a process in that a sandbox is not automatically destructed after evaluation terminates so that state can survive across events.

A sandbox differs from a Lisp environment in that a sandbox is only the data structure, not also the definitions.

Sandboxes evaluate jobs in the order in which they were received because jobs can perform side effects.  Results can be retrieved in any order.

Code should have sandbox boundaries anywhere asynchrony (e.g. to separate a responsive graphical user interface from slow computations) or trust boundaries (e.g. a service should normally evaluate a user’s jobs in that user’s personal sandbox) are helpful.

Sandboxes form a hierarchy.

All communication is via the super-sandbox, using immutable values, ensuring complete mediation.

Sandboxes can reclaim their time, space, and sub-sandbox limit by destructing their sub-sandboxes.

Hierarchies are suspect, but they seem to be unavoidable in this situation.  Confining less trusted code implies a partial order.

Sandboxes forming a hierarchy combined with I/O as values is useful for purposes other than security.  Examples include ‘bisimulation testing’ (comparing I/O of old and new implementations) for refactoring, constructing live coding environments (which must be confined to undo I/O), and legacy software adaptation (mapping old I/O to new I/O).
