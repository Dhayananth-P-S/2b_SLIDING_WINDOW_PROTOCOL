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
'''py
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send : "))
l=list(range(size))
s=int(input("Enter Window Size : "))
st=0
i=0
while True:
   while(i<len(l)):
    st+=s
    c.send(str(l[i:st]).encode())
    ack=c.recv(1024).decode()
if ack:
 print(ack)
 i+=s
'''

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
![Screenshot 2024-09-10 082647](https://github.com/user-attachments/assets/1ea53df3-5518-4375-b3ac-980edaaf6af0)
![Screenshot 2024-09-10 082709](https://github.com/user-attachments/assets/70f0c72c-8c3b-4c4b-b255-6956ffcbb658)

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
