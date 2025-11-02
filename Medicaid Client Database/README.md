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

### Key Features:
<ul>
<li>Centralized Billing Workflow – Daily entries automatically feed into monthly billing summaries, reducing manual effort and minimizing errors.</li>
<li>User-Friendly Entry Forms – Custom forms and sub-forms to efficiently enter, update, and validate client records and service data.</li>
<li>Automated Reporting – Monthly and on-demand reports provide insights into service utilization, quota tracking, and potential billing exceptions.</li>
 <li>Data Governance – Normalized table structures and relationships ensure data consistency and improve long-term maintainability.</li>
</ul>


### Skills & Tools Applied:
<ul>
<li>Database Architecture & Design: Relational design, table normalization, and referential integrity</li>   
<li>Microsoft Access Development: Forms, sub-forms, queries, macros, and report design</li>
<li>SQL: Joins, subqueries, criteria filters, calculated fields, and complex query logic</li>
<li>Data Validation & Quality Controls: Input rules, lookup tables, and structured form workflows</li>
<li>Reporting: Custom billing, utilization, and compliance reports for both clients and case managers</li>   
</ul>
<br></br>

## Database Elements:

### Tables
| Table Name |Purpose |
| --- | --- |
| MasterClientList | Stores client demographic and authorization information. |
| Case Managers | Contains case manager profiles and related staffing information. |
| Jan-Dec_Billing |Monthly tables used to capture service units for each respective month. |
| Archive_Table_2025 | Consolidated archive containing all billing data for the 2025 calendar year. |
<p></p>

### Queries:
| Query Name | Purpose |
| --- | --- |
| Jan-Dec_Unit_Totals | Calculates monthly unit totals for each case manager, including Medicaid and Private Pay segments. |
| Monthly Totals | Lists clients, corresponding Case Manager along units used per month. |
| Monthly_Totals_TCM | Provides case managers with a detailed view of their clients and each client's monthly unit utilization. |
| TCM List | Generates a list of targeted case management (TCM) clients along with their MCO and date of birth. |
| UHC Clients | List of United Health Care clients and their corresponding authorization number. |
| janJOIN-decJOIN | Update queries used to sync new client additions across monthly billing tables. |
<p></p>

### Forms:
| Form Name | Purpose |
| --- | --- |
| FRM_IA_Billing | Main navigation menu for the database. |
| Case Manager Form | Enter case manager information and photo. Contains subform for TCM monthly unit totals |
| Client Billing Overview | High-level view of client billing activity, including units, billed amounts, and amounts paid year-to-date. |
| Client Master Form | Centralized form for managing client demographic and authorization details, with optional photo upload. |
| Billing_Jan-Dec | Monthly billing entry forms that calculate billing amounts automatically and allow payment entry tracking. |
| Jan-Dec_Unit_Totals | Subform summarizing monthly TCM unit totals. |
<p></p>

### Reports: 
| Report Name| Purpose |
| --- | --- |
| Overall Monthly Totals | Running total units per month for each client |
| Overall Units Used-TCM | Case Manager client specific monthly units used/remaining |
<p></p>
<br></br>

# Database Overview:
 
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

Union queries are used throughout the database to combine client demographic data with monthly billing entries. Each month includes its own union query, which merges four key fields from the MasterClientList with corresponding fields from the monthly Jan_Billing (and similar) tables.
The join is performed using the Medicaid ID as the shared key, ensuring accurate alignment of client records across tables.
These union queries power the monthly billing entry forms and allow case managers to view a complete picture of each client’s billing activity without duplicating data.
<p></p>

### Overall Units Used - TCM
<img src="https://github.com/julyndav/SQL/blob/main/Medicaid%20Client%20Database/Project%20Images/Overall%20Units%20Used%20TCM.png" alt="union query" width="600"/>

This report is generated and emailed to all case managers on a monthly basis. It provides a detailed breakdown of each client’s unit utilization and remaining authorized units. This prevents overbilling and helps ensure clients do not exceed their allotted service limits, which would result in claim denials.
<p></p>
The report also uses conditional formatting to highlight clients who are approaching their unit limits:
<ul>
<li>Yellow highlight – Remaining units drop to 50. </li>
<li>Red highlight – Remaining units fall to 20 or fewer, signaling that a case manager must submit paperwork for additional units. </li>
This automated alerting ensures proactive management of client authorizations and minimizes compliance risks.
</ul>
<p></p>

### Other Database Details:
<ul>
   <li><b>Excel Exporting:</b> All major tables and datasets can be exported to Excel for external reporting, auditing, or ad-hoc analysis.</li>
 <li><b>Front-End / Back-End Split:</b> The database is split for security and stability. The front-end (forms, queries, reports) is distributed to senior staff, while the back-end securely stores all tables and prevents accidental data modification.</li>
 <li><b> Monthly Emails:</b> Case managers and upper management receive automated monthly unit utilization summaries to support oversight and operational decision-making.</li>
   </ul>
<p></p>
