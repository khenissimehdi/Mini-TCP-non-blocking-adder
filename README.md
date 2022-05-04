# Mini TCP non-blocking adder
We want to write a server that handles multiple clients with a single thread
in a non-blocking fashion and that allows additions of two integers for each client.

# Protocol SumOneShot
The client send the 8 Bytes (4 bytes is an integer means he is going to send Two) than closes the connection on write
mode.
The server send 4 Bytes (one Integer) as the result of the summing of the values sent by the client, and close the full
connection.
Example : 
client send 1,3 
server respond 4

# Guide lines
1. The attachment of the SelectionKey have to store a ByteBuffer of size Integer.BYTES * 2 ( when you accept the client)
2. On Write mode the server have to make sure that it sent all the values.
3. In method processSelectedKeys the server should handle the exceptions in the right way.

