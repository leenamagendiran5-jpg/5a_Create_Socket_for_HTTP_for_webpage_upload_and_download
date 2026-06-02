# 5a_Create_Socket_for_HTTP_for_webpage_upload_and_download
## AIM :
To write a PYTHON program for socket for HTTP for web page upload and download
## Algorithm

1.Start the program.
<BR>
2.Get the frame size from the user
<BR>
3.To create the frame based on the user request.
<BR>
4.To send frames to server from the client side.
<BR>
5.If your frames reach the server it will send ACK signal to client otherwise it will send NACK signal to client.
<BR>
6.Stop the program
<BR>
## Program 

1) SERVER:
```
import socket
s = socket.socket()
s.bind(("localhost",8081))
s.listen(1)
print("Server running...")
while True:
c,addr = s.accept()
request = c.recv(1024).decode()
print("Request received")
if "GET" in request:
f = open("index.html","r")
data = f.read()
f.close()
response = "HTTP/1.1 200 OK\n\n" + data
c.send(response.encode())
elif "POST" in request:
data = request.split("\n\n")[1]
f = open("upload.txt","w")
f.write(data)
f.close()
c.send(
```
2) CLIENT:
```
Client
import socket
s = socket.socket()
s.connect(("localhost",8081))
ch = input("1.Download 2.Upload : ")
if ch == "1":
req = "GET / HTTP/1.1\nHost: localhost\n\n"
s.send(req.encode())
data = s.recv(4096)
print(data.decode())
else:
msg = input("Enter data to upload: ")
req = "POST / HTTP/1.1\nHost: localhost\n\n" + msg
s.send(req.encode())
data = s.recv(1024)
print(data.decode())
s.close()
```
## OUTPUT

1) SERVER:
   
<img width="949" height="1016" alt="Screenshot 2026-06-02 152857" src="https://github.com/user-attachments/assets/720950f0-3b0d-4ed9-b323-5df7b3419191" />

2) CLIENT:

<img width="956" height="1019" alt="Screenshot 2026-06-02 152919" src="https://github.com/user-attachments/assets/16a548f9-85a0-45a2-8bee-5e8d68c4e4d8" />

## Result
Thus the socket for HTTP for web page upload and download created and Executed
