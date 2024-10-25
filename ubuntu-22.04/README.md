ubuntu@ubuntu:~/docker-mininet/ubuntu-22.04$ docker build --file Dockerfile --tag quanghong/mininet:ubuntu-22.04 .
[+] Building 14.9s (10/10) FINISHED                                                              docker:default
 => [internal] load build definition from Dockerfile                                                       0.0s
 => => transferring dockerfile: 502B                                                                       0.0s
 => [internal] load metadata for docker.io/library/ubuntu:22.04                                            0.6s
 => [auth] library/ubuntu:pull token for registry-1.docker.io                                              0.0s
 => [internal] load .dockerignore                                                                          0.0s
 => => transferring context: 2B                                                                            0.0s
 => [1/4] FROM docker.io/library/ubuntu:22.04@sha256:0e5e4a57c2499249aafc3b40fcd541e9a456aab7296681a3994d  0.0s
 => [internal] load build context                                                                          0.0s
 => => transferring context: 302B                                                                          0.0s
 => CACHED [2/4] WORKDIR /root                                                                             0.0s
 => [3/4] COPY ENTRYPOINT.sh /                                                                             0.0s
 => [4/4] RUN apt-get update && apt-get install -y --no-install-recommends     curl     dnsutils     ifu  14.0s
 => exporting to image                                                                                     0.2s 
 => => exporting layers                                                                                    0.2s 
 => => writing image sha256:f37e6d55786b490200e240473dc57a9fd7ec6fc855d25bb697eb9953dc2b3f97               0.0s 
 => => naming to docker.io/quanghong/mininet:ubuntu-22.04                                                  0.0s 
ubuntu@ubuntu:~/docker-mininet/ubuntu-22.04$ docker compose run --rm mininet
WARN[0000] /home/ubuntu/docker-mininet/ubuntu-22.04/docker-compose.yml: the attribute `version` is obsolete, it will be ignored, please remove it to avoid potential confusion 
WARN[0000] Found orphan containers ([ubuntu-2204-mininet-run-ecd9a71770d4]) for this project. If you removed or renamed this service in your compose file, you can run this command with the --remove-orphans flag to clean it up. 
 * /etc/openvswitch/conf.db does not exist
 * Creating empty database /etc/openvswitch/conf.db
 * Starting ovsdb-server
 * Configuring Open vSwitch system IDs
 * Starting ovs-vswitchd
 * Enabling remote OVSDB managers
ovsdb-server is running with pid 49
ovs-vswitchd is running with pid 65
root@dca30c46790c:~# 
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