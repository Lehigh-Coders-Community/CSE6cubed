# Internet Basics (with a focus on REST)

## TCP
If you're going to be interacting with an API, you'll be using HTTP/HTTPS. What is important to note though, is that both of these protocols are built upon TCP (Transmission Control Protocol). Without getting bogged down in the details, this applies to HTTP & HTTP/2, HTTP/3 is not built upon TCP but rather QUIC. *Buttt*, this is outside the scope of this article. What is important though, especially if you're going to be building a RESTful service is to know these key points.

- You communicate with TCP via a port:
    - For simplicities sake, this means only **one** application can run on a port at a time. 
    - In the case of a webserver, this means that only **one** webserver can run on port 80/443 at a time.
- Only certain ports are available for non-root users:
    - If you're not root and you want to open a port number below 1024, you're out of luck.
- But, there's a lot of ports:
    - 65,535 to be exact.
- You normally send to a specific port and receive on a random one.
    - Your web browser will send a request to a web server on port 80/443, but receive on a different one on your machine.
    - But why?
        -  If your machine exclusively used port 80/443, you'd be at most able to open one connection on each port at a time, which is really inefficient. 
- Ports are cool, how can I play around with them?
    - Open two terminal windows (you'll need [netcat](http://netcat.sourceforge.net/) installed)
    - In one terminal type: ```echo 'HI CSE6^3' | netcat -l 2160```
        - This opens up port 2160, and will send the string ```HI CSE6^3``` upon a connection. 
    - In the other type: ```nc localhost 2160```
        - This will connect to your server from above, and display the message. 
    - You could actually do some pretty neat things with this:
        - Transfer a file from one computer to another.
        - Stream output from computer to another.

## No place like 127.0.0.1
If you're running a local server on your computer, like our netcat example from above, you'll need a way to access it. 
```localhost``` on machines is normally mapped to ```127.0.0.1```, which is called a loopback address. This is an IP address that "loops back" and will refer to your machine.
### Running a process on 127.0.0.1 or 0.0.0.0?
Another subtle detail that can be overlooked if you're copy & pasting from documentation is choosing *what* address to listen on.
Here's the key details you need to know:
- 127.0.0.1
    - Only refers to your machine.
    - If you listen on this address, your server won't be available outside your loopback.
    - Keeps your secrets.
- 0.0.0.0
    - Refers to any available network inteface.
    - If you're on the internet with no firewall, your server is available to everyone/
        - If that's what you want, then good!
    - Tells everyone your secrets.

In practice:
    - You're going to want your webservers / anything publically accessible to be on 0.0.0.0.
    - Database servers / services behind a proxy should be listeing on 127.0.0.1.
        - Let your webserver be an intermediary to them.
    
## The Firewall
This isn't meant to be an indepth look at network security, but only to make you at least aware of some security considerations.
A firewall is meant to manage incoming connections on some protocol (TCP/UDP) to specific ports. In the case of a webserver, you're gonna want to keep ports 80/443/22 open, and generally block everything else. Thankfully, this is easy to do!
### UFW
On your webserver, assuming you're on Linux, you can use UFW! UFW acts as a simple front-end in front of another firewall, IPTABLES. IPTABLES has a steep learning curve, and you're bound to make mistakes when you're starting out on using it. Hence, I'd stick with using UFW first.
UFW allows you to easily configure firewall rules, but be careful, its default is to **DENY EVERY CONNECTION**. This means you can run the risk of blocking your own SSH session if you're not careful! Thankfully though, allowing ports is relatively straightforward:
```sudo ufw allow <port>``` or for a webserver ```sudo ufw allow https```, neat right?

## DNS
![Its always DNS](https://i.imgur.com/WmRbmf5.png)

DNS is the system on the internet which translates a web address (like github.com) into an IP address that you can make a socket connection on (see everything coming together!). DNS is arranged in a hierarchical format, which is important to remember since **DNS changes are not instant**. 

See the hierarchy below, instead of me trying to draw it.
![The DNS Hierarchy](https://www.novell.com/documentation/dns_dhcp/dhcp_enu/graphics/dhc_002a.gif)

### DNS Propagation
Say you just ordered your brand new domain name from a registrar, you're so excited to host your new project and eagerly fill out the IP address in the A record column. More on DNS records later though. You hit save and type in your new domain name and ... nothing. It doesn't work. To make it succint, here's the general idea:
- Your request passes through countless DNS servers, and in order to save time, they store DNS records.
- When you lookup your new name, they don't have it in their cache.
- Eventually, their caches expire and they reach up the DNS hierarchy, or to another DNS server on new requests to get DNS info.
- This repeats until we're at one of the DNS root servers for your TLD (i.e .com, .edu, .net)
- Finally, your DNS records are found and they filter down to you. 
- Your site is accessible to you now!
While this can take up to 48 hours, its generally a lot less. You can use a site like [whatsmydns](https://www.whatsmydns.net/) to check the propagation of a website. Also, another cool site called [intoDNS](https://intodns.com) allows you to check the DNS records for a website.

### DNS and ports
Can I use DNS to point to a specific port?
The short answer is yes, but you probably shouldn't do it.
Pointing to a port needs a special DNS record named an SRV record. This is outside the scope of Internet Basics, but its helpful to know its at least possible. 

## The anatomy of a URL
We've all seen URLs before, but what's important to note is that there's a LOT of data stored in them. 
Let's break down this URL:

https://www.lehigh.edu/help?submit=troubleTicket
- https
    - This is the protocol we're using to connect.
    - This can be anything from ftp:// (for File Transfer Protocol) to ws:// (for WebSockets)
- www.lehigh.edu
    - The domain name we're accessing.
    - Goes through DNS to give us an IP.
- /help
    - A directory, or identifier that the webserver used to locate some content.
    - This need not be an actual directory.
- ?submit
    - The key portion of a key-value pair that the web server can use to gain more information about your request.
- =troubleTicket
    - The value of our key-value pair from above. 
## Recap
Let's recap on what you learned from this tutorial, and what the key takeaways are:
- You know that TCP listens and sends data via a port.
    - HTTP also uses TCP, so it uses ports, namely ports 80/443.
- You know how to send data across a port and receive it using netcat.
- You know what the loopback address is, and how it compares to 0.0.0.0
    - You also know the use cases:
        - 127.0.0.1 for yourself.
        - 0.0.0.0 for the world.
- You know what a firewall is, and how it can be used, and a popular one in use.
    - Deny everything, only open what you need.
- You know what DNS is, and how it works on a surface level.
    - You know that DNS changes are not instant. 
    - You know some neat tools that can be used to debug DNS issues.
- You can dissect a URL and understand its parts.
    - You can see where a protocol is used, and what it is.
    - You can identify key-value pairs in the URL and see what information is encoded.
