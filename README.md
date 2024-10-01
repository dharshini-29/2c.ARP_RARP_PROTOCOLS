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
## CLIENT
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
## SERVER
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("Acknowledgement Recived".encode())
## OUPUT - ARP
## CLIENT
![Screenshot 2024-10-01 085717](https://github.com/user-attachments/assets/4c646b23-89b7-4ff6-bad7-404d78bdb859)
## SERVER
![Screenshot 2024-10-01 085652](https://github.com/user-attachments/assets/b090ae43-818b-4315-9f82-b4a04c418867)





## PROGRAM - RARP
## CLIENT 
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
## SERVER
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
 ip=input("Enter MAC Address : ")
 s.send(ip.encode())
 print("Logical Address",s.recv(1024).decode())
## OUPUT -RARP
## CLIENT 
![Screenshot 2024-10-01 091903](https://github.com/user-attachments/assets/9d838507-99d8-4719-8ed7-1e668ea2a6d6)

## SERVER
![Screenshot 2024-10-01 091915](https://github.com/user-attachments/assets/7985ca80-87cc-423c-af72-e00f546d51df)




## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
