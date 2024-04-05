# Bank-Loan-Dashboard

### Dashboard Link : https://app.powerbi.com/reportEmbed?reportId=86b80952-3d95-4d6e-bc66-c4dfdd656110&autoAuth=true&ctid=9bb2360a-034c-4ecf-8228-aafe1a12b953


## Problem Statement

"Many banks struggle with efficiently managing and analyzing the vast amount of loan data they collect on a daily basis.
This leads to inefficiencies in decision-making processes and a lack of timely insights into loan performance and risk.
The objective of this Power BI project is to develop a solution that allows banks to effectively visualize and 
analyze loan data in real-time, enabling them to make informed decisions, mitigate risks, and improve overall loan management efficiency."


### Steps followed 

- Step 1 : Load data into Power BI Desktop, dataset is a csv file.
- Step 2 : As Data contains the columns related to the applicants, Income, loan
- Step 3 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.
- Step 4 :Also since by default, profile will be opened only for 1000 rows so you need to select "column profiling based on entire dataset".
- Step 5- Data has been cleanded after removing the null values.
- Step 6-: A new column "Good vs Bad Loan" added after goruping the loan status column. where charged off grouped into Bad loan and current and fully paid grouped as Good loan
- Step 7 : This is a three page report. Divided into Summary, Overview and Details.
- Step 8 : Three Table created one where all the measures placed. Second Calender Table and Third Category Table.        
- Step 9 : New measure was created to find Total Loan of Application.

Following DAX expression was written for the same,
        
        Total Loan Application = COUNT(financial_loan[id])
        
A card visual was used to represent for this.

![image](https://github.com/Ambikapandey0821/Bank-Loan-Dashboard/assets/162020155/96bb6b0b-7c54-4b98-b08d-3f4ab11ba2a4)

        
 - Step 10 : New measure was created to find the Total Funded Amount,
 
 Following DAX expression was written for this,
 
         Total Funded Amount = SUM(financial_loan[loan_amount])
 
 A card visual was used to represent this.
 
![image](https://github.com/Ambikapandey0821/Bank-Loan-Dashboard/assets/162020155/142c40a5-4998-4744-8dda-44cc48ccfa4c)

 - Step 11 : New measure was created to calculate the Total Amount Received.
 
 Following DAX expression was written to find this,
 
         Total Amount Received = SUM(financial_loan[total_payment])
 
![image](https://github.com/Ambikapandey0821/Bank-Loan-Dashboard/assets/162020155/bde0c121-dae1-400e-aac6-3fe706328dfe)

 
 - Step 12 : New measure was created to calculate the Average Interest Rate.
 
 Following DAX expression was written to find this,
 
         Avg Interest Rate = AVERAGE(financial_loan[int_rate])
 
![image](https://github.com/Ambikapandey0821/Bank-Loan-Dashboard/assets/162020155/286c7782-c408-42d3-8116-a58f6159a512)


 - Step 13 : New measure was created to calculate Average Debt to Income (DTI) .
 
 Following DAX expression was written to find this,
 
         Avg DTI Rate = AVERAGE(financial_loan[dti])
 
![image](https://github.com/Ambikapandey0821/Bank-Loan-Dashboard/assets/162020155/847d1faa-c089-475e-94bc-a2b26487d4b1)

 - Step 14 : New measure was created to calculate Good Loan %.
 
 Following DAX expression was written to find this
 
         Good Loan % = (CALCULATE([Total Loan Application],financial_loan[Good Loan vs Bad Loan]="Good Loan")/[Total Loan Application])
 
![image](https://github.com/Ambikapandey0821/Bank-Loan-Dashboard/assets/162020155/63948b1c-a591-4e35-a0db-94225d18b314)

 - Step 15 : 3 measure was created to calculate the good loan application, good loan funded amount and good loan received amount.
 
 Following DAX expression was written to find this
 
         Good Loan Application = CALCULATE([Total Loan Application],financial_loan[Good Loan vs Bad Loan]="Good Loan")
         Good Loan Funded Amount = CALCULATE([Total Funded Amount],financial_loan[Good Loan vs Bad Loan]="Good Loan")
         Good Loan Received Amount = CALCULATE([Total Amount Received],financial_loan[Good Loan vs Bad Loan]="Good Loan")
 
![image](https://github.com/Ambikapandey0821/Bank-Loan-Dashboard/assets/162020155/844b10e6-7a4c-4c41-ba99-20f8137ecf40)

 - Step 16 : New measure was created to calculate Bad Loan %.
 
 Following DAX expression was written to find this
 
         Bad Loan % = (CALCULATE([Total Loan Application],financial_loan[Good Loan vs Bad Loan]="Bad Loan")/[Total Loan Application])
 
![image](https://github.com/Ambikapandey0821/Bank-Loan-Dashboard/assets/162020155/bd61f70b-73e4-4952-acdc-163450cc7052)


 - Step 17 : 3 measure was created to calculate the Bad loan application, Bad loan funded amount and Bad loan received amount.
 
 Following DAX expression was written to find this
 
         Bad Loan Application = CALCULATE([Total Loan Application],financial_loan[Good Loan vs Bad Loan]="Bad Loan")
         Bad Loan Funded Amount = CALCULATE([Total Funded Amount],financial_loan[Good Loan vs Bad Loan]="Bad Loan")
         Bad Loan Received Amount = CALCULATE([Total Amount Received],financial_loan[Good Loan vs Bad Loan]="Bad Loan")
 
![image](https://github.com/Ambikapandey0821/Bank-Loan-Dashboard/assets/162020155/e83b9a4f-b83d-4351-a39a-b9f88018f366)

 - Step 18 : A Measure was created to to make the visuals dynamic.
  
 Following DAX expression was written to find this

          Status Category = VAR _selected_value_category = SELECTEDVALUE('Table'[Category])
          RETURN
              SWITCH(TRUE(),_selected_value_category="Total Loan Application", [Total Loan Application],
              _selected_value_category="Total Funded Amount", [Total Funded Amount],
              _selected_value_category="Total Amount Received", [Total Amount Received])


 - Step 19 : 2 Measures created to make the title dynamic.
 
 Following DAX expression was written to find this
 
         Dynamic Age title = SELECTEDVALUE('Table'[Category])&" by Age"
         Dynamic Purpose title = SELECTEDVALUE('Table'[Category]) &" by Purpose"



 
 # Report Snapshot (Power BI DESKTOP)

 
![image](https://github.com/Ambikapandey0821/HR-Analytics-Report/assets/162020155/bcf3b40e-e9c3-4aca-8c69-730c57b6edfa)

# Insights

A single page report was created on Power BI Desktop & it was then published to Power BI Service.

Following inferences can be drawn from the dashboard;

# Total Number of Employees = 1470

 -  Number of Employees (Male) = 882 

 -  Number of Employee (Female) = 588 

 -  Number of Employees Attrited (Male) = 150 (17 %)

 - Number of Employees Attrited (Female) = 87 (14.8 %)

 Thus, higher number of Male Employees Leaving the Organisation.
           

 # Some other insights
 
 # Attrition by Years at Company
 
 - 41.4% Employee leave the company with in the less than One Year.
 
 - 35.5 % Employee leave the company in the One Year.
 
 - 20.5 % Employee leave the company in the two Year.
 
   Thus, we can see that 0-1 year has the highest attrition rate. And if employees works for 5 years then attrition rate comes to 11%.
 
 # Age Group
 
 -  32.5 % Employees leave the Organisation of '18-25' age group.
 
 -  19 % Employees leave the Organisation of '26-35' age group.
 
 -  10.6 % Employees leave the Organisation of '36-45' age group.
 
 -  15.1 % Employees leave the Organisation of '46-55' age group.

 -  19.2 % Employees leave the Organisation of '55+' age group.
 
   Thus, we can see that '18-25' Agw group has the highest attrition rate. And '36-45' Age group has the lowest Attrition rate.
         
# Education Field

- 34 % Employee leave the orgnisation from life Science Education Field.

- 29.3 % Employee leave the orgnisation from Medical Field.

- 22 % Employee leave the orgnisation from Technical Field.

- 13 % Employee leave the orgnisation from Marketing Field.

- 2.67 % Employee leave the orgnisation from Human Recources Field.
       
  Thus, we can see that 34 %  Attrition is from life Science which is the highest attrition rate. And 2.67 % Employee leave the orgnisation from Human Recources Field which is lowest.

# Job Role and Job Satisfaction

- 1 is the lowest rating and 4 is the highest rating.
- Lowest Rating has the highest Attrition rate. and Highest rating has the lowest Attrition rate.
