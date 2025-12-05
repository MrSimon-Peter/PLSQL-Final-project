# PLSQL-Final-project
# Phase II: BUSINESS PROCESS MODEL (BRRS)
#### Project: Borrower Risk Rating System (BRRS)
#### Student: Mukiza Simon Pierre,ID: 27955, Group: Tuesday
#### Database: BRRS_DB
## 1.Business Process Description
##### The Borrower Risk Rating System (BRRS) evaluates loan applicants and existing borrowers by analyzing their repayment behaviors, outstanding balances, and historical loan patterns. The business process begins when a borrower submits a loan request to a loan officer, who enters the borrower’s information and loan details into the system. After submission, the BRRS automatically collects data such as past repayments, payment delays, and default history. The system then calculates a risk score, assigns a risk category, and generates an alert if the borrower is high risk. The manager reviews this information and decides whether to approve or reject the loan request.
## 2.Identify Key Entities
##### Users:Borrower,Loan Officer,Accountant,Manager
##### System:BRRS System
##### Data sources:repayment history,loan application,borrower info
## 3.One Paragraph BPMN Explanation
##### The process starts when the borrower submits a loan application to the Loan Officer, who records borrower details and loan information in the system. The BRRS system then retrieves repayment history and past borrowing behavior from its database. Meanwhile, the Accountant updates repayment information as borrowers make payments. The system analyzes repayment timeliness, missed payments, and outstanding balances to calculate a risk score. A decision gateway checks whether the risk score exceeds the high-risk threshold. If yes, a high-risk alert is generated and forwarded to the Manager; if not, the borrower is marked low or medium risk. Finally, the Manager reviews the system-generated risk assessment and decides whether to approve or reject the loan. The process ends once the managerial decision is recorded.
## 4.Start and End Points
##### Start Event:Borrower submits loan application.
##### End Event:Manager approves or rejects the loan.
## 5.Business Actors
##### a.Borrower:Provides information and requests the loan.
##### b.Loan Officer:Collects borrower details & initiates the process.
##### c.Accountant:Updates repayment records used by the scoring engine.
##### d.Manager:Makes the final loan approval decision.
## 6.System Interactions
### BRRS System Automatically:
##### Retrieves borrower’s past loan information
##### Collects repayment history
##### Computes risk score
##### Assigns risk category
##### Triggers alerts
##### Generates managerial reports
## 7.Managerial Value
##### This process helps managers identify risky borrowers early, reduce default rates, improve decision accuracy, and enhance financial stability in SACCOs and microfinance institutions. It ensures lending decisions are data-driven and compliant with financial best practices.
# PHASE III: Logical Model Design
## 1.Final Entities
##### 1. Borrower
##### 2. Loan Application
##### 3. Repayment
##### 4. Risk Assessment
##### 5. Loan Officer
##### 6. Manager
##### 7. Manager Approval
##### 8. Accountant
##### 9. Disbursement
## 2.NORMALIZATION (1NF,2NF,3NF)
## Step1:First Normal Form (1NF)
#### All BRRS tables are in 1NF because:
##### .Each table has a primary key
##### .All attributes are atomic
##### .No repeating groups
##### .No multi-valued fields
## Step2️: Second Normal Form (2NF)
#### Condition: No partial dependency on a composite PK
#### BRRS: All tables use single-column PKs,no partial dependencies possible.
## Step3: 3️.Third Normal Form (3NF)
#### Condition: No transitive dependencies
#### BRRS Checks:
##### Borrower info separated from Loan_Application
##### Officer, Manager, Accountant stored in their own tables
##### Risk_Assessment stores only IDs, not names
##### No attribute depends on another non-key attribute
