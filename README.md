# spring-cloud-eureka-server
<!-- PROJECT SHIELDS -->

<!--
*** I'm using markdown "reference style" links for readability.
*** Reference links are enclosed in brackets [ ] instead of parentheses ( ).
*** See the bottom of this document for the declaration of the reference variables
*** for contributors-url, forks-url, etc. This is an optional, concise syntax you may use.
*** https://www.markdownguide.org/basic-syntax/#reference-style-links
-->
[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![LinkedIn][linkedin-shield]][linkedin-url]

<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/yewin-mm/spring-cloud-eureka-server.svg?style=for-the-badge
[contributors-url]: https://github.com/yewin-mm/spring-cloud-eureka-server/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/yewin-mm/spring-cloud-eureka-server.svg?style=for-the-badge
[forks-url]: https://github.com/yewin-mm/spring-cloud-eureka-server/network/members
[stars-shield]: https://img.shields.io/github/stars/yewin-mm/spring-cloud-eureka-server.svg?style=for-the-badge
[stars-url]: https://github.com/yewin-mm/spring-cloud-eureka-server/stargazers
[issues-shield]: https://img.shields.io/github/issues/yewin-mm/spring-cloud-eureka-server.svg?style=for-the-badge
[issues-url]: https://github.com/yewin-mm/spring-cloud-eureka-server/issues
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/in/ye-win-1a33a292/

<h1 align="center">
  Overview
  <img src="https://github.com/yewin-mm/spring-cloud-eureka-server/blob/master/github/template/images/overview/eureka.png" /><br/>
</h1>


# spring-cloud-eureka-server
* This is the Eureka Server for registering other microservices.
* Eureka is for service discovery. Microservices (client) can register in Eureka Server and communicate each other through Eureka server by Service name.
* You can see demo projects which use this Eureka Server in below projects. 
1. [Microservice a](https://github.com/yewin-mm/spring-cloud-eureka-sample-microservice-a)
2. [Microservice b](https://github.com/yewin-mm/spring-cloud-eureka-sample-microservice-b)
3. [Microservice b Instance 2](https://github.com/yewin-mm/spring-cloud-eureka-sample-microservice-b-instance2) (sample instance of Service B)

<!-- TABLE OF CONTENTS -->
## Table of Contents
- [About The Project](#about-the-project)
    - [Built With](#built-with)
- [Getting Started](#getting-started)
    - [Before you begin](#before-you-begin)
    - [Clone Project](#clone-project)
- [Contact Me](#contact)
- [Becoming a Sponsor](#becoming-a-sponsor)
- [Contributing](#Contributing)


<a name="about-the-project"></a>
## ⚡️About The Project
This is Discovery Server for registering microservices.<br>
There are two types of service discovery, <br>
1. Client Side Service Discovery
2. Server Side Service Discovery

Eureka is for Client Side Service Discovery and the main advantages is Microservices can communicate well even without knowing ip address location.<br>
Because normally we need ip:port to call service. (Here, service means microservice) <Br>
* Let's say `Service A (producer)` call to `Service B (consumer)`.
* We need the `location (ip address:port)` of Service B to call from A.
* But here, Eureka Server provide for `registry` and for that case, Services need to register in Eureka Server.
* Eureka know the registered Service location and map as Service Name. <br> And Discovery Server is like database and storing Services location and querying Service location from it's database <br>
So that, Service A can call to Service B with `Service Name` and Eureka Server take that name and route to Service B location.
* So, Service A don't need to know for Service B location and just only need to know the Service Name which registered in Eureka, and it's the one of the advantage of using Service Discovery. <br>
Because we might migrate Service B deployed Server and if we changed that the address (ip) will change also.
* If we used the direct calling way rather than using Service Discovery approach, we need to change the url in Service A when A call to Service B. 
<br> As an example, we need to change url in RestTemplate to call B when B deployed server was changed. 
* But using with Service Discovery, we don't need to change the url as we use Service Name instead of using ip:port address when A call to B. <br> 
Because Eureka can send actual location (ip address) of registered services when one service ask for other services location by Service Name. So, we need only Service Name to call other services.
* Also, Eureka provide for `Load Balancing` collaboration with `Ribbon`. <br>
It's mean, Service B might have many Instances (duplicate service) `for handling thousands requests`.<br>
We use that kind of multi instances approach in Enterprise level applications.
* Using Load Balancer, Service A don't need to add url for each Instance location and Load Balancer will auto route to Instance of Service B. <br>
In this Example, I dropped for Service B and Service B instance. It might have more than one Instance.
* The disadvantages of using Client Side Service Discovery is all Services need to add Eureka in application and <br> 
because if Service don't connect with Eureka, Eureka don't know the service location and other service can't connect to that service through Eureka.
* In modern cloud based service deployment architecture, I `don't recommend` to use `Eureka` and use Server Side Discovery (same logic with Client Side Discovery) not to depend on connecting to Discovery from each Service. <br>
Using Server Side Discovery, every Service don't need to add code logic for Load Balancing and Load Balance will serve as Separately. <br>
eg. Kubernetes orchestrate for each Container and involved Load Balancer as native.

You can pull and test below projects with this `Eureka Server`.
1. [Microservice a](https://github.com/yewin-mm/spring-cloud-eureka-sample-microservice-a)
2. [Microservice b](https://github.com/yewin-mm/spring-cloud-eureka-sample-microservice-b)
3. [Microservice b Instance 2](https://github.com/yewin-mm/spring-cloud-eureka-sample-microservice-b-instance2) (sample instance of Service B)


<a name="built-with"></a>
### 🪓 Built With
This project is built with
* [Java](https://www.oracle.com/java/technologies/javase/javase8-archive-downloads.html)
* [Maven](https://maven.apache.org/download.cgi)

<a name="getting-started"></a>
## 🔥 Getting Started
This project is built with Java and Maven.
So, please make sure all are installed in your machine.

<a name="before-you-begin"></a>
### 🔔 Before you begin
If you are new in Git, GitHub and new in Spring Boot configuration structure, <br>
You should see basic detail instructions first in here [Spring Boot Application Instruction](https://github.com/yewin-mm/spring-boot-app-instruction).

<a name="clone-project"></a>
### 🥡 Clone Project
* Clone the repo
   ```sh
   git clone https://github.com/yewin-mm/spring-cloud-eureka-server.git
   ```

<a name="contact"></a>
## ✉️ Contact Me
Name - Ye Win <br> LinkedIn profile -  [Ye Win](https://www.linkedin.com/in/ye-win-1a33a292/)  <br> Email Address - <a href="mailto:yewin.mmr@gmail.com?">yewin.mmr@gmail.com</a> <br> WhatsApp - [+959252656065](https://wa.me/959252656065?text=Hi) <br> Website - [My Website](https://yewin.me/)

Project Link: [Spring Cloud Eureka Server](https://github.com/yewin-mm/spring-cloud-eureka-server)


<a name="becoming-a-sponsor"></a>
## 🥰 Becoming a Sponsor
If you like any of my projects or if you want to support my work, please kindly consider becoming a sponsor. <br>
It gives me great motivation and I can relentlessly maintain my projects and contribute to the open-source community.

<a href="https://www.buymeacoffee.com/yewin" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" width="150" ></a>


<a name="contributing"></a>
## ⭐ Contributing
Contributions are what make the open source community such an amazing place to be learnt, inspire, and create. Any contributions you make are **greatly appreciated**.
<br>If you want to contribute....
1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/yourname`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeatures'`)
4. Push to the Branch (`git push -u origin feature/yourname`)
5. Open a Pull Request

