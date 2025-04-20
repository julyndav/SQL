# IA Client Medicaid Database

## Project overview:

**<i>Due to the nature of the data involved, the sensitve parts have been blurred out of the project screen shots.</i>

The goal of this project was to improve and streamline the reporting process for both clients and case managers at Company IA. The database was designed to handle monthly client billing through entry forms, where total service units are recorded. These monthly totals are calculated based on the daily billing entries submitted by case managers throughout the month.

Using this system, monthly reports can be generated to monitor whether case managers are meeting their required quotas and to ensure that clients have not exceeded their unit limits. In addition, the database simplifies the process of entering, updating, and managing client information, making overall data management more efficient and reliable.
<br></br>


### Skills Used:
<ul>
<li>Microsoft Access database design and development</li>   
<li>SQL for writing SELECT and UNION queries</li>
<li>Creating user-friendly forms and sub-forms for data entry and management</li>
<li>Designing custom reports for client and case manager insights</li>
<li>Building complex queries with criteria filters, expressions, and calculated fields</li>  
<li>Data normalization and establishing table relationships</li>   
</ul>
<br></br>

## Database Elements:

### Tables
| Table Name |Purpose |
| --- | --- |
| MasterClientList | Main client information table |
| Case Managers | Case Manager information |
| Jan-Dec_Billing |Tables to hold the corresponding monthly billing data |
| Archive_Table_2025 | Holds all billing data for 2025 year |
<p></p>

### Queries:
| Query Name | Purpose |
| --- | --- |
| Jan-Dec_Unit_Totals | Monthly unit totals for each Case Manager, includes Mediciad and Private Pay columns. |
| Monthly Totals | Lists clients and their corresponding Case Manager along units used per month |
| Monthly_Totals_TCM |Case Manager client list and the units each client has used each month |
| TCM List | TCM clients with corresponding MCO and DOB |
| UHC Clients | List of United Health Care clients and their corresponding authorization number |
| janJOIN-decJOIN | Update Queries for when new clients are added to agency |
<p></p>

### Forms:
| Form Name | Purpose |
| --- | --- |
| FRM_IA_Billing | Database main menu |
| Case Manager Form | Enter case manager information and photo. Contains subform for TCM monthly unit totals |
| Client Billing Overview | Billing units, amounts billed and amounts paid for each client for the entire year |
| Client Master Form | Client information along with client photo option |
| Billing_Jan-Dec | Monthly client unit entry forms. Auto calculates billing amount and allows for payment entry |
| Jan-Dec_Unit_Totals | TCM monthly unit total sub-form |
| Subfrm_TCM_Unit_Totals | Monthly unit total subform for 'Case Manager Form' |
<p></p>

### Reports: 
| Report Name| Purpose |
| --- | --- |
| Overall Monthly Totals | Running total units per month for each client |
| TCM_Monthly_Units_Used | Case Manager client specific monthly units used/remaining |
<p></p>
<br></br>

# Database Overview:

### Data Cleaning and Preparation:


![Data_cleaning](https://github.com/julyndav/Python/blob/main/Business%20Analytics/Images/data%20cleaning1.png)

Now that the data has been cleaned, data types are set and it was determined that there are no duplicates, analysis can start. 
<br></br>


# Product Analysis
Questions to answer:

1) How many people use it every day, week, and month?
2) How many sessions are there per day? (One user might have more than one session.)
3) What is the length of each session?
4) What's the user retention rate?

### 1) Visits daily, weekly monthly usage?
<ul>
<li>Visits table will be used for this part of the analysis</li>
<li>Columns created for year, month, week values to determine activity usage.</li>
<li>Averages will be used.</li> 
<li>Coding will be separated into DAU(daily average users), WAU(weekly average users) and MAU(monthly average users)</li>
</ul>
<br></br>

To determine users by month/year/week, the date value needs to be separated out into it's individual parts. This will be based off 
of 'Start Ts' (start date and time variable).
![Date_breakdown](https://github.com/julyndav/Python/blob/main/Business%20Analytics/Images/DAU1.png)
<p></p>
<br>

Now that the date has been broken down, let's use it to find our overall averages. 
![Overall_Averages](https://github.com/julyndav/Python/blob/main/Business%20Analytics/Images/averageusers_overall.png)
<p></p>
<br>

To see the actual user average per day, the 'groupby' function will be used. 
![DailyAU](https://github.com/julyndav/Python/blob/main/Business%20Analytics/Images/DAU_code.png)
<p></p>
<br>

![DAU_graph](https://github.com/julyndav/Python/blob/main/Business%20Analytics/Images/Daily%20Average%20Users.png)

<b>Insights: </b> 
<OL>
<li>Same coding concept will be used for WAU and MAU visualizations.</li>
<li>November had a peek of approxamitly 3300 daily users.</li>
<UL>
<li>The main spike in DAU happened on November 24th. A possible explanation for this could be due to pre-christmas sale?</li>
<li>Another area to look into is the dip in the 2018 data for March 31st; what outside factors could have contributed to the dip?</li>   
</UL>   
<li>The data had starting daily user total of around 600 users by the end of the study, daily user count was almost 2000 users.</li>
<LI>From March 26,2018 to March 31,2018 showed a dramatic drop in daily usage of 1670 users. More reasearch needed on this to see why.</LI>
</OL>
<p></p>


### Weekly and Monthly Users Visualizations:
![WAUMAU](https://github.com/julyndav/Python/blob/main/Business%20Analytics/Images/WAU_MAU.png)
<p></p>

<b>Insights: </b> 
<OL>
<li>The gap/color change is for the change from 2017 to 2018.</li>
<li>Weekly user average was: 5724 and Monthly average users were: 23228 .</li>
<li>Weekly peak users topped out at 10.7K users.</li>
<li>Monthly user peak total was 32.7K users.</li>
</OL>
<br></br>

### 2) Sessions per day?:
![Session_day](https://github.com/julyndav/Python/blob/main/Business%20Analytics/Images/sess%20per%20user.png)

<b>Insights:</b> 
<OL>
<li>Number of sessions and users are fairly close in size with number of sessions being slightly higher.</li>
<li>Numbers over 1.05 show that a few users have had more than one session.</li>
<li>Average session per user: 1.08.</li>
</OL>
<br></br>

### 3) Length of Session:
Session length was determined by using Python to calculat that time between 'Start Ts' and 'End Ts'. Duration time was returned in seconds.
<p></p>
On average, a user spends 1 minute/60 seconds on the app. This time should be enough to find the event of interest, but most likely it will take more time to buy tickets through the Yandex.Afisha application. 
Will need more research on whether people completely lose interest in what they have found, or go to other resources to buy a ticket there.

![Session_length](https://github.com/julyndav/Python/blob/main/Business%20Analytics/Images/length%20of%20sess.png)

<i> From unusally large spike of 0's, it seems to correlate with visitors that have 0 conversion days. Customers wasted no time in making a purchase.</i>
<br></br>

### 4) User Retention
Retention shows us how many users (in % out of registered) were active (had sessions) on a certain day/week/month after registration/first visit.
To show the customer retention, this is where cohort analysis will be used. First is to create Cohort month which shows the first time the User has visited. 
This data will be used later in the coding process for Retention Rate and to create a heatmap as a visualization for this part of the analysis. 

<b>Retention Analysis Steps:</b>
1) Imported <b>datetime as dt</b> to work with dates.
2) Applied a function to just have the year and month with the day defaulted to 1 (the first of the month).
3) Created 'cohort month' based on first month of user's visit.
4) Created a column index for month cohort.

Getting the separate date elements will allow the creation of the index. It will show us when the user was acquired, how long they have been active and retained.

![Retention_Code](https://github.com/julyndav/Python/blob/main/Business%20Analytics/Images/retention%20code.png)
<i>Customers with an cohort index of 0(Conversion 0d), were acquired and active within the same month</i>
<p></p>

5) Now to create the pivot table that is key in getting the heatmap visual for retention. Cohort months will act as the 'rows' with the cohort index as the column labels and values based on Uid (user id) totals.
6) The Uid totals are converted into a percentage, the results are displayed as a pivot table

![Retent_pt](https://github.com/julyndav/Python/blob/main/Business%20Analytics/Images/retention%20table.png)
<p></p>

7) To display the heatmap; custom colors were selected and values formatted to show percentages appropriatley.

   ![heatmap](https://github.com/julyndav/Python/blob/main/Business%20Analytics/Images/retention%20heatmap.png)
   <p></p>

### Insights: 
The average retention rate from all cohorts decreased slowly over time. One of the few months to retain a somewhat steady user percentage was June. July, August and September faired better the the rest of the months as they were able to have a slightly higher average for most of the month. Towards the end of 2018 the rate had a declining trend.

### Reccomendation:
May 2018 had no registerable data. The data for May 2018 needs more attention to see what is going on and why the data collection period wasn't for the entire month.

## Product Analysis Conclusion:
Yandex.Afisha sees an average of 900 users daily with each users having around 1 session. The time spent on the site for that session is about 10 minutes. There was a significant spike in users around November 24th/Thanksgiving times which could be attributed to the holiday season. The 24th/25th of November is also one of the biggest shopping days of the year as a precursor to Christmas. Tickets may have been purchased as gifts but more user information would be need to to determine that. The spike in Users also coincides with an increase is session lenght to almost 18 minutes. The site my have slowed due to server traffice.
One area of concern is the plunge in both users and session lenght that occured around March 31st. With such a sharp decrease in both users and session length; a few things may have occured. It could be a site crash, site maintenance or voluntary/involuntary site take down but again, more information would be need to make a solid conclusion.

<br></br>
# Sales
In this section of the analysis, the 'visits' table that was customized for cohort analysis will be merged with the orders tables creating a new df (data frame) .

### Sales Objective:
1) How are customer purchasing items?
2) How many orders do they make during a given period of time?
3) What is the average purchase size?
4) How much money do they bring? (LTV)

### 1) Preferred way to purchase?:
Once the tables were merged, the 'groupby' function was used on the 'Device' variable, the 'revenue' was summed. The total revenue value was formatted to show
millions.  To find the number of users per each device, the same method was used to determine the total users. 

![Dev_users](https://github.com/julyndav/Python/blob/main/Business%20Analytics/Images/purchase%20how.png)
<br></br>

### 2) Orders vs Time period:
The visits table now comes into play as it already has the date brokendown into week and month, this will be used to compare the revenue vs. week/month.
Again the 'grouby' function is empolyed to group the revenue data by weekly then monthly totals. 

![Revenue vs Time](https://github.com/julyndav/Python/blob/main/Business%20Analytics/Images/revenue_vsTime.png)

To see how many orders customers are making over time, cohort analysis will be used once again along with the heatmap visualization. 
This involved creating a new table. After the required tables were merged, the resultant table was over 50K rows. For the orders cohort, number of buyers was calculated for each month, variables were grouped, cohort age was found and number of buyers for each cohort age was calculated. Once that was determined then a pivot table was created for the heatmap visualization. 

<b>Insight: </b> There are generally only one order per cohort age. It isn't until age 5 that the number of orders starts to increase but that is mostly relegated to June 2017. August and September 2017 saw almost 1 1/2 orders per cohort age.
<br></br>

### 3) Average Purchase Size:
More grouping is used on the previous table used to find orders vs time. The data was grouped by order month then the 'mean' was taken for the revenue. 
If one wanted to, you could graph this to show the average purchase size for each month.  To find the overall average purchase size, a simple line of code was used buy taking the mean of 'Revenue' and rounding it to 2 decimal places.  

#### Average Purchase Size =  5.0
<br></br>

### When do people buy?:
These are the steps taken to determine the difference betweeen when customers visit vs when they make their first purchase.
<ul>
   <li>Find the date of the first order for each user. Using the 'overview table'(contains our combined data).</li>
</ul>

![V_vs_P code](https://github.com/julyndav/Python/blob/main/Business%20Analytics/Images/visit_vs_purchase.png)
<p></p>

<OL>
<li> Merged 'first order date' column to the combined table ('overview').</li>
<li>Found first sessions per user. Created new table for this that contained only 'Uid' and 'first_session' columns</li>
<li>Merged the 'first_order_date' table with the new 'first_session' table grouped by user ids. </li>   
<li>Double checked date formats.</li>
<LI>Determined number of days between 'first_session' and 'first_order_date'. 'diff_days' variable created and added to order/session date table.</LI>
<li>Historgram created to get a visual on number of days between visiting and ordering.</li>


![Histogram_daysdiff](https://github.com/julyndav/Python/blob/main/Business%20Analytics/Images/elasped_visit_toPurchase.png)
<p></p>


</OL>
<p></p>
<b>Insight:</b>There are generally only one order per cohort age. It isn't utnil age 4 that the number of orders starts to increase but that is relegated to June 2017. August and September 2017 saw approximately 1.5 orders per cohort at age 6 and on.
<p></p>
<br></br>

### Orders Made Over Time?:
<i>This section of the analysis will use the orders df as the base for it's data. Working with first purchase date as the cohort.</i>
<p></p>

#### Analysis Steps:
<ul>
   <li>Used 'orders' table to find orders by users.</li>
   <li>Created 'order_month' column but extracting month for purchase('Buy Ts') date.</li>
   <li>Retrived month of customer's frist order.</li>
   <li>#merge the order and first order data frames based on 'user id.'</li>
   <li>Calculated the number of buyers (n_buyers) for each month grouped by 'first_order_month'.</li>
   <li>Calculated the number of orders.</li>
   <li>Combined buyer and order totals. This is start of cohort.</li>
   <li>Now to find the cohort ages and number of buyers per cohort.</li>
</ul>

![buyer_cohort](https://github.com/julyndav/Python/blob/main/Business%20Analytics/Images/buyers_per_cohort.png)

<li>Now to create a pivot table from the above data which will be represented by a heat map.</li>
<p></p>

![oversovertimeHM](https://github.com/julyndav/Python/blob/main/Business%20Analytics/Images/orders_vsTime_hm.png)
<p></p>
<br></br>


### 4) LTV (Life Time Value)
<ul>
   <li>For each Uid(user id) we determine the first month an order was placed.</li>
   <li>Next was to calculate the number of new buyers for each month.</li>
   <li>Both are now combined into one table.</li>
   <li>Group the table of orders by month of first purchase and month of purchase and sum up the revenue</li>
   <li>A cohort table was then created and the cohort age calculated.</li>
   <li>A new column was added to the above table for the ltv value by using the following code:
       report1['ltv'] = report1['Revenue'] / report1['n_buyers']</li>
   <li>Pivot table was then generated to graph the LTV heatmap from.</li>  
</ul>

   ![LTV](https://github.com/julyndav/Python/blob/main/Business%20Analytics/Images/ltv_heatmp.png)

<b> LTV Insight:</b> The June 2017 cohort had the longest duration of LTV (up to age 11), thus, contributed the longest time. However, the September 2017 cohort had the highest LTV for it's entire duration. May and June 2018 had the lowest. More information is needed to see what spurred and dampened user purchases.
<p></p>
<br></br>


# Marketing
Now to bring the cost table into play. 

![cost_tbl](https://github.com/julyndav/Python/blob/main/Business%20Analytics/Images/cost%20table.png)

### Marketing Objective:
1) How much money was spent? Overall, per source and over time.
2) How much did customer acquisition from each of the sources cost?
3) How worthwhile where the investments? (ROI)


### Marketing Costs Overall:
<ul>
<li>Now to use the 'cost' table for this analysis.</li>
<li>For overall marketing costs, sum the 'costs' column.</li>

   #### Total Overall Marketing Costs: $ 329,131.62
</ul>
<p></p>

### Marketing Cost over time:
<ul>
   <li>I chose to show how much was spent on Marketing monthly.</li>
   <li>Using the dt (date) column in the cost table, the data was grouped by month.</li>
   <li>From their the variables were used to create a graph to represent the months on the x-axis and costs along the y-axis.</li>
</ul>
<br></br>

![AdvsTime](https://github.com/julyndav/Python/blob/main/Business%20Analytics/Images/ad%20cost%20month.png)

<b> Insight:</b> The monthly marketing expense shows a natural progression for the time period. 6 of the months the marketing expense is below $25k. November and December has the highest marketing expense which could be due to the holiday season. All businesses are trying to cash in on holiday shopping dollars so it makes sense that more of an effort is put forth during that time.
<br></br>


### Marketing Cost per Source:
Even though this portion is focused on how much was spent per Ad source, I also wanted to show how much revenue was generated per ad source as well. 
Back to the concept of grouping by the variable we want to showcase then summing the requested values. Unfortunately no information was provided as to what the ad sources are.

![Source adcosts](https://github.com/julyndav/Python/blob/main/Business%20Analytics/Images/ad%20cost%20source.png)

![soure_rev](https://github.com/julyndav/Python/blob/main/Business%20Analytics/Images/source%20cost%20vs%20rev.png)

<b>Insights:</b> Source three has the highest marketing expense. If we compare the source with the highest expense and those with the highest Revenue; Source 3 is lacking on it's return. The highest Revenue sources also have marketing expenses, on average of less than $6k on average per month.

<b>Recommendation:</b> Marketing department should re-evaluate the benefit of using Source 3 as an advertising source. Source 7 had virtually no activity at all so it didn't register and should be dropped along with Sources 10 and 9 due to low performance.
<br></br>

### Customer Acquistion Costs (CAC) by Buyers:
<ul>
   <li>Using the 'costs' table, extract the 'first_order_month' and total cost for that date. This will be it's own table.</li>
   <li>To repeat the above actions but for total buyers for 'first_order_month. This will be it's own table.</li>
   <li>Now to combine the two tables on the 'first_order_month'.</li>
</ul>
   
![cac_buyer](https://github.com/julyndav/Python/blob/main/Business%20Analytics/Images/CAC_buyer.png)
   

<ul>
   <li>Results visualized as a single line chart</li>
   <li>The average CAC per buyer is: <b>$8.24.</b></li>
</ul>
<br></br>


### Customer Acquisition Costs (CAC) per Source:
<ul>
<li>Find the day and month of the first purchase of each customer</li>
<li>Sort visits by first date and group by first uid.</li>
<li>Merge with first orders</li>
<li>Group table by source_id and first day, count uid</li>
<li>Add costs using left_on=['source_id', 'first_order_dt'], right_on=['source_id', 'dt']</li>
<li>Calculate CAC, create pivot table and plot a graph.</li>
</ul>

![CAC_source](https://github.com/julyndav/Python/blob/main/Business%20Analytics/Images/CAC%20by%20source.png)

<b>Insight:</b> 
The marketing source with the highest customer acquisition cost is source 3 at 141K; almost half of source 3's revenue was marking costs. Source 3 ranks 5th amongst the platforms in terms of Revenue. Source 7 didn't even register due to it's low value. Sources 1, 2 and 5 are the top performing sources in termn of revenue generated and should be focused on. The average cost for marketing for each of the top sources is $38K with Source 5 having the highest individual ad cost of 52K. There was no source 6 or 8.

Recommendations: Under-performing sources should be given thought of termination or replacement
<br></br>

## How worthwhile where the investments? (ROI)

## ROI:
<ul>
<li>In genereal, ROI=LTV/CAC. We already have calculations on CAC per month and we have info on ltv in ltv_cohort. So let's merge.</li> 
<li>The previous table for LTV already has cohort ages.</li>
<li>Now to calculate for ROI. This variable will be added to table as new column./li> 
</ul>   
<p></p>
   
![roi](https://github.com/julyndav/Python/blob/main/Business%20Analytics/Images/ROI.png)
<p></p>
<ul>
<li>Once ROI has been determined, a pivot table can be created. From that pivot table, we'll have a heatmap giving a visual for ROI.</li>
</ul>
<p></p>

![ROI](https://github.com/julyndav/Python/blob/main/Business%20Analytics/Images/ROI%20by%20cohort.png)
<br></br>

### ROI by Marketing Source:
<ul>
 <li>Determine LTV per source.</li>
 <li>Determine CAC per source.</li>  
 <li>Find number of buyers and costs per source. 'buyers' and 'cost' will be separate tables.</li>
 <li>Merge 'buyers' and 'costs' tables together based on the source.</li>
 <li>Calculate 'cac' for each source.</li>
 <li>Merged previous 'ltv_per_source' with current table.</li>
 <li>Now to calculate 'romi'</li>
</ul>
<p></p>

![romi](https://github.com/julyndav/Python/blob/main/Business%20Analytics/Images/romis.png)

#### ROMI stands for Return on Marketing Investment. This metric shows how cost-effective your marketing investments are

![romi_source](https://github.com/julyndav/Python/blob/main/Business%20Analytics/Images/romi_source.png)

<b>Source Note:</b> Originally there were no Source 6 or 8 and Source 7 was so neglible that it's ROMI was 0. This is why there is a gap from Source 5-9.

<b>Insights:</b> There is no ROI/ROMI for Source 7 as it value was practically negligible, it didn't register enough for a cost value even with 1 users. That one user only generated 1.22 in revenue for Source 7 so curious to what item was purchased by the user. As other analysis has shown. Other than the top source, Source 1, the others maintained a fairly average ROI/ROMI regardless of marketing costs

<b>Recommendation:</b> It's advisable to reallocate the marketing budget to the source that costs lower but could yield higher ROMI in a shorter period. Source 3 is not a profitable source(along with Source 7) and although Sources 9 and 10 have a low marketing cost they also have low revenue of less than 6K.
<br></br>
<br></br>


# Analysis Conclusion
The project analysis was to evaluate the marketing effectivness of Yandex Afisha. Several studies and forms of analysis were done to determine how people use the product, when they start buying, how much money each customer brings, costs and revenue. In the First and Second Stages, data was loaded and prepared to work with. All datasets contain no missing values or duplicates.

The Data Preprocessing perform datatype adjustments, formatting, adding modified datasets, and truncating datetime to the primary dataset for analysis convenience. In the Third Stage conducted cohort analysis which was divided into three sections; User Engagement, Sales KPI, and Marketing.

#### Sales by devices: 
It was found that Desktop brought in over 710k users with a revenue of 6.45 million dollars while the touch device only brought in a little under 49K users and a net revenu of .5million dollars. More information is needed from marketing as to what the 'touch' devices are.
The sources with the greatest revenue were sources:
<ul>
<li>Source 2 - $2.6 million</li>
<li>Source 1 - $2.3 million</li>
<li>Source 5 - $1.2 million</li>
</ul>
<p></p>

#### Conversion:
By evaluating the difference in days from visit to purchase, we learned that the majority of visitors made purchases on their first visit. Almost 33K visitors made purchases on their first visit.

#### User Sessions: 
There are an unusally high amount of 0's for the 'Lenght of User Session' KPI. This may be due to visitors that went to the site in error. More info is needed to see if the visitors with 0 session lenght are from internet traffic that was redirected to the site from clicking on external links. For a user to have spent no time on the site but visited, relays that they visited in error or it was not their intended site.

*On order for a given time period, cohort analysis was done to include pivot table and heatmap. It isn't utnil age 5 that the number of orders starts to increase but that is mostly relegated to June 2017. August and September 2017 saw almost 1 1/2 orders per cohort age.

#### Average purchase size:
The month of December had more purchases than any other month for for the time frame given. The holiday season could have played a hand in this with gift purchases or sales. Again, June did not have enough time span so they are the lowest on all KPI metrics

Marketing Overall, total ad expenses were 329K. Over 141k of that was used on Source 3, the lowest performing source. The others sources had less than 50K in marketing costs with SOurces 9 and 10 at less than 6k. An interesting insight is that as the months progressed there was a peak around the holiday season then a slow delcline. It's understandable as everyone is hoping to cash in on the holiday seasons.

The average CAC is 9.15. A CAC of less than $10 per user seems feasible. Source 3 should be dropped as the ad expense is nearly halve of the revenue; giving it a lackluster ROI. Sources 7, 9 and 10 should be considered for dropping also since each had less than 40k in revenue for the combined 2017/2018'.

Seeing how things performed from a monthly standpoint gave good overall view of the various metrics. Seeing the monthly revenue and ltv gave good insights into consumer spending. It would have been nice to see some user demographics; it may be able to pinpoint some customer trends.

But form the monthly data, espeically the monthly LTV heatmap and with how technology is changing entertainment. From the 2017 data, June through September, the high numbers can be contributed to summer break for schools and colleges. Coupled with the heat of summer, going to the cinemas is major summer activity..

Another aspect that was noticed based on the revenue cycles is that towards the middle part of 2018, there is a steady decline. With more households switching to online streaming services, the desire to go to theaters is decreasing. That trend and how it effects online ticket purchases will need further study.

### Recommendations:

Information/Research is need to see if current or past customers are on some type of email list; are customers made aware of promotions or discounts. Since sources 1, 2 and 5 are so popular, maybe integrating a quick customer satifaction survey that has a product discount will give some customer insights.
What are customers purchasing? Are movies more popular than concerts on the Afisha platform. More information is needed on this from the Marketing department.
Source 4, even though it was not a high revenue maker, did moderately well vs it's marketing budget of 61k at almost 500k in revenue. More thought should be given on promoting this source more.
<p></p>

### Overall Impression(s):
Users get to the website and atleast make one purchase pretty much immediately. The ads are bringing in relevant users that want the product, but most users do not make multiple orders/visits and orders are small. Usally movie goers stay up to date on the latest and upcoming movies; it makes sense that their purchases would continue. Are customers not happy after their intial purchase?

