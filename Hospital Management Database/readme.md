# Database Diagnosis: Exploring the Anatomy of Healthcare Data

![Healthcare image](https://github.com/antonionunnally/SQL/assets/97487571/c025be70-139b-4000-96ad-7c90de4066bd)

## Table of Contents
- [Introduction](#introduction)
- [Tools used](#tools-used)
- [Data Sourcing](#data-sourcing)
- [Entity Relationship Diagram](#entity-relationship-diagram)
- [Data Dictionary](#data-dictionary)
- [SQL Queries](#sql-queries)


## Introduction:

Hospital Database Management System (DBMS) is a comprehensive SQL project designed to streamline and optimize the management of hospital operations. This project aims to provide an efficient and user-friendly solution for storing, retrieving, and manipulating various types of healthcare-related data.

**_Disclaimer_**: All dataset and information reflected in this report does not represent any company, institution, or country, but just a dummy dataset to demonstrate the capabilities of Microsoft SQL Server

### Tools used:
- Micrcosoft Excel 
- Microsoft SQL Server


### Data Sourcing
We have 9 tables 
- FactTable
- DimPatient
- DimTransaction
- DimPhysician
- DimPayer
- DimLocation
- DimDiagnosisCode
- DimCptCode
- DimDate


### Entity Relationship Diagram

![ERD Model](https://github.com/antonionunnally/SQL/assets/97487571/9c57dfe7-d9b9-451d-a1f6-99dccd5d66a2)


### Data Dictionary
The data dictionary consist of 43 rows. Attached is a Pdf file.
[Data Dictionary.pdf](https://github.com/antonionunnally/SQL/files/13814890/Data.Dictionary.pdf)


### SQL Queries

**Question 1. How many rows of data are in the FactTable that include a Gross Charge greater than $100?**

![Question 1](https://github.com/antonionunnally/SQL/assets/97487571/3ab6b5e0-0cbd-4e7c-b297-a71db585a9dd)

**Question 2. How many unique patients exist is the Healthcare_DB**

![Question 2](https://github.com/antonionunnally/SQL/assets/97487571/c61f588f-a156-467e-8477-c6881d1ca8e7)


**Question 3.How many CptCodes are in each CptGrouping**

![Question 3](https://github.com/antonionunnally/SQL/assets/97487571/a2308467-484a-4586-b179-87b18b54b975)


**Question 4a.How many physicians have submitted a Medicare insurance claim?**

![Question 4a](https://github.com/antonionunnally/SQL/assets/97487571/09f42ad6-58b0-4768-8bee-250817e337ed)

**Question 4b.How many total physicians by Payer Name?**

![Question 4b](https://github.com/antonionunnally/SQL/assets/97487571/97dcb958-92d6-49f8-90b3-0e6840b9006a)


**Question 5a. Calculate the Gross Collection Rate (GCR) for each LocationName** 
- GCR = Payments divided GrossCharge

![Question 5](https://github.com/antonionunnally/SQL/assets/97487571/9fb7d058-d053-4c67-baa8-7115c18e6c4a)


**Question 6. How many CptCodes have more than 100 units?**

![Question 6](https://github.com/antonionunnally/SQL/assets/97487571/61d544a7-cc2a-4381-8879-21bc0326ac67)


**Question 7a. Find the physician specialty that has received the highest amount of payments.**

![Question 7a](https://github.com/antonionunnally/SQL/assets/97487571/33255e4b-0803-445c-9e53-20f6b71f741e)


**Question 7b. Then show the payments by month for this group of physicians.**

![Question 7b](https://github.com/antonionunnally/SQL/assets/97487571/d0e31b3e-e474-42a7-9f98-92e23a8651a5)

**Question 8. How many CptUnits by DiagnosisCodeGroup are assigned to a "J code" Diagnosis (these are diagnosis codes with
the letter J in the code)?**

![Question 8](https://github.com/antonionunnally/SQL/assets/97487571/3e32c140-da0c-4157-b7e8-2ee5f6104e29)


**Question 9.You've been asked to put together a report that details
Patient demographics. The report should group patients
into three buckets: Under 18, between 18 - 65, & over 65**.

Please include the following columns:
- First and Last name in the same column
- Email
- Patient Age
- City and State in the same column


![Question 9](https://github.com/antonionunnally/SQL/assets/97487571/c1faabaa-4335-4071-a213-d883a288efb2)


**Question 10a. How many dollars have been written off (adjustments) due
to credentialing (AdjustmentReason )?**

![Question 10a](https://github.com/antonionunnally/SQL/assets/97487571/7bfd547c-9838-45af-a780-963bfd34677f)



**Question 10b. Which location has the highest number of credentialing adjustments? /How many physicians at this location have been impacted by
credentialing adjustments?**

![Question 10b](https://github.com/antonionunnally/SQL/assets/97487571/ff90b0a7-4769-4cf1-9353-82d6e78c8c2d)

