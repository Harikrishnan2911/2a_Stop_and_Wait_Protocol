# 2a_Stop_and_Wait_Protocol
## AIM 
To write a python program to perform stop and wait protocol
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM

server.py

import socket

# Create socket
server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

host = "127.0.0.1"
port = 12345

# Bind and listen
server.bind((host, port))
server.listen(1)

print("Server waiting for connection...")

conn, addr = server.accept()
print("Connected to:", addr)

while True:
    # Receive message from client
    client_msg = conn.recv(1024).decode()
    print("Client:", client_msg)


    if client_msg.lower() == "exit":
        break

    # Send message to client
    msg = input("Server: ")
    conn.send(msg.encode())

    if msg.lower() == "exit":
        break

conn.close()
server.close()

client.py

import socket

# Create socket
client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

host = "127.0.0.1"
port = 12345

# Connect to server
client.connect((host, port))

while True:
    # Send message to server
    msg = input("Client: ")
    client.send(msg.encode())

    if msg.lower() == "exit":
        break

    # Receive reply from server
    server_msg = client.recv(1024).decode()
    print("Server:", server_msg)

    if server_msg.lower() == "exit":
        break

client.close()

## OUTPUT
![alt text](<Screenshot (59).png>)
![alt text](<Screenshot (60).png>)
## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
