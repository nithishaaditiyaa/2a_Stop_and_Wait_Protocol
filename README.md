# 2a_Stop_and_Wait_Protocol

## AIM 

To write a python program to perform stop and wait protocol

## ALGORITHM

1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program


## PROGRAM

# Receiver.py 

```

import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(1)

print("Waiting for server...")
c, addr = s.accept()

n = int(input("Enter number of frames: "))

for i in range(n):
    data = input("Enter frame: ")

    c.send(data.encode())

    ack = c.recv(1024).decode()
    print("Server:", ack)

c.close()
s.close()

```

# Sender.py

```

import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    data = s.recv(1024).decode()

    if not data:
        break

    print("Received Frame:", data)

    s.send("ACK Received".encode())

s.close()


```

## OUTPUT


![alt text](image-2.png)


![alt text](image-3.png)



## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
