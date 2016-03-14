Confining capabilities is possible using membranes.

Confining data is impractical to impossible.  All covert channels must be eliminated.  That requires all operations at the hardware and software levels to consume the same amounts of the same types of energy, time, and space and emit the same amounts of the same types of radiation.  Such hardware and software would be very limited and inefficient.

It is possible to convert data leaks into capability leaks in password capability systems (i.e. distributed capability systems), so reference capabilities should be used instead when possible.  Access control list systems are even less secure.  They are less fine-grained and dynamic.  Knowing a password in an access control list system grants access to many would-be capabilities for an unbounded amount of time.

Distributed capabilities can be shared with attackers by remote hosts, so distributed capabilities should be distinguished in source code to ease auditing.

Leaks can occur with or without the cooperation of hardware or software trusted with the data.  Energy, time, and space consumption and radiation modulate either way.

The only practical solution to this problem seems to be consumers demanding open source hardware and software and rejecting mobile code.  Open source hardware and software makes it possible to verify the absence of Trojan horses and remote vulnerabilities.  Mobile code presents an unreasonable risk, even when sandboxed, because it is impractical to eliminate all local covert channels and mobile code converts local vulnerabilities, like side-channel vulnerabilities, into remote vulnerabilities.

Macroni does not provide distributed capabilities because their use requires cooperation.  It does not encourage the use of mobile code, but it provides best-effort sandboxing to minimize risk.
