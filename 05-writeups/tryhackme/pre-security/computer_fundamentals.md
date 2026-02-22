# INTRO

## INSIDE A COMP

 **MOTHERBOARD**

a motherboard act as a skeleton system which holds and connects all components of the computer together.

**CPU** or a processor is comparable to human brain, and computes all the instructions given, processors have multiple cores which handle tasks parallel and effieciently.

**RAM** holds info for CPU to get quick access to, like a short term memory. Once power is lost, all its content is lost.

**STORAGE** SSDS and HDDs store data even when powered off, acting as long term memory storage, HDDs have moving parts and slower performance but SSDs have no moving parts and a memory chip hence fast performance, HDDs have huge space in low cost so its popular, they connect via SATA and PCI.

**NETWORK ADAPTER** these act as a communicator for other devices, if they are embedded in motherboard they can act as expansion cards.

**PSU** power supply unit acts as a heart pumping blood, so all components require sufficient amt, if not then the systems can fail.

## Power on

Press power on --> firmware starts-->POST(power on self test)-->Select boot device-->Select bootloader

Step 1: Press the Power Button
When we press the power button on our computer system, a signal is sent to the PSU to allow power to flow. Imagine our body being powered off when we sleep. Once we wake up and receive oxygen, our body starts pumping blood and boots up.

Step 2: Firmware starts
Continuing our analogy from step 1, once the body has started up, our core components are up and running, but our brain is not yet conscious. Like our bodies, a computer system contains firmware that allows all its components to start up. The central system that manages this is called the Unified Extensible Firmware Interface (UEFI). Note: We will often see the term BIOS mentioned instead of UEFI. BIOS does the same as UEFI, but has mainly been replaced by UEFI

Step 3: Power-On Self Test
Now that our body is up and running, it is time to test if everything is functioning as it should. If something isn't, there will be some alarm signals. One of the routines that the UEFI loads is the Power-On Self Test, which tests if every required component is present, configured correctly, and functioning.

Step 4: Select Boot Device
Once our body is up and running, configured correctly and fully functional, our system searches for the location of our bootup routine to start our consciousness. In our computer system the UEFI holds an ordered list which prioritizes on which device to look first for the boot up routine for the Operating System.

Step 5: Initiate Bootloader
Now that our system knows the part of our brain where our consciousness is located, it initiates the "load routine" to start it. Our computer systems follow a similar process: On the selected boot device, the bootloader is initiated. This bootloader transfers the Operating System from the selected boot device to the Random Access Memory. Once the OS is transferred, the UEFI gives control over the different components to the OS.

Now that we know how a computer system boots, let's have a little exercise. Open the static site in this task by clicking the green "Static Site" button and follow the instructions to answer the question below.

# COMPUTER TYPES

Laptop - portablility

Desktop - consistency

Workstation - more complex tasks with precision

Server - screenless, but running continuously

Smartphone - pocket-sized computers.

Tablet - touch first computer with large screens.

Iot device - network connected device with a single purpose.

Embedded system - computer build into other device(coffee maker, automatic door sensor)

<mark> iot connects to network, and report problems, but embedded system stay for years and might not know if it exists.</mark>


One of the easiest ways to explain how computer systems provide services to other systems is to use an analogy: for example, how shops offer services to their customers. Let's have a look at a pizza takeaway.

It's Friday night, and Alice and Bob feel like having pizza. Alice looks at Luigi's Pizza's menu and tells Bob which pizza she wants. Bob takes the car, enters Luigi's address into his GPS, and starts driving. Once Bob arrives, he enters Luigi's and places his order: "Get me a large pepperoni pizza and a coke." The employee acknowledges the order and starts making the pizza. Once the order is ready, Bob returns home and has a lovely pizza night with Alice.

This seems like a standard, straightforward process. But don't be fooled. Because we are so used to ordering pizza, we have internalized the process. Let's have a closer look at each step and relate it to how computer systems interact.

Client-server analogy
Service, Client, Server

In our analogy, Bob and Alice choose to use the Pizza takeaway service. Alice is the client who passes her order to Bob, who then passes it to the Server at Luigi's Pizzas. In computer terms, we can translate this as Alice using, for example, a browser to navigate to a website. The browser is the client that requests the webpage, and the server is the system that serves it.

Note that the client is the one who always initiates the request.
Request and Response

Alice requested a large pepperoni pizza from Luigi's. Be careful, this request was not made to Bob. Bob was the one who brought the request to Luigi's. What is important to realize is that if the request is not formatted correctly or the requested resource is unavailable, we will get an error response. For example, Bob returns to Alice with the message that there were no pepperoni pizzas or that the server did not understand the order.

In computer systems, we can say that Alice used a browser (the client) to request a webpage from a server, which then sent the webpage to the client.
Protocol

One of the things we don't often realize, until we go on a trip to a foreign country, is our language. When Alice formulates her request to Bob, she uses the language Luigi's Pizza understands. Additionally, Alice uses the menu to determine which orders she can place. Bob understood the request (language and order) and went to Luigi's to bring it; he received a response he understood and brought it back to Alice.

We can compare Bob to a protocol that computer systems use to communicate. A protocol defines how a client can communicate with a server. This definition includes:

    Which commands do the client and server understand. E.g., the get command.
    How a request is structured. E.g., first the command and then the order.
    What syntax is used. E.g., Alice uses the English language.
    What response should be given to which type of request. E.g., a request for pizza results in receiving the available pizza.
    What response to give to faulty requests. E.g., the server at Luigi's Pizzas says: No pepereonni pizza available

Port

A port is used to identify a specific service running on a system. When a client wants to access a service on a server, it must connect using the correct port.

Imagine that Luigi’s takeaway service requires customers to enter through a specific door. Everyone ordering takeaway uses the same door. In the same way, a service on a server listens on a specific port.

Now imagine that Luigi’s offers multiple services, such as takeaway, dining in, and delivery. Each service uses a different door: door A for takeaway, door B for the restaurant, and door C for delivery. Similarly, a single server can run multiple services at the same time, with each service identified by a different port.
DNS

When Alice sent Bob her request, only the name of the pizza place was known. With that alone, it is not possible to reach the destination. So, Bob entered Luigi's Pizza into a GPS device, and the device returned the coordinates for Luigi's.

DNS stands for Domain Name Service and works similarly to GPS: when you enter the name of, for example, a website, DNS resolves it to server's location. These location coordinates are called an Internet Protocol (IP) address in computer terms. Imagine this IP as the address to your home (street name, house number, postal code, city, and country), but for computer systems.

Let's look at the next task to see how the client-server model applies when browsing a website.

Hypertext Transfer Protocol (Secure), abbreviated as HTTP(S), is a stateless client-server protocol used for the World Wide Web. This means that each request is processed independently, without the server retaining information about previous requests.

Although the protocol itself is stateless, modern websites and web applications implement mechanisms to introduce statefulness at the application level.
For example, when you log into a website using your credentials, the server creates a session identifier (often stored in a cookie or token) that is sent with each subsequent request.
Without these mechanisms, you would need to authenticate again with every new request, because the server would have no memory of your previous login.
HTTP Commands

In the main specifications that define HTTP (also called Request for Comments, or RFC documents), there are 9 core commands. In HTTP lingo, we use the term method instead of command. Below you can see an overview of these methods:

    GET
    POST
    PUT
    DELETE
    PATCH
    HEAD
    OPTIONS
    CONNECT
    TRACE

We will focus on discussing one of the two most common methods used: GET. We will approach this practically by examining the requests a browser sends when you navigate to a website.

Click on the "Start Virtual Machine" button below. This will show a new window in split-screen where we can open a website and inspect a GET request. If the split-screen is not showing, click the blue "Start Split-screen" button at the top of the room.
 
Set up your virtual environment
To successfully complete this room, you'll need to set up your virtual environment. This involves starting the Target Machine, ensuring you're equipped with the necessary tools and access to tackle the challenges ahead.
Target machineMachine info
Status:Off
GET

The GET method is actually pretty straightforward. We can use this method to retrieve a resource from web server. For example, GET https://tryhackme.com/index.php. This request retrieves the TryHackMe website's homepage. You don't need to type in this request yourself. When you open a browser (this is the client) and type "https://tryhackme.com," the browser constructs the message behind the scenes using information you provide and other fields defined in the HTTP specifications. When the web server receives the request, it sends a response that includes a status code (Indicating the type of response) and the requested information. The image below shows the flow of this request.

HTTP request and response flow

Let's have a look at an actual GET request and its response. Navigate to the Virtual Machine that opened next to this screen, then click the Firefox icon on the Desktop. Once the browser is open, the web page http://httpdemo.local:8080 should show. Proceed by pressing F12 or right-clicking in the browser window and selecting "Inspect". This will open the Firefox Developer Tools, which allows us to inspect, debug, and analyze web pages and traffic. Click on the "Network" tab as shown in the image below.

Dev Tools - Network tab

Now reload the page by clicking the circular logo highlighted on the image above (next to where you type the URL). You should see multiple GET requests appearing in the Developer Tools window, under the Network tab. Click on the first entry as shown below to see more information.

Dev tools - get request

In the right-hand panel, we can see more information about our GET request. We won't go into much detail, but let's have a look at some of these fields.

    Scheme: Tells us which protocol was used: HTTP or HTTPS.
    Host: Tells us the name of the host we request resources from.
    Filename: Indicates which file we requested from the host. In our request, this is "/", which actually translates to "index.html".
    Address: Displays the IP address where the website is hosted. In our example, we are hosting the website on the same device. That's why the address 127.0.0.1 is shown.
    Status: This field indicates whether the request was successful. In our example, we received a "200 OK" status, which means that the request was successful.

When a request is sent, we will get a response from the server. The response is divided into two parts: the response header and the response body. The response header contains metadata about the response, while the response body contains the requested content.

We can see this response body by clicking on the "Response" tab when displaying the details of a request. In our example, the response contains the index page of the requested website. The image below shows the content in HTML format.

GET request response body


Hypertext Transfer Protocol (Secure), abbreviated as HTTP(S), is a stateless client-server protocol used for the World Wide Web. This means that each request is processed independently, without the server retaining information about previous requests.

Although the protocol itself is stateless, modern websites and web applications implement mechanisms to introduce statefulness at the application level.
For example, when you log into a website using your credentials, the server creates a session identifier (often stored in a cookie or token) that is sent with each subsequent request.
Without these mechanisms, you would need to authenticate again with every new request, because the server would have no memory of your previous login.
HTTP Commands

In the main specifications that define HTTP (also called Request for Comments, or RFC documents), there are 9 core commands. In HTTP lingo, we use the term method instead of command. Below you can see an overview of these methods:

    GET
    POST
    PUT
    DELETE
    PATCH
    HEAD
    OPTIONS
    CONNECT
    TRACE

We will focus on discussing one of the two most common methods used: GET. We will approach this practically by examining the requests a browser sends when you navigate to a website.

Click on the "Start Virtual Machine" button below. This will show a new window in split-screen where we can open a website and inspect a GET request. If the split-screen is not showing, click the blue "Start Split-screen" button at the top of the room.
 
Set up your virtual environment
To successfully complete this room, you'll need to set up your virtual environment. This involves starting the Target Machine, ensuring you're equipped with the necessary tools and access to tackle the challenges ahead.
Target machineMachine info
Status:Off
GET

The GET method is actually pretty straightforward. We can use this method to retrieve a resource from web server. For example, GET https://tryhackme.com/index.php. This request retrieves the TryHackMe website's homepage. You don't need to type in this request yourself. When you open a browser (this is the client) and type "https://tryhackme.com," the browser constructs the message behind the scenes using information you provide and other fields defined in the HTTP specifications. When the web server receives the request, it sends a response that includes a status code (Indicating the type of response) and the requested information. The image below shows the flow of this request.

HTTP request and response flow

Let's have a look at an actual GET request and its response. Navigate to the Virtual Machine that opened next to this screen, then click the Firefox icon on the Desktop. Once the browser is open, the web page http://httpdemo.local:8080 should show. Proceed by pressing F12 or right-clicking in the browser window and selecting "Inspect". This will open the Firefox Developer Tools, which allows us to inspect, debug, and analyze web pages and traffic. Click on the "Network" tab as shown in the image below.

Dev Tools - Network tab

Now reload the page by clicking the circular logo highlighted on the image above (next to where you type the URL). You should see multiple GET requests appearing in the Developer Tools window, under the Network tab. Click on the first entry as shown below to see more information.

Dev tools - get request

In the right-hand panel, we can see more information about our GET request. We won't go into much detail, but let's have a look at some of these fields.

    Scheme: Tells us which protocol was used: HTTP or HTTPS.
    Host: Tells us the name of the host we request resources from.
    Filename: Indicates which file we requested from the host. In our request, this is "/", which actually translates to "index.html".
    Address: Displays the IP address where the website is hosted. In our example, we are hosting the website on the same device. That's why the address 127.0.0.1 is shown.
    Status: This field indicates whether the request was successful. In our example, we received a "200 OK" status, which means that the request was successful.

When a request is sent, we will get a response from the server. The response is divided into two parts: the response header and the response body. The response header contains metadata about the response, while the response body contains the requested content.

We can see this response body by clicking on the "Response" tab when displaying the details of a request. In our example, the response contains the index page of the requested website. The image below shows the content in HTML format.

Before the concept of virtualization, the rule of thumb in IT was:
“One server = one application.”

In the early days, digital services were run on physical machines, and each machine typically had a single, clear purpose, such as hosting a website or storing data. As businesses added more services, they naturally increased the number of physical servers, and the “one job per box” approach became the standard for building reliable systems.

This meant that if a company wanted to run a website, a database, an email service, and an internal app, they would need separate physical servers for each one. The problems were obvious:

    High cost: Buying multiple physical servers is expensive, not just the hardware, but also electricity, cooling, maintenance, and data center space.
    Low utilization: Most applications don’t use the server’s full capacity. Many servers stayed at 5–20% usage, wasting CPU, memory, and storage resources.
    Slow deployment: Setting up new physical servers could take days or weeks.
    Hard to scale: If an application suddenly needed more resources, you often had to buy yet another server.

In short, companies were paying a lot for hardware that wasn’t being fully utilized.

Illustration of how costly it was to have multiple physical servers for each application.
The Need for Sharing Hardware Safely and Efficiently

Virtualization introduced a new idea:
“What if multiple applications could share the same physical server safely?”

A virtualization layer, called a hypervisor, was introduced to act as a referee between virtual machines and allow each virtual computer to behave independently, like a physical computer.
The Building Analogy

Imagine if one single person lives alone in an entire 10-floor building:

    The person uses only one floor but must maintain the entire building: electricity, cleaning, water, and security.
    Most of the building stays empty and wasted.
    It’s expensive, inefficient, and unnecessary for his needs.

Now imagine dividing the building into separate apartments:

    Each apartment has its own door, walls, kitchen, and privacy.
    Different people can live independently without bothering each other.
    They all share the building’s main structure: electricity, water, and elevators, making it cheaper and more efficient for everyone.

Illustration of building analogy. The first building has multiple empty apartments, indicating the wasted resources. The other building has a building manager, representing the hypervisor and multiple apartments, representing the virtual machines.This is virtualization:

    The building = the physical server
    The apartments = virtual machines
    The tenants = applications or operating systems
    The building manager = the hypervisor (the software that divides the building safely)

Each virtual computer, known as a Virtual Machine (VM), acts as an independent system with its own operating system, apps, and settings, even though they all share the same physical hardware underneath.

Hypervisor (The Building Manager)

A hypervisor is the core technology behind virtualization. It's the software that creates and manages virtual machines.

It is a special piece of software that:

    Divides a physical computer into multiple virtual ones.
    Gives each virtual machine its own share of CPU, memory, and storage.
    Keeps everything isolated and safe.
    Manages the lifecycle of virtual machines (start, stop, pause, clone, delete).

Hypervisors have two main types of implementation, each of which is used for specific scenarios, from home labs to large data centers:

    Type 1 hypervisors run directly on the physical hardware, making them fast, efficient, and ideal for servers and professional environments.
    Type 2 hypervisors run within an existing operating system, making them easier to install and ideal for learning, testing, or small setups.

Below is a table showing which use case is best suited to each hypervisor type. The use cases can run on both hypervisor types, but it's not the best approach given the main objectives of each.
Use Case 	Type 1 	Type 2
Test Malicious Files 	  	X
Production Server 	X 	 
Database Server 	X 	 
Software Testing 	  	X
Kali Linux 	  	X
Data Center 	X 	 

When using virtualization to test malicious files, care should be taken to ensure that the host machine does not become infected by the malware being tested in the guest machine. One approach is to use different operating systems for the guest and host machines, or to isolate the guest machine so that it does not communicate with the host.
Virtual Machines (The Apartments)

A Virtual Machine (VM) is a virtual computer created by the hypervisor.
Even though it’s virtual, it behaves as a real machine:

    It has its own virtual CPU, RAM, storage, and network.
    It can run any operating system (Windows, Linux, etc.).
    It’s completely isolated from other VMs. This means that if one VM breaks, the others continue to work.

You can deploy VMs on your own computer using tools such as Oracle VirtualBox and VMware Workstation. This type of software acts as a type 2 hypervisor and lets you run multiple operating systems, such as Windows, Linux, and macOS.

Since you have learned what a hypervisor and VM are, let's take some examples where you might need them:

    You need to work on a different OS like Kali Linux, but you can't buy another whole system, so you install a hypervisor and run a Kali Linux VM on it.
    You want to test whether a file is malicious, so you set up an isolated virtual machine to protect your main computer from being infected.

Containers (The Rooms Inside the Apartment)

A container is a lightweight, isolated environment that runs a single application and all the necessary components to support it. Instead of bringing a whole separate operating system, a container borrows the core of the existing system by running on the kernel, which is the part of an operating system that communicates with the hardware and manages resources such as memory and running programs.

Because containers share this kernel, they start quickly and use fewer resources than full virtual machines, but it also means they must match the host system’s type. For example, you can’t run a Windows container on a Linux machine.

Containers behave like small, self-contained spaces because:

    They package the application and its dependencies (libraries, tools, versions).
    They share the host’s operating system, so they start almost instantly.
    They remain isolated from each other, so a misbehaving container doesn’t affect the others.
    They can run consistently on any machine, making them perfect for development, testing, and scalable deployments.

The easiest way to deploy containers in a VM is using Docker.
Docker is an open-source software platform that simplifies the process of building, deploying, and running applications using containerization.

The image below illustrates the relationship between Hypervisors, VMs, and containers:

Diagram showing a physical server with a hypervisor, two virtual machines, and two containers running inside one VM.

In summary, VMs provide the “full apartment” with maximum separation and flexibility, while containers offer lightweight “rooms” ideal for scalable, fast-deploying applications.

# cloud

Cloud computing is the perfect solution for the challenges in the application you’ve designed, such as moving your files from a single laptop to online storage that you can access anywhere. Instead of running your app on one computer in one country, the cloud lets you use computing resources over the internet. This makes your application easier to access, more reliable, and ready to grow as more students start using it.
How Servers Evolved to Cloud

Before we start diving into cloud details, it’s helpful to understand that cloud computing did not appear suddenly. It is the result of many years of changes in how servers were used and managed. At each step, businesses looked for ways to reduce costs, use resources more efficiently, and make their applications easier to run and scale. The timeline below shows this evolution, from physical servers to the cloud we use today:
Timeline illustrating the evolution from physical servers to the modern cloud era.
Cloud Benefits and Characteristics

After seeing how applications evolved from physical servers to the cloud, it's becoming clear why cloud computing is so widely used today. The cloud was designed to address common problems, including limited capacity, high costs, and slow growth.
The following benefits and characteristics explain how cloud computing makes applications easier to run, scale, and manage:

    Scalability: Easily scale up or down as your application's needs change.
    On-demand self-service: Create or remove servers and storage instantly, without waiting for hardware.
    Pay only for what you use: You are charged based on usage, not upfront costs.
    Security: Cloud providers protect the infrastructure with strong security measures.
    High availability: Applications keep running even if part of the system fails.
    Global access: Your application can be accessed by users anywhere in the world.

In simple terms, the cloud enables IT resources to be flexible, cost-effective, and easier to manage.
Types of Cloud

The flexibility provided by cloud computing allows applications to be run in different ways, depending on your needs and level of control. Because of this, cloud providers offer multiple models for deploying and using applications, each suited to different scenarios.

Let’s start with the deployment types you can choose for a cloud environment:

    Public Cloud: Used by startups, websites, and global apps because it is affordable, easy to scale, and requires no infrastructure management. Public cloud services are preferable for nearly every use case.
    Private Cloud: Used by banks, healthcare, and government organizations because it offers greater control, customization, and compliance for sensitive data.
    Hybrid Cloud: Used by companies like e-commerce platforms that need to keep sensitive data private while still scaling publicly during high demand.

Just like there are different ways to deploy a cloud environment, there are also different ways to use cloud services. Depending on your experience and needs, you can choose the level of responsibility that fits your application.

Let’s look at the main cloud service models:

    Infrastructure as a Service (IaaS): You rent basic computing resources such as virtual servers, storage, and networking. You are responsible for managing the operating system and your application, while the provider manages the physical hardware.
    Platform as a Service (PaaS): The cloud provider manages the infrastructure and the operating system. You focus on building, deploying, and running your application without worrying about servers.
    Software as a Service (SaaS): You use a complete application over the internet. The provider manages everything, and you access the software through a browser or app, for example, Gmail or Zoom.

Think of cloud service models like different ways of renting a place to live:

An analogy image showing how cloud service models can be compared to renting an apartment.
Major Cloud Vendors

There are several cloud vendors offering a variety of services, but Amazon Web Services (AWS) is the industry leader, with the most extensive offerings and global reach. Other well-known cloud providers include:

    Microsoft Azure: A strong competitor, especially in enterprise and hybrid cloud environments.
    Google Cloud Platform (GCP): Known for powerful data analytics, AI, and machine learning tools.
    Alibaba Cloud: A major player in Asia, offering competitive cloud services globally.
    IBM Cloud: Focuses on hybrid cloud and AI-driven solutions for businesses.
    Oracle Cloud: Focuses on enterprise applications and databases.

Each of these vendors offers a range of services, but AWS remains the most popular due to its vast infrastructure and support for businesses of all sizes.
How Companies Are Using the Cloud

    Netflix runs its entire platform on AWS so it can scale globally, stay online during peak demand, and stream content reliably to millions of users at once.
    Spotify uses the cloud to handle millions of songs and users, scaling quickly when new music or features are released.
    Instagram relies on the cloud to store massive amounts of photos and videos and deliver them fast to users around the world.
    Online stores use the cloud to handle traffic spikes during black friday without buying permanent infrastructure.

These companies use the cloud because it lets them scale easily, reduce costs, stay reliable, and focus on improving their products instead of managing hardware.

Next, you’ll apply these same ideas by deploying your cyber security training app in a simulated cloud environment!


