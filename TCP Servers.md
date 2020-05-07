# TCP Servers

### Event Queues

- Most of NodeJS architecture is built around events. 
- Objects that emit events in NodeJS are instances of the EventEmitter(EE)
- EventEmitter’s are good for handling asynchronous events. 
- Functions can be registered as listeners for an event.
- These instances can emit events and pass the listener’s data.

### OSI Model
- Compiuters have been networked since the early 1970s. 
- In the mid 1980s the “Open Systems Interconnection Reference Model” (OSI model) was developed 
- This seven layer OSI model has continued to accurately describe the different processes in computer networking 
- A developer or engineer is responsible for a specific layer and communicating with the layer above and below. 
- Not every computer network solution uses all seven layers
- HTTP skips the Presentation and Session layers and lives directly on top of the Transport layer.

| #	| Layer	| Protocol Data Unit	| Function	| Examples |
|---|-------|---------------------|-----------|----------|
|7	| Application	| Data	| Height Level APIs	| HTTP, IMAP, POP, SSH|
|6	| Presentation	| Data	| Data translating, including encryption, character encoding, and compression	| Strings encoded with null terminated strings vs Strings defined by an Integer Length|
|5	| Session	Data	| Manages a session though passing data back and fourth	| NetBios and Remote Procedure Protocol (RPC)|
|4	| Transport	| Segment / Datagram	| Reliable transmission of data between points on a network	TCP and UDP|
|3	| Network	| Packet	| Managing the network through addressing, routing, and traffic control	| IP and ICMP|
|2	| Data Link	| Frame	| Reliable transmission of frames between to physical layer nodes	| Ethernet and IEEE 802.11 wireless LAN|
|1	| Physical	| bit	| transmission and reception of raw data streams over a physical medium	| USB, Bluetooth, Ethernet physical layer, SMB, Telephone network modem|

### Internet Protocol Suite
- The Internet Protocol Suite is the conceptual model for the protocols used by the internet (TCP/IP)
- Uses four layers - `Link, Internet, Transport, and Application`
- Reference when discussing network communication and data exchange.

| Layer	| Function| Examples |
|-------|---------|----------|
| Application	| Provides high level data exchange for use in user application development	| HTTP, SMTP, FTP, DHCP|
| Transport	| Provides process to process data exchange	| TCP, UDP, µTP|
| Internet	| Maintains computer addressing and identification and manages packet routing	| IPv4, IPv6, ICMP|
| Link layer | Used to move packets between two different hosts	| MAC, ARP, DSL, Ethernet|

### TCP (**Transmission Control Protocol**)
- TCP is widely used by *application* layer protocols.
- TCP creates a two way communication between hosts.
- TCP data transfers manage each IP packet between the hosts carries a single TCP Segment. 
- TCP segments are made up of header and data sections.

### TCP HEADER
- TCP Header is used at each end to control the type of interaction being sent. 

It contains the following information:
```
Byte 0: Source port - a 16 bit source port
Byte 3: Destination port - a 16 bit destination port
Byte 4: Sequence number - a 32 bit sequence number that sets the initial sequence number and manages the accumulated sequence number
Byte 8: Acknowledgement number - if ACK is set it contains a 32 bit acknowledgement number that is the next sequence number that the sender is expecting. It is used for acknowledging the bytes it has so far received
Byte 12: Data Offset, NS flag, and 3 undefined bits - a 4 bit data offset specifies the size of the tcp header in 32 bit words.
Byte 13: CWR, ECE, URG, ACK, PSH, RST, SYN, and FYN flags - 9 flag bits
> NS - an experimental feature for a nonce sum - a nonce is a random cryptographic number used to prevent people from lying about who they are (authentication)
> CWR - used to acknowledge that a TCP segment with the ECE flag has been received, and the Window has been reduced to alleviate congestion
> ECE - if SYN is 1 it indicates that the peer is ECN capable, other otherwise its used to indicate that there is network congestion.
> URG - indicates that the Urgent pointer filed is significant
> ACK - indicates that the ACK field is significant - all packets after the initial SYN should have this flag set
> PSH - used to ask to push the buffered data to the receiving application.
> RST - used to reset the connection
> SYN - sent only on the first packet sent from each end to synchronize the sequence numbers
> FIN - indicates the last package from a sender, and is used in closing a connection
Byte 14: Window size - a 16 bit window size
Byte 16: Checksum - a 16 bit checksum used for error checking the header
Byte 18: Urgent pointer - if URG is set it contains a 16 bit urgent Pointer
Byte 20: Options - a variable 0 to 320 bit (divisible by 32) options section
```

