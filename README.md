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
