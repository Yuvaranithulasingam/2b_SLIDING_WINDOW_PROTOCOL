# EX:NO:2b          IMPLEMENTATION OF SLIDING WINDOW PROTOCOL

## AIM
To implement to sliding window protocol.
## ALGORITHM:
1. Start the program.</br>
2. Get the frame size from the user</br>
3. To create the frame based on the user request.</br>
4. To send frames to server from the client side.</br>
5. If your frames reach the server it will send ACK signal to client</br>
6. Stop the Program</br>
## PROGRAM
### CLIENT:
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
### SERVER:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True: 
 print(s.recv(1024).decode())
 s.send("acknowledgement recived from the server".encode())
```
## OUPUT
### CLIENT:
![CLIENT1b](https://github.com/Yuvaranithulasingam/2b_SLIDING_WINDOW_PROTOCOL/assets/121418522/d7e60a2b-08e5-41a0-8a35-d7eedc47a426)
### SERVER:
![SERVER1b](https://github.com/Yuvaranithulasingam/2b_SLIDING_WINDOW_PROTOCOL/assets/121418522/b7363e32-7a76-4f13-9354-5d19aac1dcaf)

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
