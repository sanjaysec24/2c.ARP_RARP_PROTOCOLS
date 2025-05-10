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
## SERVER
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode()) 
```
## CLIENT
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
```

## OUPUT - ARP
## SERVER
![image](https://github.com/user-attachments/assets/0cfda9d1-2754-4973-bcf7-055cc8385921)
## CLIENT
![image](https://github.com/user-attachments/assets/ef2b17d1-a115-4860-9a76-6144263f1651)

## PROGRAM - RARP
## SERVER
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
    ip=input("Enter MAC Address : ")
    encode())
    print("Logical Address",s.recv(1024).decode())
```
## CLIENT
```
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```
## OUPUT -RARP
## SERVER
![image](https://github.com/user-attachments/assets/c0f45d88-03c6-4cb4-a30e-2d87afab6d7b)
## CLIENT
![image](https://github.com/user-attachments/assets/fdac2886-4459-4d9d-8a7f-2d673b7a9bde)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
