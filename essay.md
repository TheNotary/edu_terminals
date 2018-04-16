# Programming Terminals
July 5, 2016


#### Presentation Notes and Resources:
  - Audience:  Anyone interested in Working with APIs to Generate Helpful Reports
  - [slides](slides/index.html)
  - [Git](http://lmgtfy.com/?q=install+git+windows) the source code saving software
  - [Atom](http://lmgtfy.com/?q=install+atom+windows) the source code writing text editor
  - [Ruby](http://lmgtfy.com/?q=install+ruby+windows) the programming language


#### ToC

Rough Notes:
  -


###### Section 1 - Basic Web API Tools?
  -


###### Section 2 - All about terminals
  - Terminals!
    - A terminal comes with windows... but it really sucks hard
    - A terminal comes with git, and is decent
    - What makes a good terminal?
    - Terminals are Just like Folder Browsing but more powerful
      - Let's do a side-by-side comparison
      - mkdir
      - ls
      - cd
      - echo hello
      - echo hello > my_file
      - cat my_file
    - So let's break those codes up... What are Commands and Arguments?


###### Section 3 - All about git
  - What it does
  - Common Commands
    - git init
    - git add .
    - git commit -m "INSERT MESSAGE DESCRIBING THE CHANGE YOU MADE TO YOUR CODE"
  - Sharing your code on Github.com




###### Section 4 - All about Fundamental Programming
  - It's all just strings

  From the perspective of an API developer, programming is simply reading string data, preforming some kind of logic against the string, and outputting the results of this logic step.  

  - Type Primitives "It's like math and variables"

  - Your first program (puts "Fancy Report")

  - Methods/ Functions


# Section 1 - How Do I Even Install Basic Web API Tools?

API programming is done with a few basic applications:

- A terminal,
- A source code management application, and
- A text editor.  

I'll walk through the installation process on all these things now...  


## Git

Here are the install steps for git which get us both git, a software management solutions, and also git bash.  





















.
.
.



## HTTP
###### graph of https://example.com/resource (https is circled)

So the most commonly used protocols on the web are HTTP and the secure variant, HTTPS.  

It stands for...

###### Slide of server/ client
Most client/ server interactions on the web begin with a browser-client sending an HTTP request to a web server.  

The interaction ends with the web server sending back an HTTP response.  


###### Slide of request file

These requests and responses are nothing more than strings of text.  
That's why they call it hyper text transfer protocol, it's all just a bunch of text.  


###### Firefox Inspector of request

By far, my favorite way to view request and response files is through firefox.  
I've included a slide of the view, but I may as well demonstrate this live.  


###### Slide of TCP Dump in action

I can use a CLI utility to view packets.  CLI stands for command line interface and just means you can run the program on the terminal.  
`sudo tcpdump -A -s 0 -i lo 'tcp port 80 and (((ip[2:2] - ((ip[0]&0xf)<<2)) - ((tcp[12]&0xf0)>>2)) != 0)'`

  - `-i lo` tells tcpdump to only listen to my loop back adapter, only showing transactions to and from 127.0.0.1
  - there's a filter section between single quotes that make it so I only see the really interesting packets  


###### Slide of using bash to send a TCP stream

Using this snippet we can actually send a valid http request using echo and bash
```
exec 3<>/dev/tcp/localhost/80
echo -e "GET /cgi-bin/bash_hi HTTP/1.1\r\nHost: 127.0.0.1\r\nConnection: close\r\n\r\n" >&3
cat <&3
```


>> So that's all there's is to it!  The transaction between a server/ client is pretty much just an exchange of files.  



###### ASK!

PLEASE ASK ME ANYTHING!  WHAT ARE YOU CURIOUS ABOUT REGARDING THE WEB!!!!



# Section 2 - What do web servers do?


## Ports

Do you all know about ports?
What are ports?  How many are there?  (2^16, 65,536 ports)
I like to think of ports as doors.  
Sometimes some kind of service will be waiting behind a door listening for a client to knock and then will perform some action for said client.  

Can somebody shout out some examples of services that listen on ports?  
  - Web Servers (80)
  - Samba (tcp: 139, 445; udp: 137, 138)
  - SSH (22)
  - irc (6667)
  - l4d (27015)


Have a look at this URL.

`https://google.com:80`

If we key that into an address bar, we'll be instructing our web browser client to...
  - utilize the https protocol,
  - convert the hostname `google.com` into an IP address like 216.58.192.14, and then
  - send data through a tcp stream to port 80 of the IP address to google.com


>>  SO we can specify a port in a URL!  That's so cool!
>>  Ports are like doors!


## Static File Serving


###### slide:  http://search.lores.eu/index.html

So let's say I'm a webserver.  
And I'm listening behind port 80.  
And someone requests from me a file, like index.html.  
What do you think I'm going to do?

Yeah, if index.html is an actual html file on my file system, I'll simply send it to the client making the request along with some headers.  


## FastCGI

To me, static files are pretty boring.  In recent years, we've gotten much cooler front end assets.  
CSS is actually nice now, javascript is sweet.  HTML5 has good stuff like corner radiii and canvas.  
But I like server side API calls and persistent storage a lot, you only get that from the backend.  


## rack/ wsgi

###### Slide:  <plain words>  Rack, wsgi

Has anyone heard of these terms, rack, and wsgi?  
Does anyone know what they are?  (specifications)

These are adapters applications, they connect things in the HTTP server world to the programming world.  
Let's think about just rack.  
On one end of rack, it wants to hear web requests from web clients.  
So half of rack is that it's a web server.  
The other half of rack is a function call.  
It's calling an application <GOOGLE ME>.

So when you boot up a rack application, you're booting up a web server.  One that is really to run arbitrary ruby commands in.  


###### Slide:  basic rack app

This is a valid rack app.  Valid rack apps need to expose a 'call' method (which will be called on the reciept of web requests) and it needs to respond with an array containing http 1.1 codes.  


# Section 3 -








Who
haz
thoughts?
