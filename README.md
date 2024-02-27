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
SERVER:
```
import socket

# Create a socket object
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Define the server address and port
server_address = ('localhost', 8888)

# Bind the server to the address and port
server_socket.bind(server_address)

# Listen for incoming connections
server_socket.listen(1)

print("Server is waiting for connections...")

while True:
    # Accept a connection from a client
    client_socket, client_address = server_socket.accept()
    
    print(f"Connection from {client_address}")
    
    # Receive the IP address from the client
    ip_address = client_socket.recv(1024).decode()
    
    # Simulate mapping IP to MAC address (for demonstration purposes)
    mac_address = "00:1A:2B:3C:4D:5E"
    
    # Send the MAC address back to the client
    client_socket.send(mac_address.encode())
    
    # Close the connection with the client
    client_socket.close()
```
CLIENT:
```
import socket

# Create a socket object
client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Define the server address and port
server_address = ('localhost', 8888)

# Connect to the server
client_socket.connect(server_address)

# Get the IP address to be converted into MAC address
ip_address = input("Enter IP Address: ")

# Send the IP address to the server
client_socket.send(ip_address.encode())

# Receive the MAC address from the server
mac_address = client_socket.recv(1024).decode()

print(f"The MAC Address for {ip_address} is: {mac_address}")

# Close the connection with the server
client_socket.close()

```
## OUPUT - ARP
![Screenshot 2024-02-27 195503](https://github.com/Srikaavyaathamizh/2c.ARP_RARP_PROTOCOLS/assets/144870938/1c084ceb-fb4f-4975-95e6-f6e4e00cd915)

![Screenshot 2024-02-27 195520](https://github.com/Srikaavyaathamizh/2c.ARP_RARP_PROTOCOLS/assets/144870938/74df96b5-b91c-4bc6-b300-0a0eda306bef)


## PROGRAM - RARP
SERVER:
```
import socket

# Create a socket object
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Define the server address and port
server_address = ('localhost', 8000)

# Bind the server to the address and port
server_socket.bind(server_address)

# Listen for incoming connections
server_socket.listen(1)

print("Server is waiting for connections...")

while True:
    # Accept a connection from a client
    client_socket, client_address = server_socket.accept()
    
    print(f"Connection from {client_address}")
    
    # Receive the MAC address from the client
    mac_address = client_socket.recv(1024).decode()

    # Simulate mapping MAC to IP address (for demonstration purposes)
    ip_address = "192.168.1.10"

    # Send the IP address back to the client
    client_socket.send(ip_address.encode())

    # Close the connection with the client
    client_socket.close()
```
 CLIENT:
```
import socket

# Create a socket object
client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Define the server address and port
server_address = ('localhost', 8000)

# Connect to the server
client_socket.connect(server_address)

# Get the MAC address to be converted into IP address
mac_address = input("Enter MAC Address: ")

# Send the MAC address to the server
client_socket.send(mac_address.encode())

# Receive the IP address from the server
ip_address = client_socket.recv(1024).decode()

print(f"The IP Address for {mac_address} is: {ip_address}")

# Close the connection with the server
client_socket.close()
```
## OUPUT -RARP

![Screenshot 2024-02-27 200004](https://github.com/Srikaavyaathamizh/2c.ARP_RARP_PROTOCOLS/assets/144870938/4b0c32a3-b9ca-45a7-8119-9998c095fd30)

![Screenshot 2024-02-27 200026](https://github.com/Srikaavyaathamizh/2c.ARP_RARP_PROTOCOLS/assets/144870938/05fd922a-c030-4a20-b8ad-adbbad41af1e)


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
