I/O is vulnerable to attacks on availability.  A sandbox can attempt to exhaust channel capacity or storage capacity.

These time and space sharing problems can be solved with scheduling and quotas, as usual.

Existing scheduling information can be used for I/O scheduling.

An installation endowment can define a storage quota (e.g. for a program's configuration files), but that requires a notion of "program" that must be defined atop Macroni (because the initial sandbox acts as the kernel).
