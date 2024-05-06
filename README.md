# Ex-4 Execution_of_NetworkCommands

## AIM :
Use of Network commands in Real Time environment
## Software : 
Command Prompt And Network Protocol Analyzer
## Procedure: To do this EXPERIMENT- follows these steps:
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

## Program
### Ping command
### Client:
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
### Server:
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
<hr>

## Trace Route command
```
from scapy.all import *
target = ["www.google.com"]
result, unans = traceroute(target,maxttl=32)
print(result,unans)
```
<hr>

## Output
### Ping Command
### Client:
<img width="936" alt="Screenshot 2024-04-15 at 1 37 02 PM" src="https://github.com/aaron-h-2k5/4.Execution_of_NetworkCommends/assets/144250957/779c27fc-0f39-47a0-aafd-92b922234137">

### Server:
<img width="936" alt="Screenshot 2024-04-15 at 1 36 29 PM" src="https://github.com/aaron-h-2k5/4.Execution_of_NetworkCommends/assets/144250957/c941309e-b439-4ca1-94af-90ecedc72a4d">
<hr>

## Trace Route command:
<img width="936" alt="Screenshot 2024-04-15 at 1 33 35 PM" src="https://github.com/aaron-h-2k5/4.Execution_of_NetworkCommends/assets/144250957/e0e91b9d-7d7f-49ba-a6ed-5e84bdd547a5">

## Result
Thus Execution of Network commands Performed 

