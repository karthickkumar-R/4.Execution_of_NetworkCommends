# 4.Execution_of_NetworkCommands
## AIM :Use of Network commands in Real Time environment
## Software : Command promt and Pycharm.

## Algorithms :

#### In this EXPERIMENT- students have to understand basic networking commands e.g cpdump, netstat, ifconfig, nslookup ,traceroute and also Capture ping and traceroute PDUs using a network protocol analyzer
#### All commands related to Network configuration which includes how to switch to privilege mode
#### and normal mode and how to configure router interface and how to save this configuration to
#### flash memory or permanent memory.
#### This commands includes
#### • Configuring the Router commands
#### • General Commands to configure network
#### • Privileged Mode commands of a router
#### • Router Processes & Statistics
#### • IP Commands
#### • Other IP Commands e.g. show ip route etc.

## Program :
### Client :

```py
import socket
import requests

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
                response = requests.get("http://" + hostname)
                if response.status_code == 200:
                    c.send("Ping successful: Website is reachable".encode())
                else:
                    c.send("Ping failed: Website is not reachable".encode())
            except Exception as e:
                c.send("Ping failed: {}".format(e).encode())
        else:
            c.send("Hostname not provided".encode())
    except Exception as e:
        print("Error:", e)
    finally:
        c.close()
```
### Server :

```py
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
### Trace Route :
```py
from scapy.all import *
target = ["www.google.com"]
result, unans = traceroute(target,maxttl=32)
print(result,unans)
```

## Output
### Client :

![Screenshot 2024-05-07 153318](https://github.com/karthickkumar-R/4.Execution_of_NetworkCommends/assets/150005103/a08fafe0-d16b-4500-9473-3a75ecbf18fd)

### Server :

![Screenshot 2024-05-07 153348](https://github.com/karthickkumar-R/4.Execution_of_NetworkCommends/assets/150005103/2d2c2600-e879-4449-8140-e3d53b272e8a)

### Trace command :

![Screenshot 2024-05-07 153415](https://github.com/karthickkumar-R/4.Execution_of_NetworkCommends/assets/150005103/8cd8b745-6010-4b42-bee4-a8670e588fa5)


## Result
Thus Execution of Network commands Performed 
