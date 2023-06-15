# Data Engineer Tech Challenge TAP -2023

This test is split into 4 sections

1. **data pipelines**
2. **databases**
3. **system design**
4. **presentation**

## Submission Guidelines

Please create a Github repository containing your submission and send us an email containing a link to the repository.

Dos:

- Frequent commits
- Descriptive commit messages
- Clear documentation
- Comments in your code

Don'ts:

- Only one commit containing all the files
- Submitting a zip file
- Sparse or absent documentation
- Code which is hard to read

## Section 1: Data Pipelines

An e-commerce company requires that users sign up for a membership on their websire in order to purchase a product from the platform. As a data engineer under this company, you are required to design and implement a product pipeline to process the membership applications submitted by users. 

Applications are batched into a verying number of datasets and dropped into a folder on an hourly basis. You are required to set up a pipeline to ingest, clean, perform validity checks, and create membership IDs for successful applicants. Applications are considered successful if:
- mobile number is 8 digits (excluding country code)
- applicant is over 18 years old as of application year (i.e. 2023)
- applicant has a valid email (email ends with @emailprovider.com or @emailprovider.net)

You are required to format processed datasets in the following manner:
- Provide `first_name` and `last_name` columns
- Provide a `date_of_birth` column with the format **YYYYMMDD**
- Remove any rows which do not contain a name field. You are to treat this as unsuccessful applications.
- Create a new field `above_18` based on the applicant's birthday. Applications that don't fulfil the age criteria should be treated as unsuccessful applications. 
- Membership IDs for successful applications shuold be the applicant's last name, followed by a SHA_256 hash of his/her birthday, truncated to the first 5 digits of the hash (i.e .<last_name>_<hash(YYYYMMDD)>)

In addition, specifiy a **test plan** as you create the pipeline.

You are required to consolidate these datasets and output both successful and unsuccessful applications into **separate** folders for downstream follow-up by other engineers. As an additional requirement, these engineers should be alerted when the datsets have been processed. A message should be sent to the engineers regarding the quality of the recently processed dataset. Provide a sample of the alert message that will be produced on processing **application_dataset1.csv**. The message should **minimally** contain:
- number of rows processed
- number successful applications, include successful file name
- number of unsuccessful applications, include unsuccessful file name
- **include any other data quality metrics that you deem necessary**

_Note: please submit the processed dataset too._

## Section 2: Databases 

You are appointed by a car dealership to create their database infrastructure. There is only one store. In each business day, cars are being sold by a team of salespersons. Each transaction would contain information on the date and time of transaction, customer transacted with, and the car that was sold.

The following are known:

- Each car can only be sold by one salesperson.
- There are multiple manufacturers’ cars sold.
- Each car has the following characteristics:
- Manufacturer
- Model name
- Serial number
- Weight
- Price

Each sale transaction contains the following information:

- Customer Name
- Customer Phone
- Salesperson
- Characteristics of car sold

Set up a PostgreSQL database using the base `docker` image [here](https://hub.docker.com/_/postgres) given the above. We expect at least a `Dockerfile` which will stand up your database with the DDL statements to create the necessary tables. Produce entity-relationship diagrams as necessary to illustrate your design.

Your team also needs you to query some information from the database that you have designed. Note that the business requirements for the database is **not limited** to the 2 queries below, do design your database to account a wide range of business use cases. You are tasked to write a `sql` statement for each of the following task:

1. I want to know the list of our customers and their spending.

2. I want to find out the top 3 car manufacturers that customers bought by sales (quantity) and the sales number for it in the current month.

## Section 3: System Design

Prepare a presentation to your project team on how you plan to design data infrastructure on the cloud for a company whose main business is in processing images. Your role is the `Tech Lead` for this project.

The company has a web application which collects images uploaded by customers. The company also has a separate web application which provides a stream of images using a Kafka stream. The company’s software engineers have already some code written to process the images.

The company would like to save processed images for a minimum of **7 days for archival purposes**. Ideally, the company would also want to be able to have some Business Intelligence (BI) on key statistics including number and type of images processed, and by which customers.

Produce a system architecture diagram (e.g. Visio, Powerpoint) using any of the commercial cloud providers' ecosystem to explain your design. Please also indicate clearly if you have made any assumptions at any point.

Share about the `pros` and `cons` of your design to justify the decisions you have made.

## Section 6: What is Data Engineering?

You are tasked to help an agency to consolidate data to reduce data silos over a 3 months period. You will prepare a presentation to executive leadership to influence them to sponsor this data engineering initiative.

Your use-case can be any business function that you are familiar with. You should consider the different perspectives of the stakeholders. Do include a definition of the use case as well as be prepared to dive deep in technical considerations.
Choose one of the following topics and prepare the presentation in relation to the scenario above:

1. What is Data Engineering?
2. Explain the value of using any Data Engineering concepts or technology needed to the solve data silos.
3. What is a Data Warehouse?

This is a 5 minute face to face presentation. The audience includes senior managers, including directors from technical as well as non-technical backgrounds.

Management is interested to hear what can be done with data engineering to solve the problem described above. Please exercise your own judgement to make any reasonable assumptions and submit the powerpoint presentation.
