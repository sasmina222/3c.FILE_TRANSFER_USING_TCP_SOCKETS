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
server
```
import socket

port = 60000

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

host = socket.gethostname()

s.bind((host, port))

s.listen(5)

print("Server is waiting for connection...")

conn, addr = s.accept()

print("Connected to:", addr)

data = conn.recv(1024)

print("Server received:", data.decode())

filename = 'mytext.txt'

with open(filename, 'rb') as f:
    while True:
        l = f.read(1024)

        if not l:
            break

        conn.sendall(l)

print("Done sending")

conn.close()
s.close()
```
client
```
import socket

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

host = socket.gethostname()
port = 60000

s.connect((host, port))

s.send("Hello server!".encode())

with open('received_file.txt', 'wb') as f:
    while True:
        data = s.recv(1024)

        if not data:
            break

        f.write(data)

print("Successfully received the file")

s.close()

print("Connection closed")
```
## OUPUT
<img width="854" height="359" alt="image" src="https://github.com/user-attachments/assets/6edcaef6-5601-4e3f-878d-3b51c1ee2a00" />




## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
