## How Does a Listener Work Securely?

Listeners evaluate code in a sub-sandbox.  This prevents evaluating code from crashing or hanging a listener.

Listeners wait for the future of each expression to resolve before accepting another expression to evaluate.  The future might resolve to a defect error because its sandbox crashed, causing that listener to microreboot its sub-sandbox.  The user can tell a listener to stop waiting and microreboot its sub-sandbox if it hangs.

Only debugging tools (like listeners) and implementations of the representation interface are allowed to call the representation interface.  This prevents other software from violating capability security by breaking encapsulation.  The system can recognize its components by their capability.  Types define their representation by defining an implementation of the representation interface.

The value resulting from evaluating an expression is converted to its representation in its sandbox so that mutable values can be represented.  The resulting string is immutable, so it can cross a sandbox boundary.


## How Does a Listener Work When Microrebooting?

A listener edits a temporary module by appending top-level forms to it that it has evaluated successfully.  A temporary module can be initialized with a normal module.

Redefinition of a non-built-in is normally a defect error, but in a listener it only results in a warning comment in the transcript (unless it is a duplicate parameter, which is still a defect error).

The cause of a microreboot is appended as a comment in the transcript.

A listener can be configured to run the debugger when its sub-sandbox is microrebooted.

After a microreboot, the temporary module is reloaded and the user can reedit the immediately previous input.


## Usability

In the transcript, input is not prefixed, `#null` results are ignored, and results are commented so that the transcript is suitable for cutting and pasting into a module.
