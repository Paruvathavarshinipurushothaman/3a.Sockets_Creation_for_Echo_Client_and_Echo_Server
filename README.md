# 3a.CREATION FOR ECHO CLIENT AND ECHO SERVER USING TCP SOCKETS
# AIM
To write a python program for creating Echo Client and Echo Server using TCP
Sockets Links.
## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server .
4. Send and receive the message using the send function in socket.
## PROGRAM
## echo_server:
```

import socket

# Create socket object
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

host = '127.0.0.1'
port = 5050

server_socket.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)
server_socket.bind((host, port))

# Listen for connections
server_socket.listen(1)
print("Echo Server is waiting for connection...")

# Accept client connection
client_socket, addr = server_socket.accept()
print("Connected to:", addr)

try:
    while True:
        # Receive message
        data = client_socket.recv(1024)

        if not data:
            break

        message = data.decode()
        print("Client:", message)

        # Send same message back
        if message.lower() == 'exit':
            break

        client_socket.sendall(data)

except ConnectionError:
    print("Client connection was interrupted.")

finally:
    client_socket.close()
    server_socket.close()
    print("Server connection closed.")

```
## Client
```

import socket

# Create socket object
client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

host = '127.0.0.1'
port = 5050

try:
    # Connect to server
    client_socket.connect((host, port))
    print("Connected to Echo Server")

    while True:
        message = input("Enter message: ")

        # Send message
        client_socket.sendall(message.encode())

        if message.lower() == 'exit':
            break

        # Receive echoed message
        data = client_socket.recv(1024).decode()
        print("Server echoed:", data)

except ConnectionError:
    print("Connection to server lost.")

finally:
    client_socket.close()


```
## OUTPUT
## echo_server:
<img width="1272" height="265" alt="image" src="https://github.com/user-attachments/assets/57cbbf9f-6e20-48e3-be8d-b683accd8b8d" />

## echo_client:
<img width="1272" height="305" alt="image" src="https://github.com/user-attachments/assets/b08a09db-e051-483a-ac1a-1b6c405fe88f" />


## RESULT
Thus, the python program for creating Echo Client and Echo Server using TCP Sockets Links 
was successfully created and executed.
