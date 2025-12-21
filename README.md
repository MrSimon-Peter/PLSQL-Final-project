# PLSQL-Final-project
# Phase II: BUSINESS PROCESS MODEL (BRRS)
#### Project: Borrower Risk Rating System (BRRS)
#### Student: Mukiza Simon Pierre,ID: 27955, Group: Tuesday
#### Database: BRRS_DB
<img width="1915" height="1013" alt="BPMN OG" src="https://github.com/user-attachments/assets/34b23582-deb3-4794-be19-fd4d0e58782d" />

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
<img width="1919" height="1008" alt="ERD OG" src="https://github.com/user-attachments/assets/a95111f4-a7a5-4a46-b282-c7c52055dda6" />

## 1.Entities
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
### Step1:First Normal Form (1NF)
#### All BRRS tables are in 1NF because:
##### .Each table has a primary key
##### .All attributes are atomic
##### .No repeating groups
##### .No multi-valued fields
### Step2️: Second Normal Form (2NF)
#### Condition: No partial dependency on a composite PK
#### BRRS: All tables use single-column PKs,no partial dependencies possible.
### Step3: 3️.Third Normal Form (3NF)
#### Condition: No transitive dependencies
#### BRRS Checks:
##### Borrower info separated from Loan_Application
##### Officer, Manager, Accountant stored in their own tables
##### Risk_Assessment stores only IDs, not names
##### No attribute depends on another non-key attribute
## DATA DICTIONARY (BRRS_DB)
### 1. BORROWER
#### | Column      | Type          | Key | Description          |
#### | ----------- | ------------- | --- | -------------------- |
#### | borrower_id | NUMBER        | PK  | Unique borrower ID   |
#### | full_name   | VARCHAR2(100) |     | Borrower full name   |
#### | national_id | VARCHAR2(20)  |     | Rwanda national ID   |
#### | phone       | VARCHAR2(20)  |     | Contact phone number |
#### | email       | VARCHAR2(50)  |     | Email address        |
#### | address     | VARCHAR2(100) |     | Physical address     |
### 2. LOAN APPLICATION
#### | Column           | Type         | Key                       | Description                   |
#### | ---------------- | ------------ | ------------------------- | ----------------------------- |
#### | loan_id          | NUMBER       | PK                        | Unique loan record            |
#### | borrower_id      | NUMBER       | FK  borrower.borrower_id | Loan owner                    |
#### | loan_amount      | NUMBER       |                           | Amount requested              |
#### | loan_type        | VARCHAR2(30) |                           | Type (Microloan, SME, etc.)   |
#### | application_date | DATE         |                           | Date of application           |
#### | status           | VARCHAR2(20) |                           | Pending / Approved / Rejected |
### 3. REPAYMENT
#### | Column       | Type         | Key                           | Description              |
#### | ------------ | ------------ | ----------------------------- | ------------------------ |
#### | repayment_id | NUMBER       | PK                            | Unique payment record    |
#### | loan_id      | NUMBER       | FK  loan_application.loan_id | Related loan             |
#### | amount_paid  | NUMBER       |                               | Amount repaid            |
#### | payment_date | DATE         |                               | Date of payment          |
#### | method       | VARCHAR2(20) |                               | Cash, Mobile Money, Bank |
### 4. RISK_ASSESSMENT
#### | Column          | Type         | Key                           | Description                   |
#### | --------------- | ------------ | ----------------------------- | ----------------------------- |
#### | assessment_id   | NUMBER       | PK                            | Unique assessment record      |
#### | borrower_id     | NUMBER       | FK  borrower.borrower_id     | Borrower being scored         |
#### | loan_id         | NUMBER       | FK  loan_application.loan_id | Loan being assessed           |
#### | risk_score      | NUMBER       |                               | Calculated risk score (0–100) |
#### | risk_level      | VARCHAR2(10) |                               | Low / Medium / High           |
#### | assessment_date | DATE         |                               | Date of scoring               |
#### | officer_id      | NUMBER       | FK  loan_officer.officer_id  | Officer who assessed          |
### 5. LOAN OFFICER
#### | Column     | Type          | Key | Description          |
#### | ---------- | ------------- | --- | -------------------- |
#### | officer_id | NUMBER        | PK  | Unique officer ID    |
#### | full_name  | VARCHAR2(100) |     | Name of loan officer |
### 6. MANAGER
#### | Column     | Type          | Key | Description       |
#### | ---------- | ------------- | --- | ----------------- |
#### | manager_id | NUMBER        | PK  | Unique manager ID |
#### | full_name  | VARCHAR2(100) |     | Manager name      |
### 7. MANAGER APPROVAL
#### | Column          | Type          | Key                                | Description               |
#### | --------------- | ------------- | ---------------------------------- | ------------------------- |
#### | approval_id     | NUMBER        | PK                                 | Unique approval entry     |
#### | assessment_id   | NUMBER        | FK  risk_assessment.assessment_id | Assessment being approved |
#### | manager_id      | NUMBER        | FK  manager.manager_id            | Manager who approves      |
#### | approval_status | VARCHAR2(20)  |                                    | Approved / Rejected       |
#### | approval_date   | DATE          |                                    | Date of approval          |
#### | comments        | VARCHAR2(200) |                                    | Manager remarks           |
### 8. ACCOUNTANT
#### | Column        | Type          | Key | Description          |
#### | ------------- | ------------- | --- | -------------------- |
#### | accountant_id | NUMBER        | PK  | Unique accountant ID |
#### | full_name     | VARCHAR2(100) |     | Accountant name      |
### 9. DISBURSEMENT
#### | Column            | Type   | Key                           | Description                        |
#### | ----------------- | ------ | ----------------------------- | ---------------------------------- |
#### | disbursement_id   | NUMBER | PK                            | Unique disbursement ID             |
#### | loan_id           | NUMBER | FK  loan_application.loan_id | Loan being disbursed               |
#### | accountant_id     | NUMBER | FK  accountant.accountant_id | Accountant processing disbursement |
#### | disbursed_amount  | NUMBER |                               | Amount released                    |
#### | disbursement_date | DATE   |                               | Date of disbursement               |
## PHASE IV: Database Creation
#### In this step, the Oracle database environment was prepared for schema implementation. The correct pluggable database was activated and tested, and the project administrator account was verified with full privileges. Naming conventions and implementation scripts were prepared to ensure a smooth transition to the table implementation phase.
## PHASE V: Table Implementation & Data Insertion
<img width="1920" height="1080" alt="Create Project Admin User" src="https://github.com/user-attachments/assets/5337eb3d-c6cf-4f27-930a-a78cc88fc21f" />

### Table Creation:
#### TABLE 1: BORROWER
##### .Stores borrower personal details
##### .borrower_id uniquely identifies each borrower
##### .national_id is unique to avoid duplicates
#### TABLE 2: LOAN_APPLICATION
##### Each loan application belongs to one borrower
##### borrower_id links this table to Borrower
##### status stores values like Pending, Approved, Rejected
#### TABLE 3: REPAYMENT
##### Each repayment is linked to one loan application
##### repayment_amount stores how much was paid
##### repayment_date is automatically recorded
#### TABLE 4: RISK_ASSESSMENT
##### Each risk assessment belongs to one loan application
##### risk_score stores numerical risk value
##### risk_level can be Low, Medium, High
##### assessment_date records when assessment was done
#### TABLE 5: LOAN_OFFICER
##### Stores staff responsible for loan processing
##### email is unique per officer
##### officer_id uniquely identifies each loan officer
#### TABLE 6: MANAGER
##### Stores manager details
##### Managers are responsible for final review
##### manager_id uniquely identifies each manager
#### TABLE 7: MANAGER_APPROVAL
##### Links loan applications and managers
##### approval_status → Approved / Rejected
##### remarks stores comments from the manager
##### Records who approved what and when
#### TABLE 8: ACCOUNTANT
##### Stores accountant details
##### Accountants handle financial processing
##### accountant_id uniquely identifies each accountant
#### TABLE 9: DISBURSEMENT
