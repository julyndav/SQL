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

#### Main Menu
![Main Menu](https://github.com/julyndav/SQL/blob/main/Medicaid%20Client%20Database/Project%20Images/Main%20Dashboard%20Menu.png)

<ul>
   <li>Interactive buttons to go to various forms and reports</li>
   <li>Billing Month buttons take the user to the individual months</li>
<br></br>

#### Client Information
![Client Information](https://github.com/julyndav/SQL/blob/main/Medicaid%20Client%20Database/Project%20Images/Client%20information.png)

<ul>
   <li>Interactive buttons to go to various forms and reports</li>
   <li>Billing Month buttons take the user to the individual months</li>
<br></br>
