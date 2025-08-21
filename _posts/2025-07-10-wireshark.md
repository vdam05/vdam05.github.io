## Wireshark

# How to start
Wireshark is used for monitoring web traffic in real time and analyzing it. To install Wireshark, go to the download page for Wireshark at ![wireshark_download_page](https://www.wireshark.org/download.html). From there, you can follow the steps on the installer and can even install additional tools like tshark, which is Wireshark on a CLI.

For Linux, you can type in 'sudo apt install wireshark' to grab the Wireshark package. Then type the command 'wireshark' to open the GUI for wireshark. 

- You can choose a network interface to start capturing web traffic and save it into a pcap file later on. Or you can open a pcap file to see the traffic on it in the File > Open section.
![wireshark_net_int](/images/wireshark_network_interface.png)
- To actually start capturing, go to Capture. You can start/stop/restart your capture here. Once done, you can save your traffic as a pcap file at File > Save As.

# Wireshark Windows
- Packet List: shows all the packets captured and their general information. There is also IPv4 and IPv6 addresses.
  - You can order packets by the time that they arrive (packet number does not mean that they arrive in that exact order), packet number, group packets up by destination IP, source IP, the protocol used, or the common information. You can order both ways. Click on the respective column name. 
- Packet Details: where we see more details about the number of bytes captured, what network interface was used, the MAC address of source and destination, what protocol was used, source and destination port numbers and so on. It also shows the actual data in hex form. 
- Packet Bytes: this includes information in the packet details but in bytes. There is also a string representation of it as well.

![wireshark_windows](/images/wireshark-2.png)

# Filtering 
- To filter for specific packet content, go to Edit > Find Packet. 
  - Here you can search in the Packet List, Packet Details or Packet Bytes window for specific strings, hexadecimal values, or for multiple strings that matches a regex.
- To filter for specific protocols, port numbers, IP addresses, and so on, type in the command in the bar with the bookmark in front. In addition, in Analyze > Display Filters, you could store commonly used filters and their function to refer later. It looks to be just like a programming statement, with use of boolean conditions and object properties. More on display filters here: [wireshark_display_link](https://www.wireshark.org/docs/wsug_html_chunked ChWorkBuildDisplayFilterSection.html)
![wireshark_display_filter](/images/wireshark-display.png)
- It is similar for capture filters. Go to Capture > Options to manage filters. Choose an interface and at the bottom, you can type in a filter or multiple where it says "Capture filter for selected interfaces:".

*For either filters, best to create some basic rules so syntax is easily followed and then combine rules using boolean operations like 'and', 'or', 'not'. &&, ||, ! also works similar to a programming language.* 

# Streams
Since packets are out of order, in the Analyze > Follow section, you can reconstruct the conversation from ordering the packets, such as a TCP conversation or HTTP packets.

# Objects
In the File > Export Objects section, you can filter out objects, like images, that are in certain packets, such as HTTP packets. 
![wireshark_export_objects](/images/wireshark-export-obj.png)