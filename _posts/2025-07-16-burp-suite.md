# Burp Suite 
Burp Suite is used a lot in pentesting as a proxy. Therefore, you can craft specific payloads (as in the packet headers and data) and can test how the web application responded. This is called fuzzing (as in testing different inputs). 

# Features of Burp Suite
*It requires you to open a new browser with Burp Suite for it to work, rather than using the browser you already opened. Also, the browser will run HTTP, not HTTPS. That's why we can see those bytes and not have to decode them.*
- In the Proxy section, you can turn on Intercept, which stops the requests from being made and you can see the packet bytes, the data that you are sending when you click on a link or search for something, and even manipulate those bytes before actually forwarding them to the server. 
  - There is also the HTTP history tabs that show all the packets that you sent while the browser is opened.
- Intruder: It works iteratively, allowing you to change certain bytes in a brute force manner. Then we get the different responses back based on what we changed by choosing a type of attack and putting a variable for the loop. For example, we could loop through different cookie values in the header. 
  - Click on Positions > Add/Clear/Auto $ for the variable changes on where the pointer is. The command "Auto $" tries to put a variable where it could affect the payload, such as in the cookie.
  - Sniper attack: highlight a certain string that we are looping through. Then we can choose a payload type (like numbers, characters, etc) that will be put in. For example, we can iteratively create payloads with a certain variable number from 0 to 20 and get back those responses in full details.
- Repeater: This is for freely changing individual packets and seeing what the response is. Unlike intruder which gives you multiple responses after the loop, repeater gives you the response immediately for each request.
