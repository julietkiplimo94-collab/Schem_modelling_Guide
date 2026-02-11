
#What is Power BI?#

Power BI is a business Intelligence tool built by Microsoft that turns raw data into interactive insights.
It has a very user-friendly interface that allows you to create a beautiful, comprehensive dashboard easily. 

Power BI gained its popularity because of its versatility; it allows you to get data from numerous sources, Ms Excel, Csv files, etc, clean it, analyze it, and then create visuals that are easy to understand.

###Types of Power BI applications:###

1. Power BI Desktop: Is a free Windows application for creating reports and dashboards. You connect your data, clean it, build visualizations, and save your reports.

2. Power BI Service (Cloud): This is the cloud-based version of Power BI. Once you’ve created your reports in Power BI Desktop, you can publish them to Power BI Service for sharing, collaboration, and real-time updates.

3. Power BI Mobile: This is the mobile app that allows you to access your Power BI reports on the go, whether you’re using an iPhone or Android device.

4. Power BI Report Server: Power BI Report Server lets you host reports on your own servers securely.

###How to Install Desktop Version:###

1. Download and Install:

Go to the Microsoft store on your PC or the official Power BI website and install Power BI Desktop.


2. Open Power BI Desktop:

 After installation, launch Power BI Desktop. 

 Click 'Blank report' to start a new project.


![Power Bi](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/pldu86dsef0n4x67hzph.png)

3. Load Data:

Step 1: Click the Get Data option in the Ribbon (as shown below), then pick your file type.

Select your file; it will have the following extension(.xlsx file) if it's an Excel file and .csv if it's a CSV file. 

You will then see a pop-up window with a preview of your data >> click Load.

![Power bI](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/n8oygjq34yvykpku26ha.jpeg)


##SCHEMAS & DATA MODELLING IN POWER BI.##

**What is Data Modelling?**


This refers to the process of organizing and structuring data to create meaningful relationships between different tables, which allows efficient data analysis and visualization.

Major Concepts in Data Modelling:

***Fact table:*** A fact table is the central table in a star schema. It contains the quantitative data (facts) you want to analyze. These facts should be numerical and measurable.

 - Tables can be imported *(static data)* or connected to live data sources *(dynamic data)*.

**Relationships:** Relationships define how tables interact with one another in the model.

 - They are established based on keys:

    - **Primary Key:** A unique identifier in one table.
    - **Foreign Key:** A column in another table that references the primary key.

**Cardinality:** Refers to the nature of the relationship between tables:

*One-to-One (1:1):* Each row in Table A matches exactly one row in Table B.

 *One-to-Many (1:M):* A single row in Table A matches multiple rows in Table B.

 *Many-to-Many (M:M):* Multiple rows in Table A match multiple rows in Table B.

***Dimensional table:***  This is a core data warehouse component in star/snowflake schemas that stores descriptive, textual attributes (e.g., product names, customer locations, time periods) for analyzing business metrics stored in fact tables. 

***Flat table;*** This is one table that consolidates all data into one wide table, removing the need for relationships by denormalizing data into a single, spreadsheet-like structure. 

###Star Schema:###

This is a centralized data modeling technique with a central fact table containing numbers/measures, e.g., sales,  connected to surrounding dimension tables (providing context like product, customer), forming a star shape for faster, simpler analysis and reporting by logically grouping data.


![Star Schema](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/jvx1hcrbrb0axr0d9qbr.jpg)


 **Features of a star schema:**

- A central fact table connects to dimension tables directly, forming a star shape.

- Simple to design and maintain, with denormalized, flat dimension tables.
Generally faster for query execution due to fewer joins.

- Used and preferred for BI tools like Power BI and Tableau, and when fast read performance is the priority.

*Disadvantage: Higher storage consumption and data redundancy.*

###A snowflake schema:###

Is a normalized data modeling technique for data warehouses where a central fact table connects to dimension tables, which are further broken down into sub-dimension tables to eliminate data redundancy.



![Snowflake](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/gs2j28baw4jqzoucypav.png)




**Features of  a snowflake schema:**

- A central fact table connects to normalized dimension tables, which are further broken down into sub-dimension tables, creating a snowflake-like structure.

- Used for Higher complexity data modelling, requiring more normalization.

- Potentially slower due to the need for more {join} operations, 
Used in Complex systems with complex hierarchies, or when saving storage space is critical.

*Disadvantages: Harder to navigate for ad-hoc reporting; increased complexity in updates.*

***Key Differences between Star schema and Snowflake schema:***

Star Schemas  |  Snowflake Schemas
------------- |------------------------
1. Denormalized  | Denormalized
2. Uses fewer Joins  |  Uses more joins
3. Uses more Storage space | Uses less Storage space
4. Star is better for fast analysis | Snowflake is better for data                           integrity
 

##DATA MODELLING:##

We have learned all the necessary concepts in data modelling, so now let’s get to building our first model!

***Step 1: Loading Data into Power BI.***

Import data from your preferred source (Excel, databases, web APIs, etc.)

  ***Step 1. (a) Clean and prepare your data with Use Power Query:***

Load Power Query by clicking 'Transform data' under the table view:

![Power Query](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/asiklw0vr4t6un4z2hu2.png)

Transform your data, ensuring it has no blanks, duplicates, or wrongly formatted data types.

***Step 2: Create a cardinal relationship between your tables:***

- Go to the Model View in the Power BI Desktop ribbon.
- Drag and drop fields to connect tables, or use the Manage Relationships feature.
- Define the type of relationship (e.g., 1:M) and enforce cross-filter direction.

***Step 3: Build the Model:***

First, design a star schema by identifying fact and dimension tables.
Then eliminate circular relationships (one table depending on another, hence creating loops).

>Use a surrogate key (unique ID) when natural keys are not consistent.

***Step 4: Add Calculated Columns and Measures:***

Create calculated columns or measures using DAX (Data Analysis Expressions) for derived insights.

***Step 5: Optimize the Model:***

Start by removing unnecessary columns and rows. Then Use Measures to summarize tables or aggregations to reduce data size.
Define hierarchies (e.g., Year > Quarter > Month > Day) for faster analysis.

***Features of Power BI Data Modeling.*** 

1. Model View:
This is a visual representation of the data model, showing tables and Relationships.

2. Cross-Filter Direction:
This determines how filters flow between related tables:

- Single: Filters flow in one direction.
- Both: Filters flow in both directions, useful for complex models.

3. Role-Playing Dimensions:
This is a single dimension table used in multiple roles (e.g., a Date table for OrderDate, Delivery Date).

4. Calculated Tables:
• Tables created using DAX for specific analysis needs, such as grouping or summarizing data.

5. Hierarchies:
• Organize columns into a hierarchy for easier drill-down analysis in reports.(e.g., Year > Month > Day).

**IMPORTANCE OF MODELLING IN DATA ANALYSIS:**

1. Improves Query Performance: 
Well-modeled data (e.g., star schema) uses simple joins, allowing Business Intelligence tools to retrieve data faster and more efficiently than when dealing with unorganized data

2. Data Integrity & Consistency: 
By defining clear relationships(primary/foreign keys), the model prevents data anomalies, missing values, and redundancies.

3. Scalability: 
A well-developed model grows with the business. It allows for the addition of new data sources or increased data volumes without affecting the data or performance of the model.

4. Improved Decision-Making: 
Accurate models allow Stakeholders to confidently make data-driven decisions without questioning the underlying data quality.

5. Single Source of Truth: 
A good data model standardises definitions across the organisation (e.g., how "revenue" is calculated), ensuring that finance, sales, and marketing all report the same figures.

>Without proper modeling, organizations often face slow, buggy reports, conflicting numbers, and high maintenance costs. 

*Reference: Data analysis made easy by Ezekiel Akele.*
