## How Does a Debugger Work Securely?

Only debugging tools are allowed to access debugging data.  This prevents other software from violating capability security by breaking encapsulation.  The system can recognize its components by their capability.

The debugger ignores user-defined type representations so that defective or malicious implementations are rendered harmless.


## How Does a Debugger Work When Microrebooting?

Modules can be configured to memory dump when they were loaded directly into a sandbox (acting as a ‘program’) and it was destructed for crashing or hanging.  The number of dumps to retain is configurable per module.

A dump contains the reason for destruction, the final state of the sandbox, and the last several bindings and mutations.  How many bindings and mutations to record is configurable per module.

The debugger can view these dumps.  The display is based on primitive types and user-defined type definitions so that user-defined types’ state can always be accurately observed.
