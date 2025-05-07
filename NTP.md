#ccna-day37

### Overview
Used to establish a server to synchronize system time. 
NTP clients request the time from NTP servers.
The 'distance' of an NTP from the original reference is called the "stratum".

### Stratum
A reference clock is usually a very accurate time device like an atomic clock or GPS clock.
Reference clocks are stratum 0. All servers directly connected to reference clocks are stratum 1.

Stratum 15 clocks are considered the maximum, anything further is considered unreliable.

### Configuration
*Manual Clock Configuration*
```ios
# clock set TIME DATE
# show clock detail
```

```ios
# ntp server [IP] - set ntp server to use to synchronize time
# ntp master - use this server as a NTP server

---- setup NTP authentication on server ----
# ntp authenticate
# ntp authentication-key KEY-NUMBER md5 KEY
# ntp trusted-key KEYNUMBER

---- setup NTP authentication on client ----
# ntp authenticate
# ntp authentication-key KEY-NUMBER md5 KEY
# ntp server IP key KEY-NUMBER
```