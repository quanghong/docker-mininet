```bash
docker build --file Dockerfile --tag quanghong/mininet:ubuntu-22.04 . &> build.log
```

root@dca30c46790c:~# mn --switch ovsbr --test pingall
*** Error setting resource limits. Mininet's performance may be affected.
*** Creating network
*** Adding controller
*** Adding hosts:
h1 h2 
*** Adding switches:
s1 
*** Adding links:
(h1, s1) (h2, s1) 
*** Configuring hosts
h1 h2 
*** Starting controller
c0 
*** Starting 1 switches
s1 ...
*** Waiting for switches to connect
s1 
*** Ping: testing ping reachability
h1 -> h2 
h2 -> h1 
*** Results: 0% dropped (2/2 received)
*** Stopping 1 controllers
c0 
*** Stopping 2 links
..
*** Stopping 1 switches
s1 
*** Stopping 2 hosts
h1 h2 
*** Done
completed in 0.535 seconds
root@dca30c46790c:~# h1 ping h2
bash: h1: command not found
root@dca30c46790c:~# mn
*** Error setting resource limits. Mininet's performance may be affected.
*** Creating network
*** Adding controller
*** Adding hosts:
h1 h2 
*** Adding switches:
s1 
*** Adding links:
(h1, s1) (h2, s1) 
*** Configuring hosts
h1 h2 
*** Starting controller
c0 
*** Starting 1 switches
s1 ...
*** Starting CLI:
mininet> h1 ping h2
PING 10.0.0.2 (10.0.0.2) 56(84) bytes of data.
64 bytes from 10.0.0.2: icmp_seq=1 ttl=64 time=8.33 ms
64 bytes from 10.0.0.2: icmp_seq=2 ttl=64 time=0.698 ms
^C
--- 10.0.0.2 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 0.698/4.514/8.330/3.816 ms
mininet> h2 ping h1
PING 10.0.0.1 (10.0.0.1) 56(84) bytes of data.
64 bytes from 10.0.0.1: icmp_seq=1 ttl=64 time=1.41 ms
64 bytes from 10.0.0.1: icmp_seq=2 ttl=64 time=0.113 ms
^C
--- 10.0.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1004ms
rtt min/avg/max/mdev = 0.113/0.763/1.413/0.650 ms
mininet> s1 ping h1
PING 10.0.0.1 (10.0.0.1) 56(84) bytes of data.
64 bytes from 10.0.0.1: icmp_seq=1 ttl=127 time=6.72 ms
64 bytes from 10.0.0.1: icmp_seq=2 ttl=127 time=23.4 ms
^C
--- 10.0.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1006ms
rtt min/avg/max/mdev = 6.719/15.036/23.354/8.317 ms
mininet> wireshark
*** Unknown command: wireshark
mininet> sudo wireshark
*** Unknown command: sudo wireshark
mininet> exit
*** Stopping 1 controllers
c0 
*** Stopping 2 links
..
*** Stopping 1 switches
s1 
*** Stopping 2 hosts
h1 h2 
*** Done
completed in 73.873 seconds