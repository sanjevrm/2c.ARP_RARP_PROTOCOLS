# 2c.SIMULATING ARP /RARP PROTOCOLS
## Name:Sanjev R M
## REG NO:212223040186
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
### Client:
```python
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
### Server:
```python
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
```
   
## OUPUT - ARP
### client:
![image](https://github.com/sanjevrm/2c.ARP_RARP_PROTOCOLS/assets/155142423/009540cc-34a0-415c-bd6d-6f69f70cbf1d)

### Server:
![image](https://github.com/sanjevrm/2c.ARP_RARP_PROTOCOLS/assets/155142423/594fd732-2b62-4b0d-a8da-b44bfef0f4a1)


# PROGRAM - RARP
### Client:
```python
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
### Server:
```python
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
    ip=input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address",s.recv(1024).decode())
```  

## OUPUT -RARP
### client:
![image](https://github.com/sanjevrm/2c.ARP_RARP_PROTOCOLS/assets/155142423/a4dae5ab-1412-4648-aae1-c6445033e8fb)

### server:
![image](https://github.com/sanjevrm/2c.ARP_RARP_PROTOCOLS/assets/155142423/90aa19bc-ff5d-41ae-b4b6-95fa7fe93fdb)



## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.

executed.
