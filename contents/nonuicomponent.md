---
layout: default
---
---
# NON-UI Component
---

Through [UI component]({{ site.globalurl }}/contents/uicomponent.md) menu, we saw how to pick reusable components, how to design them, and how to implement them in component based project (CBD).

In this page, we will talk about more complex but interesting topic: NON-UI Component.

This website a little mentions about the concept of NON-UI component in [Reusable Component](http://) page. We are not talking about graphic user interface anymore. NON-UI Component more fouces on the communication among 
nodes. The nodes could be buniess computers, processing computers (P/C), enterprise resource planning (ERP) system, and other external systems. It does not matter whatever the nodes are, what operating system they are running on, and what programming language they use with. The importance is INTERFACEs, which are a PROTOCAL to be promised between two nodes. The blue area of Figure1 shows the position of NON-UI Component in a system.<br />

#### Figure1. NON-UI components in a system ####

![image]({{ site.globalurl }}/contents/img/reuse6.jpg)

In [POSCO MES Project](http://), to exhange the data between hetrogenous systems, there is used an [enpterprised application intergration (EAI)](http://) product, [U-Cube](http://). There are five level layers: programmable logic controller (PLC), Process Computer (P/C), Business Computer (B/C), Enterprise Resource Planning (ERP), Management Information System (MIS). Each node could have different platforms. Table1 shows five layer in system heirachy structure. Note that there are EAI servers among the nodes.<br />

#### Figure2. NON-UI components in a system ####

![image]({{ site.globalurl }}/contents/img/reuse7.jpg)

EAI server has some benefits in terms of system operation. The first advantage is easy integration and standardzation of interfaces. The second is simply and speedy adding, changing, removing nodes. The history of data is another good point in operating EAI server. Finally, it causes the cutting down the costs.<br />

While EAI of POSCO is socket communication based service, there is web-based non-ui solutions today like [RESTful API](http:// ).<br /> 

Representational state transfer (REST) is also called RESTful web services, which is considered as today most effective way of providing interoperability between existing systems using Internet technonlogies such as Hypertext Transfer Protocol (HTTP).<br />

In [POSCO MES Project](http://), to handle the controller layer, used Oracle MVC framework, which is abstract interfaces defined to control the requests from GUIs such as web pages. To implement the model layer of MVC model, Oracle Business Component for Java (BC4J), which is Oracle's solution to handle multi-tier, database applications from reusable business components. 

But, this website will use [RESTful API](http:// ) with the [NodeJS](http://) and [Angular](http://) Component Solution to introduce the concepts of CBD as well as UI Reusable Component. <br />
Also, we need to change the system diagram to fit WEB service. However, the philosophy of component-oriented development methodology in enterprise environments will be followed.<br />

![image]({{ site.globalurl }}/contents/img/reuse8.jpg)

What is the next step to understand NON-UI componet more?

Here gives a business situation to process the project using NON-UI components.

> A company's Production department requires application automatically to receive and transact the information of product generated from processing computers. Also, Sales department needs the appliaton to handle therir sales result which is requested by desktop or notebook, mobile phone, and tarblet. All result of product and sales must be automatically delivered to ERP system. Production department system has Window Operate System, Sales Deapartment system has Linux Operate System, and ERP system is Unix sytem. What is the solution? <br />

In this project, the receivers and senders are different operator systems and devices. To develop the system consistently and integrately, we need only one solution, and here we will use RESTful API. All requirements are like Figuer4. Interface Diagram.

#### Figure4. Interface Diagram ####
![image]({{ site.globalurl }}/contents/img/reuse9.jpg)

Well, what is the first step? To communicate between heterogeneous systems, we have to decide protocol specification called 'INTERFACE'. Note that receiver has to make the interface layout. First, assume that the receiver is ERP system, and sender is manufaturing system. So, manufacturing system sends the product result data to ERP system through interface. Second, when ERP system receives data, it becomes a sender, and send the answer-back to manufacturing system through interface.<br />
Table1 shows the product result interface layout, and Table2 shows the answer-back layout.<br />

### Table1. product result interface ###

|Field name     |Type       |Number          |Decimal |Definition            |Data Example        | 
|---------------|-----------|----------------|--------|----------------------|--------------------|
|IFName         |String     |20              |        |interface name        |ABC000001           |
|SendType       |String     |10              |        |send  type            |PUT/PUSU/GET/DELETE |
|SendPg         |String     |20              |        |sender program name   |MBL000001           |
|SendDt         |Date       |14              |        |sender date           |20161020123141      |
|SendUrl        |String     |100             |        |sender host name      |erp1.server.ca:8080 |    
|SendServer     |String     |20              |        |sender host url       |MESServer01         |
|ReceivePgm     |String     |20              |        |receiver program      |ABC000001           |
|ReceiveDt      |Date       |14              |        |receiver date         |20161020123149      |
|ReceiveUrl     |String     |100             |        |receiver host url     |mes1.mbl.ca:8080    |
|ReceiveServer  |String     |20              |        |receiver host name    |ERPServer01         |
|ProdID         |String     |20              |        |product id            |STL345890           |
|ProdNm         |String     |50              |        |product name          |Stainless steel v01 |
|ProductDt      |Date       |14              |        |product date          |20161020123109      |
|ProdAmt        |Number     |9               |2       |product amount        |6500                |
|ProdShift      |String     |1               |        |product work shift    |A                   |
|ProdFactory    |Number     |6               |        |product factory       |FAC004              |

### Table2. answer-back interface ###

|Field name     |Type       |Number          |Decimal |Definition            |Data Example        | 
|---------------|-----------|----------------|--------|----------------------|--------------------|
|IFName         |String     |20              |        |interface name        |MBL000009           |
|SendType       |String     |10              |        |send  type            |PUT/PUSU/GET/DELETE |
|SendPg         |String     |20              |        |sender program name   |ABC000001           |
|SendDt         |Date       |14              |        |sender date           |20161020123155      |
|SendUrl        |String     |100             |        |sender host name      |erp1.server.ca:8080 |    
|SendServer     |String     |20              |        |sender host url       |ERPServer01         |
|ReceivePgm     |String     |20              |        |receiver program      |MBL000009           |
|ReceiveDt      |Date       |14              |        |receiver date         |20161020123149      |
|ReceiveUrl     |String     |100             |        |receiver host url     |mes1.mbl.ca:8080    |
|ReceiveServer  |String     |20              |        |receiver host name    |MESServer01         |
|SuccessFlag    |String     |1               |        |Success Flag          |'Y' or 'N'          |

Manufacturing server will send message to ERP server according to the interface of table1. In this time, url will be http://erp1.server.ca:8080/ABC000001. When the program ABC000001 of ERP server receives the data message, and if it has no problem to transact, the program returns the answer-back message (ANS-BACK) to manufacturing server for notice the success or fail.<br />

Two demo pages shows the send/receive message simmulation between Manufacturing system and ERP.

Each system is implemented with NodeJS-based application, and using simmulator, manufacturing system send and receive data message in real-time. We can see to increase the number of traffic on the screen.


In fact, in POSCO system, there are recorded nearly traffic number of 900,000 per day, and total about 5,500,000,000 bytes are used for sending and receiving message.


In [Advanced]({{ site.globalurl }}/contents/advance) menu, we can more deeply dive into the component ocean.


