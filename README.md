
# EMPLOYEE TURNOVER ANALYSIS


# DASHBOARD LINK: [Employee Turnover Dashboards.pdf](https://github.com/user-attachments/files/16870849/Employee.Turnover.Dashboards.pdf)


# Problem Statement:
An organization where I worked was experiencing increased employee turnover, particularly across specific departments and job roles. This trend was affecting productivity and increasing recruitment costs. However, the exact causes such as the impact of business travel, job tenure, performance ratings, and compensation are not well understood. 
This analysis is targeted to identify the key factors driving attrition to inform targeted retention strategies and optimize HR decision-making. Addressing these issues is essential to stabilizing the company's workforce and reducing turnover-related costs. 

# Description:
This is an employee report that provides insights into employee attrition, featuring departures by department, job roles affected, business travel imparts, and total years in the current role, aiding in workforce management and retention strategies. 

The second and third Dashboards focus is a report that consolidates employee data, featuring attrition by job level, overtime performance, ratings, monthly income, and attrition increase levels, offering critical insights for effective HR strategies and decision-making.

The Employee Turnover Analysis is designed to investigate and understand the patterns and causes of employee attrition within the organization. This comprehensive analysis focuses on several key aspects:

Departures by Department and Job Role:
Examines turnover rates across different departments and job roles to identify areas with the highest attrition. This helps pinpoint specific teams or positions that may require targeted interventions.

Impact of Business Travel:
Analyzes the relationship between the frequency and duration of business travel and employee turnover. This insight aims to determine if travel requirements are a contributing factor to higher attrition rates.

Total Years in Current Role:
Assesses the correlation between an employee's length of time in their current role and their likelihood of leaving the organization. This helps in understanding if shorter tenure is associated with higher turnover.

Performance Ratings and Overtime:
Review performance ratings and overtime hours to evaluate their impact on turnover. This includes examining if lower performance ratings or excessive overtime correlate with higher attrition.

Monthly Income and Job Level:
Investigates how variations in monthly income and job level affect employee retention. This helps determine if compensation and job hierarchy play significant roles in employee decisions to stay or leave.

Attrition Trends and Insights:
Consolidates the above data to identify trends and generate insights into the main drivers of turnover. This analysis provides actionable information to develop effective HR strategies and retention plans.

The goal of this analysis is to equip HR with data-driven insights that enable the creation of targeted strategies to reduce turnover, enhance employee satisfaction, and manage workforce costs effectively.

Let's get into it!

# Steps 1: Data preparation 
Downloaded and loaded the data into Power BI using the "Get Data" option, then I used the "transform" to check for null values, inconsistencies and data types. 
It happened that the dataset was clean, I only needed to change a few columns to their correct data type. 
    
    
![Subset of Dataset](https://github.com/user-attachments/assets/739f7333-023b-4743-b8de-044908b1c0ce)


# Step 2: Data Visualization 
This step provides an overview of all the dashboards I created for this report. The first is the demographic insights, the second and third focuses on the turnover analysis, and the final dashboard is dedicated to employee wellness. 

# Demographics
Step 1: 
Total employee; select a card visual, add the sum of employees, and customize the card to taste. 

    
    
![Card Visuals](https://github.com/user-attachments/assets/71772095-b3d1-497d-abf8-45cdbbfa50e6)

Employee count and Attrition count; to obtain these two values, I took the following steps 
* Navigated to the table view, clicked "new Column" and apply the following DAX for Attrition Count

      Attrition count = switch(true(), 'HR-Employee-Attrition' [Attrition] = "Yes", 1, 'HR-Employee-Attrition' [Attrition] = "No", 0,)

The above DAX will yield the desired results: if "Attrition" is "Yes" the count is 1; if it's "No" the count is 0. 
Summing all the 1 give the total attrition count that is 237, and subtracting 237 from the employee count yields the count of active employees that is 1233.

Below is the DAX used to get Active Employees:

    Active Employees = sum('HR-Employee-Attrition' [EmployeeCount] - sum ('HR-Employee-Attrition' [Attrition Count])

Then I dragged and dropped the sum of each into appropriate fields and customized the card outlook. 

Step 2: Total Attrition by Education field By stacked Bar Chart
I chose the stacked bar chart, dragged and dropped the "Attrition column" into the legend and the sum of "EmployeeCount" into the values option.
   
    
 ![Attrition by ](https://github.com/user-attachments/assets/f18086ff-2403-4a98-be09-56b4ef83968a) 

Step 3: Using data groups, I aggregated certain values together to form meaningful subsets. 
* Total Attrition by Age


   ![Attrition by age](https://github.com/user-attachments/assets/3099bea9-12fe-44ed-acb4-823ec49e2a8c)

* Total Attrition by Distance from home


  ![Attrion by distance from home](https://github.com/user-attachments/assets/298e7d52-51c5-4af9-aa97-97cff820ae21)

* Total Attrition by work-life balance


  ![Attrition by work life](https://github.com/user-attachments/assets/5d83e759-24ea-4f9f-8636-450fba2ec15a)

I created the above visuals using the concept of data grouping to organize and display data effectively. 

* Chose the columns I wanted to group, clicked on the "Data groups" option, and chose "New data groups" 
* Changed the group type from Bin to list. 
* For "Attrition by Work-Life Balance", I grouped 1 as "bad", 2 as "Average", 3 as "Good" and 4 as "Excellent" 
* A new group was created then I dragged and dropped into the appropriate fields. Then I visualize the data with a stacked bar chart. 
* Used the same grouping steps for "Attrition By Age" and "Attrition by Distance from Home" 
* For "Attrition by Distance from Home", 1-10 is near, 10 -20 is considered far, etc. 
* Then I dragged and dropped the data in appropriate fields and visual them. 

Step 4: Total Attrition by Marital Status using Clustered Bar Chart 
Y-axis = Marital Status
X-axis = Sum of Attrition Count 
Legend = Gender 
   
    

   ![Attrition by marital status](https://github.com/user-attachments/assets/77fa2818-50a1-409c-8027-b44537d2cfe5)

Step 5: Gender count using a donut chart 
Female Employee Attrition; 
Legend = Gender 
Values = sum of Attrition Count 
Filtered to show just female data. 
Followed the same step for Male Employee Attrition.
   
    

 ![Male and  Female Employee](https://github.com/user-attachments/assets/cd206754-77b6-4189-9fe9-9f5471c41fbd)


# Turnover Analysis 1
Step 1: Total Attrition by job role using a Stacked Bar chart
Y-axis = JobRole 
X-axis = sum of Attrition Count 
Legend = Gender 
  
    
    
![Attrition by job role](https://github.com/user-attachments/assets/8de85040-0230-4eef-af3e-a6d2f4f83788)

Step 2: Total Attrition by Business travel using a clustered bar chart 
Y-axis = BusinessTravel 
X-axis = sum of Attrition Count 
Legend = Gender 
   
    
    
![Att  by Bus  Tr](https://github.com/user-attachments/assets/817bee84-2a71-4d85-8a07-1e121af66ea7)

Step 3: Total Attrition by Department using a Donut chart 
Legend = Department 
Values = sum of Attrition Count 
    

![Attrition by department](https://github.com/user-attachments/assets/5540f933-e913-42d5-af6b-bcff7e4fa6ca)

Step 4: Total Attrition by Years in current role using a stacked column chart 
X-axis = YearsInCurrentRole
Y-axis = sum of Attrition Count 
Legend = Department 
    

![Att by Curr  Role](https://github.com/user-attachments/assets/4e620333-7fae-4f90-abb5-636e0ff46298)

Step 5: Total Attrition by Job Role
Presented in columns.
    

![column visual](https://github.com/user-attachments/assets/1fa5de1c-66ec-4b3f-a7af-b75d615465e8)

Step 6: Values on card visuals 
* 11.28 is the Average of Total working years
    

![Avg WY](https://github.com/user-attachments/assets/176dd4d2-f1b2-4fb0-9918-53206b4fe110)

* 9 is the count of Job Roles
   

 ![Job role count](https://github.com/user-attachments/assets/6fbc7e26-cde1-4a2e-9114-a3460c89c041)


# Turnover Analysis 2
Step 1: Attrition by Age and Gender using a Clustered Column chart 
X-axis = Age
Y-axis = Sum of Attrition Count 
Legend = Gender
    

![Att by age and gender](https://github.com/user-attachments/assets/1ab252a4-fbb8-40e9-ab9b-81411adb4ccb)  

Step 2: Total Attrition by Performancen Ratings using a Pie Chart  
Legend = PerformanceRating 
Values = Sum of Attrition Count 
The "Performance Rating" column with the values 3 and 4 has been grouped and modified as "Low" and "High" respectively. 
    

![Att by P R](https://github.com/user-attachments/assets/87cd0a0d-b570-4b10-a26a-538373228265) 

Step 3: Total Attrition by Overtime using a Stacked Column chart 
X-axis = Overtime
Y-axis = sum of Attrition Count 
   

 ![Total Att by O T](https://github.com/user-attachments/assets/d4e77ce6-71f9-452c-bf82-2ecf0fe71eca)

Step 4: Total Attrition by Job Level using a Funnel 
* This column was grouped into 5. 
* From 1 as "Entry Level"  to 5 as "Executive"
* Chose the funnel visual, dragged and dropped "Attrition Count" and "Job Level(grouped)" into appropriate fields.
    

![Att by J L](https://github.com/user-attachments/assets/550a1862-1e3c-4f2a-a786-2c3bb4b5b876) 

Step 5: Monthly Income and Attrition by Job Role using a Line chart 
X-axis = JobRole
Y-axis = Average of MonthlyIncome 
Secondary y-axis = sum of Attrition Count
    

![Monthly income and att count by JR](https://github.com/user-attachments/assets/09ff6e0c-552e-42e3-82d7-a010a035250a)


# Employee Wellness
Step 1: Total Attrition by Environmental Satisfaction using a Stacked column chart 
* Environmental Satisfaction is rated on a scale of 1 to 4. 
* Data grouping is used to group 1 as "Very Dissatisfied" to 4 being "Satisfied" 
X-axis = Environment Satisfaction 
Y-axis = sum of Attrition Count
   

 ![Att by envirin sat](https://github.com/user-attachments/assets/672f15b6-e6a0-4933-af3f-c85aaa075a21)

Step 2: Total Attrition by Job Involvement using a Stacked bar chart 
Data is grouped as Very Low, Low, Moderate, and High 
Y-axis =  Job Involvement 
X-axis = sum of Attrition Count
   

 ![Att by job In](https://github.com/user-attachments/assets/0d03fe57-1029-4d88-8bce-21e8c02b079b) 

Step 3: Relationship Satisfaction using a stacked column chart 
* Relationship Satisfaction is grouped into Very Dissatisfied, Dissatisfied, Satisfied, and Very Satisfied. 
X-axis = Relationship Satisfaction 
Y-axis = sum of Attrition Count 


Step 4: Performance Rating using a Stacked column chart 
* Performance Rating is grouped into High and Low. 
X-axis = Performance Rating 
Y-axis = sum of Attrition Count 
   

 ![Perf  Rating](https://github.com/user-attachments/assets/d97100c7-143f-4bcf-8274-d05e27df9096)

Step 5: Attrition by Work-Life Balance using a Pie Chart 
* Work-Life Balance is grouped into 4, 1 represents "Bad", 2 for "Average", 3 for "Good" and 4 as "Excellent" 
Legend = Work-Life Balance 
Values = sum of Attrition Count
    

![Att by W L](https://github.com/user-attachments/assets/be5e8576-77dd-46bb-87c4-9a72c45f9154) 

Step 6: Attrition by Job Satisfaction using a Stacked Column chart 
* Job satisfaction is grouped into 4 where 1 indicates "Very Dissatisfied" and 4 represents "Very Satisfied" and everything in between follows this other. 
Y-axis = sum of Attrition Count 
X-axis = Job Satisfaction
   

 ![Att by Job sat](https://github.com/user-attachments/assets/45ea082b-e82e-4dec-bede-beda64697fad)

Step 7: Card Visuals 
* 6.50k is the average of Monthly Income 
   

 ![Avg monthly income](https://github.com/user-attachments/assets/d79f2a0c-e178-444f-acd8-2eaff7443cb6)

* 65.89 is the average hourly rate
  

  ![Avg hourly rate](https://github.com/user-attachments/assets/8e43c155-83b9-4bf1-b857-14ea3c447fc4)
