![screenshot](https://raw.githubusercontent.com/tlsbollei/CTF-Writeups/refs/heads/main/images/supa3.png)

CTF Questions :

```yaml
Task 1: How to filter for packets coming from 192.168.10.10/25 and sent to Aruba devices in WireShark?


Task 2: Which display filter is used to display all DHCP traffic?

Task 3: How do you quickly spot large gaps in time between packets in a trace file containing 10,000 packets?
1. Set the Time column to Seconds Since Epoch and scroll through the trace file
2. Open and examine the Notes section of Wireshark's Expert infos window
3. Set the Time column to Seconds Since Previously Displayed Packet and sort the Time column

Task 4: Which of these filters can be used as either a capture or display filter?
Choose the correct answer:
1. Dns
2. Udp
3. Dhcp

Task 5: What is the sensible information involved in the pcap file?
```

CTF Answers :
```yaml
Task 1 :
ip.src == 192.168.10.108/25 && eth.dst[0:3] == 9C:1C:12
Why?

Source IP Address (192.168.10.10) with a CIDR Notation /25 = ip.src
&& = AND operator in WireShark
eth.dst[0:3] = eth defines a MAC address, splits the mac address in half = because the first 3 correspond to the OUI registered to Aruba Networks
Aruba Network OUI can be discovered on the internet - it is "9C:1C:12"
```

```yaml
Task 2 :
DHCP
(bootp could also be used, but its just an old version of modern DHCP)
```

```yaml
Task 3 :
3. Set the Time column to Seconds Since Previously Displayed Packet and sort the Time column
```

```yaml
Task 4:
2. Udp, can be used as a display and a capture filter
dns and dhcp are typically used as display filters
```

```yaml
Task 5:
1. Open WireShark, import challenge1.pcap
2. The term "Sensible Information" likely implicates the existence of login credentials
3. To test out this theory, add a display filter "http". This filter will show us only the HTTP packets
4. We are left with 2 packets - A HTTP GET request and a HTTP POST request
5. Double-click the latter and in the form we can see "uname" and "psw" and therefore the answer to task 5
  Username: rocky
  Password: Melory66! 
```
![screenshot](https://raw.githubusercontent.com/tlsbollei/CTF-Writeups/refs/heads/main/images/supa4.png)
![screenshot](https://raw.githubusercontent.com/tlsbollei/CTF-Writeups/refs/heads/main/images/supa5.png)
![screenshot](https://raw.githubusercontent.com/tlsbollei/CTF-Writeups/refs/heads/main/images/supa6.png)


