# DNS Lookup

The first step in the navigation process is to find the location of the server the user is trying to reach.
For example, let's say I'm trying to reach the server at 'www.google.com', the hostname in this case will
be google.com. While this is human-readable, servers can really make little of it, as they are not primarily
identified by
such labels, and those labels are used because it'd be tricky to remember the correct IP address of
`www.google.com`. So instead, the browser performs a DNS lookup. This DNS lookup acts as the translator that takes
in the
human-friendly label, and finds the actual ID of the server, which is it's IP address.

You might be wondering if the browser performs this action every time a webpage is visited. The response, as is common
in software engineering, is that it varies.

The browser executes this process for each distinct hostname it encounters, subsequently storing the outcome in a cache
to speed up subsequent requests to the same hostname.

To summarize, upon encountering a hostname, the browser first consults its local cache, essentially querying itself: "
Have I visited this hostname previously?" If the information is not found, it will likely contact your ISP, which can
function as a recursive resolver. This resolver may then communicate with the root server, followed by the Top Level
Domain (TLD) server. The TLD server, in turn, might contact the authoritative name server which will then provide the IP
address of the queried server. This tiered structure of
servers is conclusive, with each level providing progressively more detail regarding the location of the server's IP
address.

Once the browser has the IP address of the server, the next step is the [TCP three-way handshake](./tcp-handshake.md).
