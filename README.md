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
# Client (sender)
    import socket
    client = socket.socket()
    client.connect(('localhost', 8000))
    while True:
    msg = input("Enter message (or 'exit'): ")
    client.send(msg.encode())
    if msg.lower() == 'exit':
        break
    try:
        ack = client.recv(1024).decode()
        print("Received from server:", ack)
    except socket.timeout:
        print("No ACK, retransmitting...")
    client.close()

# Server (receiver)
    import socket
    server = socket.socket()
    server.bind(('localhost', 8000))
    server.listen(1)
    print("Server listening...")
    conn, addr = server.accept()
    print("Connected by", addr)
    while True:
    data = conn.recv(1024).decode()
    if not data:
        break
    print("Received:", data)
    conn.send("ACK".encode())
    if data.lower() == 'exit':
        print("Closing connection")
        break
    conn.close()

## OUTPUT

<img width="508" height="155" alt="exp2cna1" src="https://github.com/user-attachments/assets/bcd38d3d-e3a0-4536-b5dc-fb40a02b64dc" />
<img width="515" height="72" alt="exp2cna2" src="https://github.com/user-attachments/assets/112ab393-501f-4e24-86c7-9a0ce84b8ec0" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
