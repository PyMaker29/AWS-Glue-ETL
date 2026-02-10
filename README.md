# Hands-On Glue ETL 

This repository contains a complete, self-contained hands-on project to learn and practice serverless data integration and ETL workflows using sample sales data.

You will:
- Set up a basic folder structure in storage
- Catalog raw CSV files automatically
- Build and run transformation jobs to clean, join, and enrich data
- Explore data quality checks, visual preparation, scheduling, and workflow orchestration

All steps use console-based tools and the provided sample files — everything needed is included here.

## Project Goal

Transform raw customer and order data from simple CSV files into cleaned, enriched, and query-ready output using serverless ETL techniques.

## Sample Data

Two small datasets provided as CSVs:

**customers.csv**

| CustomerID | FirstName  | LastName     | FullName          |
|------------|------------|--------------|-------------------|
| 293        | Catherine  | Abel         | Catherine Abel    |
| 295        | Kim        | Abercrombie  | Kim Abercrombie   |
| 297        | Humberto   | Acevedo      | Humberto Acevedo  |

**orders.csv** (excerpt)

| SalesOrderID | SalesOrderDetailID | OrderDate  | DueDate    | ShipDate   | EmployeeID | CustomerID | SubTotal   | TaxAmt    | Freight   | TotalDue   | ProductID | OrderQty | UnitPrice | UnitPriceDiscount | LineTotal |
|--------------|--------------------|------------|------------|------------|------------|------------|------------|-----------|-----------|------------|-----------|----------|-----------|-------------------|-----------|
| 71782        | 110667             | 5/1/2014   | 5/13/2014  | 5/8/2014   | 276        | 293        | 33319.986  | 3182.8264 | 994.6333  | 37497.4457 | 714       | 3        | 29.994    | 0                 | 89.982    |
| 44110        | 1732               | 8/1/2011   | 8/13/2011  | 8/8/2011   | 277        | 295        | 16667.3077 | 1600.6864 | 500.2145  | 18768.2086 | 765       | 2        | 419.4589  | 0                 | 838.9178  |

## Getting Started

1. **Deploy base setup**  
   Use the included `setup-code.yaml` file to create:  
   - Storage bucket  
   - Service role  
   - Query workgroup  

   (Follow your console's stack creation process and upload this template.)

2. **Create folder structure in the bucket**  
   Make these folders manually:

   bucket-name/\
   ├── athena/\
   ├── processedData/\
   ├── rawData/\
   │   ├── customers/\
   │   │   └── customers.csv\
   │   └── orders/\
   │       └── orders.csv\
   ├── scriptLocation/\
   └── tmpDir/


3. **Add the sample files**  
Upload `customers.csv` → `rawData/customers/`  
Upload `orders.csv` → `rawData/orders/`

## Main Learning Path

### 1. Catalog the raw data
- Run a crawler over the `rawData` folder  
- Check the resulting database and tables  
- View inferred schemas and any partitions

### 2. Run transformation jobs (ETL)
- Create jobs that:  
  - Read from the cataloged raw tables  
  - Clean data (fix formats, handle missing values)  
  - Join customers with orders  
  - Add calculated fields  
  - Write cleaned results to `processedData/`  
- Use visual builder or generated code scripts

### 3. Check data quality
- Define simple rules (required fields, value ranges)  
- Run quality checks on raw and processed data  
- Review pass/fail results

### 4. Visual data preparation
- Use the visual prep tool to preview, filter, and clean samples  
- Export cleaned versions or use as starting point for jobs

### 5. Automate with triggers & workflows
- Create time-based or event-based triggers  
- Build multi-step workflows (e.g., crawl → transform → quality check)

### 6. Explore results
- Run queries against the processed output  
- Verify joins, calculations, and cleaning worked as expected

## Key Concepts Covered

- Serverless extract-transform-load pipelines  
- Automatic schema detection from files  
- Metadata catalog for tables and partitions  
- Reusable connection settings  
- Visual and code-based job creation  
- Data validation and anomaly detection  
- No-code data cleaning  
- Scheduling and dependency chaining

Everything here is designed to run locally within your own environment using the included samples and setup file.
