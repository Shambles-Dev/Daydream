Show a diagram of the sandbox hierarchy with color-coding for host-specificity.

initial sandbox -> user interface -> development tools and applications

The initial sandbox and user interface are host-specific.  The initial sandbox is the hardware or operating system abstraction layer and runtime system.  The user interface either implements a window system or passes window system operations through to the initial sandbox, and it launches programs and mediates capability sharing between them.

Development tools might be host-specific.  They might use machine code or a portable code format.

Applications are not host-specific.
