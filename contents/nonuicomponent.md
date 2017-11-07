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

Well, what is the first step? To communicate between heterogeneous systems, we have to decide protocol specification called 'INTERFACE'. Note that receiver has to make the interface layout. Table1 











> When a project starts, components should be classified in the view of reusability and be checked the adaptibility through developping and applying the prototypes. In the next phase, it should be defined and analyzed in the business and system perspective for developping the components. In the stage of implementation, such deliverables will be more clearly designed and implemented as components.<br />

We will follow the above process. <br />
The fisrt step is displaying all functionalities to achive A company's requirements.

### Table1. classfication of functionality ###

|Function                      |Production Department|Sales Department|ERP Team|
|------------------------------|---------------------|----------------|--------|
|Working Shift Group           |Need                 |Need            |Need    |
|Production amount by Shift    |Need                 |Need            |Need    |
|Total Stock                   |Need                 |Need            |Need    |
|Price                         |Not Need             |Need            |Need    |
|Discount rate                 |Not Need             |Need            |Need    |

As you can see in Table1, 'Working Shift Group', 'Production amount by Shift', and 'Total Stock' could be used all dempartments. So, they will subject to candidate of UI component. Also, Price and Discount rate will subject to UI component for Sales Department and ERP Team.<br />

So, we will make each page like these: ProductOutputQuery.html, SalesProductsQuery.html, BillOfMaterialQuery.html<br />

ProductOutputQuery.html will include Logo, Titile, Working Shift Group Lov component, Production amount by Shift output, Total Stock output, and Current Products results tables including Plate Steel, Specail Steel, Stainless Steel, Mn Steel<br />

SalesProductsQuery.html will include Logo, Titile, product name, Price, Discount rate, and Current Products Order tables including customer, due-date, amount, detination, comments<br />

BillOfMaterialQuery.html will include Logo, Titile, Working Shift Group Lov component, Production amount by Shift output, Total Stock output, and original price by date tables with product name, result amount, sales amount, suplus amount<br />

Now, we finished all preparation to create applications.<br />
In Production Department project, we will create some components: ShowLogoACompany.js, ShowTitle.js, ShowReactProductResultByShift.js, ShowTableReactCurrentResultByProductionByShift.js<br />

In Sales Department project, we will create only ShowTableSalesMonitorByProducttionaByShift.js.<br />

Lastly, ERP Team can just use the reusable compnents from two projects.<br />

You need to note that in Sales Department project, they do not need to develop the ShowLogoACompany.js, ShowTitle.js, ShowReactProductResultByShift.js. They can use the existing components form the previous project. Also, ERP Team do not involve new project. They can use all components which are needed to create new pages.<br />

In this example, we assumed to make only one page for each department. However, what if there are needed a hundred pages? We can understand A company can superisingly cut down their budget for new projects and software maintenances.<br />

To demonstrate this example, I create the sample reusable components with [REACT](http://)<br /> 
For this case, each source codes will be like these: <br />

Figure2 shows where each pages will be located in the entire system.<br />

In the next step, we are talking about the [NON-UI Component](http://).




