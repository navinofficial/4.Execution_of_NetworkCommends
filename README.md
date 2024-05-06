# 4.Execution_of_NetworkCommands
Reg no:212223230141
Name:Navinkumar v
## AIM 
Use of Network commands in Real Time environment
## Software
Command Prompt And Network Protocol Analyzer
## Procedure
To do this EXPERIMENT- follows these steps:
<BR>
In this EXPERIMENT- students have to understand basic networking commands e.g cpdump, netstat, ifconfig, nslookup ,traceroute and also Capture ping and traceroute PDUs using a network protocol analyzer 
<BR>
All commands related to Network configuration which includes how to switch to privilege mode
<BR>
and normal mode and how to configure router interface and how to save this configuration to
<BR>
flash memory or permanent memory.
<BR>
This commands includes
<BR>
• Configuring the Router commands
<BR>
• General Commands to configure network
<BR>
• Privileged Mode commands of a router 
<BR>
• Router Processes & Statistics
<BR>
• IP Commands
<BR>
• Other IP Commands e.g. show ip route etc.
<BR>
## program
### client:
```
import socket 
from pythonping import ping
s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
while True:
    c, addr = s.accept()
    print("Connection from", addr)
    try:
        hostname = c.recv(1024).decode().strip()
        if hostname:
            try:
                response = str(ping(hostname, verbose=False))
                c.send(response.encode())
            except Exception as e:
                c.send("Ping failed: {}".format(e).encode())
        else:
            c.send("Hostname not provided".encode())
    except Exception as e:
        print("Error:", e)
    finally:
        c.close()
```
### server:
```
import socket
s = socket.socket()
s.connect(('localhost', 8000))
try:
    while True:
        ip = input("Enter the website you want to ping: ")
        s.send(ip.encode())
        response = s.recv(1024).decode()
        if response:
            print("Ping Result:", response)
        else:
            print("No response from server.")
except Exception as e:
    print("Error:", e)
finally:
    s.close()
```
### Trace Route command
```
from scapy.all import *
target = ["www.google.com"]
result, unans = traceroute(target,maxttl=32)
print(result,unans)
```
## Output
### client
![image](https://github.com/navinofficial/4.Execution_of_NetworkCommends/assets/151710204/5e9fe127-d328-401e-97e6-b20be65a7896)
### server
![image](https://github.com/navinofficial/4.Execution_of_NetworkCommends/assets/151710204/ae3fb206-b63f-4a16-b19f-c1c7ba5085bc)
### Trace Route command
![image](https://github.com/navinofficial/4.Execution_of_NetworkCommends/assets/151710204/5071c4f9-43dd-4d0a-8723-e223ed589b02)
## Result
Thus Execution of Network commands Performed.
