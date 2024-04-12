# 2c.SIMULATING ARP /RARP PROTOCOLS
### NAME:GOKUL S
### REF.NO:212223040051
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
CLIENT:
~~~PYTHON
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
~~~
SERVER:
~~~PYTHON
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
~~~
## OUPUT - ARP
## CLIENT
![image](https://github.com/SGokul2005/2c.ARP_RARP_PROTOCOLS/assets/147121825/3e7f1fb2-e7b2-40df-b659-ad06d69b0652)
## SERVER
![image](https://github.com/SGokul2005/2c.ARP_RARP_PROTOCOLS/assets/147121825/3389f745-a8d4-40a4-9d63-204d9383d2a9)

## PROGRAM - RARP
## CLIENT
~~~PYTHON
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
~~~
## SERVER
~~~PYTHON
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
    ip=input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address",s.recv(1024).decode())
~~~
## OUPUT -RARP
CLIENT:
![image](https://github.com/SGokul2005/2c.ARP_RARP_PROTOCOLS/assets/147121825/4f497ab6-cb50-44b6-a08a-8b4f3fa4f662)
SERVER:
![image](https://github.com/SGokul2005/2c.ARP_RARP_PROTOCOLS/assets/147121825/b43cd6da-d386-4036-adcf-8ff657f6978c)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
