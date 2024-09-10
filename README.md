# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
## Client
```py
import socket
s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
c, addr = s.accept()
size = int(input("Enter number of frames to send: "))
l = list(range(size))
window_size = int(input("Enter Window Size: "))
st = 0
i = 0

while i < len(l):
    end = min(i + window_size, len(l))
    c.send(str(l[i:end]).encode())
    ack = c.recv(1024).decode()
    if ack:
        print(f"Received acknowledgment: {ack}")
    i += window_size
c.close()
s.close()

```

## Server
```py
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True: 
    print(s.recv(1024).decode())
    s.send("acknowledgement received from the server".encode())
```
## OUPUT
## Client
![Screenshot 2024-09-10 083754](https://github.com/user-attachments/assets/b018dde5-686a-4b02-88c5-31959a68ab78)
## Server
![Screenshot 2024-09-10 083736](https://github.com/user-attachments/assets/1547a314-61fd-43dd-9b49-024acbcd36a5)

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
