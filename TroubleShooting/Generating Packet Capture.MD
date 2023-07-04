How to Generate Packet Capture (PCAP) Files

Written By Mamta Buch ()

Updated at July 8th, 2021

Introduction
TCPDUMP (http://www.tcpdump.org/tcpdump_man.html) is a network protocol analyzer. It lets you capture packet data from a live network or read packets from a previously saved capture file, either printing a decoded form of those packets to the standard output or writing the packets to a file.

Without any options set, tcpdump will use the PCAP library to capture traffic from the first available network interface and displays a summary line on stdout for each received packet. The input file doesn't need a specific filename extension, the file format and an optional gzip compression will be automatically detected. 

Root access is needed to run tcpdump, hence the addition of sudo in front of the tcpdump commands shown below.

Examples
Trace all packet at port 5060 and dump to the stdout.
sudo tcpdump port 5060
Trace all packets at port 1040 or port 540 on eth1 and dump to the stdout.
sudo tcpdump -i eth1 port 1040 or port 540
Trace all packets via any interface at port 5060 and dump details to the stdout.
sudo tcpdump -i any -V port 5060
Trace all packets via any interface at port 5060 for 30s and save to a file called test.pcap in PCAP format.
sudo tcpdump -i any -G 30 -W 1 -w t.pcap port 5060
Trace all packet via any interface between <host A> and <host B> for 30s and save to a file called t.pcap in PCAP format.
sudo tcpdump -i any -G 30 -W 1 -w t.pcap host <host A> and host <host B>
Trace via any interface on port 5060 in a ring buffer, this will keep a max of 20 files swapping to new files at 5 minutes
sudo tcpdump -i any -w etherealLoop.pcap -G 300 -W 20  port 5060 
Trace all packets via interface em1 sent to a single IP address.
sudo tcpdump -i em1 host 8.8.8.8
Trace all packets via bonded interface bond0 sent to specific IP addresses.
sudo tcpdump -i bond0 host 8.8.8.8 or host 8.8.4.4
Trace all packets via any interface sent to a specific subnet.
sudo tcpdump -i any net 8.8.8.0/24
