---
layout: default
---
---
# UI Component
---

There is a little introduction about UI component in [Reusable Component](http://) page of this website. UI Component provides the functionalities to produce the graphic user interfaces (GUIs). The blue area of Figure1 shows the position of UI Component in a system.<br />

![image]({{ site.globalurl }}/contents/img/reuse4.jpg)

In the view layer of MVC model, the components will be used to display a logo, list of values (LOV), tables, scrolls and so on using JAVA script, Tag Library, Applet, NodeJS, Angular and so on. Also, in Controller layer of MVC model, the components can control and transact the requested data from GUIs. <br />

In [POSCO MES Project](http://), to implement the view layer, JAVA script, Tag Library, and Applet was used, and to handle the controller layer, used Oracle MVC framework, which is abstract interfaces defined to control the requests from GUIs such as web pages. To implement the model layer of MVC model, Oracle Business Component for Java (BC4J), which is Oracle's solution to handle multi-tier, database applications from reusable business components. <br />

POSCO has been applying strong security policies to protect their asset of IT solution such as deliverables, source codes. Therefore, this website can not show the real source codes or running system. <br />

Instead, this website will use the [REACT](http://) and [Angular](http://) Component Solution to introduce the concepts of CBD as well as UI Reusable Component. <br />
As well we can change the system diagram to fit the [REACT](http://) and [Angular](http://). However, the philosophy of the MVC model will be followed. So, there seems no big problem to understand the concept of component-oriented development methodology in enterprise environments. <br />

![image]({{ site.globalurl }}/contents/img/reuse5.jpg)

What is the next step to understand UI componet more?

Here gives a business situation to process the project using UI components.

> A company's Production department requires web pages to query and transact the output of product. After a few months later, Sales department will involve another project to develop the sales inquiry pages to connect with the product result. ERP team wants to monitor the sales and product rate on a daily base. Sales team and ERP team want to reduce their project budget through using Production department's system modules. What is the solution? <br />

As you know, the answer is applying a component based development methodology to the project.
Then, what is the first step? Do you remember we alreay mentioned the procedure for applying the reuable components to system in a project?

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


In the next step, we are talking about the [NON-UI component]({{ site.globalurl }}/contents/nonuicomponent.md).

























