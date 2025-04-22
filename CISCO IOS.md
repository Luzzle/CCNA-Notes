#ccna-day4

Connected through devices console port either RJ45 or USB mini B
Rollover cable: Cable usually is RJ45 and DB9 used to connect to Cisco devices.

##### Default Settings
Parity: None
Baud Rate: 9600

[[Commands]]
### User Exec Mode
Indicated by > after the hostname of the device. 
Cannot make any configuration changes to the device.

### Privileged Exec Mode
Indicated by #.
Can view config, restart device etc.. but cannot make any configuration changes beyond saving the config file.

### Global Configuration Mode
Required to make any configuration changes on the device.

## Config Files
##### Running-config
Current active configuration file. CLI commands edit active config
Saving running-config sets it to startup-config

##### Starting-config
Config file that opens on device restart

