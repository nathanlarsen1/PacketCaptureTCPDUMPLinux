<h1>Packet Capture with TCPDUMP in Linux</h1>


<h2>Project description</h2>
For this project, I acted as a Cybersecurity Analyst on a security team for an organization. One of my job roles required me to capture and analyze live network traffic from a Linux virtual machine.<br/><br/>

<h2>Language and Applications</h2>

- <b>TCPDUMP</b>
- <b>Curl</b>

<h2>Environments Used </h2>

- <b>Linux</b></br></br>

<h2>Identify network interfaces</h2>
Before I did anything else, I needed to identify the network interfaces that could be used to capture network packet data. I chose to use ifconfig to for this task.</br></br>
                                                
<p align="center">
<img src="https://i.imgur.com/QnMexuQ.png" height="80%" width="80%" alt="Open the file that contains the allow list"/>
<br />
<br />
</p>

Then, I used a with statement to open the file.</br></br>

<p align="center">
<img src="https://i.imgur.com/RwHOLAc.png" height="60%" width="60%" alt="Open the file that contains the allow list"/>
<br />
<br />
</p>

In the algorithm I created, the with statement is used with the .open() function in read mode to open the allow list file to read it. The reason for opening the file is to access the IP addresses stored in the file. The .open() function was used with the argument "r" which means the file is opened in read-only mode.</br></br>

<h2>Read the File Contents</h2>

I used the .read() method to convert the file contents into a string for the variable ip_addresses.</br></br> 

<p align="center">
<img src="https://i.imgur.com/s618TSC.png" height="80%" width="80%" alt="Read the file contents"/>
<br />
<br />
</p>

<h2>Convert the String into a List</h2>

The .split() method was used to convert the ip_addresses string into a list. This was done in order to separate the the individual IP addresses into a formated list.<br/><br/>

<p align="center">
<img src="https://i.imgur.com/Iuu68tk.png" height="60%" width="60%" alt="Convert the string into a list"/>
<br />
<br />
</p>

<h2>Iterate Through the IP Addresses List</h2>

A for loop is used to iterate through the ip_addresses list.<br/><br/>

<p align="center">
<img src="https://i.imgur.com/HwG3LTV.png" height="60%" width="60%" alt="Iterate through the IP addresses list"/>
<br />
<br />
</p>

<h2>Remove IP Addresses That Are on the Remove List</h2>

A conditional statement was used to check if any of the addresses in the remove_list exist in the ip_addresses list. If an address is found to exist in the ip_addresses list and the remove_list then it is removed from the ip_addresses list.<br/><br/>

<p align="center">
<img src="https://i.imgur.com/AkdWrLr.png" height="40%" width="40%" alt="Remove IP addresses that are on the remove list"/>
<br />
<br />
</p>

<h2>Update the File with the Revised List of IP Addresses</h2>

The .join() method was used to take the ip_addresses list and turn it into a string prepatory to saving it to the file.<br/><br/>

<p align="center">
<img src="https://i.imgur.com/m9mrkN3.png" height="80%" width="80%" alt="Update the file with the revised list of IP addresses"/>
<br />
<br />
</p>

The .open() function was used in write mode to open the "allow_list.txt" file. The reason for opening the file is to write the correct IP addresses to the file. The .open() function was used with the argument "w" which means the file is opened in write mode.</br></br>

<p align="center">
<img src="https://i.imgur.com/SCC6GEk.png" height="60%" width="60%" alt="Update the file with the revised list of IP addresses"/>
<br />
<br />
</p>

The .write() function was used to write the changes to the "allow_list.txt" file.</br></br>

<h2>Update the File with the Revised List of IP Addresses</h2>

The .join() method was used to take the ip_addresses list and turn it into a string prepatory to saving it to the file.<br/><br/>

<p align="center">
<img src="https://i.imgur.com/BnoPJ2G.png" height="80%" width="80%" alt="Update the file with the revised list of IP addresses"/>
<br />
<br />
</p>


<h2>Summary</h2>

In this excerise, I demonstrated the use of Python used by a Cybersecurity Analyst. This example displayed how algorithms in Python can be used to perform several necessary functions to improve accuracy and efficiency of daily tasks.

