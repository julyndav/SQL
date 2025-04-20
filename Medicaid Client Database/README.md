# IA Client Medicaid Database

## Project overview:

**<i>Due to the nature of the data involved, the sensitve parts have been blurred out of the project screen shots.</i>

The goal of this project was to improve and streamline the reporting process for both clients and case managers at Company IA. The database was designed to handle monthly client billing through entry forms, where total service units are recorded. These monthly totals are calculated based on the daily billing entries submitted by case managers throughout the month.

Using this system, monthly reports can be generated to monitor whether case managers are meeting their required quotas and to ensure that clients have not exceeded their unit limits. In addition, the database simplifies the process of entering, updating, and managing client information, making overall data management more efficient and reliable. The database also centralizes billing data for furture analysis and creating ageing reports. 
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
<i>TCM > Targeted Case Manager</i>
<br></br>
 
### Main Menu
<img src="https://github.com/julyndav/SQL/blob/main/Medicaid%20Client%20Database/Project%20Images/Main%20Dashboard%20Menu.png" alt="Main Menu" width="600"/>

<ul>
   <li>Interactive buttons to go to various forms and reports.</li>
   <li>Billing Month buttons take the user to the individual months.</li>
</ul>
<p></p>

### Client Information
<img src="https://github.com/julyndav/SQL/blob/main/Medicaid%20Client%20Database/Project%20Images/Client%20information.png" alt="Client Information" width="600"/>

<ul>
   <li>Client information entry.</li>
   <li>Place holder for possible client photo.</li>
   <li>Medicaid ID is primary key.</li>
   <li>Status dropdown: Can select either 'Medicaid' or 'PrivatePay' which are non medicaid clients.</li>
   <li>MCO dropdown: Managed Care Organization (MCO) selection. Clients are under the following MCOs, United Health Care(U), Sunflower(S) or Healthy Blue(HB).</li>
</ul>
<p></p>

### Case Manager Information
<img src="https://github.com/julyndav/SQL/blob/main/Medicaid%20Client%20Database/Project%20Images/Case%20Managers.png" alt="Case Manager Form" width="600"/>

<ul>
   <li>Place holder for employee photo.</li>
   <li>Sub-form (Unit Summary). Lists case manager's monthly unit totals that they billed for. PP=Private Pay(no medicaid funding). Unit Summary values can be entered on this form or when entering the monthly billing units.</li>
   <li>ID is primary key.</li>
</ul>
<p></p>

### Billing per Client
<img src="https://github.com/julyndav/SQL/blob/main/Medicaid%20Client%20Database/Project%20Images/Client%20Billing%20Overview.png" alt="Billing per Client form" width="600"/>

<ul>
   <li>There is no data entry on this form, simply for information purposes.</li>
   <li>OTCM Units >> Other TCM Units. If another case manager bills on a client that is not their's, those units go in this field.</li>
 </ul>
<p></p>

### Billing per Client
<img src="https://github.com/julyndav/SQL/blob/main/Medicaid%20Client%20Database/Project%20Images/Client%20Billing%20Overview.png" alt="Billing per Client form" width="600"/>

<ul>
   <li>There is no data entry on this form, simply for information purposes.</li>
   <li>OTCM Units >> Other TCM Units. If another case manager bills on a client that is not their's, those units go in this field.</li>
 </ul>
<p></p>

### TCM Units Report
<img src="https://github.com/julyndav/SQL/blob/main/Medicaid%20Client%20Database/Project%20Images/TCMs%20unit%20report.png" alt="tcm unit report" width="600"/>

<ul>
   <li>Running total of units that a Case Managers clients have used for the year.</li>
   <li>IU >> Initial Units. All Medicaid clients are alloted 240 units per year.</li>
   <li>PA >> Prior Authorization. When client exceed their 240 unit limit, case managers can request additional units.</li>
 </ul>
<p></p>

### Clients by TCM
<img src="https://github.com/julyndav/SQL/blob/main/Medicaid%20Client%20Database/Project%20Images/TCM%20List.png" alt="tcm unit report" width="600"/>

<ul>
   <li>A simple client list by case manager.</li>
   </ul>
<p></p>

### View UHC Auths
<img src="https://github.com/julyndav/SQL/blob/main/Medicaid%20Client%20Database/Project%20Images/UHC%20Clients.png" alt="uhc auths" width="600"/>

<ul>
   <li>All United clients require an Authorization or claims will be denied.This list keeps tracks of those with and without authorizations.</li>
   </ul>
<p></p>
