![image](https://github.com/Ambikapandey0821/Bank-Loan-Dashboard/assets/162020155/a5d0c18b-de59-4aa3-98f3-48425ba05350)# Bank-Loan-Dashboard

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
      Note - Debt-to-income ratio (DTI) compares how much you owe each month to how much you earn. Specifically, it's the percentage of your gross monthly income (before taxes) that goes towards payments for rent, mortgage, credit cards, or other debt.
 
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
         Dynamic Month title = SELECTEDVALUE('Table'[Category]) &" by Month"

 
 # Report Snapshot (Power BI DESKTOP)

 
![image](https://github.com/Ambikapandey0821/Bank-Loan-Dashboard/assets/162020155/7e802851-1e86-4f5d-b853-dd9ee897d8c0)

![image](https://github.com/Ambikapandey0821/Bank-Loan-Dashboard/assets/162020155/1580d493-9905-47d0-86ba-16821750aebd)

![image](https://github.com/Ambikapandey0821/Bank-Loan-Dashboard/assets/162020155/b22d78a5-cbd2-4d54-96c0-1cf1b73e8f4f)

# Insights

Following inferences can be drawn from the dashboard;

# Total Number of Loan Applications = 38.6K

 - Total Amount Funded = 435.8 M 

 - Total Amount Received = 473.1 M 

 - Average Interest Rate = 12 %

 - Average DTI  = 13.3 %
           
 # Loan
 
 - Good Loab = 86.2%
 - Bad Loan = 13.8%
 
 
 # Tenure
 
 -  73 % Loans are issued for 36 Months
 -  27 % Loans are issued for 60 Months

         
# Purpose - Top 5 Purpose for loans 

- Debt Consolidation
- Credit card
- Others
- Home Improvement
- Major Purchase


# States - Top % States for Loans

- CA
- NY
- FL
- TX
- NJ
