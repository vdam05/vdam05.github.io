# JuiceShop
Today, we are doing challenges on the OWASP Juice Shop API. 

Tools used: Burp Suite

# Challenges

# DOM XSS
Main vulnerability: DOM XSS

In the Search tab, your search is appended within the DOM. So we can manipulate the DOM this way by adding the piece of JS code and then reload the website.

# Admin Login
Main vulnerability: SQL injection

In the Login page, use a regular SQL injection payload as:

    Username: ' OR 1==1 -- -
    Password: a

This will allow you to login as admin.

## View Basket
Main vulnerability: Broken Object Level Authentication (BOLA)

Looking around in the packet for "showing your basket" a bit, it uses a REST API seeing how the URL has `/rest` in it. I also see a `/basketID/1` which most likely means that the endpoint is for each customer's basket. Therefore, by changing the ID in the URL, I can look at someone else's basket.

# Admin Registration
Main vulnerability: Mass Assignment

Trying to send a packet at the "registration" page and then getting a response in Burp Suite, I see that there is a key called `role` with the value `customer`. This means default role is customer. 

But I could add this key-value pair to the end of the request JSON in the "registration" packet 

    ...
        "role": "admin"
    }
    ...

Therefore, this would make my account have admin privileges.


