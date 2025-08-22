# Burp Suite 
Burp Suite is used a lot in pentesting as a proxy. Therefore, you can craft specific payloads (as in the packet headers and data) and can test how the web application responded. This is called fuzzing (as in testing different inputs). 

# HTTP vs WebSocket
They are both ways of communication between the user and the server. However, HTTP is used more as the user sending the request and the server sending back the response. One party asks for data, the other sends in a snappy manner. Meanwhile, web sockets are for persistent connection between the two parties. The idea is similar to the idea of tunnels in VPNs, where data flows between 2 endpoints inside that tunnel. Once either endpoint breaks the connection, then it would stop data flowing. This is therefore useful for live videos and calls.  

# Features of Burp Suite
*It requires you to open a new browser with Burp Suite for it to work, rather than using the browser you already opened. Also, the browser will run HTTP, not HTTPS. That's why we can see those bytes and not have to decode them.*
- In the Proxy section, you can turn on Intercept, which stops the requests from being made and you can see the packet bytes, the data that you are sending when you click on a link or search for something, and even manipulate those bytes before actually forwarding them to the server. 
  - The Target section do also show you your history of the packets to certain websites and also show you your history of websites opened (along with its file structures and packets related).
  - There is also the HTTP history tabs that show all the packets that you sent while the browser is opened.
  - The Inspect table also shows you all the content variables for that packet and you can edit directly in it and it would reflect in the packet immediately.
- Intruder: It works iteratively, allowing you to change certain bytes in a brute force manner. Then we get the different responses back based on what we changed by choosing a type of attack and putting a variable for the loop. For example, we could loop through different cookie values in the header. 
  - Click on Positions > Add/Clear/Auto $ for the variable changes on where the pointer is. The command "Auto $" tries to put a variable where it could affect the payload, such as in the cookie.
  - We can choose a payload type (like numbers, characters, etc) that will be put in where the variables art at.
  - Sniper attack: go through all payload strings possible. Repeat for each position.
  - Battering ram attack: go through all payload strings possible and put them in all positions simultaneously.
  *You can also put your strings in a file that will be read from for payloads in the Payload Type.*
- Repeater: This is for freely changing individual packets and seeing what the response is. Unlike intruder which gives you multiple responses after the loop, repeater gives you the response immediately for each request. It is quite convenient.
