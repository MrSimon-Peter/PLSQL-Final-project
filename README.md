# PLSQL-Final-project
# Phase I
## Borrower Risk Rating System (BRRS) 
### 1. Introduction 
#### The Borrower Risk Rating System (BRRS) is a PL/SQL-based solution designed for microfinance institutions, SACCOs, savings groups, and small lending businesses. The system evaluates borrower performance by analyzing repayment behavior, outstanding loan balances, and patterns of lateness. Its primary objective is to help institutions identify high‑risk borrowers early and improve loan recovery. 
### 2. Problem Statement 
#### Many Rwandan lending institutions struggle with delayed repayments, loan defaults, and limited tools to objectively assess borrower risk. Traditional manual assessment is slow, inaccurate, and prone to errors. The BRRS system addresses this by providing automated borrower scoring and behavior monitoring. 
### 3. Project Objectives 
#### • To evaluate borrower repayment history using PL/SQL logic. 
#### • To assign risk ratings (Low, Medium, High) based on repayment patterns. 
#### • To store and analyze loan repayment data using Collections and Records. 
#### • To generate alerts for borrowers with high‑risk scores. 
#### • To produce automated risk reports for decision‑making. 
### 4. Proposed System Overview 
#### The BRRS system processes borrower information and repayment logs to compute a risk score ranging from 0 to 100. Based on the score, the system classifies borrowers into Low, Medium, or High risk groups. It uses PL/SQL procedures, validations, exception handling, and conditional logic to ensure consistent and reliable scoring. 
### 5. Database Schema
#### The system uses the following main tables: 
##### 1. BORROWERS(borrower_id, full_name, phone, registration_date) 
##### 2. LOANS(loan_id, borrower_id, loan_amount, issue_date, due_date, status) 
##### 3. REPAYMENTS(repayment_id, loan_id, amount_paid, payment_date, status) 
#### PL/SQL Collections store repayment histories during processing, and Records hold consolidated borrower assessment data. 
