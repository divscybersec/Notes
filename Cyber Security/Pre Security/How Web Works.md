#### DNS
DNS (Domain Name System) provides a simple way for us to communicate with devices on the internet without remembering complex numbers.

**TLD (Top-Level Domain)**
A TLD is the most righthand part of a domain name. So, for example, the [tryhackme.com](http://tryhackme.com/) TLD is **.com**. There are two types of TLD, gTLD (Generic Top Level) and ccTLD (Country Code Top Level Domain). Historically a gTLD was meant to tell the user the domain name's purpose; for example, a .com would be for commercial purposes, .org for an organisation, .edu for education and .gov for government. And a ccTLD was used for geographical purposes, for example, .ca for sites based in Canada, .co.uk for sites based in the United Kingdom and so on. Due to such demand, there is an influx of new gTLDs ranging from .online , .club , .website , .biz and so many more.

**Second-Level Domain**
Taking [tryhackme.com](http://tryhackme.com/) as an example, the .com part is the TLD, and tryhackme is the Second Level Domain. When registering a domain name, the second-level domain is limited to 63 characters + the TLD and can only use a-z 0-9 and hyphens (cannot start or end with hyphens or have consecutive hyphens).

**Subdomain**
A subdomain sits on the left-hand side of the Second-Level Domain using a period to separate it; for example, in the name [admin.tryhackme.com](http://admin.tryhackme.com/) the admin part is the subdomain. A subdomain name has the same creation restrictions as a Second-Level Domain, being limited to 63 characters and can only use a-z 0-9 and hyphens (cannot start or end with hyphens or have consecutive hyphens). You can use multiple subdomains split with periods to create longer names, such as [jupiter.servers.tryhackme.com](http://jupiter.servers.tryhackme.com/). But the length must be kept to 253 characters or less. There is no limit to the number of subdomains you can create for your domain name.

#### Record Types

**A Record**
These records resolve to IPv4 addresses, for example 104.26.10.229

**AAAA Record**
These records resolve to IPv6 addresses, for example 2606:4700:20::681a:be5

**CNAME Record**
These records resolve to another domain name, for example, TryHackMe's online shop has the subdomain name [store.tryhackme.com](http://store.tryhackme.com/) which returns a CNAME record [shops.shopify.com](http://shops.shopify.com/). Another DNS request would then be made to [shops.shopify.com](http://shops.shopify.com/) to work out the IP address.

**MX Record**
These records resolve to the address of the servers that handle the email for the domain you are querying, for example an MX record response for [tryhackme.com](http://tryhackme.com/) would look something like [alt1.aspmx.l.google.com](http://alt1.aspmx.l.google.com/). These records also come with a priority flag. This tells the client in which order to try the servers, this is perfect for if the main server goes down and email needs to be sent to a backup server.

**TXT Record**
TXT records are free text fields where any text-based data can be stored. TXT records have multiple uses, but some common ones can be to list servers that have the authority to send an email on behalf of the domain (this can help in the battle against spam and spoofed email). They can also be used to verify ownership of the domain name when signing up for third party services.

#### DNS Request Flow

1. When you request a domain name, your computer first checks its local cache to see if you've previously looked up the address recently; if not, a request to your Recursive DNS Server will be made.
2. A Recursive DNS Server is usually provided by your ISP, but you can also choose your own. This server also has a local cache of recently looked up domain names. If a result is found locally, this is sent back to your computer, and your request ends here (this is common for popular and heavily requested services such as Google, Facebook, Twitter). If the request cannot be found locally, a journey begins to find the correct answer, starting with the internet's root DNS servers.
3. The root servers act as the DNS backbone of the internet; their job is to redirect you to the correct Top Level Domain Server, depending on your request. If, for example, you request [www.tryhackme.com](http://www.tryhackme.com/), the root server will recognise the Top Level Domain of .com and refer you to the correct TLD server that deals with .com addresses.
4. The TLD server holds records for where to find the authoritative server to answer the DNS request. The authoritative server is often also known as the nameserver for the domain. For example, the name server for [tryhackme.com](http://tryhackme.com/) is [kip.ns.cloudflare.com](http://kip.ns.cloudflare.com/) and [uma.ns.cloudflare.com](http://uma.ns.cloudflare.com/). You'll often find multiple nameservers for a domain name to act as a backup in case one goes down.
5. An  authoritative DNS server is the server that is responsible for storing the DNS records for a particular domain name and where any updates to your domain name DNS records would be made. Depending on the record type, the DNS record is then sent back to the Recursive DNS Server, where a local copy will be cached for future requests and then relayed back to the original client that made the request. DNS records all come with a TTL (Time To Live) value. This value is a number represented in seconds that the response should be saved for locally until you have to look it up again. Caching saves on having to make a DNS request every time you communicate with a server.


#### HTTP / HTTPS
HTTP is what's used whenever you view a website, developed by Tim Berners-Lee and his team between 1989-1991. HTTP is the set of rules used for communicating with web servers for the transmitting of webpage data, whether that is HTML, Images, Videos, etc.

HTTPS is the secure version of HTTP. HTTPS data is encrypted so it not only stops people from seeing the data you are receiving and sending, but it also gives you assurances that you're talking to the correct web server and not something impersonating it.

#### URL
A URL is predominantly an instruction on how to access a resource on the internet.

**Scheme:** This instructs on what protocol to use for accessing the resource such as HTTP, HTTPS, FTP (File Transfer Protocol).

**User:** Some services require authentication to log in, you can put a username and password into the URL to log in.

**Host:** The domain name or IP address of the server you wish to access.

**Port:** The Port that you are going to connect to, usually 80 for HTTP and 443 for HTTPS, but this can be hosted on any port between 1 - 65535.

**Path:** The file name or location of the resource you are trying to access.

**Query String:** Extra bits of information that can be sent to the requested path. For example, /blog?**id=1** would tell the blog path that you wish to receive the blog article with the id of 1.

**Fragment:** This is a reference to a location on the actual page requested. This is commonly used for pages with long content and can have a certain part of the page directly linked to it, so it is viewable to the user as soon as they access the page.

eg : http://user:pass@tryhackme.com:80/view?id=1#task1


#### Request Methods

**GET Request**
This is used for getting information from a web server.  

**POST Request**
This is used for submitting data to the web server and potentially creating new records  

**PUT Request**
This is used for submitting data to a web server to update information

**DELETE Request**  
This is used for deleting information/records from a web server.

#### HTTP Status Code

| **100-199 - Information Response** | These are sent to tell the client the first part of their request has been accepted and they should continue sending the rest of their request. These codes are no longer very common. |
| ---------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **200-299 - Success**              | This range of status codes is used to tell the client their request was successful.                                                                                                    |
| **300-399 - Redirection**          | These are used to redirect the client's request to another resource. This can be either to a different webpage or a different website altogether.                                      |
| **400-499 - Client Errors**        | Used to inform the client that there was an error with their request.                                                                                                                  |
| **500-599 - Server Errors**        | This is reserved for errors happening on the server-side and usually indicate quite a major problem with the server handling the request.                                              |

| **200 - OK**                     | The request was completed successfully.                                                                                                                                                                                       |
| -------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **201 - Created**                | A resource has been created (for example a new user or new blog post).                                                                                                                                                        |
| **301 - Moved Permanently**      | This redirects the client's browser to a new webpage or tells search engines that the page has moved somewhere else and to look there instead.                                                                                |
| **302 - Found**                  | Similar to the above permanent redirect, but as the name suggests, this is only a temporary change and it may change again in the near future.                                                                                |
| **400 - Bad Request**            | This tells the browser that something was either wrong or missing in their request. This could sometimes be used if the web server resource that is being requested expected a certain parameter that the client didn't send. |
| **401 - Not Authorised**         | You are not currently allowed to view this resource until you have authorised with the web application, most commonly with a username and password.                                                                           |
| **403 - Forbidden**              | You do not have permission to view this resource whether you are logged in or not.                                                                                                                                            |
| **405 - Method Not Allowed**     | The resource does not allow this method request, for example, you send a GET request to the resource /create-account when it was expecting a POST request instead.                                                            |
| **404 - Page Not Found**         | The page/resource you requested does not exist.                                                                                                                                                                               |
| **500 - Internal Service Error** | The server has encountered some kind of error with your request that it doesn't know how to handle properly.                                                                                                                  |
| **503 - Service Unavailable**    | This server cannot handle your request as it's either overloaded or down for maintenance.                                                                                                                                     |

#### Headers
Headers are additional bits of data you can send to the web server when making requests.

**Common Request Headers**

﻿**Host:** Some web servers host multiple websites so by providing the host headers you can tell it which one you require, otherwise you'll just receive the default website for the server.  

**User-Agent:** This is your browser software and version number, telling the web server your browser software helps it format the website properly for your browser and also some elements of HTML, JavaScript and CSS are only available in certain browsers.  

**Content-Length:** When sending data to a web server such as in a form, the content length tells the web server how much data to expect in the web request. This way the server can ensure it isn't missing any data.

**Accept-Encoding:** Tells the web server what types of compression methods the browser supports so the data can be made smaller for transmitting over the internet.

**Cookie:** Data sent to the server to help remember your information (see cookies task for more information).  

**Common Response Headers**

**Set-Cookie:** Information to store which gets sent back to the web server on each request (see cookies task for more information).  

**Cache-Control:** How long to store the content of the response in the browser's cache before it requests it again.  

**Content-Type:** This tells the client what type of data is being returned, i.e., HTML, CSS, JavaScript, Images, PDF, Video, etc. Using the content-type header the browser then knows how to process the data.  

**Content-Encoding:** What method has been used to compress the data to make it smaller when sending it over the internet.

#### Other Components

**Load Balancers**
When a website's traffic starts getting quite large or is running an application that needs to have high availability, one web server might no longer do the job. Load balancers provide two main features, ensuring high traffic websites can handle the load and providing a failover if a server becomes unresponsive.

**CDN (Content Delivery Networks)**
A CDN can be an excellent resource for cutting down traffic to a busy website. It allows you to host static files from your website, such as JavaScript, CSS, Images, Videos, and host them across thousands of servers all over the world. When a user requests one of the hosted files, the CDN works out where the nearest server is physically located and sends the request there instead of potentially the other side of the world.  

**Databases**
Often websites will need a way of storing information for their users. Webservers can communicate with databases to store and recall data from them. Databases can range from just a simple plain text file up to complex clusters of multiple servers providing speed and resilience. You'll come across some common databases: MySQL, MSSQL, MongoDB, Postgres, and more; each has its specific features.

**WAF (Web Application Firewall)**
A WAF sits between your web request and the web server; its primary purpose is to protect the webserver from hacking or denial of service attacks. It analyses the web requests for common attack techniques, whether the request is from a real browser rather than a bot. It also checks if an excessive amount of web requests are being sent by utilising something called rate limiting, which will only allow a certain amount of requests from an IP per second. If a request is deemed a potential attack, it will be dropped and never sent to the webserver.

