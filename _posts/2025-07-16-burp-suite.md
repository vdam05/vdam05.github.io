# Burp Suite 
Burp Suite is used a lot in pentesting as a proxy. Therefore, you can craft specific payloads (as in the packet headers and data) and can test how the web application responded. This is called fuzzing (as in testing different inputs). 

# Features of Burp Suite
Intercepter: When turning this on, you can start browsing and in the window, it would stop the requests from being made and you can see the packet bytes, the data that you are sending when you click on a link or search for something, and even manipulate those bytes before actually forwarding them to the server.
Repeater: It works iteratively, allowing you to change certain bytes in a brute force manner. Then we get the different responses back based on what we changed. For example, we could loop through different cookie values in the header.
