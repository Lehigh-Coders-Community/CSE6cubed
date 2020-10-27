## TBD
## Intro

HTTP is the protocol which underpins the modern internet. There's only one problem though, it sends everything in **plain text**. Why is this bad? It means everything you send to a website (or API, you get the gist) can be read by anyone in between you and the server. This problem is why the HTTPS (Hyper Text Transfer Protocol Secure) was invented.

## HTTP[S] Recap
To recap, HTTP/S is a stateless protocol. What this means is that each request is independent of each other, notwithstanding any user defined state (cookies, sessions ids, etc). The HTTP standard also defines numerous status codes & methods for use.
### Status Codes:
[Full listing](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status), but these are the few that you should know:

#### 200 OK
If the server is working correctly, a return value of this code means your request succeeded. Anything not 2XX generally means: an error (on your end), an error (on the server), or a redirect.

#### 404 Not Found
I'm sure we've all experienced this before, quite simply, this means the resource you were requesting isn't available. 

#### 400 Bad Request
You sent the server something it couldn't parse. For example, this might be if you sent some JSON but missed a comma somewhere.

#### 403/1
Receiving a 403 or 401 response code implies that you need some sort of authorization to access a resource. Generally, you may receive this if the web server admin had a misconfiguration, you were logged out of a site due to inactivity and tried to access a page, or you tried to access a page without the right credentials. 

#### 500
The server had an error with your request, or somewhere along the line in processing it. This is generally a catch all error for what could be any combination of errors. For example, if a developer is careless with response codes, a 500 could mean a **400**, **403**, to just a syntax error in the server. 

### HTTP Methods
[Full listing](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods), but here's the big ones:

#### GET
A request that does not need any body, or if one is present, its ignored. This method is used to retrieve some content, but never to change any. For example, a GET request is sent to retrieve a web page.

#### POST
A request that can have a body. This method is used to create some content. For example, when you register for an account somewhere.

#### PUT
Very similar to POST, but is used to update or create content with a specific ID. For example, when you edit your user account.

#### DELETE
A request that has no body, or if one is present, is ignored. Used to delete a specific piece of content. 

## HTTPS & You
Knowing at least the basics of HTTPS is essential for building any web app. With the ease of obtaining SSL/TLS certificates (more later), and Let's Encrypt (also later), there's no excuse to not be using HTTPS. Moreover, some new Web 2.0 features, such as WebRTC and Geolocation, will **not** work without the site using HTTPS. Additionally, some specific domain names, such as those ending in .dev **require** https to actually be connected to. 

### So, what makes up HTTPS
HTTPS is made up of 3 main items. This will be intentionally brief, and will not go into the weeds of asymmetric/symmetric encryption.
1. Your Certificate Signing Request (CSR)
    - Used by a certificate authority, or yourself to generate a new private key.
2. Your private key.
    - Stored on your server to encrypt/decrypt incoming data.
3. Your certificate.
    - Sent to the client's browser to verify the identity of your server. If this doesn't validate, you get an error page and something along the lines of "Certificate Error" in your browser.
4. Your browser/OS keychain.
    - Used to verify the certificate sent by your server.

### How do I get HTTPS on my site?

#### **I'm using a hosting company**
Generally a company like Namecheap and GoDaddy will allow you to purchase an SSL certificate for a yearly fee. Installation here is normally painless, sometimes even 1-click! If you encounter any problems, support is available.

#### **I'm using something like Heroku**
Heroku (or someone similar) will allow you to either purchase an SSL certificate for a nominal fee, or you'll be provided one for free. Normally, you won't be able to bring your own certificate as you're assigned a subdomain and just a barebones server. Of course, I'm sure an **Enterprise™** account will let you.

#### **I'm running my own VPS on a cloud provider.**

Use Let's Encrypt. Depending on your webserver, you'll be able to do a simple automated installation. One thing to note though, is that Let's Encrypt certificates expire after a short time, generally 60 days. 

[Let's Encrypt](https://letsencrypt.org/)

#### **I'm running my own web server on my laptop and I just need HTTPS to test something out**
You'll want to self sign a certificate for testing. You can safely ignore your browser warnings for local testing. You can follow any number of Google tutorials, but here's one I've used before that's written pretty well.

[Self Sign an SSL Cert](https://www.digitalocean.com/community/tutorials/openssl-essentials-working-with-ssl-certificates-private-keys-and-csrs)

