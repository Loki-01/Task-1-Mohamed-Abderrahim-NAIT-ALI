Data Cleaning — E-Commerce Order Dataset

DecodeLabs Data Analytics Internship · Task 1
Author: Mohamed Abderrahim NAIT ALI


Overview

End-to-end data cleaning pipeline applied to a raw e-commerce order dataset of 1,200 records and 14 columns. The task covers pre-cleaning auditing, structured remediation across six change records, post-cleaning validation, and delivery of a production-ready Excel file with a documented change log.


Repository Structure

├── Project_1DecodeLabs.ipynb                  # Full cleaning notebook
├── Dataset for Data Analytics.xlsx            # Raw source data (input)
└── Dataset_for_Data_Analytics_CLEANED.xlsx    # Cleaned output (2 sheets)
    ├── Cleaned_Data                           # Final cleaned dataset
    └── Change_Log                             # Audit trail (CR001–CR006)


Dataset

PropertyValueRecords1,200 ordersColumns14FormatExcel (.xlsx)

ColumnTypeNotesOrderIDStringUnique order identifierDateDateOrder dateCustomerIDStringCustomer identifierProductStringProduct categoryQuantityIntegerUnits orderedUnitPriceFloatPrice per unitTotalPriceFloatFinal order valueShippingAddressStringDelivery addressPaymentMethodStringPayment channelOrderStatusStringDelivered / Cancelled / Returned etc.TrackingNumberStringShipment trackingItemsInCartIntegerCart size at time of orderCouponCodeStringDiscount code (309 originally missing)ReferralSourceStringAcquisition channel


Cleaning Pipeline

Phase 1 — Pre-Cleaning Audit

Baseline metrics captured before any modifications:

CheckResultTotal rows1,200Missing values (CouponCode)309Duplicate rows (all columns)0Duplicate OrderIDs0

Phase 2 — Cleaning Operations (Change Log)

Change IDOperationImpactCR001Imputed 309 missing CouponCode values with 'NONE'0 nulls remaining; preserves structural meaning (no coupon applied)CR002Checked for exact duplicate rows across all 14 columns0 foundCR003Checked OrderID for duplicate unique identifiers0 found; 0 remainingCR004Standardized Date column to ISO 8601 format YYYY-MM-DD0 malformed dates remainingCR005Stripped whitespace from 6 text columnsAll text fields normalizedCR006Rounded UnitPrice and TotalPrice to 2 decimal placesNumeric precision standardized

Text columns normalized in CR005: Product, PaymentMethod, OrderStatus, ShippingAddress, ReferralSource, CouponCode.

Phase 3 — Post-Cleaning Validation

CheckResultTotal rows1,200 (no records lost)Missing values0 across all columnsDuplicate OrderIDs0Malformed dates0


Output

The cleaned dataset is saved to Dataset_for_Data_Analytics_CLEANED.xlsx with two sheets:

Sheet 1 — Cleaned_Data: The full 1,200-row dataset after all cleaning operations, ready for analysis or downstream modeling.

Sheet 2 — Change_Log: Structured audit trail with Change ID, description of each operation, measured impact, and resolution status — all marked Resolved.


How to Run

Requirements

bashpip install pandas openpyxl

Execution

bash# Place 'Dataset for Data Analytics.xlsx' in the same directory as the notebook
# Open in Google Colab or Jupyter and run all cells top to bottom
# Output file will be saved to the working directory


Tech Stack

ToolPurposePythonCore languagepandasData loading, cleaning, validationopenpyxlExcel read/write (.xlsx)Google ColabExecution environment


Author

Mohamed Abderrahim NAIT ALI
Energy and Mechanical Engineer · Data Scientist
USTHB Algeria · GomyCode Data Science Bootcamp · DecodeLabs Batch 2026
