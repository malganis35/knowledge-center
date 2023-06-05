==================================
Power BI Introduction
==================================

.. sectnum::
    

source: https://mazarsfr-my.sharepoint.com/:p:/g/personal/cao-tri_do_mazars_fr/Ebrg-BTaZERPoSMeGKVoVnQBBcdwsZPcZ-NyQCklgWfvXw?e=kC6Kr4

How Power BI was born ?
====================================================================

The importance of Excel
--------------------------------------------------------------------

- Excel is the most widely used data manipulation tool today
- It is indeed the first application one thinks of when they need to analyze data
- Its "Pivot Table" functionality is very popular with analysts

Excel and its add-ins
--------------------------------------------------------------------

- Microsoft had the idea to allow Excel users to go **further**, whether in terms of data processing or visualization

- To do this, Microsoft has incorporated new features to Excel, in the form of add-in :
    - Power Query
    - Power Pivot
    - Power View
    - Power Map

- The incorporation of these add-ins into Excel has given more power to the end users
- Indeed, users have become capable of doing things that were previously reserved for more "technical" people
- The goal is of course to make these tasks as accessible as possible to anyone


Power Query
--------------------------------------------------------------------

- Power Query is a tool that allows users to **connect**, from Excel, to different **data sources**, thanks to a **multitude of native connectors**
- You can also process the data (clean, filter, enrich, calculate) through an **intuitive graphical interface**
- The **query language "M"** allows to go further in the transformations if necessary
- Power Query is accessible from the "Data" tab, in the "Retrieve and transform" group

.. image:: /docs/power_bi/power_bi_introduction/power_query_excel.png


Power Pivot
--------------------------------------------------------------------

- Power Pivot is a tool for manipulating very, very **large amounts of data** with Excel 
    - Initially, Excel is limited to a little over a million rows
- We can also:
    - Create **relationships** between different tables
    - Create **measures** according to specific calculation rules, **KPIs**
    - Establish **hierarchies** within tables
- For the record, Microsoft bought a database using an "in memory" technology called **Vertipaq**
- This later led to the creation of **Power Pivot**, the first Microsoft tool to use this database
- The Vertipaq database was then adapted to several applications, such as **tabular cubes** or **Power BI**
    - This is why there are **many similarities** between Power Pivot, Power BI and tabular SSAS cubes
- With Power Pivot, we create a **data model in memory**
    - It is a kind of cube integrated in the Excel workbook
- The data can then be analyzed using pivot tables connected to this data model
    - Analysts can then proceed with "ad-hoc" reporting
- Power Pivot was introduced with Excel 2010, and natively integrated in Excel since its 2013 version, but it must be activated

.. image:: /docs/power_bi/power_bi_introduction/power_pivot_excel.png

Power Maps
--------------------------------------------------------------------

- Power Map is a **3D visualization** tool, allowing to represent data on **geographic maps**
- It is also possible to set up **animated presentations**
- Power Map was introduced with Excel 2013 (download), then natively integrated and renamed "**3D Maps**" since Excel 2016

.. image:: /docs/power_bi/power_bi_introduction/power_maps_excel.png


Power View
--------------------------------------------------------------------

- Power View is a tool for **visualizing** data by generating **graphs, charts, maps and interactive visuals**
- These visuals are based on data stored in Excel files, whether they are pivot tables or tables stored in the Power Pivot model
- Users can create all kinds of reports, using elements such as tables, 2D/3D graphics, text, etc.
- The reports created are directly linked to the data, and therefore reflect the most recently loaded data in the file 
- The report objects are **interactive**
    - A simple click on a value of a visual will allow you to perform a filter on this value on all other visuals of the report

.. image:: /docs/power_bi/power_bi_introduction/power_view_excel.png


Excel add-ins in brief
--------------------------------------------------------------------

In sum:
    - Power Pivot allows you to create a cube in a few steps, without having to deal with the very daunting side of SSAS
    - Power Query allows you to retrieve data from different sources to feed the Power Pivot cube
    - Power View allows you to visualize data in a different way, in the form of a dashboard/report. Easy to use, and can be integrated with Excel or Sharepoint

A parallel can be drawn between Microsoft's "classic" BI tools and Excel's BI add-ins:

.. image:: /docs/power_bi/power_bi_introduction/microsoft_bi_suite.png


What is Power BI?
====================================================================

A range of products and services
-------------------------------------------------------------------
- Power BI is a suite of products and services:
    - Power BI Desktop
    - Desktop application 
    - Allows you to import data, transform them, create reports ...
- Power BI Online
    - Software as a Service (SaaS)
    - The reports are deployed there
    - Ability to create dashboards
- Power BI Mobile
    - Applications on smartphones and tablets
    - Allows you to view reports and dashboards 

.. image:: /docs/power_bi/power_bi_introduction/power_bi_ecosystem.png

Image source: http://docs.microsoft.com 


Power BI Desktop
-------------------------------------------------------------------
- Power BI Desktop is an application that runs on **Windows**, totally detached and independent from Excel
- It includes the functionalities of **Power Query, Power Pivot, Power View and Power Map**, under a different but very intuitive interface
- Power BI Desktop allows you to **combine** the possibilities offered by all these add-ins into a single application **purely dedicated to BI**
- To summarize, with Power BI Desktop, you can:
    - Retrieve data from various sources
    - Transform this data to clean and consolidate it
    - Set up a data model that will store this data
    - Edit the links between the tables of the model
    - Create measures in the model
    - Design reports based on the data model
    - Implement data security rules
- Power BI Desktop generates Power BI projects in .pbix format
- These files contain all the work done:
    - The data model
    - Transformations applied to data
    - Data (compressed)
    - Visualizations
- These reports can be published on the Power BI Online service to be shared with the rest of the company


Power BI Online
-------------------------------------------------------------------
- Power BI Online is a set of cloud-based services
    - It is also called "Power BI Service".
    - It publishes all the work that has been done on Power BI Desktop (data, transformations, reports, etc.)
- In Power BI Online, you can perform other tasks, such as:
    - Create dashboards
    - Share content between users
    - Create alerts
    - Manage data access
    - Refresh datasets used by reports
    - etc.
- It is possible to **design reports** directly on the **Power BI Online** service
- This is very useful for users who want to create new reports from existing datasets, without having to bother installing the Power BI Desktop application
- Note that the report creation interface on Power BI Online is **almost** identical to that of Power BI Desktop 
    - There are some minor limitations compared to PBI Desktop


Power BI Mobile
-------------------------------------------------------------------
- With Power BI Mobile, users can freely consume their reports from any device: laptop, smartphone, tablet...
- There is also an "offline" functionality to allow the consumption of reports even without being connected to any network

.. image:: /docs/power_bi/power_bi_introduction/power_bi_mobile.png

Image source: http://docs.microsoft.com 


Power BI additional components
-------------------------------------------------------------------

- Power BI Desktop, Power BI Online and Power BI Mobile are the foundation of the Power BI suite
- Other elements are added to complete this suite, including:
    - Data gateways (Power BI Gateway)
    - Power BI Embedded
    - Custom visuals (AppSource)
    - Power BI Report Server
- Power BI Gateways
    - Gateways that allow Power BI Service to connect to data sources that are not in the cloud (on-premises) 
    - The data gateway is installed on the server that has the data to feed the deployed reports
- Power BI Embedded
    - Use of reports / dashboards in third party applications
    - Same principle as when you want to integrate a Youtube video in a web page or an application (generated code, to be integrated in the application)
- Customized visuals from the AppSource
    - A "marketplace" with a whole collection of complementary visuals, developed by Microsoft and third-party developer partners

.. image:: /docs/power_bi/power_bi_introduction/power_bi_app_store.png

- Power BI Report Server 
    - A version of Power BI that uses a local report server 
    - It is an alternative for companies who do not wish to use the cloud
    - Please note that many features of Power BI features are not available in this "local" version. 

.. image:: /docs/power_bi/power_bi_introduction/power_bi_report_server.png