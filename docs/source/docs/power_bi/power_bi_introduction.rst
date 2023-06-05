==================================
Power BI Introduction
==================================

.. sectnum::
    

source: `Course Emerick DUVAL EM Lyon <https://mazarsfr-my.sharepoint.com/:p:/g/personal/cao-tri_do_mazars_fr/Ebrg-BTaZERPoSMeGKVoVnQBBcdwsZPcZ-NyQCklgWfvXw?e=kC6Kr4>`_

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


The Q&A feature
-------------------------------------------------------------------

- A very interesting feature of Power BI is called **Q&A** 
    - Questions & Answers
- It allows you to ask questions in **natural language**, and to be offered a set of answers in the form of adapted visuals
- To do this, Power BI analyzes the **words used** in the question, and tries to understand what they refer to in relation to the **model**

Q&A functionality is available on **dashboards** and in **reports** on Power BI Online 


Q&A for dashboard

.. image:: /docs/power_bi/power_bi_introduction/q&a_dashboard.png

Q&A for report

.. image:: /docs/power_bi/power_bi_introduction/q&a_report.png

- For the moment, Q&A only supports questions asked in English.
    - The Spanish language is available in pre-release 


.. image:: /docs/power_bi/power_bi_introduction/q&a_en.png

.. image:: /docs/power_bi/power_bi_introduction/q&a_map.png

- To get the most out of the Q&A feature, make sure you have a **good data model** with **relevant** table, column and measure names
- At the data model level, it is possible to define **synonyms**, to help the Q&A functionality
    - For example: SalesAmount = Revenue, Item = Product, etc.
- The functionality is interactive, and above all very fast, thanks to the storage in memory (almost instantaneous answers)



Summary
--------------------------------------------

.. image:: /docs/power_bi/power_bi_introduction/power_bi_summary.png


Comparison with Microsoft BI Suite
--------------------------------------------

To continue the comparison with the MS BI suite:

.. image:: /docs/power_bi/power_bi_introduction/power_bi_comparison.png


Regular updates
--------------------------------------------

- The first standalone version of Power BI was released in July 2015
- The product has evolved a lot since then, and for good reason: Power BI has a new release every month 
    - Each release includes new features on Power BI Desktop, Power BI service, etc.
- To see the history of the evolutions 



Declination of the Power BI offer
=======================================================================================

Free version of Power BI
---------------------------------------------

- The free version of Power BI is quite limited, but allows you to get a feel for the tool
- The following features are available:
    - 10 GB of storage on the Power BI service
    - Daily data refresh
    - Ability to connect to multiple sources (on-premises / cloud)
    - Publish on the web 
- But in a corporate context, the free version quickly shows its limitations, such as the impossibility to share reports for example


The different offers
---------------------------------------------
- Microsoft offers a set of paid packages for using Power BI in an enterprise context
- The paid offer is broken down as follows:
    - Power BI Pro:
        - Personal license
    - Power BI Premium (per capacity) :
        - Licensing at the corporate level (not at the individual level)
        - Many additional features
    - Power BI Premium Per User (PPU):
        - Almost identical features to Premium by capacity...
        - ... but with per-user billing

Image source: http://docs.microsoft.com 

.. image:: /docs/power_bi/power_bi_introduction/power_bi_licensing.png


Power BI Pro
---------------------------------------------

- In the free version, reports cannot be shared
    - They can only be published on the Power BI service
- The Pro license allows you to **share** published reports with other users who **also** have a Pro license 
    - A Pro user can share his report with a free user...
    - ... but the latter will be denied access when it accesses the URL 
- It therefore seems complicated to use Power BI in a company while remaining in the free version 
- Moreover, the Pro version allows you to go a little further than the free version in terms of capacity and features
- With notably :
    - 10GB of storage per user 
    - With a maximum size per dataset of 1GB
    - Shared datasets
    - Email subscriptions
    - Workspaces
    - Analyze in Excel


Power BI Premium (per capacity)
---------------------------------------------

- ower BI Premium allows you to go even further than the Pro version 
- Whether in terms of functionality, storage, number of users...
- Unlike a Pro license, whose price is based on the number of users, Power BI Premium (per capacity) is a subscription, whose monthly price does not depend on the number of users
- Some benefits of the Power BI Premium subscription:
    - We pay for a capacity dedicated to the month (and not to the person)
        - Published reports can be **consumed** by **all employees** of the company
        - The Pro license is only used to **publish** content
    - Microsoft is responsible for maintaining all services, adapting the hardware to the needs of the company 
    - Datasets up to 400GB 
    - More frequent data refreshes
    - Incremental updates
    - Management of paginated reports
    - Ability to switch to on-premises reports 
        - Power BI Report Server (discussed later)
- The subscription is monthly, and the price is calculated per **node**
    - As an example, a 2 node P1 configuration costs 8400€/month
- If a company has a **very large number of employees**, and wants all Power BI reports to be consumable without restriction, there is a good chance that the company will benefit financially by going with a Premium subscription 
- Microsoft has set up a calculator allowing companies to estimate the cost of a Premium subscription:
- Example 1: 
    - Company with 10,000 employees
        - 5000500 of them generate content (reports/dashboards) and share it
            - They are called "authors".
        - employees regularly consume BI content 
        - The remaining 4500 consume the content only very occasionally
    - In this configuration, only 500 employee "authors" require a Pro license to generate and share content
    - Paying Pro licenses for all "consumers" of the reports would be very expensive: 
        - 5500 Pro licenses : 46 200€ / month
        - 10000 Pro licenses : 84 000€ / month
    - The Power BI Premium version would allow all "consumers" to access BI content at a much more reasonable price

.. image:: /docs/power_bi/power_bi_introduction/power_bi_calculator_exemple1.png

- Example 2:
    - Company with 300 employees
        - 50 of them are authors
        - 125 employees regularly consume BI content 
        - The remaining 125 consume content only very occasionally
    - Only 50 authors, and 250 consumers
        - By paying Pro licenses to each user:
        - 300 x 8,40 = 2 520€ / month
    - With Power BI Premium :
        - The most basic configuration would cost more than 4 200€ / month

.. image:: /docs/power_bi/power_bi_introduction/power_bi_calculator_exemple2.png

- It is therefore necessary to make a precise analysis of the needs, as well as the number of users (authors and consumers) in order to know which offer is the most interesting
- For a detailed Pro vs Premium comparison: https://powerbi.microsoft.com/en-us/pricing/


Power BI Premium Per User (PPU)
---------------------------------------------

- Since April 2021, Microsoft offers a **Premium Per User (PPU)** license
- It allows you to take advantage of almost all the features previously reserved for Premium licenses by capacity, at a much more affordable price (16.90€ / user / month)
- A **PPU** license also includes the features of the Pro license (such as report sharing)


Comparison of offers
---------------------------------------------

.. image:: /docs/power_bi/power_bi_introduction/power_bi_licensing_comparison1.png

.. image:: /docs/power_bi/power_bi_introduction/power_bi_licensing_comparison2.png

.. image:: /docs/power_bi/power_bi_introduction/power_bi_licensing_comparison3.png

.. image:: /docs/power_bi/power_bi_introduction/power_bi_licensing_comparison4.png

.. image:: /docs/power_bi/power_bi_introduction/power_bi_licensing_comparison5.png


Power BI Report Server
=====================================================================================

Presentation: Power BI ... without the cloud
-------------------------------------------------------------

- When we talk about Power BI, we immediately think "cloud".
- However, Microsoft has introduced an on-premises version of Power BI, called Power BI Report Server
- Unlike Power BI Service, which is a cloud-based analytics platform hosted by Microsoft, Power BI Report Server is a product that is installed and configured on a **dedicated enterprise server**

Image source: http://docs.microsoft.com 

.. image:: /docs/power_bi/power_bi_introduction/power_bi_report_server_architecture.png


From SSRS to Power BI Report Server
-------------------------------------------------------------

- Power BI Report Server is a product based on the **SQL Server Reporting Services (SSRS)** framework of the Microsoft BI Suite
    - It is therefore possible to deploy SSRS reports on it 
    - This also means that you can **easily** migrate from an SSRS implementation to Power BI Report Server

.. image:: /docs/power_bi/power_bi_introduction/power_bi_ssrs.png


Operation
-------------------------------------------------------------

- Once Power BI Report Server is installed on an enterprise server, it can be used to publish reports built on Power BI Desktop to the server for sharing
- These reports become accessible to all the company's consumers, **without sending the data outside**
- **Note**: any user wishing to **publish** a report on Report Server must have a Pro licence
- Thus, it is possible to have 10 report authors, but only one of them has a Pro
    - The latter will be able to retrieve the .pbix files of his colleagues and publish them himself
- Power BI Report Server is available under two different licenses:
    - Power BI Premium
    - SQL Server Enterprise (with Software Assurance option)
- The advantage of using the Power BI Premium license is that it allows for a hybrid deployment, combining cloud and local resources
- If the company really does not want to use a cloud solution, it will turn to the SQL Server Enterprise license


An improved SSRS
-------------------------------------------------------------

- The Power BI Report Server portal is an enhanced **SQL Server Reporting Services** portal, allowing you to :
    - Create directories to organize reports
    - Create and integrate key performance indicators (KPI) 
    - View Power BI reports, mobile reports
    - View paged reports (SSRS)
    - Manage shared data sources and datasets 
- On Power BI Report Server, we are basically on a Reporting Services (SSRS)  server, with the ability, in addition, to drop Power BI content inside
- The interface is really the same as the SQL Server Reporting Services portal
- It is very different from the "normal" Power BI interface

Image source: http://docs.microsoft.com 

The interface 
-------------------------------------------------------------

.. image:: /docs/power_bi/power_bi_introduction/power_bi_report_server.png
    :width: 500


Interface comparison
-------------------------------------------------------------

Report Server Portal

.. image:: /docs/power_bi/power_bi_introduction/power_bi_report_server_portal.png
    :width: 500

Power BI Online Portal

.. image:: /docs/power_bi/power_bi_introduction/power_bi_report_server_online_portal.png
    :width: 500


Interface customization
-------------------------------------------------------------

- As with Reporting Services, it is possible to customize the interface of Power BI Report Server 
- This is very interesting for companies that often want to have a portal that "looks like" them
- However, you can't change the layout of the elements... so it's quite limited
- Example of customization

.. image:: /docs/power_bi/power_bi_introduction/power_bi_report_server_customization.png

- This results in:

.. image:: /docs/power_bi/power_bi_introduction/power_bi_report_server_customization_after.png


Limitations of Power BI Report Server
-------------------------------------------------------------
- Life Cycle:
    - 4 updates per year for Report Server, compared to **monthly updates** for the cloud version
    - To benefit from the latest features (which are not necessarily identical to the Cloud version), you must reinstall the server every 3 months 
    - The support for each version (critical updates, security updates) only lasts for one year, i.e. after this period, it is necessary to upgrade to a more recent version, otherwise the solution will be vulnerable 

Image source: http://docs.microsoft.com 

.. image:: /docs/power_bi/power_bi_introduction/power_bi_report_server_update.png
    :width: 400

- Security:
    - Security groups have no effect in Report Server
    - Data access must be secured at the source level
- Dashboards:
    - Unable to create dashboards on the Report Server version
- Power BI Report Server does not support : 
    - The Q&A feature
    - Workspaces
    - The datasets 
