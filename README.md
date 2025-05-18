# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
CLIENT
```
import socket
s = socket.socket()
host = socket.gethostname()
port = 60000
s.connect((host, port))
s.send("Hello server!".encode())
with open('received_file', 'wb') as f:
 while True:
     print('receiving data...')
     data = s.recv(1024)
     print('data=%s', (data))
     if not data:
         break
f.write(data)
f.close()
print('Successfully get the file')
s.close()
print('connection closed')
```
SERVER
```
import socket 
port = 60000 
s = socket.socket() 
host = socket.gethostname() 
s.bind((host, port)) 
s.listen(5) 
while True:
 conn, addr = s.accept() 
 data = conn.recv(1024)
 print('Server received', repr(data))
 filename='mytext.txt'
 f = open(filename,'rb')
 l = f.read(1024)
 while (l):
     conn.send(l)
     print('Sent ',repr(l))
     l = f.read(1024)
 f.close()
 print('Done sending')
 conn.send('Thank you for connecting'.encode())
 conn.close()
```
## OUPUT

CLIENT

![Screenshot 2025-05-18 194230](https://github.com/user-attachments/assets/90e76d76-80a7-47e7-be58-5080db55e638)

SERVER

![Screenshot 2025-05-18 194240](https://github.com/user-attachments/assets/a90cb7dc-d3c1-4663-aa67-b8016102c2a4)

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
