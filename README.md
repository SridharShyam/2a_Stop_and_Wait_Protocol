# 2a_Stop_and_Wait_Protocol
.
### NAME : SHYAM S
### REGISTER NUMBER : 212223240156
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
### server:
```python
import socket

server = socket.create_server(('localhost', 8000))
print("Server listening...")

conn, addr = server.accept()
print(f"Connected with {addr}")

while (data := conn.recv(1024).decode()):
    print(f"Received: {data}")
    conn.sendall(b"ACK")
    if data.lower() == 'exit':
        break

conn.close()
print("Connection closed")

```

### client:
```python
import socket

client = socket.create_connection(('localhost', 8000))

while (msg := input("Enter message ('exit' to quit): ")):
    client.sendall(msg.encode())
    if msg.lower() == 'exit':
        break
    try:
        if client.recv(1024).decode() == "ACK":
            print("Server acknowledged")
    except socket.timeout:
        print("No ACK, retransmitting...")

client.close()
print("Connection closed")

```
## OUTPUT
### client:
![image](https://github.com/user-attachments/assets/a9bdb39c-56cb-458b-a0d0-a77559dcb745)

### server:
![image](https://github.com/user-attachments/assets/9eabc590-d4df-451d-b87d-2996c95ff440)

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
