Microrebooting avoids the disruption caused by restarting a whole program by restarting only the necessary part.  Systems that use it can recover from most defects without human intervention or data loss.

It requires hard/soft-state separation.

In Macroni, this is achieved by stateful modules defining a pair of event handlers (exported functions), one for hard state exporting, one for hard state importing.  The hard state exporting function is passed the version it is exporting to and the hard state importing function is passed the version it is importing from so that they know how to convert the data.
