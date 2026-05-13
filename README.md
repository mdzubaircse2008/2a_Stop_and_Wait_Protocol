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
```
server.py

import socket
s = socket.socket()
s.connect(('localhost', 8000))
while True:
    data = s.recv(1024).decode()
    if data.lower() == "exit":
        print("Server ended the chat")
        break
    print("Server says:", data)
    s.send("Acknowledgement Received".encode())
s.close()

client.py

import socket
s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
print("Waiting for connection...")
c, addr = s.accept()
print("Connected to:", addr)
while True:
    i = input("Enter a data: ")
    c.send(i.encode())
    if i.lower() == "exit":
        print("Connection closed")
        c.close()
        break
    ack = c.recv(1024).decode()
    print(ack)

```
## OUTPUT
<img width="1490" height="1009" alt="image" src="https://github.com/user-attachments/assets/87072f88-3524-4217-ba03-d8f58a07d631" />
<img width="1497" height="1003" alt="image" src="https://github.com/user-attachments/assets/b9a96dd0-ecd9-4b6d-a828-e99a635153d2" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
