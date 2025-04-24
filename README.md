# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
### Name: Ezhil Nevedha K
### Reg.no: 212223230055
## AIM:
To write a python program to perform sliding window protocol
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM:
### server.py
```
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
```
### client.py
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement recived from the server".encode())
```
## OUPUT:
![image](https://github.com/user-attachments/assets/66c6b7d0-da1f-41af-843f-960a94f090dc)

![image](https://github.com/user-attachments/assets/10b0659b-6c9b-4f24-877c-43e08503e00b)

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
