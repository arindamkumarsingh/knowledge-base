# DHCP, NTP and DNS

Time matters much more, if in a cisco device if the time is wrong its a big deal as the security certs depend on valid dates to know if they are expired, VPNs and other connection relie on it and logging becomes **accurate**.

IF the time stamps of the logging events is wrong we cannot sequence the events and wont be able to reverse engineer what happened.

Manual clock setting is the quick fix and NTP is the real solution.

Commands:-

`show clock` = gives current date, time etc.

`show clock detail` = to know where the time came from , from hardware or from human.

`clock set` - can do that from priveleged EXEC mode

after doing this command if run the 2nd command it will show the source changed from hardware calendar to user configuartiuon

`clock timezone (area) -h` = device can be recalculated based on the new offset