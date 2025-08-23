# Burp Suite 
Updated: 08/23/2025

Burp Suite is used a lot in pentesting as a proxy. Therefore, you can craft specific payloads (as in the packet headers and data) and can test how the web application responded. This is called fuzzing (as in testing different inputs). 

Burp Suite is a Proxy.

# HTTP vs WebSocket
They are both ways of communication between the user and the server. However, HTTP is used more as the user sending the request and the server sending back the response. One party asks for data, the other sends in a snappy manner. Meanwhile, web sockets are for persistent connection between the two parties. The idea is similar to the idea of tunnels in VPNs, where data flows between 2 endpoints inside that tunnel. Once either endpoint breaks the connection, then it would stop data flowing. This is therefore useful for live videos and calls.  

# Features of Burp Suite
*It requires you to open a new browser with Burp Suite for it to work, rather than using the browser you already opened.*
- Target: It can show you your history of websites opened (along with its file structures and packets related).
- Proxy: you can turn on Intercept, which stops the requests from being made and you can see the packet bytes, the data that you are sending when you click on a link or search for something, and even manipulate those bytes before actually forwarding them to the server. 
  - There is also the HTTP history tabs that show all the packets that you sent while the browser is opened. It will show you both successful and failed packets 
    - To see the packet where you edited it, click on a packet and change from Original Packet to Edited Packet
  - The Inspector table also shows you all the content variables for that packet and you can edit directly in it and it would reflect in the packet immediately.
  - By right-clicking on a packet, you can also send that packet to Intruder, Repeater or Decoder as well.
- Intruder: It works iteratively, allowing you to change certain bytes in a brute force manner. Then we get the different responses back based on what we changed by choosing a type of attack and putting a variable for the loop. For example, we could loop through different cookie values in the header. 
  - Click on Positions > Add/Clear/Auto $ for the variable changes on where the pointer is. The command "Auto $" tries to put a variable where it could affect the payload, such as in the cookie.
  - We can choose a payload type (like numbers, characters, etc) that will be put in where the variables art at.
  - Sniper attack: go through all payload strings possible. Repeat for each position.
  - Battering ram attack: go through all payload strings possible and put them in all positions simultaneously.
  *You can also put your strings in a file that will be read from for payloads in the Payload Type.*
- Repeater: This is for freely changing individual packets and seeing what the response is. Unlike intruder which gives you multiple responses after the loop, repeater gives you the response immediately for each request. It is quite convenient.
- Decoder: This is 
# Setting up a browser with Burp automatically as proxy
Rather than opening a new browser in the Proxy section every time, you can set a default browser that you use with
Burp as proxy. It is different depending on browsers.

In Firefox, it would be in the Settings > Network Settings > Manual proxy configuration (choose IP as 127.0.0.1 which is localhost and port 8080 as default Burp port) 
