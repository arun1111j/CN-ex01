# STUDY OF SOCKET PROGRAMMING WITH CLIENT-SERVER MODEL
# EXP: 1
# DATE :08-03-2023

# AIM :
## To write a python program to perform stop and wait protocol
# ALGORITHM :
## 1. Start the program.
## 2. Get the frame size from the user
## 3. To create the frame based on the user request.
## 4. To send frames to server from the client side.
## 5. If your frames reach the server it will send ACK signal to client otherwise it will sendNACK signal to client.
## 6. Stop the program
# Server:
## 1. Create a server socket and bind it to port.
## 2. Listen for new connection and when a connection arrives, accept it.
## 3. Send server‟s date and time to the client.
## 4. Read client‟s IP address sent by the client.
## 5. Display the client details.
## 6. Repeat steps 2-5 until the server is terminated.
## 7. Close all streams.
## 8. Close the server socket.
## 9. Stop.
# Client:
## 1. Create a client socket and connect it to the server‟s port number.
## 2. Retrieve its own IP address using built-in function.
## 3. Send its address to the server.
## 4. Display the date & time sent by the server.
## 5. Close the input and output streams.
## 6. Close the client socket.
## 7. Stop

# CLIENT PROGRAM :
```PYTHON 3
import socket
from datetime import datetime
s=socket.socket()
s.bind(('localhost',8080))
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
while True:
	i=input("ENter a data:")
	c.send(i.encode())
	ack=c.recv(1024).decode()
	if ack:
		print(ack)
		continue
	else:
		c.close()
		break
print("Client Address : ",addr)
now = datetime.now()
c.send(now.strftime("%d/%m/%Y %H:%M:%S").encode())
ack=c.recv(1024).decode()
if ack:
  print(ack)
c.close()
```
# SERVER PROGRAM : 
```PYTHON 3
import socket
s=socket.socket()
s.connect(('localhost',8080))
while True:
	print(s.recv(1024).decode())
	s.send("Recieved".encode())
s.connect(('localhost',8000))
print(s.getsockname())
print(s.recv(1024).decode())
s.send("acknowledgement recived from the server".encode())
```

# CLIENT OUTPUT : 
![image](https://github.com/arun1111j/CN-ex01/assets/128461833/53d0fa2a-5da2-4600-af0a-e16e17d8c5a2)

# SERVER OUTPUT :
![image](https://github.com/arun1111j/CN-ex01/assets/128461833/27417292-5dc5-49b8-ae83-7930b043953c)

# RESULT:
## Thus, python program to perform stop and wait protocol was successfully executed.
