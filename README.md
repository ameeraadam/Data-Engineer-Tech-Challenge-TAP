# Data Engineer Tech Challenge TAP -2023

This test is split into 6 sections

1. **data pipelines**
2. **databases**
3. **system design**
4. **charts & APIs**
5. **machine learning**
6. **presentation**

## Submission Guidelines

Please create a Github repository containing your submission and send us an email containing a link to the repository.

Dos:

- Frequent commits
- Descriptive commit messages
- Clear documentation
- Comments in your code

Donts:

- Only one commit containing all the files
- Submitting a zip file
- Sparse or absent documentation
- Code which is hard to read

## Section 1: Data Pipelines

The objective of this section is to design and implement a solution to process a data file on a regular interval (e.g. daily). Assume that there are 2 data files `dataset1.csv` and `dataset2.csv`, design a solution to process these files, along with the scheduling component. The expected output of the processing task is a CSV file including a header containing the field names.

You can use common scheduling solutions such as `cron` or `airflow` to implement the scheduling component. You may assume that the data file will be available at 1am everyday. Please provide documentation (a markdown file will help) to explain your solution.

Processing tasks:

- Split the `name` field into `first_name`, and `last_name`
- Remove any zeros prepended to the `price` field
- Delete any rows which do not have a `name`
- Create a new field named `above_100`, which is `true` if the price is strictly greater than 100

_Note: please submit the processed dataset too._

## Section 2: Databases

### Option 1

You are appointed by the applications team in an e-commerce company to create a database infrastructure for their sales transactions. Purchases are being made by members of the e-commerce company on their website. A member can purchase any number of products within a single transaction.

The following are known for each product listed for sale on the e-commerce website:
- Item Name
- Manufacturer Name
- Cost
- Weight (in kg)

Each transaction made by a member should minimally contain the following information:
- Membership ID
- Item(s) bought
- Date of transaction

i) Draw an entity-relationship diagram to represent the data models required to fulfill the above requirements. **Please submit your design in an image format (e.g. `.jpg`/`.png`)**

ii) You are also tasked to build and deploy your design in i). Set up your database using PostgreSQL with the Docker [image](https://hub.docker.com/_/postgres) provided. **You are required to submit the DDL statements for the tables, and the necessary scripts to deploy the Docker image (minimally a Dockerfile)**.

iii) Additionally, you are requested to justify your database design by providing the relevant SQL queries to satisfy some of their requirements. Some of these requirements include:
- Get the total cost of item(s) purchased by a member in a transaction
- A manufacturer rebranding resulted in a change of the manufacturer's name only

**Please submit the queries for use to satisfy the above scenarios.**

### Option 2

You are tasked to design and create the database system required for analytical use cases. Your users are asked to generate reports on HDB resale prices provided in [data.gov.sg](https://data.gov.sg/dataset/resale-flat-prices), to provide a statistical overview of housing prices in Singapore.

Some of the use cases the users are required to report on can be:
- What are the average resale prices of each flat type in each town?
- What are the top 10 towns that has resale flats with the oldest lease commence date (by year)


**Note**:
For convenience of testing, the following constraints are given:
- Date range can be from January 2022 to December 2022 (inclusive)
- For questions towards time factors, the column {remaining_lease} can be disregarded. We will only look at the lease by year.


i) Draw an entity-relationship diagram to represent the data models required to fulfill the above requirements. **Please submit your design in an image format (e.g. `.jpg`/`.png`)**

ii) You are also tasked to build and deploy your design in i). Set up your database using PostgreSQL with the Docker [image](https://hub.docker.com/_/postgres) provided. **You are required to submit the DDL statements for the tables, and the necessary scripts to deploy the Docker image (minimally a Dockerfile)**.

iii) **Please submit the relevant SQL queries to fulfill the use cases listed above.**

## Section 3: System Design

You are given the role of the `Tech Lead` of a project for a company whose main business is in processing sensor data and ground surveys. 
This project aims to redesign and shift all of its existing on-premise infrastructure onto the cloud. 
Prepare a presentation to your technical project team on how you plan to design the data 
infrastructure on the cloud provider of your choice.

The company receives data from multiple sources. There are 2 data sources of data:

1. Sensor data from external sites deliver data to the company via the use of data streams. 
The stream application is hosted by the company. *Assume there are only 
1-2 sensor sites pushing data to Kafka consumer(s) in the application.*

2. There are surveyors tasked to manually upload survey data on a regular basis. They would upload data to the system 
via API through a web application hosted by the company.

As the technical lead for the engineering project within the company, you are required to design the system architecture
depicting the end-to-end flow of every pipeline on the cloud. 
The architecture should **minimally** address the requirements/concerns below:


- Code has already been written by the company's software engineers to process the data. 
This code also has to be migrated and hosted on the cloud. 

- For archival purposes, **any data** (raw and processed) has to be stored in the cloud environment for 60 days, 
after which it has to be purged from the environment for compliance and privacy. 

- The cloud environment should also host a Business Intelligence resource where the company's analysts can access and 
perform analytical computation on the data stored.

- To ensure that the system is robust, the team would require components that enable effective monitoring, 
and ease of deployment for engineers.

You are required to produce a system architecture diagram (e.g. `Visio`, `Powerpoint`, `draw.io`) for the above. 
You may use any of the cloud providers (e.g. `AWS`, `Azure`, `GCP`) to host your environment. 
Do indicate any assumptions made, and provide detailed explanations to your design considerations.

## Section 4: Charts and APIs

Your team decided to design a dashboard to display the statistic of COVID19 cases. You are tasked to display one of the components of the dashboard which is to display a visualisation representation of number of COVID19 cases in Singapore over time.

Your team decided to use the public data from https://documenter.getpostman.com/view/10808728/SzS8rjbc#b07f97ba-24f4-4ebe-ad71-97fa35f3b683.

Display a graph to show the number cases in Singapore over time using the APIs from https://covid19api.com/.

_Note: please submit screenshots of the dashboard_

## Section 5: Machine Learning

Using the dataset from https://archive.ics.uci.edu/ml/datasets/Car+Evaluation, create a machine learning model to predict the buying price given the following parameters:

- Maintenance = High
- Number of doors = 4
- Lug Boot Size = Big
- Safety = High
- Class Value = Good

## Section 6: What is Data Engineering?

You are tasked to help an agency to consolidate data to reduce data silos over a 3 months period. You will prepare a presentation to executive leadership to influence them to sponsor this data engineering initiative.

Your use-case can be any business function that you are familiar with. You should consider the different perspectives of the stakeholders. Do include a definition of the use case as well as be prepared to dive deep in technical considerations.
Choose one of the following topics and prepare the presentation in relation to the scenario above:

1. What is Data Engineering?
2. Explain the value of using any Data Engineering concepts or technology needed to the solve data silos.
3. What is a Data Warehouse?

This is a 5 minute face to face presentation. The audience includes senior managers, including directors from technical as well as non-technical backgrounds.

Management is interested to hear what can be done with data engineering to solve the problem described above. Please exercise your own judgement to make any reasonable assumptions and submit the powerpoint presentation.
