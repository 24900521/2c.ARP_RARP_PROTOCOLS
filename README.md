# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.
P
## PROGRAM - ARP
Server
```

import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter Logical Address : ")
    s.send(ip.encode())
    print("Mac Address : ",s.recv(1024).decode())
```
Client
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"68:34:21:98:46:99":"192.168.252.52"}
while True:
    ip=c.recv(1024).decode()
    try:
     c.send(address[ip].encode())
    except KeyError:
     c.send("Not Found".encode())
```

## OUPUT - ARP
![WhatsApp Image 2025-09-08 at 10 45 22_ce8aed94](https://github.com/user-attachments/assets/84f660d1-d7f2-44ac-93e3-e25eea1f6e17)


## PROGRAM - RARP
server
```

import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address : ",s.recv(1024).decode())
```
Client
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"68:34:21:98:46:99":"192.168.252.52"}
while True:
    ip=c.recv(1024).decode()
    try:
     c.send(address[ip].encode())
    except KeyError:
     c.send("Not Found".encode())
```
## OUPUT -RARP
<img width="957" height="399" alt="Screenshot 2025-09-08 194536" src="https://github.com/user-attachments/assets/734e787f-7002-416d-b74d-c62be4f8db98" />


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
