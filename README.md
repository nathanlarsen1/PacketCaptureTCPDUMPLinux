<h1>Packet Capture with TCPdump in Linux</h1>


<h2>Project description</h2>
For this project, I acted as a Cybersecurity Analyst on a security team for an organization. One of my job roles required me to capture and analyze live network traffic from a Linux virtual machine.<br/><br/>

<h2>Language and Applications</h2>

- <b>TCPDUMP</b>
- <b>Curl</b>

<h2>Environments Used </h2>

- <b>Linux</b></br></br>

<h2>Project Walkthrough</h2>

<h3>1. Identify Network Interfaces</h3>

To start the project, I needed to identify the network interfaces that could be used to capture network packet data. I chose to use `ifconfig` for this task.</br></br>
                                                
<p align="center">
<img src="https://i.imgur.com/whah6Wj.png" height="100%" width="100%" alt="Open the file that contains the allow list"/>
<br />
<br />
</p>

The Ethernet network interface is identified by the entry with the `eth` prefix. I used `tcpdump` to identify the interface options available for packet capture. I discovered that eth0 interface was available.</br></br> 

<p align="center">
<img src="https://i.imgur.com/RwHOLAc.png" height="100%" width="100%" alt="Open the file that contains the allow list"/>
<br />
<br />
</p>

<h3>2. Inspect the Network Traffic of a Network Interface with TCPdump</h3>

For this part of the project, I used `tcpdump` to filter live network packet traffic on the eth0 interface.</br>

In this instance, tcpdump was run with the following options:</br>
-i eth0: Capture data specifically from the eth0 interface.</br>
-v: Display detailed packet data.</br>
-c5: Capture 5 packets of data.</br></br>

<p align="center">
<img src="https://i.imgur.com/s618TSC.png" height="100%" width="100%" alt="Read the file contents"/>
<br />
<br />
</p>

After executing the command, tcpdump reported listening on the eth0 interface, providing details about the link type and capture size in bytes.</br>

The first field on the next line is the packet's timestamp, followed by the protocol type (IP). The -v option provided more information about the IP packet fields, including TOS, TTL, offset, flags, internal protocol type (TCP in this case), and the outer IP packet's length.</br>

The subsequent section displayed the communicating systems. The arrow's direction (>) indicated the traffic flow. Each system name included a port number suffix (.5000 in the screenshot), used by the source and destination systems for this packet.</br>

The remaining data filtered the header data for the inner TCP packet. The flags field identified TCP flags. Here, the P represented the push flag, and the period indicated an ACK flag, signifying that the packet was pushing out data.</br>

The next field was the TCP checksum value, used for error detection. This section also included sequence and acknowledgment numbers, window size, and the inner TCP packet's length.</br></br>

<h3>3. Capture Network Traffic with TCPdump</h3>

Capture packet data into a file called capture.pcap. You must press the ENTER key to get your command prompt back after running this command.</br></br>

In this instance, tcpdump was run with the following options:</br>
-i eth0: Capture data from the eth0 interface.<br/>
-nn: Do not attempt to resolve IP addresses or ports to names.This is best practice from a security perspective, as the lookup data may not be valid. It also prevents malicious actors from being alerted to an investigation.<br/>
-c9: Capture 9 packets of data and then exit.<br/>
port 80: Filter only port 80 traffic. This is the default HTTP port.<br/>
-w capture.pcap: Save the captured data to the named file.<br/>
&: This is an instruction to the Bash shell to run the command in the background.<br/><br/>

<p align="center">
<img src="https://i.imgur.com/Iuu68tk.png" height="100%" width="100%" alt="Convert the string into a list"/>
<br />
<br />
</p>

After I pressed the ENTER key I was returned to the command prompt.<br/><br/>

<p align="center">
<img src="https://i.imgur.com/HwG3LTV.png" height="100%" width="100%" alt="Iterate through the IP addresses list"/>
<br />
<br />
</p>

Curl was used to generate some HTTP (port 80) traffic that could be captured.<br/><br/>

<p align="center">
<img src="https://i.imgur.com/AkdWrLr.png" height="100%" width="100%" alt="Remove IP addresses that are on the remove list"/>
<br />
<br />
</p>

Next, I verified that packet data had been captured by running the `ls -l` command on the capture.pcap file and discovered it was 1404 bytes which showed that it contained capture data.<br/><br/>

<p align="center">
<img src="https://i.imgur.com/m9mrkN3.png" height="100%" width="100%" alt="Update the file with the revised list of IP addresses"/>
<br />
<br />
</p>

<h3>4. Filter the Captured Packet Data</h3>
The tcpdump command was used to filter the packet header data from the capture.pcap capture file.</br></br>

In this instance, tcpdump was run with the following options:</br>
-nn: Disable port and protocol name lookup.</br>
-r: Read capture data from the named file.</br>
-v: Display detailed packet data.</br>
You must specify the -nn switch again here, as you want to make sure tcpdump does not perform name lookups of either IP addresses or ports, since this can alert threat actors.</br></br>

<p align="center">
<img src="https://i.imgur.com/SCC6GEk.png" height="100%" width="100%" alt="Update the file with the revised list of IP addresses"/>
<br />
<br />
</p>

For the final step in the project, the tcpdump command was used to filter the extended packet data from the capture.pcap capture file.

In this instance, tcpdump was run with the following options:</br>
-nn: Disable port and protocol name lookup.</br>
-r: Read capture data from the named file.</br>
-X: Display the hexadecimal and ASCII output format packet data. Security analysts can analyze hexadecimal and ASCII output to detect patterns or anomalies during malware analysis or forensic analysis.<br/><br/>

<p align="center">
<img src="https://i.imgur.com/BnoPJ2G.png" height="100%" width="100%" alt="Update the file with the revised list of IP addresses"/>
<br />
<br />
</p>

<h3>Summary</h3>

In this excerise, I demonstrated the use of tcpdump used by a Cybersecurity Analyst. This example displayed how you can identify netowrk interfaces. How you can use tcpdump to capture network data for inspection, interpret the output and save and load packet data for later analysis.
