generation-based (can generate input from scratch) and mutation-based (can change bits in sample input), smart (generation/mutation can be defined by user-defined functions) or dumb (mutation mode), white box (uses static and dynamic analysis) fuzzer that prefers likely error-prone values (0, empty values, min/max values) that cause crashes or hangs

should provide input generators for the invariants the invariant inferencer uses
