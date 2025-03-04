# Optimizing Customer Insights: A Comprehensive Sales Audit
#### TripleTen Capstone Project
As a Junior Analyst with TTWC, I participated in a comprehensive sales audit for AtliQ Hardware, a leading computer hardware producer in India, aiming to enhance their data automation and provide actionable business insights. My primary focus was on customer analysis, where I employed SQL for data extraction, grouping, table creation, and running queries to analyze customer behavior metrics from an SQLite database. Additionally, I used Python for data cleaning and exploratory analysis, and Tableau for creating dynamic visualizations. By segmenting customer data based on geographic and behavioral metrics, I provided AtliQ with detailed insights into customer habits, product performance, and market trends, helping them make more effective sales and marketing strategies. This project showcased my proficiency in data manipulation, analytical thinking, and the ability to translate complex data into strategic business decisions.
<br></br>

## Table of Contents:
[Tableau Dashboard](https://public.tableau.com/app/profile/julynda.vaughn/viz/AtliQCustomerAnalysisv6_2/AtliQCustomerDemographics)

[Project Visualizations](https://github.com/julyndav/SQL/tree/main/AtliQ%20Hardware/Analysis%20Images)

[AtliQ Decomposition Plan](https://github.com/julyndav/SQL/blob/main/AtliQ%20Hardware/AtliQ%20Decomposition%20Plan%20Project.pdf)

[Jupyter Notebook](https://github.com/julyndav/SQL/blob/main/AtliQ%20Hardware/AtliQ%20Customer%20Analysis%20Final.ipynb)
<br></br>

### Skills Demostrated:
<ul>
<li>SQL (for data cleaning, queries, table creation)</li>
<li>Panda Libraries (for data visualizations)</li>
<li>Dashboard Design (Tableau)</li>
<li>Extract and Loading Data</li>
</ul>
<br></br>


## Required Project Libraries:
| Library |Purpose |
| --- | --- |
| SQLite3 | Allows connection to external database files |
| Pandas| Main library for working with data |
| Numpy | Used for numerical operations on large quantities of data |
| Seaborn | Python visualization library based on matplotlib |
| Matplotlib | Python visualization library |
| DateTime | Manipulating data in to date/time formats |
| Pathlib | To transfer dataframes into csv files for export and use with Tableau |
| ipython-sql | Use sql within the Jupyter environment |

<br></br>


# AtliQ Hardware Project Overview:
## Description of Data: 
This is an overview of the database tables used for Analysis. Note that since this analysis is customer focused, some of the tables will not be used. 
#### To help with the intial analysis we used software for get a visual of the dataset tables and how they relate to each other.
![Table Relationships](https://github.com/julyndav/SQL/blob/main/AtliQ%20Hardware/readmepics/Database%20flowchart.png)

<br></br>

## Analysis Steps:
| Step |Description |
| --- | --- |
| 1 | Create project decomposition plan |
| 2 | Connect to SQLite database |
| 3 | Import libraries |
| 4 | Upload and review the data |
| 5 | Geographic segmentation |
| 6 | Customer segmentation and analysis |
| 7 | Sales Analysis |
| 8 | Customer to Products Analysis |
| 9 | Cohort Analysis along with Customer Churn Rate |
| 10 | Project Conclusion(s) |
| 11 | Project citation of sources |

<br></br>

## AtliQ Project Analysis Plan 

The TTWC team assigned to AtliQ will conduct the necessary research, and create informative dashboards that AtliQ will be able to use later. Certain sections of the TTWC team will select one of the three above areas to focus on. My team is responsible for Customer Analysis. 

During the Customer Analysis, customer segmentation will be used to understand the purchasers and gain an understanding on more effective sales, marketing, and personalization strategies. Each segment can answer a myriad of questions that the company may have. To further help with the segmentation, we will connect the customers to the products and sales data to give a better overview of the customer focused analysis.  

To really embrace the real-world feel and to set good habits, the decomposition plan was created as if I was an actual Analyst for TTWC.  Below is a snippet of the decomposition plan, you can see the entire plan from the link in the Table of Contents. 

![Decomposition Plan](https://github.com/julyndav/SQL/blob/main/AtliQ%20Hardware/readmepics/decomp.png)
<br>
<br></br>


The goal is to segment the customer data on various metrics and create an actionable dashboard. This will allow AtliQ to gain a better understanding of their customers' habits and possibly give insight on new, potential markets. 

<p></p>
<i> *Note: TTWC is a fictional company. This entire analysis was a capstone project to simulate real-world work environment.</i>
<br></br>


## SQLite required to connect to the supplied database:
![Database Connection](https://github.com/julyndav/SQL/blob/main/AtliQ%20Hardware/readmepics/dbase%20connection.png)
<br></br>

## Now to import the libraries that will be used for the analysis:
![Import Libraries](https://github.com/julyndav/SQL/blob/main/AtliQ%20Hardware/readmepics/libraries.png)
<br></br>


## Brief Analysis Overview:
#### Geographic Segmentation
This section will focus on geographical analysis of the data from a customer standpoint.

Some good questions to ask are:<li>
How many customers are there in total<li>
What countries contain AtliQ customers?<br></br>
<p></p>

![Customer_per_Country](https://github.com/julyndav/SQL/blob/main/AtliQ%20Hardware/readmepics/Cust_per_country.png)

Showing the number of customers per country. We are only seeing the first 5 countries thanks to the '.head()' function.
<br></br>

![Number_Customers](https://github.com/julyndav/SQL/blob/main/AtliQ%20Hardware/Analysis%20Images/Customers%20per%20Region.jpg)
#### Regions:

1. EU - European Union
2. APAC - Asian Pacifc
3. NA - North America
4. LATAM - Lating America


<br></br>

## Customer to Product Analysis
In order to create a full and detailed customers table that will be exported to tableau where customer segmentation can be visualized better, SQL was used to combine the requried data from selected tables. The visualizations in this section are to get a better idea of what to focus on in the main visualization environment and to explore the data with the newly created table. 
<br></br>

![Combining_tables](https://github.com/julyndav/SQL/blob/main/AtliQ%20Hardware/readmepics/sql_combine_tables.png)
<i> SQL used to combine tables</i>
<br></br>

![Table_Preview](https://github.com/julyndav/SQL/blob/main/AtliQ%20Hardware/readmepics/Snippet_Comb_Table.png)
<i> Preview of combined table.</i>
<br></br>

Now that the tables have been combined into a 'working' table, it was time to see what the product volumne as it compared to country. The newly created 'atliq_cust_tbl.' contains a row for customer product total so it will be used to determine product volumne per country.

![Prod_vs_Country](https://github.com/julyndav/SQL/blob/main/AtliQ%20Hardware/Analysis%20Images/total_by_country.png)
<b>Insight:</b> India, USA and South Korea have the highest customer product totals. It makes sense for India to be at the top since AtliQ is an India based business. The bar chart has grouped all of the customers for that country; the lines in the bars separate each business.
<br></br>

## Churn Rate
To determine customer turnover and to see if there were any concerning customer trends, Python was used to find the churn rate. 

![Churn_Rate](https://github.com/julyndav/SQL/blob/main/AtliQ%20Hardware/readmepics/churn_rate.png)
Insight: There seems to be a cycle in the plot where there is a period of a four month increase in purchases by the customer. This increase goes from September to December. It's extremly evident in 2021. More information will need to be gathered to see if the lockdowns during the recent pandemic is the reason for the sudden spike in customer activity.

## Customer Purchasing Trends?

![Avg_trend](https://github.com/julyndav/SQL/blob/main/AtliQ%20Hardware/readmepics/avg_purchase_trend.png)
<b>Insight:</b> There seems to be a cycle in the plot where there is a period of a four month increase in purchases by the customer. This increase goes from September to December. It's extremly evident in 2021. More information will need to be gathered to see if the lockdowns during the recent pandemic is the reason for the sudden spike in customer activity.
<br></br>
<br></br>

## Project Conclusion(s):

### Analysis Conclusion:
AtliQ appears to have a dedicated customer base. There were no significant change in customer numbers that grossley affected purchase quantities. The current discount rates between 22-26% seems to hold onto the customers.

The one area that may need further research is the 2021-22 time frame to see how the pandemic, lockdown and supply issues impacted the numbers. 2021 saw a drastic increase in cusomter purchases. One insight into this may have been the strict lockdowns imposed within AtliQ's competitor supply regions that customers typically used. Again more research into this is needed.

It would be advisable to see other market competitors are recovering from the pandemic as this may impact customer purchasing behavior. If competitors that ranked high as a hardware supplier make a full recovery, other marketing tactics will need to be employed by AtliQ to stay competitive and hold onto their current customer base.

From the above analysis and the cyclical trend that has been shown, AtliQ is on course to show more growth barring any outside factors. For a more overall analysis conclusion, the entire TTWC team will need to give their insights on the other areas of analysis.
<br></br>


## Resources used for the completetion of the project:
<blockquote>
<b>Project Resources:</b>
<li> Quick DBD for database flowchart layout</li>
<li> https://learnsql.com/blog/grouping-data-in-microsoft-sql-server/</li>
<li>https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.to_csv.html</li>
<li>https://learnsql.com/blog/how-to-join-two-tables-in-sql/</li>
<li> Markdown Cheat Sheet - https://medium.com/analytics-vidhya/the-ultimate-markdown-guide-for-jupyter-notebook-d5e5abf728fd</li>
<b>Tableau Resources:</b>
<li> https://www.tableau.com/blog/LOD-expressions</li>

