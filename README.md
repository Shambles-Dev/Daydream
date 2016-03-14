<div align="center">
<h3>:warning: Macroni is in its design phase.  There is no code to run. :warning:</h3>
</div>

Macroni
=======

[Macroni](docs/Name.md) is an operating system (that can also run as a process) and integrated development environment for a Lisp dialect.

Macroni solves problems current computing systems have while remaining compatible with them.


<table>
  <tr>
    <th colspan="2">Social Features</th>
  </tr>
  <tr>
    <th>Problem</th>
    <th>Solution</th>
  </tr>
  <tr>
    <td><p>Untrustworthy computing is ubiquitous.</p></td>
    <td><p>Macroni is <a href="https://en.wikipedia.org/wiki/Open_source">open source</a>.</p></td>
  </tr>
  <tr>
    <td><p>Plutocrats deprive others of freedom.</p></td>
    <td><p>Macroni is licensed under the <a href="LICENSE.txt">AGPLv3</a>.</p></td>
  </tr>
  <tr>
    <td><p>Human replacement technology is destroying livelihoods, lives, creativity, and progress.</p></td>
    <td><p>Macroni promotes <a href="docs/Evolutionary_Problems_and_Computing_Solutions.md">intelligence augmentation technology</a> by exposing all software as a toolbox instead of a black box.</p></td>
  </tr>
</table>


<table>
  <tr>
    <th colspan="2">Operating System Features</th>
  </tr>
  <tr>
    <th>Problem</th>
    <th>Solution</th>
  </tr>
  <tr>
    <td><p>Most code is not portable.</p></td>
    <td><p>Macroni was designed to be <a href="docs/Portability.md">portable</a>.  It does not expose anything host-specific to applications.</p></td>
  </tr>
  <tr>
    <td><p>Secure user interaction is usually unnatural, complex, and annoying.</p></td>
    <td><p><a href="docs/User_Interface.md">Secure user interaction</a> in Macroni is familiar, simple, and authorization is almost entirely implicit.</p></td>
  </tr>
  <tr>
    <td><p>Most code is vulnerable to attacks on integrity and confidentiality.</p></td>
    <td><p>Macroni uses the <a href="docs/Capability_Security_Model.md">capability security model</a>.  Malware cannot corrupt or leak what it cannot reach.</p></td>
  </tr>
  <tr>
    <td><p>Most code is vulnerable to attacks on availability.</p></td>
    <td>
      <p>Macroni uses <a href="docs/Sandboxes.md">sandboxes</a> and <a href="docs/Microrebooting.md">microrebooting</a>.  Malware can only waste its own time and space.</p>
      <p>Microrebooting is also used for self-healing from defects and hot-swapping to update software.</p>
    </td>
  </tr>
  <tr>
    <td><p>Most schedulers are vulnerable to attacks on availability.</p></td>
    <td><p>Macroni’s <a href="docs/Scheduler.md">scheduler</a> prevents cutting in line, and its sandboxes cannot construct more sandboxes than were delegated to them.</p></td>
  </tr>
  <tr>
    <td><p>I/O can be used to attack availability.</p></td>
    <td>
      <p>Macroni does not support system calls, in which less privileged code calls more privileged code.  All communication between sandboxes is via more privileged code calling less privileged code with immutable arguments (if necessary) returning a <a href="docs/Futures.md">future</a> that should resolve to an immutable result.  Blocking on futures is not supported (polling futures and destructing sandboxes is) because that would be an availability vulnerability.</p>
      <p>Macroni is event-driven.  Only the initial sandbox performs I/O, where it can be collated, optimized, and securely scheduled and quotas can be enforced.  Other sandboxes regard all <a href="docs/Input_Output.md">I/O</a> (including I/O errors) as values.</p>
    </td>
  </tr>
  <tr>
    <td><p>Power loss can cause data loss.</p></td>
    <td>
      <p>Macroni provides optional <a href="docs/Transparent_Persistence.md">transparent persistence</a>.  The checkpoint interval is configurable.</p>
      <p>The world can also be saved explicitly.</p>
    </td>
  </tr>
</table>


<table>
  <tr>
    <th colspan="2">Integrated Development Environment Features</th>
  </tr>
  <tr>
    <th>Problem</th>
    <th>Solution</th>
  </tr>
  <tr>
    <td><p>Manually matching brackets is difficult.</p></td>
    <td><p>Macroni’s <a href="docs/Source_Code_Editor.md">source code editor</a> is a structure editor that can toggle highlighting based on the depth of bracket nesting around the cursor.</p></td>
  </tr>
  <tr>
    <td><p>Manually refactoring code is difficult.</p></td>
    <td><p>Macroni’s source code editor can automatically <a href="docs/Refactoring.md">refactor</a> code.</p></td>
  </tr>
  <tr>
    <td><p>Noticing changes broke code is usually difficult.</p></td>
    <td><p>Macroni’s source code editor performs static analysis in the background to warn about defects and bad practices (e.g. wrong number of arguments, wrong type, wrong value, needlessly wide scope, needlessly mutable variable, non-macro-generated dead code, deleting a definition broke another module, etc.).</p></td>
  </tr>
  <tr>
    <td><p>Discovering code is usually difficult.</p></td>
    <td><p>Macroni supports docstrings, and its source code editor can search for modules, module scoped variables and their values, types, signatures, and docstrings matching patterns.</p></td>
  </tr>
  <tr>
    <td><p>Comprehending code is usually difficult.</p></td>
    <td><p>Macroni’s source code editor can cross-reference code to display what binds, mutates, or reads a variable, what calls a procedure, what a procedure calls, and all implementations of a generic function.</p></td>
  </tr>
  <tr>
    <td><p>Checking your comprehension of code is usually difficult.</p></td>
    <td><p>Macroni provides <a href="docs/Listeners.md">listeners</a> (REPLs) for interactively testing code.</p></td>
  </tr>
  <tr>
    <td><p>Asserting all relevant invariants is usually difficult.</p></td>
    <td><p>Macroni provides an <a href="docs/Invariant_Inferencer.md">invariant inferencer</a>.</p></td>
  </tr>
  <tr>
    <td><p>Unvalidated input and unsanitized output can be used to directly or indirectly attack integrity, confidentiality, and availability.</p></td>
    <td><p>Macroni provides a <a href="docs/Taint_Checker.md">taint checker</a>.</p></td>
  </tr>
  <tr>
    <td><p>Discovering defects by testing is usually difficult.</p></td>
    <td><p>Macroni provides a <a href="docs/Fuzzer.md">fuzzer</a>.</p></td>
  </tr>
  <tr>
    <td><p>Comprehending defects is usually difficult.</p></td>
    <td><p>Macroni’s <a href="docs/Debugger.md">debugger</a> records the last several bindings and mutations along with the dump.  How many to record is configurable.</p></td>
  </tr>
  <tr>
    <td><p>Recognizing unreliable code is usually difficult.</p></td>
    <td><p>Macroni’s debugger can display modules sorted by how often sandboxes were microrebooted for crashing or hanging while the program counter was in them and the source locations of those program counters.</p></td>
  </tr>
  <tr>
    <td><p>Locating bottlenecks is usually difficult.</p></td>
    <td><p>Macroni provides a <a href="docs/Time_Profiler.md">time profiler</a>.</p></td>
  </tr>
  <tr>
    <td><p>Locating memory leaks is usually difficult.</p></td>
    <td><p>Macroni provides a <a href="docs/Space_Profiler.md">space profiler</a>.</p></td>
  </tr>
  <tr>
    <td><p>Most programming languages suffer from versioning hell.</p></td>
    <td><p>Macroni enforces the use of <a href="docs/Versioning.md">simplified semantic versioning</a>.</p></td>
  </tr>
  <tr>
    <td><p>Most programming languages suffer from build system hell.</p></td>
    <td><p>Macroni builds itself.</p></td>
  </tr>
</table>


<table>
  <tr>
    <th colspan="2">Lisp Features</th>
  </tr>
  <tr>
    <th>Problem</th>
    <th>Solution</th>
  </tr>
  <tr>
    <td>
      <p>Different programming languages have different strengths, so use the right tool for the job.</p>
      <p>Unfortunately, different programming languages usually do not link together.</p>
    </td>
    <td>
      <p>Lisp’s strength is extending itself including embedding programming languages in itself, so it is the right tool for every job.</p>
      <p>Lisp links with itself.</p>
    </td>
  </tr>
  <tr>
    <td><p>Discovering defects is usually difficult.</p></td>
    <td><p>Lisp macros can perform any static or dynamic analysis.</p></td>
  </tr>
  <tr>
    <td><p>Debugging macros and external code generators is usually difficult.</p></td>
    <td><p>Lisp macros are no more difficult to debug than functions.  Errors report the macro call location, not a location in the generated code.</p></td>
  </tr>
</table>


<table>
  <tr>
    <th colspan="2">Lisp Dialect Features</th>
  </tr>
  <tr>
    <th>Problem</th>
    <th>Solution</th>
  </tr>
  <tr>
    <td><p>Some programming languages ignore errors, maximizing the destructiveness of defects and the difficulty of debugging.</p></td>
    <td><p>Macroni does not ignore errors.</p></td>
  </tr>
  <tr>
    <td><p>Most programming languages overcomplicate error handling.</p></td>
    <td><p>Macroni handles defect errors by microrebooting and represents system errors as values.</p></td>
  </tr>
  <tr>
    <td><p>Ensuring local security requires memory safety and type safety.</p></td>
    <td><p>Macroni is memory safe and type safe.</p></td>
  </tr>
  <tr>
    <td><p>Most programming languages ignore arithmetic errors.</p></td>
    <td>
      <p>In Macroni, integer underflow and overflow causes promotion to bigint.  64-bit integer modular arithmetic is supported (via dedicated functions) but is not the default.</p>
      <p>In Macroni, integer and float division by zero, float underflow and overflow, and float invalid operations are defect errors.</p>
    </td>
  </tr>
  <tr>
    <td><p>Macro systems are usually too dangerous, limited, or verbose.</p></td>
    <td><p>Macroni uses an <a href="docs/Macros.md">implicit renaming macro system</a> that is hygienic by default, procedural, and concise.</p></td>
  </tr>
  <tr>
    <td><p>Lists waste time and space.</p></td>
    <td><p>Macroni uses immutable <a href="docs/Vectors.md">vectors</a> (trees of short arrays) instead of lists.  Immutable vectors provide efficient random access and structure sharing with more locality of reference and less pointer overhead, and they can be efficiently constructed forward.</p></td>
  </tr>
  <tr>
    <td><p>Some programming languages use 1-based array indexing, making computing indices error-prone and verbose.</p></td>
    <td><p>Macroni uses 0-based vector indexing.</p></td>
  </tr>
  <tr>
    <td><p>Most Lisp dialects conflate the empty list, the null pointer, and false, sometimes causing the semipredicate problem.</p></td>
    <td><p>Macroni distinguishes between <code>'()</code> (the empty immutable vector), <code>#null</code>, and <code>#f</code>.</p></td>
  </tr>
  <tr>
    <td><p>Most Lisp dialects are case-insensitive, unlike math and most computing systems.</p></td>
    <td><p>Macroni is case-sensitive, but uppercase in identifiers is intended to only be used for math transcription and interoperability.</p></td>
  </tr>
  <tr>
    <td><p>Global scope causes maintenance problems.</p></td>
    <td><p>Macroni’s widest scope is <a href="docs/Modules.md">module</a> scope.</p></td>
  </tr>
  <tr>
    <td><p>Dynamic scope does not compose.</p></td>
    <td><p>Macroni does not support dynamic scope.</p></td>
  </tr>
  <tr>
    <td><p>Some Lisp dialects use separate namespaces for variables and procedures, making functional programming verbose.</p></td>
    <td><p>Macroni uses a single namespace for variables and procedures.</p></td>
  </tr>
  <tr>
    <td><p>Some programming languages’ built-in constructs are unnecessarily inconsistent with user-defined constructs, interrupting the programmer’s flow and causing accidental complexity.</p></td>
    <td><p>Macroni’s <a href="docs/Built-Ins.md">built-in</a> constructs are as consistent as possible with user-defined constructs.</p></td>
  </tr>
  <tr>
    <td><p>Most programming languages suffer from the expression problem.</p></td>
    <td><p>Macroni’s <a href="docs/Object_System.md">object system</a> defines types and generic functions while enforcing encapsulation.</p></td>
  </tr>
  <tr>
    <td>
      <p>Most Lisp dialects coerce the empty list and false to false and all other values to true in Boolean contexts, which is useless.</p>
      <p>Most Lisp dialects do not coerce false to 0 and true to 1 in arithmetic contexts, which prevents the use of bitwise operations and branchless programming.</p>
    </td>
    <td>
      <p>Macroni coerces empty data structures, <code>""</code>, <code>#null</code>, <code>#f</code>, and zero to <code>#f</code> and all other values to <code>#t</code> in Boolean contexts, which is useful for bitwise operations and processing strings and data structures.</p>
      <p>Macroni coerces <code>#f</code> to <code>0</code> and <code>#t</code> to <code>1</code> in arithmetic contexts.</p>
    </td>
  </tr>
  <tr>
    <td>
      <p>Some programming languages only provide floating-point numbers, making working with binary files and network protocols error-prone and verbose.</p>
      <p>Some programming languages do not follow conventions for numeric promotion, making arithmetic verbose.</p>
    </td>
    <td>
      <p>Macroni provides signed bigint and 64-bit binary floating-point numbers.</p>
      <p>Macroni follows conventions for numeric promotion (e.g. integers are promoted to floats when used in arithmetic with them).</p>
    </td>
  </tr>
  <tr>
    <td><p>Some programming languages use biased rounding or truncation, causing avoidable cumulative error.</p></td>
    <td><p>Macroni uses unbiased rounding but supports explicit truncation.</p></td>
  </tr>
  <tr>
    <td><p>Some programming languages define 0⁰ as a defect error, breaking several branches of math.</p></td>
    <td><p>Macroni correctly defines 0⁰ as 1.</p></td>
  </tr>
  <tr>
    <td><p>Some programming languages only provide quotient (truncating division) and remainder (truncating modulo) despite floor division and modulo being more useful in practice.</p></td>
    <td><p>Macroni provides floor division returning an integer and (flooring) modulo.</p></td>
  </tr>
  <tr>
    <td><p>Some programming languages use mutable strings despite their mutability being useless and it preventing strings from being hashable and internable.</p></td>
    <td><p>Macroni uses immutable strings.</p></td>
  </tr>
  <tr>
    <td><p>Some programming languages do not support UTF-8, breaking modern text.</p></td>
    <td><p>Macroni source code and dynamically constructed strings are <a href="https://www.unicode.org/reports/tr15/">NFC</a> <a href="https://www.unicode.org/versions/latest/">UTF-8</a> without a <a href="https://en.wikipedia.org/wiki/Byte_order_mark">BOM</a>.  Be aware that file system paths are regarded as byte vectors instead of strings because they might not be NFC or UTF-8!</p></td>
  </tr>
  <tr>
    <td><p>Some Lisp dialects allow whitespace and special characters in symbols, which is only useful for obfuscation.</p></td>
    <td><p>Macroni’s symbols are <a href="https://www.unicode.org/reports/tr31/">UAX #31</a> identifiers (which disallow whitespace and special characters) with adjustments to allow conventional Lisp symbols, but characters outside the <a href="https://en.wikipedia.org/wiki/ASCII">ASCII</a> range in identifiers are intended to only be used for math transcription and interoperability.</p></td>
  </tr>
  <tr>
    <td><p>Regular expressions are usually difficult for humans to read and for structure editors to edit, and they usually support non-regular features that are inefficient.</p></td>
    <td><p>Macroni uses something similar to <a href="docs/sre.txt">Scheme regular expressions</a>.</p></td>
  </tr>
  <tr>
    <td><p>Generators use mutation, so they cannot backtrack.</p></td>
    <td><p>Macroni uses something similar to <a href="https://htmlpreview.github.io/?https://github.com/Shambles-Dev/Macroni/blob/master/docs/SRFI%2041%20%20Streams.htm">Scheme streams</a>.</p></td>
  </tr>
  <tr>
    <td><p>Most programming languages do not regard random access data structures as functions, making using them verbose.</p></td>
    <td><p>Macroni regards random access data structures as functions.</p></td>
  </tr>
  <tr>
    <td><p>Most Lisp dialects have limited support for dictionaries.</p></td>
    <td>
      <p>Macroni provides immutable and mutable insertion-order-preserving, order-insignificant <a href="docs/Dictionaries.md">dictionaries</a>.</p>
      <p>They can be processed as dictionaries, sequences of vectors containing key-value pairs, or sets.  Set operations on key-value pairs have their uses.</p>
      <p>The syntax for (immutable) dictionary literals is easy for humans to read and suitable for structure editing (e.g. <code>{("key a" "value a") ("key b" "value b")}</code>).</p>
    </td>
  </tr>
  <tr>
    <td><p>State often becomes corrupt.</p></td>
    <td><p>Macroni minimizes state by only allowing <a href="docs/Mutation.md">mutation</a> where it is necessary (state must survive across events and revocable capabilities must work) or unobservable and helpful (temporary local state can improve simplicity and efficiency).</p></td>
  </tr>
  <tr>
    <td><p>Most Lisp dialects have statement-like expressions (e.g. binding and mutating forms) that return meaningful values, encouraging their misuse inside other expressions.</p></td>
    <td><p>Macroni’s statement-like expressions return <code>#null</code>.</p></td>
  </tr>
  <tr>
    <td><p>Most Lisp dialects overcomplicate equality.</p></td>
    <td>
      <p>Macroni defines two equality predicates: <code>=</code> and <code>is</code>.</p>
      <p>Both test the value equality (a.k.a. structural equality) of immutable types.</p>
      <p><code>=</code> tests the value equality of mutable types.</p>
      <p><code>is</code> tests the identity equality (a.k.a. physical equality) of mutable types.</p>
    </td>
  </tr>
  <tr>
    <td><p>Tail calls usually waste space.</p></td>
    <td><p>Macroni performs tail call elimination.</p></td>
  </tr>
  <tr>
    <td><p>Optional and keyword parameters do not fit the evaluation model.</p></td>
    <td><p>Macroni does not support optional or keyword parameters.  It does support generic functions with different definitions for different arities and rest (variadic) parameters.</p></td>
  </tr>
  <tr>
    <td><p>Most programming languages do not define the order of evaluation of function arguments, making programming error-prone.</p></td>
    <td><p>Macroni evaluates function arguments from left to right.  Optimizers may use a different order only if the difference would be unobservable.</p></td>
  </tr>
  <tr>
    <td><p>First-class continuations usually do not compose.</p></td>
    <td><p>Macroni supports only <a href="docs/Continuations.md">multi-prompt delimited continuations</a>, which do compose.</p></td>
  </tr>
  <tr>
    <td><p>Multiple return values do not fit the evaluation model.</p></td>
    <td><p>Macroni uses pattern matching for destructuring instead.</p></td>
  </tr>
  <tr>
    <td><p>Optimizers usually cannot optimize Lisp dialects well.</p></td>
    <td><p>Macroni’s restrictions on mutation and exposure from types and modules make static analysis easier for computers and humans.</p></td>
  </tr>
  <tr>
    <td><p>Optimizers are slow.</p></td>
    <td><p>In Macroni, a module can be compiled quickly with no optimization and a lot of instrumentation, then compiled again with aggressive profile-guided optimization in the background, and then the improved code can be hot-swapped in.</p></td>
  </tr>
  <tr>
    <td><p>Garbage collection usually does not scale.</p></td>
    <td><p>Macroni’s sandboxes’ heaps are separate.  Garbage collection between them is potentially parallel with no blocking.</p></td>
  </tr>
  <tr>
    <td><p>Garbage collection usually causes pauses.</p></td>
    <td><p>Macroni’s <a href="docs/Garbage_Collector.md">garbage collector</a> is incremental.</p></td>
  </tr>
  <tr>
    <td><p>Garbage collection is usually slow.</p></td>
    <td>
      <p>Macroni’s garbage collector is fast for several reasons:
        <ul>
          <li>Macroni allocates on the stack instead of the heap when possible.</li>
          <li>It is quiescent when not allocating on the heap.</li>
          <li>It uses a bump allocator, the fastest kind of allocator.</li>
          <li>It uses a semi-space algorithm, so it is less likely to cause thrashing and it makes one less traversal than mark-and-sweep.</li>
          <li>It self-optimizes for locality of reference.</li>
          <li>Destructing a sandbox deallocates its memory without performing garbage collection.</li>
        </ul>
      </p>
    </td>
  </tr>
</table>
