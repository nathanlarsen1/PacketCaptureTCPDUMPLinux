<h1>Packet Capture with TCPDUMP in Linux</h1>


<h2>Project description</h2>
For this project, I acted as a Cybersecurity Analyst on a security team for an organization. One of my job roles required me to capture and analyze live network traffic from a Linux virtual machine.<br/><br/>

<h2>Language and Applications</h2>

- <b>TCPDUMP</b>
- <b>Curl</b>

<h2>Environments Used </h2>

- <b>Linux</b></br></br>

<h2>Project Walkthrough</h2>
<h3>Identify network interfaces</h3>
Before I did anything else, I needed to identify the network interfaces that could be used to capture network packet data. I chose to use `ifconfig` to for this task.</br></br>
                                                
<p align="center">
<img src="https://i.imgur.com/whah6Wj.png" height="80%" width="80%" alt="Open the file that contains the allow list"/>
<br />
<br />
</p>

The Ethernet network interface is identified by the entry with the `eth` prefix. I used `tcpdump` to identify the interface options available for packet capture.</br></br> 

<p align="center">
<img src="https://i.imgur.com/RwHOLAc.png" height="60%" width="60%" alt="Open the file that contains the allow list"/>
<br />
<br />
</p>

<h3>Inspect the network traffic of a network interface with tcpdump</h3>

For this part of the project, I used `tcpdump` to filter live network packet traffic on the eth0 interface.</br></br> 

<p align="center">
<img src="https://i.imgur.com/s618TSC.png" height="80%" width="80%" alt="Read the file contents"/>
<br />
<br />
</p>

  This command will run tcpdump with the following options:</br>
       - \-i eth0: Capture data specifically from the eth0 interface.</br>
       - \-v: Display detailed packet data.</br>
       - \-c5: Capture 5 packets of data.</br>


1.	In the example data at the start of the packet output, tcpdump reported that it was listening on the eth0 interface, and it provided information on the link type and the capture size in bytes:

2.	On the next line, the first field is the packet's timestamp, followed by the protocol type, IP:

3.	The verbose option, -v, has provided more details about the IP packet fields, such as TOS, TTL, offset, flags, internal protocol type (in this case, TCP (6)), and the length of the outer IP packet in bytes:
4.	In the next section, the data shows the systems that are communicating with each other:

The direction of the arrow (>) indicates the direction of the traffic flow in this packet. Each system name includes a suffix with the port number (.5000 in the screenshot), which is used by the source and the destination systems for this packet.


The remaining data filters the header data for the inner TCP packet:

The flags field identifies TCP flags. In this case, the P represents the push flag and the period indicates it's an ACK flag. This means the packet is pushing out data.

The next field is the TCP checksum value, which is used for detecting errors in the data.

This section also includes the sequence and acknowledgment numbers, the window size, and the length of the inner TCP packet in bytes.

<h3>Capture network traffic with tcpdump</h3>

Capture packet data into a file called capture.pcap:
You must press the ENTER key to get your command prompt back after running this command.
This command will run tcpdump in the background with the following options:
•	-i eth0: Capture data from the eth0 interface.
•	-nn: Do not attempt to resolve IP addresses or ports to names.This is best practice from a security perspective, as the lookup data may not be valid. It also prevents malicious actors from being alerted to an investigation.
•	-c9: Capture 9 packets of data and then exit.
•	port 80: Filter only port 80 traffic. This is the default HTTP port.
•	-w capture.pcap: Save the captured data to the named file.
•	&: This is an instruction to the Bash shell to run the command in the background.<br/><br/>

<p align="center">
<img src="https://i.imgur.com/Iuu68tk.png" height="60%" width="60%" alt="Convert the string into a list"/>
<br />
<br />
</p>

A for loop is used to iterate through the ip_addresses list.<br/><br/>

<p align="center">
<img src="https://i.imgur.com/HwG3LTV.png" height="60%" width="60%" alt="Iterate through the IP addresses list"/>
<br />
<br />
</p>

2.	Use curl to generate some HTTP (port 80) traffic. When the curl command is used like this to open a website, it generates some HTTP (TCP port 80) traffic that can be captured.<br/><br/>

<p align="center">
<img src="https://i.imgur.com/AkdWrLr.png" height="40%" width="40%" alt="Remove IP addresses that are on the remove list"/>
<br />
<br />
</p>

3.	Verify that packet data has been captured.<br/><br/>

<p align="center">
<img src="https://i.imgur.com/m9mrkN3.png" height="80%" width="80%" alt="Update the file with the revised list of IP addresses"/>
<br />
<br />
</p>

<h3>Filter the captured packet data</h3>
Use the tcpdump command to filter the packet header data from the capture.pcap capture file.</br></br>

<p align="center">
<img src="https://i.imgur.com/SCC6GEk.png" height="60%" width="60%" alt="Update the file with the revised list of IP addresses"/>
<br />
<br />
</p>

This command will run tcpdump with the following options:
•	-nn: Disable port and protocol name lookup.
•	-r: Read capture data from the named file.
•	-v: Display detailed packet data.
You must specify the -nn switch again here, as you want to make sure tcpdump does not perform name lookups of either IP addresses or ports, since this can alert threat actors.</br></br>



2.	Use the tcpdump command to filter the extended packet data from the capture.pcap capture file.<br/><br/>

<p align="center">
<img src="https://i.imgur.com/BnoPJ2G.png" height="80%" width="80%" alt="Update the file with the revised list of IP addresses"/>
<br />
<br />
</p>

This command will run tcpdump with the following options:
•	-nn: Disable port and protocol name lookup.
•	-r: Read capture data from the named file.
•	-X: Display the hexadecimal and ASCII output format packet data. Security analysts can analyze hexadecimal and ASCII output to detect patterns or anomalies during malware analysis or forensic analysis.

<h3>Summary</h3>

In this excerise, I demonstrated the use of Python used by a Cybersecurity Analyst. This example displayed how algorithms in Python can be used to perform several necessary functions to improve accuracy and efficiency of daily tasks.

•	identify network interfaces,
•	use the tcpdump command to capture network data for inspection,
•	interpret the information that tcpdump outputs regarding a packet, and
•	save and load packet data for later analysis.


