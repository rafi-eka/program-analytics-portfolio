# Data Dictionary — Cooperative Data Reconciliation

## 1. Purpose

This document defines the structure, meaning, and validation rules for the synthetic datasets used in the Cooperative Data Reconciliation & GIS project.

## 2. Dataset A: Cooperative Members

| Column | Data Type | Description | Validation Rule |
|---|---|---|---|
| member_id | Text | Unique identifier assigned to a cooperative member | Must be unique and non-empty |
| member_name | Text | Synthetic member name | Must not be empty |
| village | Text | Village where the member is registered | Standardized village naming |
| nik_status | Text | Availability status of the national identity number | Available or Missing |
| registration_date | Date | Date the member was registered | Valid date format |
| membership_status | Text | Current membership status | Active or Inactive |

## 3. Dataset B: Farm Mapping Records

| Column | Data Type | Description | Validation Rule |
|---|---|---|---|
| plot_id | Text | Unique identifier assigned to a mapped farm plot | Must be unique and non-empty |
| member_id | Text | Member identifier associated with the plot | Must match a member record where possible |
| village | Text | Village where the plot is located | Standardized village naming |
| mapped_status | Text | Status of the farm mapping record | Mapped or Pending |
| area_ha | Decimal | Recorded farm area in hectares | Must be greater than zero when available |
| polygon_available | Boolean | Indicates whether polygon geometry is available | True or False |

## 4. Key Matching Fields

- `member_id`: Primary matching key in this synthetic demonstration.
- `village`: Supporting field for identifying potential inconsistencies.
- `plot_id`: Identifier for an individual farm plot.

In real-world datasets, identifiers may be missing or inconsistent. Such records should be flagged for review rather than automatically assigned a match.

## 5. Data Quality Checks

- Missing required values.
- Duplicate member and plot identifiers.
- Member records without corresponding farm mapping records.
- Farm mapping records without corresponding member records.
- Inconsistent village names.
- Invalid or missing farm area values.
- Records awaiting mapping.

## 6. Privacy and Limitations

All data used in this project will be synthetic. No real national identity numbers, personal contact details, confidential membership records, or sensitive geographic coordinates will be included.

The matching rules are intended for demonstration and should be adapted to the data governance requirements of an actual program.
