# IA Client Medicaid Database

## Project overview:
<i>Due to the sensitive nature of the underlying data, screenshots in this repository have been blurred or masked.</i>

The database was built to centralize billing information, support accurate monthly reporting, and improve efficiency for both case managers and administrative staff. Daily service entries submitted by case managers roll up into monthly totals, which are then used to generate billing statements and performance reports. These reports help ensure:
<ul>
<li>Case managers meet their required monthly service quotas</li>
<li>Clients do not exceed their authorized service units</li>
<li>Billing data is consistent, accurate, and audit-ready</li>
</ul>
<p>
In addition, the system simplifies the management of client demographic information, improves data entry workflows through structured forms, and establishes a reliable data foundation for future analyses such as aging reports or long-term service utilization trends.
</p>


### Skills Used:
<ul>
<li>Microsoft Access database design and development</li>   
<li>SQL for JOINS, QUERIES and SUBQUERIES</li>
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
| Overall Units Used-TCM | Case Manager client specific monthly units used/remaining |
<p></p>
<br></br>

# Database Overview:
<i>TCM > Targeted Case Manager</i>
<br></br>
 
### Main Menu
<img src="https://github.com/julyndav/SQL/blob/main/Medicaid%20Client%20Database/Project%20Images/Menu.png" alt="Main Menu" width="600"/>

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
   <li>MCO dropdown: Managed Care Organization (MCO) selection. Clients are under the following MCOs, United Health Care(U), Sunflower(S) or Aetna(A).</li>
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

### Billing Month Entry
<img src="https://github.com/julyndav/SQL/blob/main/Medicaid%20Client%20Database/Project%20Images/Monthly%20Billing%20Form.png" alt="monthly billing" width="600"/>

<ul>
   <li>Small Unit_Totals sub form. You can enter case managers monthly units and private pay units. Only Medicaid units can be billed for. Private Pay have to be processed by the TCM. 'Total TCM Units' and 'Total Billed Units' - this is to ensure that all TCM units have been billed for; the two values should be the same. The 'Refresh' button is to make sure all units entered are in the totals.</li>
 <li>In the actual entry form, 'Units', 'OUnits', 'Paid', 'Claim#', and 'Note' are the only fields to enter data.  'Total Units', '$Bill', and 'Balance' are all calculated fields.</li>
   </ul>
<p></p>
<br></br>

## MISC Database Elements:

### Union Query Sample
<img src="https://github.com/julyndav/SQL/blob/main/Medicaid%20Client%20Database/Project%20Images/Monthly%20Billing%20Union%20Code.png" alt="union query" width="600"/>

<ul>
   <li>The union queries allow information from two separate tables, 'MasterClientList' and 'Jan_Billing' to be combined into one. This is for the monthly billing entry forms. Each month has their own union query.</li>
 <li>The 4 columns from the "MasterClientList'table are joined with the columns from the 'Jan_Billing' table based on the Medicaid ID's from both tables as the key column. </li>
   </ul>
<p></p>

### Join Query Sample
<img src="https://github.com/julyndav/SQL/blob/main/Medicaid%20Client%20Database/Project%20Images/join%20query.png" alt="union query" width="600"/>

<ul>
   <li>This is an example of one of the monthly Update Queries. For this database, join queries are used to ensure that newly entered clients are added to the monthly billing entry forms. The monthly billng forms are tied to their corresponding billing query.</li>
   </ul>
<p></p>

### Overall Units Used - TCM
<img src="https://github.com/julyndav/SQL/blob/main/Medicaid%20Client%20Database/Project%20Images/Overall%20Units%20Used%20TCM.png" alt="union query" width="600"/>

<ul>
   <li>This is a monthly update report that all Case Managers receive via email. This allows them to see how their clients are using their units and keeps them from running out of units. Once a client has exhuasted their alloted units, any claims submitted after that will be denied. This report contains conditional formatting. When the clients 'Remaining Units' drops to 50, the client is highlighted yellow. When their remaining units drop to 20 or less, the client is highlighted red, signalling that the case manager needs to submit paperwork for additional client units.</li>
   </ul>
<p></p>

### Other Database Information
<ul>
   <li>Tables can be exported into Excel files.</li>
 <li>Database was split into a front and rear end. The front end can be dispersed to other senior staff members while the back-end keeps all tables safe from accidental editing.</li>
 <li>Each month the TCM's and upper management receive client unit reports via email.</li>
 <li>The only other staff with access to this database is the President of the company; allowing them to view billing and unit status at anytime via their front-end portal.</li>
   </ul>
<p></p>
