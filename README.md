# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
### Name:Swetha D
### Reg no:22223040222
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
# Client
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send:"))
l=list(range(size))
s=int(input("Enter Window Size:"))
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
# Server
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement received from the server".encode())
```
## OUPUT
<h3>Client</h3>
<img width="575" height="223" alt="image" src="https://github.com/user-attachments/assets/21a14e96-f7a3-4719-b77c-6bc4282de2c8" />
<h3>Server</h3>
<img width="478" height="162" alt="image" src="https://github.com/user-attachments/assets/be0c9a00-c9ed-4fb1-85e3-d50515361c76" />


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
