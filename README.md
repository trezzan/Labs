# Labs

## Week 9
### Milestone 0
Run ifconfig/ipconfig/ip and determine the name/id of your primary network interface **etho0**

What is your primary interface's IP address? Is it different from your public IP? Why or why not? **inet 192.168.230.131  netmask 255.255.255.0  broadcast 192.168.230.255, they are different**

What is the MAC address of your primary interface? **00:0c:29:15:c3:25**

Identify and understand your loopback interface **loop  txqueuelen 1000  (Local Loopback)
        RX packets 20  bytes 1116 (1.0 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 20  bytes 1116 (1.0 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0**
        
What is the IP address of codepath.com? **198.58.125.217** 

What is the IP address of google.com? **172.217.5.78**

Why would the IP address of google.com change between runs or from different locations? **yes, they have multiple query servers running across the nation**

Using the IP for codepath.com from the previous, pass it to nslookup **217.125.58.198.in-addr.arpa	name = thecodepath.com**

Does the domain returned from nslookup match? If not, why not? **no, it has the at the front. it's probably a cname or forwarder.**

Compare the traceroutes for codepath.com and google.com 

How many of the hops are the same? What accounts for this? **i cant tell, they're just stars**

Which has more hops? What accounts for the difference? **they both maxxed out the 30 hops setting**

What's one thing that makes telnet insecure? **it has no encryption or login protection**

Can you telnet to codepath.com? What port is open and why? **no, the port is closed**

Identify some differences between the two **curl has more uses, but requires libraries. wget is self contained and simple to use. curl also can be written into its own applications since it has a library.**

Which would you be more likely to use for interacting with a RESTful API from the command line? **curl has more tools, and can handle the GET, PULL, POST, and DELETE requests**

Which support recursive downloading? **wget**

Which are you more likely to find pre-installed on a Linux OS? **wget**

What is the syntax for each for downloading a file to the current directory? **wget [URL]**
**curl [options / URLs]**

Why is key authentication preferred to passwords? **keys are more difficult to spoof or steal**

What is the syntax for copying a file from a local folder to a remote one? **ssh sample.ssh.com**

### Milestone 1

netcat local listener [FAILED] - **see screencap**

dict.org - **nc dict.org 2628
220 pan.alephnull.com dictd 1.12.1/rf on Linux 4.4.0-1-amd64 <auth.mime> <25341746.23903.1527645421@pan.alephnull.com>
DEFINE wn peripatetic
150 1 definitions retrieved
151 "peripatetic" wn "WordNet (r) 3.0 (2006)"
peripatetic
    adj 1: of or relating to Aristotle or his philosophy;
           "Aristotelean logic" [syn: {Aristotelian},
           {Aristotelean}, {Aristotelic}, {peripatetic}]
    2: traveling especially on foot; "peripatetic country
       preachers"; "a poor wayfaring stranger" [syn: {peripatetic},
       {wayfaring}]
    n 1: a person who walks from place to place
    2: a follower of Aristotle or an adherent of Aristotelianism
       [syn: {Aristotelian}, {Aristotelean}, {Peripatetic}]
250 ok [d/m/c = 1/0/17; 0.000r 0.000u 0.000s]**

root@kali:~# **nc -z 192.168.0.1 80-90
^C**

root@kali:~#**nmap  -v scanme.nmap.org
Starting Nmap 7.60 ( https://nmap.org ) at 2018-05-29 22:00 EDT
Initiating Ping Scan at 22:00
Scanning scanme.nmap.org (45.33.32.156) [4 ports]
Completed Ping Scan at 22:00, 0.07s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 22:00
Completed Parallel DNS resolution of 1 host. at 22:00, 0.03s elapsed
Initiating SYN Stealth Scan at 22:00
Scanning scanme.nmap.org (45.33.32.156) [1000 ports]
Discovered open port 22/tcp on 45.33.32.156
Discovered open port 80/tcp on 45.33.32.156
Discovered open port 9929/tcp on 45.33.32.156
Discovered open port 31337/tcp on 45.33.32.156
Completed SYN Stealth Scan at 22:01, 34.49s elapsed (1000 total ports)
Nmap scan report for scanme.nmap.org (45.33.32.156)
Host is up (1.1s latency).
Not shown: 990 closed ports
PORT      STATE    SERVICE
22/tcp    open     ssh
25/tcp    filtered smtp
42/tcp    filtered nameserver
80/tcp    open     http
135/tcp   filtered msrpc
139/tcp   filtered netbios-ssn
445/tcp   filtered microsoft-ds
514/tcp   filtered shell
9929/tcp  open     nping-echo
31337/tcp open     Elite**

this excersize stayed at this output
root@kali:~# **sudo nmap -sS -O scanme.nmap.org/24
Starting Nmap 7.60 ( https://nmap.org ) at 2018-05-29 22:03 EDT
Stats: 0:00:00 elapsed; 0 hosts completed (0 up), 256 undergoing Ping Scan
Ping Scan Timing: About 2.54% done; ETC: 22:03 (0:00:00 remaining)**


root@kali:~# **nmap 192.168.230.131
Starting Nmap 7.60 ( https://nmap.org ) at 2018-05-29 22:10 EDT
Nmap scan report for 192.168.230.131
Host is up (0.000018s latency).
All 1000 scanned ports on 192.168.230.131 are closed
Nmap done: 1 IP address (1 host up) scanned in 0.27 seconds

**Read data files from: /usr/bin/../share/nmap
Nmap done: 1 IP address (1 host up) scanned in 34.92 seconds
           Raw packets sent: 1079 (47.448KB) | Rcvd: 1069 (42.820KB)**

### Milestone 2 

root@kali:~# **sudo tcpdump -D
1.eth0 [Up, Running]
2.any (Pseudo-device that captures on all interfaces) [Up, Running]
3.lo [Up, Running, Loopback]
4.nflog (Linux netfilter log (NFLOG) interface)
5.nfqueue (Linux netfilter queue (NFQUEUE) interface)
6.usbmon1 (USB bus number 1)
7.usbmon2 (USB bus number 2)**

root@kali:~# **sudo tcpdump -n src host 198.58.125.217
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 262144 bytes
22:23:10.210072 IP 198.58.125.217.80 > 192.168.230.131.38314: Flags [S.], seq 1001676267, ack 1506270750, win 64240, options [mss 1460], length 0
22:23:10.210519 IP 198.58.125.217.80 > 192.168.230.131.38316: Flags [S.], seq 2081838546, ack 2351157952, win 64240, options [mss 1460], length 0
22:23:10.214548 IP 198.58.125.217.80 > 192.168.230.131.38316: Flags [.], ack 388, win 64240, length 0
22:23:10.214696 IP 198.58.125.217.80 > 192.168.230.131.38322: Flags [S.], seq 1905884946, ack 336968324, win 64240, options [mss 1460], length 0
22:23:10.215011 IP 198.58.125.217.80 > 192.168.230.131.38318: Flags [S.], seq 601227344, ack 4079837490, win 64240, options [mss 1460], length 0
22:23:10.215653 IP 198.58.125.217.80 > 192.168.230.131.38320: Flags [S.], seq 1321030039, ack 127115371, win 64240, options [mss 1460], length 0
22:23:10.388860 IP 198.58.125.217.80 > 192.168.230.131.38316: Flags [P.], seq 1:1387, ack 388, win 64240, length 1386: HTTP: HTTP/1.1 200 OK
22:23:10.389482 IP 198.58.125.217.80 > 192.168.230.131.38316: Flags [P.], seq 1387:6351, ack 388, win 64240, length 4964: HTTP
22:23:15.403033 IP 198.58.125.217.80 > 192.168.230.131.38316: Flags [FP.], seq 6351, ack 388, win 64240, length 0
22:23:15.404290 IP 198.58.125.217.80 > 192.168.230.131.38316: Flags [.], ack 389, win 64239, length 0
22:23:15.441762 IP 198.58.125.217.80 > 192.168.230.131.38314: Flags [.], ack 2, win 64239, length 0
22:23:15.441989 IP 198.58.125.217.80 > 192.168.230.131.38318: Flags [.], ack 2, win 64239, length 0
22:23:15.442423 IP 198.58.125.217.80 > 192.168.230.131.38320: Flags [.], ack 2, win 64239, length 0
22:23:15.442858 IP 198.58.125.217.80 > 192.168.230.131.38322: Flags [.], ack 2, win 64239, length 0
22:23:15.481517 IP 198.58.125.217.80 > 192.168.230.131.38314: Flags [FP.], seq 1, ack 2, win 64239, length 0
22:23:15.481705 IP 198.58.125.217.80 > 192.168.230.131.38318: Flags [FP.], seq 1, ack 2, win 64239, length 0
22:23:15.481789 IP 198.58.125.217.80 > 192.168.230.131.38320: Flags [FP.], seq 1, ack 2, win 64239, length 0
22:23:15.482042 IP 198.58.125.217.80 > 192.168.230.131.38322: Flags [FP.], seq 1, ack 2, win 64239, length 0**

How many requests to load the main codepath.com page? **18 requests load it**

What type of resource accounts for most of the requests? **coming from port 80**

Now try the same exercise with https://security.codepath.com. What differences do you see in the output? What accounts for those differences? **runs through port 443 and is encrypted**

Listen for DNS queries on port 53:
Think of a domain name that probably exists (common word or phrase + .com) but that you've never visited before (suggestion: zombo.com) and open it in a browser
Look at the tcpdump output for the UDP packets trying to resolve the domain. The destination IP should be the DNS: **192.168.230.131**

### Milestone 3

Look at the source and destination IPs; how much of the traffic is inbound vs. outbound? **When specifying traffic to and from my IP, about 25% is inbound and 75% is outbound.**

Try nslookup on a couple of IPs that aren't in your network. See if you can figure out who those IPs belong to: **root@kali:~# nslookup 172.217.14.110
110.14.217.172.in-addr.arpa	name = lax31s01-in-f14.1e100.net.
Authoritative answers can be found from:
root@kali:~# nslookup 72.21.91.29
** server can't find 29.91.21.72.in-addr.arpa: NXDOMAIN
root@kali:~# nslookup 104.70.224.245
245.224.70.104.in-addr.arpa	name = a104-70-224-245.deploy.static.akamaitechnologies.com.
Authoritative answers can be found from:**

Try to identify traffic associated with at least one process on your host that's either part of the OS itself or is auto-launched at startup: **Summary: 2018-05-31 00:30:53	63.251.109.88	443	192.168.230.131	192.168.230.131	34256		Application Data**

See if you can spot any ARP packets used to resolve IPs to MAC addresses: **2018-05-31 00:30:47	Vmware_15:c3:25		Vmware_e0:eb:88	00:50:56:e0:eb:88			192.168.230.131 is at 00:0c:29:15:c3:25; no, there were only two packets**

### Milestone 4

What's the purpose of the request to checkip.dyndns.org? **it redirects the DNS requests to a malicious site**

What's up with the three jpg requests? Why two different domains? **i am assuming the DNS redirect got the image from more than one place after the previous requests were canceled.**

How was the malware delivered? What isn't Mike telling us? **Mike says he clicked an atatchment and it downloaded the malware. it looks like it came from a spoofed microsoft update download.**


### Milestone 5 & 6

I could not proceed with the airodump-ng and aircrack-ng sections. They require the host be running the software, and I was virtualizing my Kali VM. My apologies. 

## Week 10

### Milestone 0

### Milestone 1

### Milestone 2

### Milestone 3
