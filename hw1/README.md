#HW01: Network Layers- Franklin
##TCP/IP network stack

'''
arp -a
Interface: 192.168.0.19 --- 0x10
 Internet Address      Physical Address      Type
 76.107.86.251         28-80-88-c6-7b-d1     dynamic
 192.168.0.1           28-80-88-c6-7b-d2     dynamic
 192.168.0.16          64-1c-b0-c9-1b-07     dynamic
 192.168.0.255         ff-ff-ff-ff-ff-ff     static
 224.0.0.22            01-00-5e-00-00-16     static
 224.0.0.251           01-00-5e-00-00-fb     static
 224.0.0.252           01-00-5e-00-00-fc     static
 239.255.255.250       01-00-5e-7f-ff-fa     static
 255.255.255.255       ff-ff-ff-ff-ff-ff     static
'''
'''
In [2]: netlayers.arp_table()
Name  IP               MAC                Company
---------------  -----------------  ---------------------------
76.107.86.251    28:80:88:c6:7b:d1  NETGEAR
192.168.0.1      28:80:88:c6:7b:d2  NETGEAR
192.168.0.16     64:1c:b0:c9:1b:07  Samsung Electronics Co.,Ltd
192.168.0.255    ff:ff:ff:ff:ff:ff
224.0.0.22       01:00:5e:00:00:16
224.0.0.251      01:00:5e:00:00:fb
224.0.0.252      01:00:5e:00:00:fc
239.255.255.250  01:00:5e:7f:ff:fa
255.255.255.255  ff:ff:ff:ff:ff:ff
'''

###Layer 2: Datalink
1. How many Different things are listed in the output of the arp -a command?
*There are 10 different outputs. The first 3 addresses are dynamic types. The next 7 are static addresses.*

2. What are the different devices connected to your home network- can you identify what they are based on this info?
*The 1st 3 dynamic addresses are user devices (one being mine and the others being a phone and desktop computer) connected to the network. The last 7 adresses are static which are temporary. I have a broadcast address range of 192.168.0.255 - 255.255.255.255. between these are my multicast mac addresses.*



'''
$ ping google.com
Pinging google.com [142.250.68.174] with 32 bytes of data:
Reply from 142.250.68.174: bytes=32 time=44ms TTL=110
Reply from 142.250.68.174: bytes=32 time=45ms TTL=110
Request timed out.
Reply from 142.250.68.174: bytes=32 time=84ms TTL=110

Ping statistics for 142.250.68.174:
    Packets: Sent = 4, Received = 3, Lost = 1 (25% loss),
Approximate round trip times in milli-seconds:
    Minimum = 44ms, Maximum = 84ms, Average = 57ms
'''
'''
$ ping localhost
Pinging DESKTOP-J8IVQTN [::1] with 32 bytes of data:
Reply from ::1: time<1ms
Reply from ::1: time<1ms
Reply from ::1: time<1ms
Reply from ::1: time<1ms

Ping statistics for ::1:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms
'''

###Layer 3: network
1. what is the difference between 'ping google.com' and 'ping localhost'?

 *local host has sent and received 4 packets while google sent 4 and received 3. Localhost is my laptop with 32 bytes of data, represented as ::1, so the round trip was 0 due to me 'replying' to myself. Pinging google.com as a website gave me replies until the request to reach google over the internet timed out. It also gave me the IP address for google.com.*
