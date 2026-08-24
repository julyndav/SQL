# Client Medicaid Database

A Microsoft Access database designed to centralize Medicaid client billing, improve reporting accuracy, and streamline monthly service tracking for case managers and administrative staff.
         
<i>All data shown in this repository; client names, IDs, and figures are fictional and for illustration only.</i>
<br>

## Project overview:
I redesigned an inefficient legacy billing system that relied on multiple Excel monthly tables. 

<b>The updated database:</b>
<ul>
<li>Consolidates all claim activity into a single transactional table (Transaction_TBL)</li>
<li>Prevents duplicate monthly entries for clients via append queries with NOT EXISTS logic</li>
<li>Keeps billing data accurate, consistent, and audit-ready</li>
<li>Supports automated monthly and year-to-date reporting
<li>Standardizes client demographics, authorizations, and case manager assignments</li>
</ul>
Beyond billing workflow improvements, the database also standardizes demographic and authorization records, supports operational oversight, and provides a stronger data foundation for future utilization and trend analysis.
<p>
<br>

## Key SQL and Database Features:

#### Centralized Billing Workflow
<ul>
 <li>New monthly records are generated via an append query that pulls Medicaid IDs from 'MasterClientList' and inserts them into 'Transaction_TBL' only if a record doesn't already exist for that month (NOT EXISTS).</li></ul>

#### Aggregated Reporting Queries
<ul>
 <li>Monthly and year-to-date utilization calculated with SUM aggregations, including conditional logic per month using IIf(Month(ServiceMonth)=X, Units, 0)</li>

<li>Complex queries join multiple tables (MasterClientList, Transaction_TBL, Case_Managers) to generate comprehensive client billing reports</li>

<li>Running totals and remaining units calculated with expressions like (InitialUnits + PA_Units - SUM(TotalUnits))</li>

<li>Dynamic filtering with HAVING [Enter TCM Initials] lets case managers view reports tailored to their caseload</li>
</ul>

#### Main Reporting Query
Produces a year-at-a-glance summary for each client, showing monthly billed units, OTCM units, total units, remaining units, and authorization balances. This demonstrates using joins, grouping, conditional aggregation, calculated fields, and parameterized filters.

#### Data Governance & Automation
<ul>
 <li> Queries enforce data integrity, ensuring no duplicate transactions </li>
<li> Conditional formatting alerts case managers when clients approach unit limits, preventing overbilling</li>
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
<li>SQL development: joins (left/inner), append and update queries, criteria filters, and calculated fields</li>
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
| TCMList | Case manager client roster |
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
<img src="https://github.com/julyndav/SQL/blob/main/Medicaid%20Client%20Database/Menu.png" alt="Main Menu" width="600"/>

<ul>
   <li>Interactive buttons navigate to various forms and reports</li>
   <li>Month buttons open the Transaction table, filtered via a query</li>
</ul>
<p></p>

### Client Information
<ul>
   <li>Client information entry.</li>
   <li>Place holder for optional client photo.</li>
   <li>Medicaid ID is primary key.</li>
   <li>Status dropdown: Can select either 'Medicaid' or 'PrivatePay' which are non medicaid clients.</li>
   <li>MCO dropdown: Managed Care Organization (MCO) selection. Clients are under the following MCOs, United Health Care(U), Sunflower(S) or Healthy Blue(HB).</li>
</ul>
<p></p>

### Case Manager Information
<ul>
   <li>Place holder for optional employee photo.</li>
   <li>Sub-form (Unit Summary). Lists case manager's monthly unit totals that they billed for. PP=Private Pay(no medicaid funding).Values can be entered here or during monthly billing entry</li>
</ul>
<p></p>

### Billing per Client
<img src="https://github.com/julyndav/SQL/blob/main/Medicaid%20Client%20Database/Client_Billing_Overview.png" alt="Billing per Client form" width="600"/>

<ul>
   <li>Read-only form, for information purposes only
"OTCM Units" = Other TCM Units — units billed by a case manager on a client that isn't theirs go into this field</li>
 </ul>
<p></p>

### TCM Units Report
<img src="https://github.com/julyndav/SQL/blob/main/Medicaid%20Client%20Database/TCM_Unit_Report.png" alt="tcm unit report" width="600"/>

<ul>
   <li>Running total of units a case manager's clients have used for the year</li>
   <li>"IU" = Initial Units. All Medicaid clients are allotted 240 units per year</li>
   <li>"PA" = Prior Authorization. Additional units case managers can request once a client exceeds their 240-unit limit</li>
 </ul>
<p></p>

### Clients by TCM
<img src="https://github.com/julyndav/SQL/blob/main/Medicaid%20Client%20Database/TCM%20List.png" alt="tcm unit report" width="600"/>

<ul>
   <li>A simple client list by case manager.</li>
   </ul>
<p></p>

### View UHC Auths

<ul>
   <li>All United Healthcare clients require an authorization, or claims will be denied; this list tracks which clients have one and which don't</li>
   </ul>
<p></p>

### Billing Month Entry
<img src="https://github.com/julyndav/SQL/blob/main/Medicaid%20Client%20Database/Monthly%20Billing%20Form.png" alt="monthly billing" width="600"/>

<ul>
   <li>Small Unit_Totals subform: enter case managers' monthly units and private pay units. Only Medicaid units can be billed. Private Pay units are processed by the TCM. "Total TCM Units" and "Total Billed Units" should match, confirming all TCM units have been billed; the Refresh button ensures all entered units are reflected in the totals</li>
 <li>In the entry form itself, only 'Units', 'OUnits', 'Paid', 'Claim#', and 'Note' are entered manually — 'Total Units', '$Bill', and 'Balance' are calculated fields</li>
   </ul>
<p></p>
<br></br>

## Additional Database Elements:

### Monthly Append Query
<img src="https://github.com/julyndav/SQL/blob/main/Medicaid%20Client%20Database/Project%20Images/Monthly_Append_Query.png" width="600"/>

Uses INSERT INTO ... SELECT with NOT EXISTS logic to prevent duplicate monthly transactions per client.
<p></p>

### Overall Units Used - TCM
<img src="https://github.com/julyndav/SQL/blob/main/Medicaid%20Client%20Database/Project%20Images/Overall%20Units%20Used%20TCM.png" alt="union query" width="600"/>

Generated and emailed to all case managers monthly, providing a detailed breakdown of each client's unit utilization and remaining authorized units — helping prevent overbilling and ensuring clients don't exceed allotted service limits (which would otherwise trigger claim denials).
<p></p>
TThe report uses conditional formatting to flag clients approaching their unit limits:
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
