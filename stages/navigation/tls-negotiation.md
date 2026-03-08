# TLS Negotiation

The TLS negotiation is the final step in the navigation process after the TCP three-way handshake for secure HTTPS
connections.
The primary purpose of the TLS negotiation is to establish a secure connection between the client and the server before
any sensitive data is exchanged.

The negotiation starts with the client sending a 'Client Hello' message to the server, which contains the MAX version of
the supported TLS version, with the latest being 1.3 at the time of writing, and a list of cipher suites that the
client supports.
A cipher suite is a string representation of all the different things
involved in the handshake, like the key exchange, public key authentication, and the actual encryption. One of the
most
common cipher suites is the TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256 cipher suite, which uses the ECDHE (Elliptic Curve
Diffie-Hellman) key exchange algorithm, which is used to get a shared secret between the client and the web server,
with RSA being the public key authentication mechanism used to verify the identity of the server, using AES for the
actual encryption, with a 128-bit key size, and using the GCM mode of operation for the encryption, with SHA256 as
the
hash function. To get into the more technical bits of the cipher suite I'd recommend this video from
the [Computerphile YouTube
channel](https://www.youtube.com/watch?v=86cQJ0MMses).

You can think of the cipher suite as a string that contains the instructions for a TLS negotation.
The server then responds with a 'Server Hello' message which contains the chosen TLS version from the client's provided
list, the chosen cipher suite, and some other information.
The server then also sends a 'Certificate' message, which contains the server's public key, all of which is to verify
the server.

The client then sends a 'Client Key Exchange' message, which contains the client key exchange data, which is used to
generate a shared secret between the client and the server. The client then sends a 'Finished' message, which contains
the
client's finished data which can be used to verify that this negotiation hasn't been tampered with, and the server also
then sends a 'Finished' message.

If you've noticed we now have 8 back and forth messages between the client and the server, which does add latency, but
is necesary to ensure that the connection is secure. Luckily, TLS 1.2 is designed to perform these 5 steps in two round
trips, with 1.3 improving on that to make it in one trip to make that even faster.

After the TLS negotiation is complete, the client and server can then start exchanging data.
