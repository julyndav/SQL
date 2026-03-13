# IA Client Medicaid Database

<i>Due to the sensitive nature of the underlying data, screenshots in this repository have been blurred or masked.</i>

This project is a Microsoft Access database designed to centralize Medicaid client billing, improve reporting accuracy, and streamline monthly service tracking for case managers and administrative staff. All screenshots in this repository have been blurred or masked due to sensitive client data.
<br>

## Project overview:
I redesigned an inefficient legacy billing system that relied on multiple monthly tables. 

<b>The updated database:</b>
<ul>
<li>Consolidates all claim activity into a single transactional table (Transaction_TBL)</li>
<li>Prevents duplicate monthly entries for clients via append queries with NOT EXISTS logic</li>
<li>Billing data remains accurate, consistent, and audit-ready</li>
 <li>Supports automated monthly and year-to-date reporting</li>
 <li>Standardizes client demographics, authorizations, and case manager assignments</li>
</ul>
<p>
In addition to billing workflow improvements, the database also standardizes demographic and authorization records, supports operational oversight, and provides a strong data foundation for future utilization and trend analysis.
</p>
<br>

## Key SQL and Database Features:

#### Centralized Billing Workflow
<ul>
 <li>New monthly records are generated via an append query that pulls Medicaid IDs from MasterClientList and inserts them into Transaction_TBL only if a record does not already exist for that month (NOT EXISTS).</li></ul>

#### Aggregated Reporting Queries
<ul>
 <li>Monthly and year-to-date utilization is calculated with SUM aggregations, including conditional logic per month using IIf(Month(ServiceMonth)=X, Units, 0).</li>

<li>Complex queries join multiple tables (MasterClientList, Transaction_TBL, Copy Of Case Managers) to generate comprehensive client billing reports.</li>

<li>Running totals and remaining units are calculated with expressions like (InitialUnits + PA_Units - SUM(TotalUnits)).</li>

<li>Dynamic filtering with HAVING [Enter TCM Initials] allows case managers to view reports tailored to their caseload.</li>
</ul>

#### Main Reporting Query
<ul>
 <li>Produces a year-at-a-glance summary for each client, showing monthly billed units, OTCM units, total units, remaining units, and authorization balances.</li>
<li>Demonstrates SQL skills in joins, grouping, conditional aggregation, calculated fields, and parameterized filters.</li>
</ul>

#### Data Governance & Automation
<ul>
 <li> Queries enforce data integrity, ensuring no duplicate transactions. </li>
<li> Conditional formatting alerts case managers when clients approach unit limits, preventing overbilling.</li>
</ul>
<p></p>

#### Additional capabilities include:
<ul>
<li>Front-end / Back-end database split for stability</li>
<li>Excel export for ad-hoc reporting or auditing</li>
<li>Automated monthly utilization summaries for leadership</li>
</ul>
<p></p>
<br>

## Primary Skills Demonstrated:
<ul>
<li>Relational database design & normalization</li>   
<li>Systems modernization & workflow optimization</li>
<li>SQL development: Joins(Left/Inner), Append and Update Queries, Criteria Filters and Calculated Fields</li>
<li>Data integrity & governance awareness</li>
<li>Operational reporting & audit support</li> 
<li>Application workflow design</li> 
<li>Debugging & technical problem solving</li> 
</ul>
<br></br>

## 🧩 Database Structure:

### Tables
| Table Name |Purpose |
| --- | --- |
| MasterClientList | Centralized client demographic & authorization data |
| Case_Managers | Case manager profiles and caseload relationships |
| Transaction_TBL | Consolidated transactional record of all billed units |
| Archive_Table_2025 | Historical billing archive for prior year activity |
<p></p>

### Queries:
| Query Name | Purpose |
| --- | --- |
| Monthly_Append_Query | Generates new monthly transaction records from client list |
| Compliation_Query | Produces individual client billing profile (year-at-a-glance) |
| Monthly_Totals_TCM | Case manager monthly utilization and quota tracking |
| TCMList | Case manager client roster extract |
| UHC_Clients | Authorization monitoring list for United Health Care clients |

Queries were redesigned to run against the single transaction table, replacing multiple legacy month-specific tables.
<p></p>

### Forms:
| Form Name | Purpose |
| --- | --- |
| FRM_IA_Billing | Main navigation and workflow entry point |
| Case_Manager_Form | Case manager profile with unit summary subform. Option to view client list. |
| Client_Billing_Overview | Read-only client billing and payment overview |
| Client_Master_Form | Centralized client information management |
| Transaction | *Subform* Monthly billing entry with automated calculations |

The entry workflow minimizes manual calculations and enforces consistent billing across clients.
<p></p>

### Reports: 
| Report Name| Purpose |
| --- | --- |
| Overall_Monthly_Totals | Running monthly totals by client |
| Overall_Units_Used-TCM | Remaining units & authorization monitoring |

Conditional formatting highlights clients nearing unit limits to support proactive case management and prevent claim denials.
<p></p>
<br></br>





# Database Overview:
 
### Main Menu
<img src="https://github.com/julyndav/SQL/blob/main/Medicaid%20Client%20Database/Project%20Images/Menu.png" alt="Main Menu" width="600"/>

<ul>
   <li>Interactive buttons to go to various forms and reports.</li>
   <li>Month buttons take the user to the Transaction table that is filtered via a query.</li>
</ul>
<p></p>

### Client Information
<img src="https://github.com/julyndav/SQL/blob/main/Medicaid%20Client%20Database/Project%20Images/Client_information.png" alt="Client Information" width="600"/>

<ul>
   <li>Client information entry.</li>
   <li>Place holder for possible client photo.</li>
   <li>Medicaid ID is primary key.</li>
   <li>Status dropdown: Can select either 'Medicaid' or 'PrivatePay' which are non medicaid clients.</li>
   <li>MCO dropdown: Managed Care Organization (MCO) selection. Clients are under the following MCOs, United Health Care(U), Sunflower(S) or Healthy Blue(HB).</li>
</ul>
<p></p>

### Case Manager Information
<img src="https://github.com/julyndav/SQL/blob/main/Medicaid%20Client%20Database/Project%20Images/Case_Managers.png" alt="Case Manager Form" width="600"/>

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

### Monthly Append Query
<img src="https://github.com/julyndav/SQL/blob/main/Medicaid%20Client%20Database/Project%20Images/Monthly_Append_Query.png" width="600"/>

The monthly append query uses <b>INSERT INTO ... SELECT</b> with <b>NOT EXISTS</b> logic to prevent duplicate monthly transactions per client. 
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
<br></br>



## Outcomes

This project demonstrates the ability to:
<ul>
<li>Modernize and optimize an existing system rather than simply rebuild it
<li>Align database structure to real operational workflows
<li>Design reporting around business rules, not just raw tables
<li>Translate case management processes into scalable data models

It reflects both technical database skills and analytical thinking grounded in real-world program operations.
