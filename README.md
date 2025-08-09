# Accounting/Finance Project

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




