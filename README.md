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

Client <br>
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
Server  <br>
<img width="934" height="100" alt="image" src="https://github.com/user-attachments/assets/7c53ce26-5b1d-4301-b335-2b3482625126" />


Client<br>
<img width="942" height="203" alt="image" src="https://github.com/user-attachments/assets/684fbe70-d14d-41f8-9ce7-8544cdf97282" />


## PROGRAM - RARP
Server
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
        vc.send("Not Found".encode())
```
Client
```
import socket 
s=socket.socket() 
s.connect(('localhost',9000)) 
while True: 
    ip=input("Enter MAC Address : ")
    s.send(ip.encode()) 
    print("Logical Address",s.recv(1024).decode())
```
## OUPUT -RARP
Server<br>
<img width="942" height="90" alt="image" src="https://github.com/user-attachments/assets/37d1bfd7-5346-4911-ac92-63baa0d6216b" />

Client<br>
<img width="937" height="205" alt="image" src="https://github.com/user-attachments/assets/6a6a9878-4751-44dd-b57d-2538df65b313" />


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
