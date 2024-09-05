Related to the [[OSI Model]]

TCP (Transmission Control Protocol): Connection-Oriented

UDP (User Datagram Protocol: No Connection)

---

TCP:

- Establishes a connection between sender and reciever with a handshake before sending data
		- Syn
		- Syn/ACK
		- ACK
- Guarantees reliable  delivery of data through acknowledgments
- Ensures data es delivered on the right order

Header field:

![[TCP_Header_field.png]]
![[TCP_Control_Flags.png]]![[TCP_Control_flags2.png]]

TCP Ports are usually from 1 to 65,535

---

UDP:

Connectionless, more simplistic but less reliable as it does not guarantee packages will be delivered. Its used for real-time apps as games or VoIP. Its simple and stateless. Each packet is independent

![[TCPvsUDP.png]]

