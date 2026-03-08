# TCP Three-Way Handshake

Once the browser completes the DNS lookup and the browser now has the web server's IP address, the next step in the
navigation process is to establish a TCP connection to the server.
TCP which stands for Transmission Control Protocol is a reliable, ordered, and error checked connection-oriented
protocol.
The browser uses the IP address to establish a TCP connection to the server using the TCP three-way handshake mechanism.
You can somewhat think of this handshake as the client ensuring the server wants to 'talk' and negotiate the parameters
of the connection. Simply, it ensures that both computers agree on how the session is going to be handled before any
actual data is transmitted.

## The three step process

This process is more commonly called the SYN-SYN-ACK, or the SYN SYN-ACK ACK handshake.

1. It starts with the client sending a SYN packet to the server. The SYN which is a synchronization message is used by
   the client to initiate the session/connection.
2. The server should then respond with a SYN-ACK packet, which is a Synchronize Acknowledgement packet, that confirms
   the client's request by sending it's own SYN.
3. The client should then respond with an ACK packet, which is an Acknowledgement packet and it confirms to the server
   that the connection has been established.

This three-way handshake has to be completed before the browser even requests for any actual data from the server, and
this in the case of a secure HTTPS connection is followed by another part of the process called
the [TLS negotiation](./tls-negotiation.md). which is a 5 step process, making it 8 steps in total before content is
even requested.
