# Internet Basics (with a focus on REST)

## The Gameplan
- What is HTTP built on, and why you should care.
    - How do we communicate without using HTTP.
- The basics of DNS.
    - A records.
    - CNAME records.
    - Debugging DNS.
- The anatomy of a URL.
    - What's a URI.
        - A URL?
- The basics of a server.
    - 127.0.0.1 vs 0.0.0.0 vs localhost
    - Firewalls.
        - UFW
- Beyond HTTP.
    - SSH
    - S/FTP
    - ping
    - netcat

## What is HTTP built on, and why you should care.
HTTP is built upon TCP, or the Transmission Control Protocol. TCP is one of many protocols which exist at the 4th layer of the networking model (for further reading, go [here](https://en.wikipedia.org/wiki/Transport_layer)). TCP transmits information from one computer to another by sending a stream of bytes (1's and 0's) to an IP address. What makes TCP important for HTTP is that TCP provides for an ordered and guaranteed delivery of information. Moreover on the topic of TCP, its important, but not necassarily essential for this basics article to know that TCP communicates via ports (65,535 to be exact). For our cases, HTTP/HTTPS operate on ports 80/443. 
### How do we communicate without using HTTP
Going on from the above, we're going to need a port. Its important to note that any port below 1024 will require root priviledges on Mac / Linux. 
Open two terminal windows (you'll need [netcat](http://netcat.sourceforge.net/) installed)
- In one terminal type: ```echo 'HI CSE6^3' | netcat -l 2160```
    - This opens up port 2160, and will send the string ```HI CSE6^3``` upon a connection. 
- In the other type: ```nc localhost 2160```
    - This will connect to your server from above, and display the message. 
- You could actually do some pretty neat things with this:
    - Transfer a file from one computer to another.
    - Stream output from computer to another.

## The basics of DNS
DNS is the system which allows a domain name to be translated to an IP address. Knowing a bit about DNS is going to be invaluable if you want to do anything on the web though. To start, DNS records are contained on something called a nameserver. These serve as types of "phonebooks" that can translate a name to an IP address. Also, like a phonebook, these nameservers aren't always up to date. This is because in between your computer and the root DNS servers, are a plethora of intermediaries. Becuase of all these intermediaries, it can take up to 48hrs for a DNS update to be available to everyone. 
### An "A" Record
An **A** record is placed in a nameserver to point a domain name to an IP address. For example, if you want to point lehigh.edu -> 8.8.8.8, you would set an A record. A more concrete example would be if you just purchased your brand new domain name, and wanted to point it to your server hosting your site. 
### A CNAME Record. 
Unlike an A record, a CNAME points from one domain name to another. This can be useful if you have a domain name you own, and would like to point it to something with an existing domain name (like GitHub pages!). For example, you could use a CNAME record to point myname.me -> myname.github.io. 

### Debugging DNS
![Its always DNS](https://i.imgur.com/WmRbmf5.png)
If there's a problem, its probably involving DNS. 
One of the most common problems is that your DNS hasn't propagated yet, in other words, your domain is lagging behind your changes. You can use a site like [WhatsMyDNS](https://www.whatsmydns.net/) to see if your changes have propagated worldwide (neato, right?). If you'd like to take a deeper look at the records of your domain, you can use another site called [IntoDNS](https://intodns.com) to view various DNS records, like A / CNAME records. 

## Anatomy of a URL
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

#### What's a URI?
A URI is a term used when you are referring to a specific resource. This is completely agnostic of *how* you're accessing the resource. 
#### A URL?
A URL is a type of URI, but not only does it point to a specific resource, it tells you how to access it. For example, something like https://www.lehigh.edu would be a URL, whereas just saying www.lehigh.edu would be a URI.

## Basics of a server
A server is something used to send data to a client via the internet. For our cases, we'll only be dealing with webserver, which will be explained in greater detail in another article. What is important for our basics tutorial is knowing the difference between multiple address your server could be run on.
### 127.0.0.1 vs 0.0.0.0 vs localhost
If you're running a local server on your computer, like our netcat example from above, you'll need a way to access it. 
```localhost``` on machines is normally mapped to ```127.0.0.1```, which is called a loopback address. This is an IP address that "loops back" and will refer to your machine.
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
### Firewalls
This isn't meant to be an indepth look at network security, but only to make you at least aware of some security considerations.
A firewall is meant to manage incoming connections on some protocol (TCP/UDP) to specific ports. In the case of a webserver, you're gonna want to keep ports 80/443/22 open, and generally block everything else. Thankfully, this is easy to do!
### UFW
On your webserver, assuming you're on Linux, you can use UFW! UFW acts as a simple front-end in front of another firewall, IPTABLES. IPTABLES has a steep learning curve, and you're bound to make mistakes when you're starting out on using it. Hence, I'd stick with using UFW first.
UFW allows you to easily configure firewall rules, but be careful, its default is to **DENY EVERY CONNECTION**. This means you can run the risk of blocking your own SSH session if you're not careful! Thankfully though, allowing ports is relatively straightforward:
```sudo ufw allow <port>``` or for a webserver ```sudo ufw allow https```, neat right?

## Beyond HTTP
The internet is much more than HTTP, and you'll need to be familiar with other protocols outside of it. 
### SSH
SSH is an abbreviation for Secure Shell. This is what you use to access another computer's command line over a network. You'll most likely be using this to setup your server. In Lehigh terms, you'll be using this to access your personal webspace at https://www.lehigh.edu/~xyz123. If you have a Lehigh account, feel free to give SSH a try by doing ```ssh <your_username>@ssh.lehigh.edu```. 
### S/FTP
FTP is an abbreviation for File Transfer Protcol. As its name suggests, this is used to transfer files across a network. Unfortuately, it is unencryptd, so we'll focus on SFTP. 
SFTP uses SSH to transfer files and is encrypted. You'll generally be using this to sync files (if you're not using Git, or for large files) between your computer and another one across a network. 
### Ping
Ping is a simple command you can use to test if a remote host is up & running. If you can't connect to a server, its always useful to try and ping what you're trying to access, and another server. If both fail, the problem is most likely on your end. 
For example:
```ping lehigh.edu``` Domain name you want to access.
```ping 9.9.9.9``` The other servert to check if you can also access it.
### Netcat
Netcat is a program (used earlier in the article) which you can use to send arbitrary data across a network. Its always useful if you want to see if you can access a specific port. 