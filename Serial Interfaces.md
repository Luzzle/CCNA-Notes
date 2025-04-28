#ccna-day28 

### Overview
Serial interfaces are used to directly interface with network equipment. 

One side of a serial connection functions as **Data Communications Equipment (DCE)** with other side functioning as **Data Terminal Equipment (DTE)**.
The DCE needs to specify the *clock rate* of the connection.

The default encapsulation is HDLC.
You can configure PPP with 
```ios
(config-if)# encapsulation ppp
```


