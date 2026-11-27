# 3b.CREATION FOR CHAT USING TCP SOCKETS
## AIM
To write a python program for creating Chat using TCP Sockets Links.
## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server
4. Send and receive the message using the send function in socket.
## PROGRAM
### server.py
~~~
import socket

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

s.bind(('localhost', 8000))
s.listen(1)

print("Server waiting for connection...")

c, addr = s.accept()

print("Client connected:", addr)

while True:
    msg = c.recv(1024).decode()

    if msg.lower() == "exit":
        print("Client disconnected")
        break

    print("Client:", msg)

    reply = input("Server: ")
    c.send(reply.encode())

    if reply.lower() == "exit":
        break

c.close()
s.close()
~~~
### client.py
~~~
import socket

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

s.connect(('localhost', 8000))

print("Connected to server")

while True:
    msg = input("Client: ")

    s.send(msg.encode())

    if msg.lower() == "exit":
        break

    reply = s.recv(1024).decode()

    if reply.lower() == "exit":
        print("Server disconnected")
        break

    print("Server:", reply)

s.close()
~~~
## OUPUT
<img width="1491" height="286" alt="Screenshot 2026-11-23 135223" src="https://github.com/user-attachments/assets/37469fa6-542d-45c9-9dff-cf47e1c02113" />

## RESULT
Thus, the python program for creating Chat using TCP Sockets Links was successfully 
created and executed.
