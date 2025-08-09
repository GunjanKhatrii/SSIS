# SSIS Introduction Visuals and Diagrams

This document contains a collection of visuals and diagrams to help explain the foundational concepts of SQL Server Integration Services (SSIS). These visuals will be helpful for anyone looking to understand SSIS workflows, ETL processes, and package structures.

## 1. ETL Process Overview

The ETL process in SSIS consists of three main stages:

```mermaid
graph TB
    subgraph1[Data Sources] --> B[Extract]
    B -->C[Transform]
    subgraph subgraph1["Data Sources"]
        direction TB
        E[SQL Server]
        F[Excel]
        G[Flat Files]
    end
    C -->|Data Conversion| H[Load]
    C -->|Lookup| H
    H --> D[Data Warehouse]
```

- **Extract**: Retrieve data from various sources like SQL Server, Excel, and flat files.
- **Transform**: Apply transformations such as data conversions and lookups.
- **Load**: Store the transformed data into a data warehouse.

## 2. SSIS Package Workflow

An SSIS package is divided into **Control Flow** and **Data Flow** components:

```mermaid
flowchart TB
    subgraph subgraph1["Data Flow"]
        direction TB
        D[Source] --> E[Transformations]
        E --> F[Destination]
    end
    subgraph subGraph0["Control Flow"]
        B1[Execute SQL Task]        
        B3[Script Task]
        B4[File System Task]
        B2["Data Flow"]
    end
```

- **SSIS Package**: The overall container that includes all components.
- **Control Flow**: Manages the sequence of tasks (e.g., Execute SQL Task, Data Flow Task, Script Task, File System Task).
- **Data Flow**: A subsection of the Control Flow that manages the flow of data from sources to destinations, using transformations such as data conversions and lookups.

## 3. Control Flow vs. Data Flow

Control Flow and Data Flow are distinct components in SSIS. Below is a visual representation showing examples of each:

```mermaid
graph TB
    subgraph Control Flow
        A[Data Flow]
        B[Execute SQL Task]
        C[Script Task]
    end
    subgraph Data Flow
        D[Data Transformation]
        E[Lookup]
        F[Aggregation]
    end
```

- **Control Flow**: Examples include looping through files, executing SQL commands, or running custom scripts.
- **Data Flow**: Examples include transforming data, performing lookups, and aggregations.

## 4. Connections in SSIS

SSIS uses various connection types to integrate with different data sources:

- **OLE DB Connection**: For SQL Server databases.
- **Excel Connection**: To read from or write to Excel files.
- **Flat File Connection**: To handle CSV or text files.

Connections are used within the Data Flow to connect **Sources** and **Destinations**.

## 5. Error Handling in SSIS

Error handling is critical in SSIS to maintain data quality. The diagram below shows how to handle errors in a Data Flow Task:

```mermaid
flowchart TB
    A[Data Flow Task] --> B{Error Output?}
    B -->|Yes| C[Redirect to Error Output]
    C --> D[Flat File Destination]
    B -->|No| E[Continue Processing]
```

- **Error Output**: Errors are redirected to an output path for further review.
- **Flat File Destination**: Failed rows are saved for analysis.


## 6. Accounting/Finance Project

To demonstrate the concepts covered in this document, let's set up an accounting/finance example:

### Dataset Overview
The dataset will consist of the following:
- **SQL Server Database**: Contains financial transactions and customer details.
- **Excel File**: Contains exchange rates for different currencies.
- **Flat File (CSV)**: Contains a list of suppliers.

### Datasets
1. **Financial Transactions Table** (SQL Server):
   - **Table Name**: `financial_transactions`
   - **Columns**:
     - `transaction_id` (INT, Primary Key)
     - `customer_id` (INT, Foreign Key)
     - `transaction_date` (DATE)
     - `amount` (DECIMAL)
     - `currency` (VARCHAR)

2. **Customer Details Table** (SQL Server):
   - **Table Name**: `customer_details`
   - **Columns**:
     - `customer_id` (INT, Primary Key)
     - `customer_name` (VARCHAR)
     - `email` (VARCHAR)
     - `phone` (VARCHAR)

3. **Exchange Rates File** (Excel):
   - **File Name**: `exchange_rates.xlsx`
   - **Sheet Name**: `Rates`
   - **Columns**:
     - `currency_code` (VARCHAR)
     - `exchange_rate` (DECIMAL)
     - `effective_date` (DATE)

4. **Supplier List File** (CSV):
   - **File Name**: `suppliers.csv`
   - **Columns**:
     - `supplier_id` (INT)
     - `supplier_name` (VARCHAR)
     - `contact_name` (VARCHAR)
     - `phone` (VARCHAR)




