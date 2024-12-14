# Exploratory Data Analysis

# Project Description:
The project aims to find employee remuneration and expenses to find out trends, outliers, and key patterns. This will involve a deep analysis of the dataset using statistical and visualization techniques to understand the distribution of salaries and expenses for various departments and job roles.
 
 
# Project Title:
Exploratory Data Analysis of Employee Remuneration and Expenses

# Objective:
To extract knowledgeable insights from employee remuneration and expenses data to help in making decisions and highlight areas needing further analysis.

# Dataset:
A dataset containing 2023 employee data, including:
•	Year
•	Name
•	Department
•	Job title
•	Remuneration
•	Expenses

# Methodology:
# 1.	Data Ingestion: 
•	Store the data which is in raw format in S3 bucket named “emp-rem-exp-raw-vij”.
•	Upload the dataset excel file
# 2.	Data Profiling: 
•	Leverage AWS Glue DataBrew to analyze the dataset.
•	Connect the dataset “employee-remuneration-and-expenses-earning-over-75000”.
•	Generate a report of count of rows and columns, missing values and duplicate values.
•	Save the end result under “Data-Profiling” folder in transform “emp-rem-exp-trf-vij” bucket.
# 3.	Data Cleaning:
•	Create a project “emp-rem-exp-prj-vij” in AWS Glue DataBrew.
•	Remote white spaces and any unwanted details.
•	Fill any empty spaces
•	Remove any null values
•	Changed the type of Year from String to Integer.
•	Removed Whitespaces from Department and Title
•	Changed type of Remuneration to Integer
•	Changed type of Expenses to Integer
•	Save the recipe steps
•	Run the job to run the cleaning process
•	The output will be stored in Data Cleaning folder in “emp-rem-exp-trf-vij” bucket in PARQUET format in snappy compression type.
# 4.	Data Pipeline: 
•	Design an ETL pipeline using AWS Glue Studio.
•	Give a name to the file – “emp-rem-exp-desc-etl-vij”
•	Load data from Data Cleaning/System from “emp-rem-exp-trf-vij”
•	Drop “name” column
•	Use transform function with filter “max” remuneration for department and “min” remuneration for department
•	Apply inner join option
•	Calculate both minimum and maximum remuneration for all the departments
•	Store the end results in transform bucket.

# Tools and Technologies:
•	AWS S3: Data Storage
•	AWS Glue DataBrew: Data Profiling and Data Cleaning
•	AWS Glue Studio: ETL Pipeline

# Deliverables: 

•	Cleaned and processed dataset stored in AWS S3
•	Data profiling summary report
•	ETL pipeline documentation for exploratory analysis
•	Visualizations comparing minimum and maximum remuneration across all departments
•	Analysis report detailing insights and findings from the exploratory analysis
•	Recommendations for further analysis or potential implications based on the findings

# Descriptive Analysis

# Project Description:
The goal is to provide a statistical summary of employee data to understand the distribution of remuneration and expenses. The focus is on identifying central tendencies, variability, and any significant patterns across the dataset.
 
 
# Project Title:
Descriptive Statistical Analysis of Employee Data

# Objective:
To summarize and describe the main features of the dataset quantitatively and visually.

# Dataset:
Contains detailed information about employee remuneration and expenses for the year 2023.
•	Year
•	Name
•	Department
•	Job title
•	Remuneration
•	Expenses

# Methodology:
# 1.	Data Collection and Preparation:
•	Load the dataset using AWS services 
# 2.	Data Ingestion:
•	Store the data in S3 bucket “emp-rem-exp-raw-vij”
# 3.	Data Profiling:
•	Utilize AWS Glue DataBrew to analyze the dataset.
•	Generate a report including rows, columns, missing cells and duplicate values.
# 4.	Data Cleaning:
•	Create a project “emp-rem-exp-prj-vij” in AWS Glue DataBrew
•	Changed the type of Year from String to Integer.
•	Removed Whitespaces from Department and Title
•	Changed type of Remuneration to Integer
•	Changed type of Expenses to Integer
•	Save the cleaning steps as recipe
# 5.	Data Pipeline:
•	Design an ETL pipeline using AWS Glue
•	Load cleaned data from transform bucket “emp-rem-exp-trf-vij”
•	Aggregate data based on “total expenses” by “department”
•	Calculate the total expenses made by each and every department
•	Store the end result in transform bucket
# 6.	Data Visualization:
•	Create a chart showcasing total expenses by each and every department

# Tools and Technologies:
•	AWS S3: Data storage
•	AWS Glue DataBrew: Data profiling and cleaning
•	AWS Glue: ETL pipeline design and execution
•	AWS CloudWatch: Monitoring and logging

# Deliverables:
1.	Cleaned and processed dataset stored in AWS S3
2.	ETL pipeline documentation
3.	Summary report of data profiling results
4.	Visualizations of sum of total expenses across all departments
5.	Analysis report detailing insights and findings from the descriptive analysis
6.	Recommendations for further analysis or potential business implications based on the findings

# Data Quality Control

# Project Description:
Ensuring the dataset meets quality standards by implementing control measures and audits to validate data accuracy and integrity.
 

# Project Title:
Data Quality Control for Employee Remuneration Dataset

# Objective:
To implement robust checks for data accuracy, completeness, and reliability.

# Background:
High-quality data is essential for meaningful analysis and decision-making. The current dataset requires quality checks to avoid misinterpretation.

# Scope:
Focuses on remuneration and expenses data for the year 2023, addressing all observed inconsistencies.

# Dataset:
Contains detailed information about employee remuneration and expenses for the year 2023.
•	Year
•	Name
•	Department
•	Job title
•	Remuneration
•	Expenses

# Methodology:
# Data Enriching:
•	Create a table using Amazon DynamoDB to create a table “emp-rem-exp-table-vij”.
•	Export the end result to the raw bucket
•	Use AWS Glue Crawler to create metadata tables in Data Catalog from the end result
•	Standardize all the schemas using Glue transformations for seamless integration. 
# Data Governance:
•	Apply AWS Glue option to Evaluate Data Quality to assess completeness and uniqueness metrics, referencing expenses.
•	Use ETL pipelines to route "passed" and "failed" data into separate S3 buckets for transparency.
•	Implement governance rules ensuring adherence to industry and regulatory standards.
# Data Protection:
•	Use AWS Key Management Service (KMS) to create and manage encryption keys.
•	Secure S3 buckets with customer-managed KMS keys.
•	Establish cross-region replication rules with encryption for disaster recovery.
# Data Observability:
•	Use Amazon CloudWatch to create dashboards.
•	Number of objects in S3 buckets.
•	Bucket sizes and estimated total charges.
•	Logs of system activity and errors.
•	Configure alarms for deviations in storage usage or ETL pipeline performance.
•	Allow for detailed tracking of AWS Glue jobs and S3 operations for comprehensive observability.


 
# Tools and Technologies:
•	Data Enriching: AWS DynamoDB, AWS Glue Crawler
•	Data Governance: AWS Glue, S3, AWS Glue Data Quality
•	Data Protection: AWS KMS, S3 Bucket Policies
•	Data Observability: Amazon CloudWatch, AWS Glue Logs

# Deliverables:
1.	A consolidated, enriched dataset with enhanced metadata stored in S3.
2.	ETL pipeline diagrams illustrating governance workflows.
3.	Secure and replicated S3 buckets with encryption policies.
4.	CloudWatch dashboards for real-time data monitoring.
5.	Comprehensive documentation detailing enrichment, governance, protection, and observability methods.

# Timeline:
2 weeks for quality control measures.

