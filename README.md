### NAME   : SANTHOSH.T
### REG NO : 212223220100
### DEPARTMENT: INFORMATION TECHNOLOGY

# Echoserver
Echo server and client using python socket

# AIM:

To develop a simple webserver to serve html programming pages.

## DESIGN STEPS:

### Step 1:

Design of echo server and client using python socket

### Step 2:

Implementation using Python code

### Step 3:

Testing the server and client 

## PROGRAM:

### Server code:
```python
import socket

HOST = "127.0.0.1"  # Standard loopback interface address (localhost)
PORT = 65432  # Port to listen on (non-privileged ports are > 1023)

with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
    try:
        s.bind((HOST, PORT))
    except Exception as e:
        print(f"Error binding to {HOST}:{PORT}: {e}")
        exit()
    
    s.listen()
    print(f"Listening on {HOST}:{PORT}...")

    try:
        conn, addr = s.accept()
    except Exception as e:
        print(f"Error accepting connection: {e}")
        exit()

    with conn:
        print(f"Connected by {addr}")
        while True:
            try:
                data = conn.recv(1024)
                if not data:
                    break
                conn.sendall(data)
            except Exception as e:
                print(f"Error receiving/sending data: {e}")
                exit()


```
### Client Code:
```python
import socket
HOST = "127.0.0.1"  # The server's hostname or IP address
PORT = 65432  # The port used by the server
with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
    s.connect((HOST, PORT))
    s.sendall(b"Hello, world")
    data = s.recv(1024)

print(f"Received {data!r}")
```

## OUTPUT:

![Screenshot 2024-09-16 214320](https://github.com/user-attachments/assets/09dace97-593a-4fdc-87df-defd1b66d651)

### Server side:
![Screenshot 2024-09-16 214357](https://github.com/user-attachments/assets/1f1c79f7-5610-4871-998e-7ff320c25f56)

### Client side:
![Screenshot 2024-09-16 214337](https://github.com/user-attachments/assets/0550f984-d4d2-4acf-967e-1825e5b7c715)

## RESULT:
The program is executed successfully.
