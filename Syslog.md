#ccna-day41

### Overview
- Syslog is an industry standard protocol for message logging.
- On network devices, Syslog can be used to log events such as changes in interface status, changes in OSPF neighbor status, system restarts etc...

Syslog uses **UDP Port 514**.
### Format
`SEQ:TIME-STAMP: %FACILITY-SEVERITY-NMEMONIC:DESCRIPTION`
- SEQ - A sequence number indicated the order/sequence of messages.
- TIME-STAMP: Timestamp the message was created.
- FACILITY: A value that indicates which process on the device generated the message.
- SEVERITY: A number that indicates the severity of the logged event.
- NMEMONIC: A short code for the message, indicating what happened.
#### Severity Level

| Level | Description                       | Keyword       |
| ----- | --------------------------------- | ------------- |
| 0     | System is unusable                | Emergency     |
| 1     | Action must be immediately taken  | Alert         |
| 2     | Critical Conditions               | Critical      |
| 3     | Error Conditions                  | Error         |
| 4     | Warning Conditions                | Warning       |
| 5     | Normal but significant conditions | Normal        |
| 6     | Informational Messages            | Informational |
| 7     | Debugging Messages                | Debugging     |

### Configuration
```ios
(config)# logging console LEVEL
(config)# logging monitor informational -> VTY
(config)# logging buffered SIZE LEVEL -> log to RAM
(config)# logging IP -> log to external server
(config)# logging trap debugging
```

