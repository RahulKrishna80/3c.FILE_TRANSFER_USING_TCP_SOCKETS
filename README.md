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
## SERVER:
```
import socket
port = 60000
s = socket.socket()
host = socket.gethostname()
s.bind((host, port))
s.listen(5)
while True:
    conn , addr = s.accept()
    data = conn.recv(1024)
    print('Server received', repr(data))
    filename = 'mytext.txt'
    f = open(filename,'rb')
    l = f.read(1024)
    while(l):
        conn.send(l)
        print('Sent ',repr(l))
        l = f.read(1024)
    f.close()
    print('Done sending')
    conn.send('Thank you for connecting'.encode())
    conn.close()
```
## CLIENT:
```
import socket
s = socket.socket()
host = socket.gethostname()
port = 60000
s.connect((host,port))
s.send("Hello server!".encode())
with open('mytext.txt', 'wb')as f:
    while True:
        print('receiving data...')
        data = s.recv(1024)
        print('data = %s', (data))
        if not data:
            break
        f.write(data)
    f.close()
    print('Successfully get this file')
    s.close()
    print('connection closed')
```
## OUPUT

<img width="893" height="209" alt="Screenshot 2025-11-11 085535" src="https://github.com/user-attachments/assets/9cbe28f6-aff9-462e-97af-5f96caac0349" />

<img width="875" height="306" alt="Screenshot 2025-11-11 085544" src="https://github.com/user-attachments/assets/663ec920-cc71-4caa-9556-529d91e43948" />


## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
